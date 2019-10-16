---
title: "Detection and Tracking of Abnormal Behaviors"
permalink: /Projects/DTAB/
excerpt: An internship project at Institute of Automation, Chinese Academy of Sciences <br/> <a href="https://lijinjie.top/Projects/DTAB/"><img src="https://s2.ax1x.com/2019/10/16/KkV8gA.jpg" alt="KkV8gA.jpg" border="0" width="500" /></a>
collection: Projects
date: 2019-06-27
tags:
  - projects
---

## Overview

This is my internship project, which aims to detect  intrusion, crossing a line, running and falling behaviors  automatically  in surveillance video through deep learning algorithms. Through this project, I am trying to complete the following learning  objectives:

<img src="https://s2.ax1x.com/2019/10/16/KkV8gA.jpg" alt="KkV8gA.jpg" border="0" />

1. Master Python language and object-oriented programming (OOP) ideas.
2. Master the TensorFlow deep learning framework.
3. Understand frequently-used target detection algorithms. I have implemented:  traditional algorithms include GMM and ViBe, machine learning algorithm  HOG+SVM, and deep learning algorithm YOLOV3. Now I use the YOLOV3  algorithm for target detection.
4. Understand frequently-used target tracking algorithms. Currently, I use the Deep Sort algorithm for target tracking.
5. Master some methods for optimizing computing resources

The code for the YOLOv3 algorithm and the Deep Sort algorithm refer to the following repositories: [Https://github.com/Qidian213/deep_sort_yolov3](Https://github.com/Qidian213/deep_sort_yolov3), [Https://github.com/YunYang1994/tensorflow-yolov3](Https://github.com/YunYang1994/tensorflow-yolov3) and [Https://github.com/nwojke/deep_sort](Https://github.com/nwojke/deep_sort). Thanks very much for these projects! I hope that one day, I can contribute to the open-source community like them.

I am currently training a classifier to try to identify the three  behaviors of falling, running, and standing based on target detection.

P.S. I found that YunYang posted a code analysis of YOLOV3. If you are interested, you can move to: https://github.com/YunYang1994/CodeFun/blob/master/005-paper_reading/YOLOv3.md
