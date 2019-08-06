---
title: "Design of A Settable Constant Temperature Controller"
excerpt: My first electrical project ! <br/><img src="https://s2.ax1x.com/2019/08/05/eRwQ29.png" alt="eRwQ29.png" border="0" width="500" />
collection: ProjectsBlogs
date: 2018-06-25
tags:
  - projects
---

## Requirements

Design and manufacture a constant temperature control system that can be set to the specific temperature:

1. Setting the temperature in grades (at least three)
2. The range of heat is from 50 to 100 degrees, and the error should not exceed ±5 degrees. (Score according to the accuracy)
3. Use a cellphone to set and display the temperature.
4. Powered by 220V AC.

## Final achievement

We shot this video to present the functions. Enjoy！😃

<iframe width="908" height="511" src="https://www.youtube.com/embed/2ZQEtcWF97I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Division

**Jinjie Li (Team leader)** : 

Design, simulate, and test the MCU and the analog PID control circuits; measure the PID parameters; draw the PCB board; program the MCU to drive the whole system; design and manufacture the tank; prepare for the defense.

**Tongtong Lei**: 

Design, simulate, and test the temperature measurement, button, display, and PWM circuits; calibration of temperature measurement; solder circuit boards; select and purchase come components.

**Qian Zhao**:

Design, simulate, and test the power supply, the relay drive circuits; select and purchase the heating and cooling modules; draw the PCB boards; manufacture the entire system.

**Manxin Yang**: 

Program an Android app and a WeChat Mini Program; solder circuit boards; test the display circuit; measure the PID parameters; design and manufacture the tank; prepare for the defense.

## Our plan

<img src="https://s2.ax1x.com/2019/08/04/e6qzKx.png" alt="e6qzKx.png" border="0" />

There are three buttons on the top of our tank, namely 'SET', 'UP' and 'DOWN'. If you want to set the temperature, press the 'SET' button, and the digital tube starts to flicker and displays target temperature. Continue to press the 'SET' key to select the digit, and adjust values through the 'UP' and 'DOWN' keys. After choosing the temperature and stopping operation for three seconds, the digital tube displays the current temperature and warms up or cools down to the target temperature. The heat can also be set by an Android cellphone.

Internal size: `300*200*150mm`

Accuracy: `< ±2℃` (Depend on the environment and how much water is loaded)

Adjustment time: `About 5min` (Depend on the environment and how much water is loaded)

Simulation:` Multism`

PCB design: `Altium designer`

MCU program: `STM32CubeMX`, `Keil 5`    See the program from [here](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master).

### implementation

1. MCU & PID control system

|         Function          |  Name   | Number |
| :-----------------------: | :-----: | :----: |
|      Display circuit      |   IO    |   7    |
|      Button circuit       |   IO    |   3    |
|  Temperature measurement  |   ADC   |   2    |
|          DS18B20          |   IO    |   1    |
| PWM wave generate circuit |   IO    |   4    |
|        PID circuit        | DAC/ADC |  2/1   |

Therefore, we choose STM32ZET6 core board as our MCU.

In this course, the proportion of analog circuits will become a scoring factor, so we use an analog PID circuit for temperature control.

| <img src="https://s2.ax1x.com/2019/08/04/e6LERA.png" alt="e6LERA.png" border="0" /> |
| ------------------------------------------------------------ |
| <img src="https://s2.ax1x.com/2019/08/04/e6LWdO.png" alt="e6LWdO.png" border="0" /> |

Initially, we did not design limiting circuit for integral circuits, which had terrible consequences in practical application. The maximum voltage of OP07 is ±10V. If not design limiting circuit, the voltage of the integrated circuit will increase to 10V at the beginning of heating, which is much larger than the ADC range. The PID value can be changed by adjusting the potentiometers.

2. Temperature measurement circuit

Pt resistance (Pt 100) is selected to measure temperature. Pt 100 can convert temperature signal into an analog voltage signal, and then through A/D conversion, it can be converted into a digital signal which can be processed by MCU.

<img src="https://s2.ax1x.com/2019/08/04/e6LfoD.png" alt="e6LfoD.png" border="0" />

We use a DS18B20 component as standard to calibrate Pt resistance. The calibration curve is as follow:

<img src="https://s2.ax1x.com/2019/08/04/e6LbOP.png" alt="e6LbOP.png" border="0" height="350" style="float:middle"/>

Therefore, `T = 72.643×U-19.723`

3. Display and buttons circuits

   Choose 74LS139D as decoder, and four seven-segment digital tubes to show the temperature `XXX.X`. 

   | Display                                                      | Buttons                                                      |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | <img src="https://s2.ax1x.com/2019/08/04/e6LXTS.png" alt="e6LXTS.png" border="0" /> | <img src="https://s2.ax1x.com/2019/08/04/e6LVxI.png" alt="e6LVxI.png" border="0" /> |

4. Power circuit

   The power supply needs to convert 220V 50Hz AC power into ±12V to supply operation amplifiers, into + 12V to cooling module, and + 5V to control circuit.

   <img src="https://s2.ax1x.com/2019/08/04/e6LvFg.png" alt="e6LvFg.png" border="0" />

5. Bluetooth and APP

   Select HC-08 module, which adopts the serial communication protocol and BLE4.0 to support Android and IOS system.

   Use Android Studio to develop an Android App. Use the built-in Bluetooth API to connect the App with HC-08 module. Complete the function of displaying and controlling the temperature on the cellphone.

6. Healing module

   We use a 220V, 600W heating plate to heat the tank. The heating plate is pasted at the bottom to increase the contact area between the heater and the system and make the heating more uniform. After testing, the heating efficiency is 2 ℃/min.

   PID control method needs to adjust the power of the heating plate. We connect the relay to the heating circuit and control the relay's switching-on and off by generating PWM wave (5V) through the 555 timer circuit. By changing the duty cycle of the PWM wave, the power of the heating plate can be changed.

   <img src="https://s2.ax1x.com/2019/08/04/e6LzWj.png" alt="e6LzWj.png" border="0" />

7. Cooling module

   To cool water quickly, we design a refrigeration module to speed up the heat dissipation of the system. At first, we used 12V 140W 1275 semiconductor chiller. After testing,  the cooling effect was not good. Later, we use two fans instead to accelerate the heat dissipation, which significantly accelerated the cooling speed.

8. PCB boards

   We draw two 10cm*10cm PCB boards to actuate the whole circuits and connect the two boards with an MCU board. The PCB boards are as follows and you can download them from [here](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master/PCB%20Board).	

|                            PCB_1                             |                            PCB_2                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://s2.ax1x.com/2019/08/04/e6O9ln.png" alt="e6O9ln.png" border="0" height="380" width="380" /> | <img src="https://s2.ax1x.com/2019/08/04/e6OATU.png" alt="e6OATU.png" border="0" height="380" width="380" /> |



9. Structure

<img src="https://s2.ax1x.com/2019/08/04/e6OZY4.jpg" alt="e6OZY4.jpg" border="0" />

### Process Recording

| Step 1                                                       | Step 2                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="https://s2.ax1x.com/2019/08/04/e6OWXq.jpg" alt="e6OWXq.jpg" border="0" width="400" /> | <img src="https://s2.ax1x.com/2019/08/04/e6O4BV.jpg" alt="e6O4BV.jpg" border="0" width="400" /> |
| **Step 3**                                                   | **Step 4**                                                   |
| <img src="https://s2.ax1x.com/2019/08/04/e6OOj1.jpg" alt="e6OOj1.jpg" border="0" width="400" /> | <img src="https://s2.ax1x.com/2019/08/04/e6Ojnx.jpg" alt="e6Ojnx.jpg" border="0" width="400" /> |

## Downloads

<a href="https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master" target="_blank">Program</a>

<a href="https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master/PCB%20Board" target="_blank">PCB boards</a>

Files: 

<a href="http://Li-jinjie.github.io/files/Temperature controller/Opening_reports.pdf" target="_blank">Opening report (Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/Interim_report.pdf" target="_blank">Interim Report (Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/Final_report.pdf" target="_blank">Final Report (Only my part, Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/PPT1.pdf" target="_blank">PPT (Interim version)</a>
