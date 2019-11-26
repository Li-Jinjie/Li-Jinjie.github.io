---
title: "Designing and Optimization of a Helicopter Remote Grab System"
permalink: /Projects/Helicopter_grab/
excerpt: We won the **1st** place in Simulative Search and Rescue project in 2017 China Aeromodelling Design Challenge. <br/> <a href="https://lijinjie.top/Projects/Helicopter_grab/"><img src="https://s2.ax1x.com/2019/10/03/u05vYF.jpg" alt="u05vYF.jpg" border="0" width="500" /></a>
collection: Projects
date: 2017-10-21
tags:
  - projects
  - CADC
---

## Overview

Duration: Jul. 2017 - Oct. 2017

This project is designed for the **Simulative Search and Rescue project** in the 2017 China Aeromodelling Design Challenge (CADC) competition.

The competition requires us to achieve the following functions: 

The model helicopter should take off from the take-off and landing area, fly to the Emergency & First-aid supply storage area, and then search, select, and automatically pick up a specific supply by image equipment on the helicopter. After flying over the obstacle, the supply will be delivered to the particular "victims" in the area to complete a search and rescue mission. The cycle continues until the end of the round (5 mins). The team who accomplishes the task most quickly and accurately is the winner.

## Achievements

Finally, we won the **championship** of Simulative Search and Rescue project in 2017 China Aeromodelling Design Challenge! 🥇 (19 universities of China in total)

<img src="https://s2.ax1x.com/2019/10/16/KkVMND.jpg" alt="KkVMND.jpg" border="0" width="600" align="center" />

This video records the competition. 👇

<iframe width="560" height="315" src="https://www.youtube.com/embed/Y7R1W2pjVvo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
## Division

All members come from the **Beihang Aeromodelling Team**.

<img src="https://s2.ax1x.com/2019/10/03/u046ET.jpg" alt="u046ET.jpg" border="0"/>

**Team 1:** **LI Jinjie**, LI Duye, YANG Dianhui, LI Zhenyang

**Team 2:** YI Ruizhi (team leader), LIU Jiaxin, WU Chengyi, LIU Xiaodong

**Instructors**: *Prof.* WAN Zhiqiang, LI Yongxin, WANG Funan

I was responsible for manufacturing the mechanical structure and making videos.


## The Technical Requirements

1. Model helicopters are allowed to be powered by internal combustion engines or electric motors. The internal combustion engine's volume should be below 15 𝑐𝑐 (including 91), and no-load voltage of the battery must be under 51 𝑉. No autopilot is allowed. Each flight group can use up to 2 models in the race.
2. The model helicopter shall search the target through the wireless image equipment on the helicopter.
3. Only mechanical devices are allowed to pick up and release Emergency & First-aid supplies, and manual means are not allowed.
4. Every team must use the automatic capture and delivery devices in the picking process. The
   definition of automatic capture: humans cannot participate in the direct control of the capture system. In other words, the catch and release of supplies are required to be completed automatically after issuing the trigger command to start operation.
5. The model helicopter should pick up the supplies (billiard balls with different colors) after landing in the storage area and release them automatically through the mechanical device after landing in the delivery area.

Please refer to the complete <a href="http://Li-jinjie.github.io/files/Others/CADC_2017_Rules.pdf" target="_blank">rulebook (CN)</a> for more information such as venue settings, athlete requirements, etc.


The field setting is as follows: 👇

<img src="https://s2.ax1x.com/2019/10/16/KkVYut.jpg" alt="KkVYut.jpg" border="0" />

## Solutions

Please watch the video below for more information about our plan.

<iframe width="560" height="315" src="https://www.youtube.com/embed/CFfCpMxMR4k" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**I. Steps of self-recognition grasping**

1. Judge the state of the image
2. Search for the balls in the image. The edges of balls are presented as circles on the screen
3. Select the circles on the screen
4. Based on histogram, assign colors' priority to the found circles
5. Convert the circles' coordinate from pixel coordinates of the image to physical space coordinates
6. Capture and build the capture loop

**II. Mechanical structure design**

1. The length of polar coordinates is controlled by a stepper motor and synchronous belt wheel.
2. The linear bearing can reduce friction and increase the reaction speed of the mechanism.
3. Cylinder pneumatic controls the expansion of the z-axis grab sleeve.
