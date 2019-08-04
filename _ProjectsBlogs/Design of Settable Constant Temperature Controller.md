---
title: "Design of Settable Constant Temperature Controller"
excerpt: "Short description of ProjectsBlogs item number 1<br/><img src='https://s2.ax1x.com/2019/07/25/emu7WQ.md.jpg'>"
collection: ProjectsBlogs
date: 2018-06-25
tags:
  - projects
---

## Requirements

Design and manufacture a constant temperature control system that can be set to the specific temperature, as follows:

1. Setting the temperature in grades (at least three)
2. The range of heat is from 50 to 100 degrees, and the error should not exceed ±5 degrees. (Score according to the accuracy)
3. A cellphone can set and display the temperature.
4. Powered by 220V AC.

## Final achievement

We shot this video to present the functions. Enjoy！😃

<iframe width="908" height="511" src="https://www.youtube.com/embed/2ZQEtcWF97I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Division

**Jinjie Li (Team leader)** : 

Design, simulate, and test the MCU and the analog PID control circuit; measure the PID parameters; draw the PCB board; program the MCU to drive the whole system; design and manufacture the tank; prepare for the defense.

**Tongtong Lei**: 

Design, simulate, and test the temperature measurement, button, display, and PWM circuits; calibration of temperature measurement; solder circuit boards; select and purchase come components.

**Qian Zhao**:

Design, simulate, and test the power supply, the relay drive circuits; select and purchase the heating and cooling modules; draw the PCB boards; manufacture the entire system.

**Manxin Yang**: 

Program an Android app and a WeChat Mini Program; solder circuit boards; test the display circuit; measure the PID parameters; design and manufacture the tank; prepare for the defense.

## Our plan

![1564882643702](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564882643702.png)

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

In this course, the proportion of analog circuit will become a scoring factor, so we use an analog PID circuit for temperature control.

| ![1564907939231](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564907939231.png) |
| ------------------------------------------------------------ |
| ![1564906685248](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564906685248.png) |

Initially, we did not design limiting circuit for integral circuits, which had terrible consequences in practical control. The maximum voltage of OP07 is ±10V. If not design limiting circuit, the voltage of the integrated circuit will increase to 10V at the beginning of heating, which is much larger than the ADC range. The PID value can be changed by adjusting the potentiometers.

2. Temperature measurement circuit

Pt resistance (Pt 100) is selected to measure temperature. Pt 100 can convert temperature signal into an analog voltage signal, and then through A/D conversion, it can be converted into a digital signal which can be processed by MCU.

![](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564885712300.png)

We use a DS18B20 component as standard to calibrate Pt resistance. The calibration curve is as follows:

![](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564885685191.png)

T = 72.643*U-19.723

3. Display and buttons circuits

   Choose 74LS139D as decoder, and four seven-segment digital tubes to show the temperature (XX.X). 

   | Display                                                      | Buttons                                                      |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | ![1564887679393](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564887679393.png) | ![1564888133131](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564919475759.png) |

4. Power circuit

   The power supply needs to convert 220V 50Hz AC power into ±12V to supply operation amplifiers, into + 12V to cooling module, and + 5V to control circuit.

   ![1564889710792](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564889710792.png)

5. Bluetooth and APP

   Select HC-08 module, which adopts the serial communication protocol and BLE4.0 to support Android and IOS system.

   Use Android Studio to develop an Android App. The built-in Bluetooth API is used to connect the App with HC-08 module. Complete the function of displaying and controlling the temperature on the cellphone.

6. Healing module

   We use a 220V, 600W heating plate to heat the tank. The heating plate is pasted at the bottom to increase the contact area between the heater and the system and make the heating more uniform. After testing, the heating efficiency is 2 ℃/min.

   PID control method needs to adjust the power of the heating plate. We connect the relay to the heating circuit and control the relay's switching-on and off by generating PWM wave (5V) through the 555 timer circuit. By changing the duty cycle of the PWM wave, the power of the heating plate can be changed.

   ![1564904419629](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564904419629.png)

7. Cooling module

   To cool water quickly, we chose a refrigeration module to speed up the heat dissipation of the system. At first, we used 12V 140W 1275 semiconductor chiller. After testing,  the cooling effect was not good. Later, we use two fans to accelerate the heat dissipation, which significantly accelerated the cooling speed.

9. PCB board

   We draw two 10cm*10cm PCB boards to actuate the whole circuits and connect the two boards with an MCU board. The PCB boards are as follows and you can download them from [here](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master/PCB%20Board).	

|                            PCB_1                             |                            PCB_2                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![1564906499656](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564906499656.png) | ![1564906509968](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564906509968.png) |



10. Structure

![1564910945622](C:\Users\Lijinjie\AppData\Roaming\Typora\typora-user-images\1564910945622.png)

### Process Recording

| Step 1                                                       | Step 2                                                      |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| ![version1_qq_circuit](C:\Users\Lijinjie\Desktop\模电\相册\version1_qq_circuit.png) | ![IMG_012](C:\Users\Lijinjie\Desktop\模电\相册\IMG_012.jpg) |
| **Step 3**                                                   | **Step 4**                                                  |
| ![IMG_033](C:\Users\Lijinjie\Desktop\模电\相册\IMG_033.jpg)  | ![图片2](C:\Users\Lijinjie\Desktop\模电\相册\图片2.jpg)     |

## Downloads

[Program](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master)

[PCB boards](https://github.com/Li-Jinjie/Design-of-Settable-Constant-Temperature-Controller/tree/master/PCB%20Board)

Files: Opening report (Chinese), Interim Report (Chinese), Final Report (Only my part, Chinese)

PPT: Interim version