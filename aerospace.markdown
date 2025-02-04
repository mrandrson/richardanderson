---
layout: richardbase
title: Missile Systems
permalink: /missilesystems/
---

<div style="text-align: center; margin-bottom: 40px;">
  <h1 style="font-size: 32px ; margin: 0; color: white;">Low Cost Missile Systems Design</h1>
</div>

During this project, I worked at the UTEP Aerospace center, as a part of a team working on developing a cost effective missile system. My primary role on the team was to help develop an object detection program using python packages like opencv, tensorflow, and the YOLOv3 object detection algorithm. In addition to my work on developing software for object detection, I also played a role in doing some basic and preliminary ballistics calculations in order to properly size the missile for the desired range and payload. In the process, I gained extensive experience in performing aerodynamics calculations and simulations using python and matlab.  

---

Here are some plots of calculations that went into the missile sizing estimates. A realistic model for thrust and weight based on the solid rocket engine used is used to numerically integrate the motion over the whole trajectory, including the time after the fuel has burnt out.

<div style="display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px;">

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/rocketpath.png" alt="Larson Mass Plot" style="width: auto; height: 400px;">
    <p>Figure 1: Missile Path</p>
  </div>

  <div style="text-align: center; flex: 1; min-width: 300px;">
    <img src="../assets/files/rocketspeed.png" alt="Shu Mass Plot" style="width: auto; height: 400px;">
    <p>Figure 2: Missile Velocity</p>
  </div>

</div>

Here is an example animation of a tracking script working, where it looks for and identifies a traingle based on the trained detection model, and tracks it in real time. 

<div style="text-align: center; margin-bottom: 20px;">
  <img src="../assets/files/aerospace-tracking.mp4" alt="Larson Solution" style="width: 600px; height: auto;">
</div>


