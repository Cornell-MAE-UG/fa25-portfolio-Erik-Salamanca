---
layout: project
title: Speaker Dissection for MAE 3260
description: Analysis Project
technologies: [Oscilliscope, High Speed Camera]
image: /assets/images/SP_Speaker.png
---
For this project our team decided to analysis a speaker. On this page I will write a summary of what I contributed to the project and that the end I will link a pdf of the report with my other group memebers sections of the report. We were given an echo dot (5th gen) and had to take it apart to find the speaker inside.  In doing so we identified three major components of the system. 

<p align="center">
  <img src="../../assets/images/SP_User_Control.png" width="400">
  <br>
  <em>Figure 1. This is a picture of the user control panel which has buttons for volume up (left), volume down (right), mute (top), and set up (bottom). This links to the control panel in Figure 2 through the flexible cable seen in the right side of the image.</em>
</p>

<p align="center">
  <img src="../../assets/images/SP_Control_Panel.png" width="400">
  <br>
  <em>Figure 2. This is a picture of a control panel that controls both the speaker and many other systems that are outside of the scope of this report [1]. Seen coming out of the left side of the echo dot is the flexible cable that connects to the user control panel.</em>
</p>

<p align="center">
  <img src="../../assets/images/SP_Speaker.png" width="400">
  <br>
  <em>Figure 3. This is the speaker and the subject of this report. Its two leads go to the control panel to receive the voltage input for the speaker.</em>
</p>


These figures display the major components of the system and understanding these components interact will allow parallels to be drawn to known systems. In fact, documentation was found for a model system that looks identical to this system. 

<p align="center">
  <img src="../../assets/images/SP_Model_Diagram.png" width="400">
  <br>
  <em>Figure 4. This is a model of a speaker that looks very similar to the speaker in the echo dot [2].</em>
</p>

<div style="display: flex; justify-content: center; gap: 10px;">
  <img src="../../assets/images/SP_Magnet.png" width="250">
  <img src="../../assets/images/SP_Spider.png" width="250">
  <img src="../../assets/images/SP_Dust_Cap.png" width="250">
</div>

<p style="text-align: center;">
  <em>Figure 5. Here are images of the speaker where magnets can be seen to be a part of the system as the speaker can hold up an allen key set. The spider and voice coil can be seen in the second image. In the final image the diaphragm and dust cap can be seen.</em>
</p>

Since in Figure 5 parallels can be drawn to the model in Figure 4 it is reasonable to use the ODE’s developed for the model system. Using the equations that this model generates the ODE’s of the system are [2]:

$$
u(t) = L \frac{d}{dt} i(t) + Bl \frac{d}{dt} x(t) + R\, i(t)
$$

$$
Bl\, i(t) = m \frac{d^2}{dt^2} x(t) + b \frac{d}{dt} x(t) + k\, x(t)
$$

Where u(t) is the voltage input, i(t) is the current, and x(t) is the displacement of the diaphragm. 

The easiest way to make a block diagram and transfer function for the system is to set up the state space vectors:

$$
\underbrace{
\begin{pmatrix}
\frac{d}{dt}x(t) \\
\frac{d^2}{dt^2}x(t) \\
\frac{d}{dt}i(t)
\end{pmatrix}
}_{\dot{Z}(t)}
=
\underbrace{
\begin{pmatrix}
0 & 1 & 0 \\
-\frac{k}{m} & -\frac{b}{m} & \frac{Bl}{m} \\
0 & -\frac{Bl}{L} & -\frac{R}{L}
\end{pmatrix}
}_{A}
\underbrace{
\begin{pmatrix}
x(t) \\
\frac{d}{dt}x(t) \\
i(t)
\end{pmatrix}
}_{Z(t)}
+
\underbrace{
\begin{pmatrix}
0 \\
0 \\
\frac{1}{L}
\end{pmatrix}
}_{B}
\, u(t)
$$

$$
x(t) = 
\underbrace{
\begin{pmatrix}
1 & 0 & 0
\end{pmatrix}
}_{C}
\begin{pmatrix}
x(t) \\
\frac{d}{dt}x(t) \\
i(t)
\end{pmatrix}
+
\underbrace{
\begin{pmatrix}
0
\end{pmatrix}
}_{D}
u(t)
$$

Using the state space model a block diagram can be generated that takes inputs and gives outputs. 

<p align="center">
  <img src="../../assets/images/SP_Block_Diagram.png" width="400">
  <br>
  <em>Figure 4. This is a model of a speaker that looks very similar to the speaker in the echo dot [2].</em>
</p>

Using these state space matrices the transfer functions can be made using the equation:
C(sI - A)-1B + D = G(s) [3].

$$
G(s)\;=\;\frac{X(s)}{U(s)}
\;=\;
\frac{Bl}
{L m s^{3} + (L b + R m)s^{2} + (Bl^{2} + L k + R b)s + R k}
$$




## Refrences
[1] P. Aggarwal, “Inside The Amazon Echo Dot (5 Gen): A Complete Teardown,” Pallavaggarwal.in, Nov. 07, 2023. 
[https://pallavaggarwal.in/2023/11/07/amazon-echo-dot-5gen-teardown/](https://pallavaggarwal.in/2023/11/07/amazon-echo-dot-5gen-teardown/)
[accessed Dec. 5, 2025].

[2] P. Brunet, “Nonlinear System Modeling and Identification of Loudspeakers,” Northeastern Library, Apr. 2014. 
[https://repository.library.northeastern.edu/files/neu:336724/fulltext.pdf](https://repository.library.northeastern.edu/files/neu:336724/fulltext.pdf)  
[accessed Dec. 05, 2025].

[3] M. Campbell. MAE 3260. Class Lecture, Topic: “State Space Models.” College of Engineering, Cornell University, Ithaca, NY, Oct. 6, 2025.


## Full Report

[Downloadable PDF Here](../assets/MAE3260-Final-Groupqork-Report.pdf)