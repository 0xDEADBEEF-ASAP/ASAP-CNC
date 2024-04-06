# ASAP-CNC (project is under early stage of developement)

# What? Why? How?

 ASAP-CNC is complete, minimalistic, written from scratch system that can control up to 5 axis in real time.

 All released software out there uses step/dir signals. ASAP-CNC use TMC5160 in MODE 1 instead, (with embedded motion controller) without step/dir signals (only SPI interface).

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/misc/TMC-MODE.png)
[1]

# System
- responsive (!) multiplatform g-code sender, writen in python (using only native modules)
- real time g-code interpreter for STM32H7, writen in C
- stepper motor drivers TMC5160 in MODE 1


# Futures

## G-CODE SENDER

---G-CODE---
 Automatic connection and re-connection even if different serial port is opened.

---JOG---

---MACHINE---

---TMC-SIMPLE---

---TMC-ADVANCED---

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/misc/ASAP-TMC-DRIVER-ADVANCED.gif)


 Sequential TMC-DRIVER programming - registers are programmed in order and single register can be re-programmed multiple times during single driver setup.

# HARDWARE CHANGES

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/misc/IMG_1b.jpg)

## RSENS
 Change Rsens resistors R022 according to this table:

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/misc/RSENS.png)
[1]

Rsens resistors are low impedance SMD 2512.

 For 2.0A rated stepper motor the 0.12 R (2.0A RMS) should be used. Then current should be scaled to match 2.0A peak current. If stepper motor used for application isn't getting hot, current can be scaled up. For more info check link [2].

 ![](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/Rsens_mix.jpg)

 ![](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/TMC_Rsens_removed.png)

 ![](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/Rsens_R040.jpg)

R040 is for this engine (nema 34):

![](https://github.com/0xDEADBEEF-ASAP/ASAP-CNC/blob/main/misc/Nema34_12_5Nm.jpg)

## CLOCK
 For best performance feed TMC5160 driver with common clock source up to 18 MHz (16MHz optimal).
Remove R10 and connect to pads clock source (50% duty cycle).

![](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/R10.jpg)

## CURRENT measurements (ACS724-10-AB +/- 10A)
120kHz analog output, 1us rise time. 5V supply voltage, 2,5V output offset (0A), 200mV/A. [3]

![](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/ACS724.jpg)


[![current measure](https://raw.githubusercontent.com/0xDEADBEEF-ASAP/ASAP-CNC/main/misc/vid_1.png)](https://youtu.be/c74zXEftsE0)

# RELATED media

3 axis coordinated move test:
[![current measure](https://github.com/0xDEADBEEF-ASAP/ASAP-CNC/blob/main/misc/vid_2.png?raw=true)](https://youtu.be/9pOCou4G9pE?feature=shared)



# LINKS & SORURCES
[TMC5160-DATASEET]

[1]

https://www.analog.com/media/en/technical-documentation/data-sheets/TMC5160A_datasheet_rev1.18.pdf

[2]

https://help.stepperonline.com/en/article/how-to-set-the-current-on-stepper-driver-rms-or-peak-1d29t68/

[3]

https://www.allegromicro.com/en/Products/Sense/Current-Sensor-ICs/Zero-To-Fifty-Amp-Integrated-Conductor-Sensor-ICs/ACS724-5
