
## Overview123

This is my internship project, which aims to detect  intrusion, crossing a line, running and falling behaviors  automatically  in surveillance video through deep learning algorithms. Through this project, I am trying to complete the following learning  objectives:

<img src="https://s2.ax1x.com/2019/10/07/u2VuaF.png" alt="u2VuaF.png" border="0" />

1. Master Python language and object-oriented programming (OOP) ideas.
2. Master the TensorFlow deep learning framework.
3. Understand frequently-used target detection algorithms. I have implemented:  traditional algorithms include GMM and ViBe, machine learning algorithm  HOG+SVM, and deep learning algorithm YOLOV3. Now I use the YOLOV3  algorithm for target detection.
4. Understand frequently-used target tracking algorithms. Currently, I use the Deep Sort algorithm for target tracking.
5. Master some methods for optimizing computing resources

The code for the YOLOv3 algorithm and the Deep Sort algorithm refer to the following repositories: https://github.com/Qidian213/deep_sort_yolov3 https://github.com/YunYang1994/tensorflow-yolov3 [Https://github.com/nwojke/deep_sort](Https://github.com/nwojke/deep_sort) Thanks very much for these projects! I hope that one day, I can contribute to the open-source community like them.

I am currently training a classifier to try to identify the three  behaviors of falling, running, and standing based on target detection.

P.S. I found that YunYang posted a code analysis of YOLOV3. If you are interested, you can move to: https://github.com/YunYang1994/CodeFun/blob/master/005-paper_reading/YOLOv3.md


## Functions

This part is to explain the meaning of the UI interface.

<img src="https://s2.ax1x.com/2019/10/07/u2Ezb8.png" alt="u2Ezb8.png" border="0" height="500"/>

**General functions:**

*The file path of opening*: Enter the path of a source video, which defaults to "/home/tom/桌面/行人检测算法/测试数据/监控视频/003.avi"

*Save videos*: Decide whether to save the alarm picture. If a target alarms multiple times, save only the first picture.

*The file path of saving*: Enter the saved path of the alarm pictures, which defaults to "./alarm_frame/"

------

**Detecting  intrusion**：

*Does it have a warning area*: Implement detecting intrusion function, determine whether there is an alert area? If yes, a quadrilateral area needs to be defined at four points in the window. When the target enters this area, the box on the target will turn red to alert.

------

**Detecting crossing a line**：

*Does it have a warning line*: Whether there is a warning line? If yes, a straight line needs to be determined in the next picture. When the target crosses this line, the box on the target will turn red to alert. After selecting this option, you need to choose the next two options:

1. *Single cross？* : Is it one-way crossing? The default is two-way crossing, and it will alert as long as a target crossed the line. If you choose one-way crossing, only crossing the line in one direction will alert. After selecting this option, you need to select the next option:

2. *Reverse direction？*: Whether to reverse the alarm direction of one-way crossing.

------

**Detecting running**：

*Does it have a speed limit?*：Implement detecting running function (pixels/frame). If yes, the box on the target will turn red to alert when the speed exceeds the set value. After selecting this option, you need to select the next option:

*Maximum  speed* : Set alarm speed in pixels/frame.

------

**Detecting falling**: At present, this function has a poor effect on the actual video.

*Does It judge fall？*: If yes, implement detecting falling function.

*Falling time*: Enter the minimum speed (pixels/frame). When the target's speed is less than this value, the box on the target will turn red to alert.
