---
title: "Development of a Settable Constant Temperature Controller"
permalink: /Projects/Temperature_Controller/
excerpt: 👍 My **first** electrical project ! <br/> <a href="https://lijinjie.top/Projects/Temperature_Controller/"><img src="https://s2.ax1x.com/2019/10/16/KkV33d.jpg" alt="KkV33d.jpg" border="0" width="500" /></a>
collection: Projects
date: 2018-07-05
tags:
  - projects
---

## Requirements

Duration: Feb. 2018 - Jun. 2018

Design and manufacture a constant temperature control system that can be set to a specific temperature:

1. Set the temperature in grades (at least three)
2. The range of heat is from 50 to 100 degrees, and the error should not exceed ±5 degrees. (Score according to the accuracy)
3. Use a cellphone to set and display the temperature.
4. Powered by 220V AC.

## Achievements

We shot this video to present the functions. Enjoy！😃

<iframe width="908" height="511" src="https://www.youtube.com/embed/2ZQEtcWF97I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
## Division

**LI Jinjie (Team leader) :** 

Designed, simulated, and tested the MCU and the analog PID control circuits; measured the PID parameters; drew the PCB board; **programmed** the MCU to drive the whole system; designed and manufactured the tank; prepared for the defense.

**LEI Tongtong :**

Designed, simulated, and tested the temperature measurement, button, display, and PWM circuits; ensured calibration of temperature measurement; soldered circuit boards; selected and purchased come components.

**ZHAO Qian :**

Designed, simulated, and tested the power supply and the relay drive circuits; selected and purchased the heating and cooling modules; drew the PCB boards; manufactured the entire system.

**YANG Manxin :**

Programmed an Android app and a WeChat Mini Program; soldered circuit boards; tested the display circuit; measured the PID parameters; designed and manufactured the tank; prepared for the defense.

**Instructor :** *Associate professor* TANG Yao

## Our plan

<img src="https://s2.ax1x.com/2019/08/04/e6qzKx.png" alt="e6qzKx.png" border="0"/>

The target temperature can be set using **an Android cellphone** or using **buttons**. There are three buttons on the top of our tank: 'SET', 'UP' and 'DOWN'. To set the temperature, press the 'SET' button, and the digital tube will flicker and display the target temperature. Continue to press the 'SET' key to select the digit, and adjust values through the 'UP' and 'DOWN' keys. After selecting the temperature and stopping operation for three seconds, the digital tube will display the current temperature and the device will warm up or cool down to the target temperature. 

Internal size: `300*200*150mm`

Accuracy: `< ±2℃` (Depending on the environment and how much water is loaded)

Adjustment time: `Approximately 5min` (Depending on the environment and how much water is loaded)

Simulation: `Multism`

PCB design: `Altium designer`

MCU program: `STM32CubeMX`, `Keil 5`    👉See the program [here](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master).

### Implementation

1. **MCU & PID control system**

   |         Function          |  Name   | Number |
   | :-----------------------: | :-----: | :----: |
   |      Display circuit      |   IO    |   7    |
   |      Button circuit       |   IO    |   3    |
   |  Temperature measurement  |   ADC   |   2    |
   |          DS18B20          |   IO    |   1    |
   | PWM wave generate circuit |   IO    |   4    |
   |        PID circuit        | DAC/ADC |  2/1   |

   According to our design requirements, we chose STM32ZET6 core board as our MCU.

   In this course, the proportion of analog circuits is a scoring factor, so we used an analog PID circuit for temperature control, as the following pictures shows.

   | <img src="https://s2.ax1x.com/2019/08/04/e6LERA.png" alt="e6LERA.png" border="0" /> |
   | ------------------------------------------------------------ |
   | <img src="https://s2.ax1x.com/2019/08/04/e6LWdO.png" alt="e6LWdO.png" border="0" /> |

   Initially, we did not design a **limiting circuit** for the integral circuits, which had terrible consequences in practical application. The maximum voltage of OP07 is ±10V. So if not design a limiter, the voltage of the integrated circuit will increase to 10V at the beginning of heating, which is much larger than the ADC range (0-3.3V). 

   The PID value can be changed by adjusting the potentiometers.

2. **Temperature measurement circuit**

   Pt resistance (Pt 100) was selected to measure the temperature. Pt 100 can convert
   the temperature signal into an analog voltage signal. And then through A/D
   conversion, the analog signal can be converted into a digital signal which can be processed by the MCU.

   <img src="https://s2.ax1x.com/2019/08/04/e6LfoD.png" alt="e6LfoD.png" border="0" />

   We used a DS18B20 component as standard to calibrate Pt resistance. The calibration curve is as follows:

   <img src="https://s2.ax1x.com/2019/08/04/e6LbOP.png" alt="e6LbOP.png" border="0" height="350" style="float:middle"/>

   Therefore, `T = 72.643×U-19.723`

3. **Display and buttons circuits**

   Choose 74LS139D as a decoder, and four seven-segment digital tubes to show the temperature `XXX.X`. 

   | Display                                                      | Buttons                                                      |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | <img src="https://s2.ax1x.com/2019/08/04/e6LXTS.png" alt="e6LXTS.png" border="0" /> | <img src="https://s2.ax1x.com/2019/08/04/e6LVxI.png" alt="e6LVxI.png" border="0" /> |

4. **Power circuit**

   The power supply needs to convert 220V 50Hz AC power into ±12V to supply operation amplifiers, into + 12V to the cooling module, and + 5V to the control circuit.

   <img src="https://s2.ax1x.com/2019/08/04/e6LvFg.png" alt="e6LvFg.png" border="0" />

5. **Bluetooth and APP**

   We selected the HC-08 module, which adopts the serial communication protocol and BLE4.0 to support Android and iOS system.

   We used Android Studio to develop an Android App. We used the built-in Bluetooth API to connect the App with the HC-08 module. We completed the function of displaying and controlling the temperature on the cellphone.

6. **Healing module**

   We used a 220V, 600W heating plate to heat the tank. The heating plate was pasted at the bottom to increase the contact area between the heater and the system and make the heating more uniform. After testing, the heating efficiency was 2 ℃/min.

   PID control method needs to adjust the power of the heating plate. We connected the relay to the heating circuit and controlled the relay's switching-on and off by generating PWM wave (5V) through the 555 timer circuit. By changing the duty cycle of the PWM wave, the power of the heating plate can be changed.

   <img src="https://s2.ax1x.com/2019/08/04/e6LzWj.png" alt="e6LzWj.png" border="0" />

7. **Cooling module**

   To cool water quickly, we designed a refrigeration module to speed up the heat dissipation of the system. At first, we used 12V 140W 1275 semiconductor chiller. After testing, we found the cooling effect to be ineffective. Later, we used two fans instead to accelerate the heat dissipation, which significantly accelerated the cooling speed.

8. **PCB boards**

   We drew two 10cm*10cm PCB boards to actuate the whole circuits and connect the two boards with an MCU board. The PCB boards are as follows and you can download them from [here](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master/PCB%20Board).	

   |                            PCB_1                             |                            PCB_2                             |
   | :----------------------------------------------------------: | :----------------------------------------------------------: |
   | <img src="https://s2.ax1x.com/2019/08/04/e6O9ln.png" alt="e6O9ln.png" border="0" height="380" width="380" /> | <img src="https://s2.ax1x.com/2019/08/04/e6OATU.png" alt="e6OATU.png" border="0" height="380" width="380" /> |

9. **Structure**

    <img src="https://s2.ax1x.com/2019/10/16/KkVKAO.jpg" alt="KkVKAO.jpg" border="0" />

### Process Recording

| Stage 1                                                      | Stage 2                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="https://s2.ax1x.com/2019/10/16/KkVtDP.jpg" alt="KkVtDP.jpg" border="0" width="400" /> | <img src="https://s2.ax1x.com/2019/08/04/e6O4BV.jpg" alt="e6O4BV.jpg" border="0" width="400" /> |
| **Stage 3**                                                  | **Stage 4**                                                  |
| <img src="https://s2.ax1x.com/2019/08/04/e6OOj1.jpg" alt="e6OOj1.jpg" border="0" width="400" /> | <img src="https://s2.ax1x.com/2019/08/04/e6Ojnx.jpg" alt="e6Ojnx.jpg" border="0" width="400" /> |

## Downloads

<a href="https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller" target="_blank">Program</a>

<a href="https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/PCB Board/" target="_blank">PCB boards</a>

Files: 

<a href="http://Li-jinjie.github.io/files/Temperature controller/Opening_reports.pdf" target="_blank">Opening report (Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/Interim_report.pdf" target="_blank">Interim Report (Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/Final_report.pdf" target="_blank">Final Report (Only my part, Chinese)</a>

<a href="http://Li-jinjie.github.io/files/Temperature controller/PPT1.pdf" target="_blank">PPT (Interim version)</a>
