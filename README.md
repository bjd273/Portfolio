# Portfolio — Robotics, Control Systems & Vehicle Dynamics

**Live: https://bjd273.github.io/Portfolio/**

Interactive portfolio of graduate control-systems and vehicle-dynamics work,
ported from MATLAB/Simulink coursework into simulations that run live in the
browser.

The home page is a 3D sphere of project cards. Each card runs its project's
actual simulation continuously — no click required. Selecting a card rotates
that node to face you and opens its description; from there you can open the
full project write-up.

## The projects

All seven ported from real MATLAB/Simulink coursework, each running its own
live physics or control simulation in-browser — not a screenshot or a canned
animation.

- **Double Pendulum** — Euler–Lagrange equations of motion for two coupled
  rods, integrated with a 4th-order Runge–Kutta solver. Two pendulums run the
  identical equations from starting angles differing by 0.05°, enough to make
  them diverge completely within seconds.

- **Robot Navigation** — A 41×41 grid where each move can slip sideways, and
  the slip probability depends on the previous move. The optimal policy is
  solved by backward induction over the full state space, verified by
  continuous Monte Carlo rollouts.

- **Adaptive Cruise Control** — A PID spacing controller proven against every
  vehicle within ±7% mass and ±30% drag of nominal, driven by the real
  recorded lead-vehicle speed trace from the original test.

- **14-DOF Vehicle Model** — A car corners on its actual Magic Formula tire
  curve — real mass, inertia, and geometry extracted from the reference
  model — until the front tires visibly run out of grip.

- **Active Suspension** — A quarter-car LQR compensator, its Riccati equation
  solved and verified live in-browser, trading ride comfort for suspension
  control on a single dial.

- **Aircraft Pitch Control** — A lightly-damped short-period pitch response
  tracking a real ±15°/s command through a real ±20° elevator limit, held by
  LQR with integral action.

- **Solar Racing Vehicle** — A 255 kg solar racer's launch, genuinely
  traction-limited before it becomes power-limited, integrated live from rest
  rather than estimated from a single terminal value.

## Implementation notes

Plain HTML, CSS and JavaScript — no frameworks, build step, or dependencies.
The 3D sphere — point distribution, rotation, perspective projection, depth
sorting and hit-testing — is written directly against a 2D canvas rather than
using a WebGL library.

Only front-facing cards are rendered and stepped; cards rotating out of view
are hidden and their simulations paused, so cost stays flat regardless of how
many projects are on the sphere.

## Structure

```
index.html                        # sphere home page
projects/
  double-pendulum.html            # chaotic dynamics — Lagrangian + RK4
  robot-navigation.html           # stochastic shortest path — dynamic programming
  adaptive-cruise-control.html    # PID spacing control + robustness sampling
  vehicle-14dof.html              # single-track handling model + real tire curve
  active-suspension.html          # quarter-car LQR (Riccati equation)
  aircraft-pitch.html             # LQR + integral action pitch-rate tracking
  solar-racing.html               # traction-limited longitudinal performance
```

All links are relative, so the pages resolve correctly wherever the site is
hosted.
