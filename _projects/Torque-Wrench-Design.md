---
layout: project
title: Torque Wrench Design Project
description: Design Project
technologies: [CAD, MatLAB, ANSYS]
image: /assets/images/max_stress_high_mesh.png
---
In this project for MAE 3270 Properties of Materials, Kat Volkova and I designed a torque wrench give requirements for use. These Requirments were that it must have a facotr of safety against yeild of 4, against crack growth of 2, and against fatigue stress at 10^6 cycles of 1.5. Additionally, a strain gauge would be attached to the side of the wrench and it must measure a voltage change of 1.0 mV/V at the rated torque of 600 lbf-in. Finally the wrench must be made of either aluminum, steel, or titanium. 

## Overall Model Dimensions

<p align="center">
  <img src="../../assets/images/dimensions_2.png" width="400">
  <br>
  <em>This image depicts the overall dimensions of the wrench design. This model was made by Kat.</em>
</p>

After making the model of the system I developed a MATLAB livescript to do hand calculations to see if certain materials would meet the requirements set by the problem. 

[Download MATLAB livescript here](../../assests/Material_Selector.mlx)