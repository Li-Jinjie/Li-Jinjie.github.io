---
title: "A New Type of Bionic Autonomous Integrated Navigation System"
permalink: /Projects/Navigation_System/
excerpt: 👍 We won **the Second Prize** in the 28th "Feng Ru Cup" Competition of Academic and Technological Works! <br/> <a href="https://lijinjie.top/Projects/Navigation_System/"><img src="https://s2.ax1x.com/2019/10/07/uRR5uD.png" alt="uRR5uD.png" border="0" width="500"/></a>
collection: Projects
date: 2018-11-05
tags:
  - projects
---

## Overview

Duration: Nov. 2017 - Nov. 2018

We participated in **the 28th "Feng Ru Cup" Competition of Academic and Technological Works**,  and won the second prize. Please watch this video or read the article below for more information.

<iframe width="560" height="315" src="https://www.youtube.com/embed/U4IfWXl7zYE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
In order to strengthen the autonomy and reliability of UAVs under **no GNSS** condition, by imitating efficient navigation principle of birds and insects, we designed a new type of bionic integrated navigation system  based on **the inertial measurement unit (IMU), the bionic polarized light sensor (BPS), and air data system (ADS)**. 

<img src="https://s2.ax1x.com/2019/10/10/uTXV2R.png" alt="uTXV2R.png" border="0"/>

The BPS provides useful heading angle information, and the ADS can continuously provide speed and altitude information. At the same time, the **Kalman filter** is selected for information fusion of subsystems. The polarization sensor is designed and manufactured by ourselves. 

IMU: MPU9250

BPS: BH1750

ADS: MS4525DO

MCU: STM32F103C8T6

## Achievements

| Schematic                                                    | PCB diagram                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="https://s2.ax1x.com/2019/10/07/uRffmD.png" alt="uRffmD.png" border="0" width="500"> | <img src="https://s2.ax1x.com/2019/10/07/uRfotA.png" alt="uRfotA.png" border="0" width="400"> |
| **Circuit board of the polarization sensor**                 | **Add lenses**                                               |
| <img src="https://s2.ax1x.com/2019/10/07/uR5GYd.jpg" alt="uR5GYd.jpg" border="0" width="400"/> | <img src="https://s2.ax1x.com/2019/10/16/KkVenx.jpg" alt="KkVenx.jpg" border="0" width="450"/> |

The polarization sensor is calibrated indoors, with an error of **0.1°** in an ideal state.

To verify the accuracy of the integrated navigation system, we first carried out software simulation. In the simulation, we assume that the aircraft performs uniform linear motion and is interfered with GPS signals at 300s and 600s. The chart shows a comparison of heading angle errors.

<img src="https://s2.ax1x.com/2019/10/07/uRfIkd.png" alt="uRfIkd.png" border="0" width="600">

At 300s and 600s, due to GPS interference, the green curve fluctuates in a broad range, while the blue curve is relatively stable.

These two figures show comparisons between the pitch angle error and rolling angle error.  

|                      Pitch angle error                       |                       Roll angle error                       |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://s2.ax1x.com/2019/10/07/uRfHpt.png" alt="uRfHpt.png" border="0"> | <img src="https://s2.ax1x.com/2019/10/07/uRfb1P.png" alt="uRfb1P.png" border="0"> |

When the GPS signal is not disturbed, both navigation systems can ensure the accuracy and stability of pitch angle and roll angle measurement. But when GPS interference occurs, the two measurement values (green curve) of the GPS/SINS system produce significant errors. The performance of the proposed autonomous navigation system is not affected.

This figure is a comparison of velocity errors.

<img src="https://s2.ax1x.com/2019/10/07/uRfq6f.png" alt="uRfq6f.png" border="0">

As can be seen from the error diagram, the error curve (green part) of GPS/SINS system showed high fluctuation at 300s and 600s, while the speed of the INS/ADS/BPS system flying eastward was not affected, which could maintain the accuracy and stability for a long time.

Then we conducted **an outdoor flight experiment** to test the dynamic performance of the system. The experimental results were a comparison of the attitude angle between our system and the GPS/SINS  system.

<img src="https://s2.ax1x.com/2019/10/16/KkVVj1.jpg" alt="KkVVj1.jpg" border="0" />

After establishing communication with the UAV, we collected data through the computer, and observed the waveform of attitude angle. Then we took the data solved by the GPS as a reference, marked the figure as the blue line, and marked the data solved by the combined navigation system as the red line.

|                        The roll angle                        |                       The pitch angle                        |      |
| :----------------------------------------------------------: | :----------------------------------------------------------: | ---- |
| <img src="https://s2.ax1x.com/2019/10/07/uRf26K.png" alt="uRf26K.png" border="0"> | <img src="https://s2.ax1x.com/2019/10/07/uRfROO.png" alt="uRfROO.png" border="0"> |      |

|                      The heading angle                       |
| :----------------------------------------------------------: |
| <img src="https://s2.ax1x.com/2019/10/07/uRfgl6.png" alt="uRfgl6.png" border="0" width="400"> |

The experimental results show that the attitude angle outputted by INS/ADS/BPS navigation system is close to that of the GPS and IMU system in terms of accuracy and stability. Although the experiment is still in the preliminary stage, it proves that the proposed system is a feasible and reliable autonomous navigation scheme in real flight. 

In the future, we hope to introduce advanced data fusion methods such as nonlinear and anti-interference Kalman filters into the system to further improve its accuracy and robustness. We also plan to test the system in a complex environment with GNSS interference.

## Division

Advisors: *Prof.* GUO Lei, *Dr.* ZHANG Xiao

Circuit design and flight experiments: **LI Jinjie**, WANG Shanpeng

Programming and simulation: GUO Xiaoyu, HUANG Zhenhuan

Other work: ZHAO Xueyuan, ZHANG Ruijiang

