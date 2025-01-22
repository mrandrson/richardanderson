---
layout: richardbase
title: Least Squares Regression
permalink: /personalprojects/regression
---

# Regression

One of the primary problems in machine learning is that of regression. That is, given some set of data-points $(x_i, y_i)$, we want to fit some function $f(x_i; \theta_i)$ to those points, where $\theta_i$ are the parameters passed to the fitting function. For each data-point, there will be residual $\epsilon_i$ given by $\epsilon_i = f(x_i; \theta_i) - y_i$, but this can get negative sometimes, and absolute values are discontinuous, so it would be better if we define:

$$
\epsilon_i = \bigl(f(x_i;\theta_i) - y_i\bigr)^2
$$

We are going to want to minimize the total error of the function:

$$
E = \sum\limits_{i=0}^N \epsilon_i = \sum\limits_{i=0}^N \bigl(f(x_i;\theta_i) - y_i\bigr)^2
$$

So, we want to consider how $E$ changes with time as $\theta$ is updated:

$$
\dot{E} = \frac{dE}{dt} = \sum_{i=1}^N \frac{\partial E}{\partial \theta_i} \frac{d\theta_i}{dt}
$$

Here, $\frac{\partial E}{\partial \theta_i}$ is the gradient of $E$ with respect to $\theta_i$, and $\dot{\theta}_i = \frac{d\theta_i}{dt}$ is the rate of change of $\theta_i$ over time.

The gradient of $E$ with respect to $\theta_i$ is given by:

$$
\frac{\partial E}{\partial \theta_i} = 2 \sum_{j=0}^N \bigl(f(x_j; \theta_j) - y_j\bigr) \frac{\partial f(x_j; \theta_j)}{\partial \theta_j}
$$

To ensure a monotonic decrease in $E$, we postulate that the relationship between $\frac{\partial E}{\partial \theta_i}$ and $\dot{\theta}_i$ is:

$$
\frac{\partial E}{\partial \theta_i} = -\dot{\theta}_i
$$

This relationship directly connects the change in the parameters $\theta_i$ to the gradient of the error function, ensuring consistency with the chain rule.

Substituting $\frac{\partial E}{\partial \theta_i} = -\dot{\theta}_i$ into the expression for $\dot{E}$, we obtain:

$$
\dot{E} = \sum_{i=1}^N \frac{\partial E}{\partial \theta_i} \dot{\theta}_i = \sum_{i=1}^N (-\dot{\theta}_i) \dot{\theta}_i
$$

Simplifying:

$$
\dot{E} = -\sum_{i=1}^N \dot{\theta}_i^2
$$

The term $\sum_{i=1}^N \dot{\theta}_i^2$ represents the squared velocity of the parameters $\theta_i$. This can be interpreted as the "kinetic energy" of the system. Define:

$$
K = \frac{1}{2} \|\dot{\theta}\|^2 = \frac{1}{2} \sum_{i=1}^N \dot{\theta}_i^2
$$

Thus, the time derivative of the error function can be written as:

$$
\dot{E} = -2K
$$

So, we want to minimize $E(\theta) - \frac{1}{2}\dot{\theta}^2$, as $E(\theta)$ represents the error, and as $\frac{1}{2}\dot{\theta}^2$ approaches $E(\theta)$, it will "cancel" out the error. So, if we want to minimize the total error over the time we run the optimization algorithm, we effectively want to minimize:

$$
\mathcal{E}[E, \theta, \dot{\theta}] = \int_0^t E(\theta) - \dfrac{1}{2}\dot{\theta}^2\; dt = \int_0^t dt\ L(E, \theta, \dot{\theta})
$$

So now, we vary the functional as $\delta \mathcal{E}$:

$$
\delta \mathcal{E} = \int_0^t dt\; \left[\dfrac{\partial L}{\partial \theta} \delta \theta + \dfrac{\partial L}{\partial \dot{\theta}} \delta \dot{\theta}\right] = \int_0^t dt\; \left[\dfrac{\partial L }{\partial \theta}  - \dfrac{d}{dt} \dfrac{\partial L }{\partial \dot{\theta}}\right]\delta t
$$

This is optimized by $\delta \mathcal{E} = 0$, therefore:

$$
\dfrac{\partial L }{\partial \theta}  - \dfrac{d}{dt} \dfrac{\partial L }{\partial \dot{\theta}} = 0
$$

$$
\ddot{\theta} = -\nabla_\theta E(\theta)
$$

---

## Second-Order Dynamics for Accurate and Stable Updates

To ensure pure accuracy and stability, we retain the full second-order dynamics:

$$
\ddot{\theta} = -\nabla_\theta E(\theta) - \gamma \dot{\theta}
$$

where $\ddot{\theta}$ represents the acceleration, $-\nabla_\theta E(\theta)$ is the driving force, given by the gradient of the error function $E(\theta)$, and $-\gamma \dot{\theta}$ introduces damping to control oscillations.

### Symplectic Leapfrog (Velocity-Verlet) Scheme

A symplectic integrator is employed to preserve the stability and accuracy of the dynamics. The Leapfrog (Velocity-Verlet) scheme is particularly suitable for this purpose. The update rules are as follows:

1. Perform a half-step velocity update:

    $$
    v^{n+\frac{1}{2}} = v^n - \frac{\Delta t}{2} \nabla_\theta E(\theta^n)
    $$

    where $v^n = \dot{\theta}^n$ is the velocity.

2. Update the position:

    $$
    \theta^{n+1} = \theta^n + \Delta t v^{n+\frac{1}{2}}
    $$

3. Perform a second half-step velocity update:

    $$
    v^{n+1} = v^{n+\frac{1}{2}} - \frac{\Delta t}{2} \nabla_\theta E(\theta^{n+1})
    $$

This scheme ensures long-term stability and accuracy by preserving the symplectic structure of the dynamics. To further enhance stability in the update scheme, damping is introduced in the velocity update. The modified half-step velocity update is:

$$
v^{n+\frac{1}{2}} = v^n - \frac{\Delta t}{2} \nabla_\theta E(\theta^n) - \frac{\gamma \Delta t}{2} v^n
$$

### Adaptive Time Stepping

To ensure both stability and efficiency, an adaptive time-stepping scheme is used. The time step $\Delta t$ is adjusted dynamically based on the magnitude of the gradient:

$$
\Delta t = \min\left(\Delta t_{\text{max}}, \frac{\Delta t_{\text{max}}}{1 + \|\nabla_\theta E(\theta^n)\|}\right)
$$

This ensures smaller time steps in regions of steep gradients, preventing instability.

---

Here, I show some examples of the regression algorithm in use. The regression scheme is implemented in C++, and animation is done using Python's Matplotlib package. 

<div style="display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px;">
  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/fit_evolution.mp4" alt="Larson Mass Plot" style="width: auto; height: 400px;">
    <p>Figure 1: Gaussian Fit</p>
  </div>

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/fit_evolution2.mp4" alt="Shu Mass Plot" style="width: auto; height: 400px;">
    <p>Figure 2: Sinusoidal Fit</p>
  </div>
</div>

<!---
<div style="display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px;">

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/fit_evolution.mp4" alt="Larson Mass Plot" style="width: 100%; max-width: 600px; height: auto;">
    <p>Figure 1: Gaussian Fit</p>
  </div>

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/fit_evolution2.mp4" alt="Shu Mass Plot" style="width: 100%; max-width: 500px; height: auto;">
    <p>Figure 2: Sinusoidal Fit</p>
  </div>

</div>
--->
