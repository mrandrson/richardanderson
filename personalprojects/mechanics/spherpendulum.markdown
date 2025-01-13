---
layout: richardbase
title: Spherical Pendulum Project
permalink: /personalprojects/spherpendulum/
---
## Spherical Pendulum Equations of Motion

Here, we want to consider the effect of some angular velocity $\omega$ on the motion of a spherical pendulum. In order to do so, we introduce a slightly modified set of spherical coordinates, where the $\omega t$ term is introduced to represent the motion of the pendulum about a vertical axis:

$$
x = l\sin\left(\varphi\right)\cos\left(\theta+\omega t\right) \quad \quad \quad y = l\sin\left(\varphi\right)\sin\left(\theta+\omega t\right) \quad \quad \quad z = -l\cos(\varphi)
$$

Taking the time derivative, keeping in mind that both $\varphi$ and $\theta$ are functions of time:

$$
\dot{x} = l\left(\cos(\theta+\omega t)\cos(\varphi)\dot{\varphi}-\left(\omega+\dot{\theta}\right)\sin(\theta+\omega t)\sin(\varphi)\right)
$$

$$
\dot{y} = l\left(\sin(\theta+\omega t)\cos(\varphi)\dot{\varphi}+\left(\omega+\dot{\theta}\right)\cos(\theta+\omega t)\sin(\varphi)\right)
$$

$$
\dot{z} = -l\dot{\varphi}\sin(\varphi)
$$

This enables us to write the kinetic energy as follows:

$$
T = \dfrac{1}{2}m\left(\dot{x}^2+\dot{y}^2+\dot{z}^2\right) = \dfrac{1}{2}ml^2\left(\left(\dot{\theta}+\omega\right)^2\sin^2(\varphi)+\dot{\varphi}^2\right)
$$

Ultimately allowing us to write the Lagrangian as:

$$
\mathcal{L} = T-U = \dfrac{1}{2}ml^2\left(\left(\dot{\theta}+\omega\right)^2\sin^2(\varphi)+\dot{\varphi}^2\right)-U
$$

This is all well and good; now we can write the potential due to gravity as follows. However, this is not the only force we must consider when writing the equations of motion for a pendulum spinning about its vertical axis. Indeed, the source of the vertical elevation which we hope to investigate is the fictitious "centripetal" force.

$$
U_g = -mgl\cos\left(\varphi\right)
$$

Although the centripetal force is not often written in terms of a potential, and rather in terms of the rotation vectors and axes, we use $\vec{F}=-\vec{\nabla}U$ to assign a potential to it.

$$
\vec{F}_{c} = m\omega\times\left(\omega\times\vec{r}\right)
$$

$$
\vec{\omega}\times\left(\vec{\omega}\times\vec{r}\right) = \vec{\omega}\left(\vec{\omega}\cdot\vec{r}\right)-\vec{r}\left(\vec{\omega}\cdot\vec{\omega}\right)
$$

$\omega$ and $\vec{r}$ are orthogonal, so:

$$
\vec{F}_c = -m\vec{r}\omega^2
$$

$$
F_c = m\omega^2r
$$

$$
\vec{F} = -\nabla U
$$

$$
U_c = -\int F_c\ dr = -\dfrac{1}{2}m\omega^2r^2 = -\dfrac{1}{2}m\omega^2l^2\sin^2(\varphi)
$$

Here, we have used $r \to -l\sin(\varphi)$ to represent the radial direction of rotation. We can then write an effective potential, which includes the centripetal force:

$$
U_{eff} = U_g+U_c = -mgl\cos\left(\varphi\right)-\dfrac{1}{2}m\omega^2l^2\sin^2(\varphi)
$$

$$
\mathcal{L} = \dfrac{1}{2}ml^2\left(\left(\dot{\theta}+\omega\right)^2\sin^2(\varphi)+\dot{\varphi}^2\right)+mgl\cos\left(\varphi\right)+\dfrac{1}{2}m\omega^2l^2\sin^2(\varphi)
$$

$$
\dfrac{\partial \mathcal{L}}{\partial \varphi}-\dfrac{d}{dt}\left(\dfrac{\partial \mathcal{L}}{\partial \dot{\varphi}}\right)=0
$$

$$
\dfrac{\partial L}{\partial \varphi} = ml^2\sin(\varphi)\cos(\varphi)\left(\left(\dot{\theta}+\omega\right)^2+\omega^2\right)-mgl\sin(\varphi) \quad \quad \quad \dfrac{d}{dt}\left(\dfrac{\partial L}{\partial \dot{\varphi}}\right) = ml^2\ddot{\varphi}
$$

$$
\ddot{\varphi} = \left(\left(\dot{\theta}+\omega\right)^2+\omega^2\right)\sin(\varphi)\cos(\varphi)-\dfrac{g}{l}\sin(\varphi)
$$

$$
\dfrac{\partial \mathcal{L}}{\partial \theta}-\dfrac{d}{dt}\left(\dfrac{\partial \mathcal{L}}{\partial \dot{\theta}}\right)=0
$$

$$
\dfrac{\partial L}{\partial \theta} = 0 \quad \quad \quad \dfrac{d}{dt}\left(\dfrac{\partial L}{\partial \dot{\theta}}\right) = \dfrac{d}{dt}\left(ml^2\left(\dot{\theta}+\omega\right)\sin^2(\varphi)\right) = ml^2\left(\ddot{\theta}\sin^2(\varphi)+2\left(\dot{\theta}+\omega\right)\dot{\varphi}\sin(\varphi)\cos(\varphi)\right)
$$

$$
\ddot{\theta}+2\left(\dot{\theta}+\omega\right)\dot{\varphi}\cot(\varphi)=0
$$

## Numerical Scheme

## Steady-state Solution of $\varphi$ as a Function of $\omega$

We consider here the case where $\varphi \sim \text{const.}$, therefore $\ddot{\varphi} \approx 0$.

$$
\ddot{\varphi}\approx 0 \implies \sin\varphi =0 \ \wedge\ \cos\varphi = \dfrac{g/l}{\left(\dot{\theta}+\omega\right)^2+\omega^2}
$$

Here, we are mainly interested in the non-trivial case:

$$
\varphi(\omega) \approx \cos^{-1}\left[\dfrac{g/l}{\left(\dot{\theta}+\omega\right)^2+\omega^2}\right]
$$

