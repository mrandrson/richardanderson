---
layout: richardbase
title: NEXT Data Analysis
permalink: /nextdataanalysis/
---

<div style="text-align: center; margin-bottom: 40px;">
  <h1 style="font-size: 32px ; margin: 0; color: white;">Analysis of NEXT Experiment Data</h1>
</div>

I worked on this project during the summer of 2024 as a part of the NREMST program at UT Arlington. During the project, I worked as a part of the Neutrino and Rare Event Searches Group, led by Dr. Ben Jones. I worked under the guidance of Dr. Krishan Mistry to analyze S1 and S2 pulses in the NEXT data.

<div style="display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px;">
  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/3031S1Fit.png" alt="Example S1 Fit" style="width: 100%; max-width: 600px; height: auto;">
    <p>Figure 1: S1 Fit</p>
  </div>

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/3031S2Fit.png" alt="Example S2 Fit" style="width: 100%; max-width: 600px; height: auto;">
    <p>Figure 2: S2 Fit</p>
  </div>
</div>

<p>
  Using these fits, information could be gathered, such as S2 Area, width, or height. By studying the spatial distribution of these properties in the detector, we can get a sense for the charge distribution throughout the x-y plane.
</p>

<div style="display: flex; align-items: flex-start; gap: 0; flex-wrap: nowrap;">
  <!-- Left Figures -->
  <div style="flex: 1; display: flex; justify-content: flex-end; text-align: center;">
    <div style="display: flex; flex-wrap: wrap; gap: 0;">
      <img src="../assets/files/quadrantfit1.png" alt="Quadrant 1" style="width: 40%; height: auto; margin: 0;">
      <img src="../assets/files/quadrantfit2.png" alt="Quadrant 2" style="width: 40%; height: auto; margin: 0;">
      <img src="../assets/files/quadrantfit3.png" alt="Quadrant 3" style="width: 40%; height: auto; margin: 0;">
      <img src="../assets/files/quadrantfit4.png" alt="Quadrant 4" style="width: 40%; height: auto; margin: 0;">
    </div>
  </div>

  <div style="flex: 1; max-width: 500px; align-self: flex-start; margin: 0;">
    <p>
        Since the time between S1 and S2 pulses is approximately proportional to the z distance between them, we can get a sense for the charge over time for each x-y bin. To the left I show the histograms of S2 Area versus drift time, as well as a red line showing a fit of the data to $q(t) = q_0\exp\left(-\frac{t}{\tau}\right)$ to model the charge per bin. In addition to analysis of experimental data, I have made use of the Nexus Geant-4 simulation framework to recreate detector events and understand the underlying physics to patterns in experimental data. 
    </p>
  </div>
</div>


