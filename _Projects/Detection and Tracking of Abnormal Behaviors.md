---
title: "Detection and Tracking of Abnormal Behaviors"
permalink: /Projects/DTAB/
excerpt: An internship project at Institute of Automation, Chinese Academy of Sciences <br/> <a href="https://lijinjie.top/Projects/DTAB/"><img src="https://s2.ax1x.com/2019/10/16/KkV8gA.jpg" alt="KkV8gA.jpg" border="0" width="500" /></a>
collection: Projects
date: 2019-10-08
tags:
  - projects
---

## Overview

Duration：Jun. 2019 - Sep. 2019

This is my internship project, which aims to detect  intrusion, crossing a line, running and falling behaviors  automatically  in surveillance video through deep learning algorithms. Through this project, I am trying to complete the following learning  objectives:

1. Master Python language and object-oriented programming (OOP) ideas.
2. Master the TensorFlow deep learning framework.
3. Understand frequently-used target detection algorithms. I have implemented:  traditional algorithms include GMM and ViBe, machine learning algorithm  HOG+SVM, and deep learning algorithm YOLOV3. Now I use the YOLOV3  algorithm for target detection.
4. Understand frequently-used target tracking algorithms. Currently, I use the Deep Sort algorithm for target tracking.
5. Master some methods for optimizing computing resources

<iframe width="560" height="315" src="https://www.youtube.com/embed/kFEjHOXokIw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


|       Name        |              Configuration              |
| :---------------: | :-------------------------------------: |
|     Processor     | Intel® Core™ i7-8700 CPU @ 3.20GHz × 12 |
|        GPU        |           GeForce GTX 1050 Ti           |
|      Memory       |                  16 GB                  |
| Operating system  |        Ubuntu 16.04.6 LTS 64-bit        |
| Video information |             1280*720 30FPS              |
| Processing speed  |                  7FPS                   |

The code for the YOLOv3 algorithm and the Deep Sort algorithm refer to the following repositories: [Https://github.com/Qidian213/deep_sort_yolov3](Https://github.com/Qidian213/deep_sort_yolov3), [Https://github.com/YunYang1994/tensorflow-yolov3](Https://github.com/YunYang1994/tensorflow-yolov3) and [Https://github.com/nwojke/deep_sort](Https://github.com/nwojke/deep_sort). Thanks very much for these projects! I hope that one day, I can contribute to the open-source community like them.

I am currently training a classifier to try to identify the three  behaviors of falling, running, and standing based on target detection.

P.S. I found that YunYang posted a code analysis of YOLOV3. If you are interested, you can move to: https://github.com/YunYang1994/CodeFun/blob/master/005-paper_reading/YOLOv3.md
