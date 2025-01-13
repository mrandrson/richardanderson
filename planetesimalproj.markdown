---
layout: richardbase
title: Capture Rate of Planetesimals in Collapsing Proto-stars
permalink: /pproject/
---

<div style="text-align: center; margin-bottom: 40px;">
  <h1 style="font-size: 32px ; margin: 0; color: white;">Capture Rate of Planetesimals in Collapsing Proto-stars</h1>
</div>

<p>In this project, I am working under <a href="https://sites.google.com/view/kedron-silsbee">Dr. Kedron Silsbee</a> at UTEP, where we seek to understand the capture rate of planetesimals by collapsing proto-stars. In this project, we utilize the model given by <a href="http://www.astro.yale.edu/larson/papers/Protostar69.pdf">Larson 1969</a> for modelling the collapse of the protostar. Specifically, this paper gives a model for the density profile in the isothermal case. This can be obtained by $\eta$ in equation $8$ in appendix $C$ in <a href="http://www.astro.yale.edu/larson/papers/Protostar69.pdf">Larson 1969</a>. Here, the numerical solution for $\eta$ as a function of $x$ is plotted.:</p>

<div style="text-align: center; margin-bottom: 20px;">
  <img src="../assets/files/Larson-Solution.png" alt="Larson Solution" style="width: 400px; height: auto;">
</div>

Having a numerical solution for $\eta(x)$ allows us to obtain $\rho(r, t)$, and therefore the enclosed mass as the collapse proceeds is shown at different radii before the collapse (Larson Solution) and after the collapse (Shu Solution) 

<div style="display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px;">

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/Larson-Mass.png" alt="Larson Mass Plot" style="width: 100%; max-width: 600px; height: auto;">
    <p>Figure 1: Larson Mass Plot</p>
  </div>

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/Shu-Mass.png" alt="Shu Mass Plot" style="width: 100%; max-width: 500px; height: auto;">
    <p>Figure 2: Shu Mass Plot</p>
  </div>

</div>

Using these solutions, we can obtain an expression for the potential inside the cloud. This enables us to perform simulations using REBOUND of the motion of the planetesimals, allowing us to analyze the rate at which planetesimals are captured by the collapsing protostar.
