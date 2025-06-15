# Problem 2# 1. Theoretical Foundation

## Differential Equation of Motion

The general equation for a **forced damped pendulum** is:

\[
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
\]

Where:

- $\theta(t)$: angular displacement  
- $b$: damping coefficient  
- $\frac{g}{L}$: restoring torque per unit angle  
- $A$: amplitude of external forcing  
- $\omega$: angular frequency of forcing  

---

## Small-Angle Approximation

For small angles ($\theta \ll 1$ rad), we can use the linear approximation:

\[
\sin(\theta) \approx \theta
\]

The linearized equation becomes:

\[
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
\]

---

## Analytical Solution (Linear Case)

### Homogeneous Part (No Forcing):

$$ \[
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \omega_0^2 \theta = 0
\]$$

Where $\omega_0 = \sqrt{\frac{g}{L}}$

**Damping Cases**:

- Underdamped: $b^2 < 4 \omega_0^2$
- Critically damped: $b^2 = 4 \omega_0^2$
- Overdamped: $b^2 > 4 \omega_0^2$

---

### Particular Solution (Steady State):

$\[
\theta(t) = \theta_{\text{hom}}(t) + \theta_{\text{part}}(t)
\]$

$\[
\theta_{\text{part}}(t) = B \cos(\omega t - \delta)
\]$

Where:

\[
B = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + (b \omega)^2}}
\]

\[
\delta = \tan^{-1} \left( \frac{b \omega}{\omega_0^2 - \omega^2} \right)
\]

---

## Resonance

Occurs when driving frequency $\omega$ approaches natural frequency $\omega_0$:

\[
\omega \approx \omega_0 \Rightarrow B \text{ is maximized}
\]

With damping, the resonance peak shifts and the amplitude is reduced.

---

# 2. Analysis of Dynamics

## Parameter Effects

- **Damping ($b$):** reduces amplitude, smooths motion, suppresses chaos  
- **Driving Amplitude ($A$):** increases energy input; high $A$ can induce nonlinearity and chaos  
- **Driving Frequency ($\omega$):** determines proximity to resonance  

---

## Chaotic Behavior

For large angles, the **nonlinear** equation with full $\sin(\theta)$ must be used:

\[
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
\]

- No closed-form solution → use numerical methods
- Chaos appears with:
  - Weak damping
  - Strong driving
  - Specific $\omega$ values

### Indicators of Chaos

- Sensitive dependence on initial conditions  
- Strange attractors in phase space  
- Aperiodic but bounded motion  

---

# 3. Practical Applications

| Domain          | Example                                         |
|-----------------|--------------------------------------------------|
| Engineering     | Vibration absorbers, engine valves, suspension systems |
| Renewable Energy| Pendulum-based harvesters (wave, footstep)     |
| Climate Systems | El Niño quasiperiodic models                   |
| Biomechanics    | Gait oscillation analysis                      |
| Electrical      | Analogous to driven RLC circuits               |

---

# 4. Implementation Overview (No Code)

## Numerical Method

For solving the **nonlinear** equation:

\[
\frac{d^2 \theta}{dt^2} + b \frac{d \theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
\]

Use **Runge-Kutta 4th order** or other numerical integration methods.

---

## Visualizations

- **$\theta(t)$**: angle vs. time  
- **Phase diagram**: $\theta$ vs. $\dot{\theta}$  
- **Poincaré section**: sampled at each period $T = \frac{2\pi}{\omega}$  
- **Bifurcation diagram**: long-term behavior vs. $A$ or $\omega$

---

# 5. Model Limitations and Extensions

## Limitations

- Small-angle approximation invalid for large $\theta$  
- Assumes constant $b$ and sinusoidal forcing

## Extensions

- **Nonlinear damping**: e.g., air drag $\propto \dot{\theta}^2$  
- **Random/quasiperiodic forcing**  
- **Coupled pendulums**  
- **Multi-DOF systems**: e.g., double pendulum  
