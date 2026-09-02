# Portfolio — Robotics, Control Systems & Vehicle Dynamics

Interactive portfolio of graduate control-systems and vehicle-dynamics work,
ported from MATLAB/Simulink coursework into simulations that run live in the
browser.

The home page is a 3D sphere of project cards. Each card runs its project's
actual simulation continuously — no click required. Selecting a card rotates
that node to face you and opens its description; from there you can open the
full project write-up.

## Running it

No build step, no dependencies, no server required.

```bash
open index.html
```

Or, if you prefer to serve it (identical result):

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000

## Structure

```
index.html                        # sphere home page
projects/
  double-pendulum.html            # chaotic dynamics — Lagrangian + RK4
  robot-navigation.html           # stochastic shortest path — dynamic programming
```

All links are relative, so the site works identically when opened as a local
file or served from a web root.

## The simulations

Everything is computed live in the browser — nothing is pre-rendered video or
canned animation.

- **Double Pendulum** — Euler–Lagrange equations of motion for two coupled
  rods, integrated with a 4th-order Runge–Kutta solver. Two pendulums run the
  identical equations from starting angles differing by 0.05°, which is enough
  to make them diverge completely within seconds.

- **Robot Navigation** — A 41×41 grid where each move can slip sideways, and
  the slip probability depends on the previous move. The optimal policy is
  solved by backward induction over the full state space, then verified by
  continuous Monte Carlo rollouts.

Five further projects (adaptive cruise control, a 14-DOF vehicle model, active
suspension, aircraft pitch control, and a solar racing vehicle) appear on the
sphere as in-progress placeholders and are not yet published.

## Implementation notes

Plain HTML, CSS and JavaScript with no frameworks or libraries. The 3D sphere —
point distribution, rotation, perspective projection, depth sorting and
hit-testing — is written directly against a 2D canvas rather than using a WebGL
library.

Only front-facing cards are rendered and stepped; cards rotating out of view
are hidden and their simulations paused, so cost stays flat regardless of how
many projects are on the sphere.

## Publishing

To put this on GitHub Pages: push to a GitHub repository, then in
**Settings → Pages** select the `main` branch and the root folder. No
configuration files or build step are needed.
