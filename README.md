# ASAP-CNC (project is under early stage of developement)

# What? Why? How?

 ASAP-CNC is complete, minimalistic, written from scratch system that can control up to 5 axis in real time.

 All released software out there uses step/dir signals. ASAP-CNC use TMC5160 in MODE 1 instead, (with embedded motion controller) without step/dir signals (only SPI interface).

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/TMC-MODE.png)
[1]

# System
- responsive (!) multiplatform g-code sender, writen in python (using only native modules)
- real time g-code interpreter for STM32H7, writen in C
- stepper motor drivers TMC5160 in MODE 1

# Gallery
![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/ASAP-TMC-ADVANCED.gif)


# Futures

## G-CODE SENDER

---G-CODE---
 Automatic connection and re-connection even if different serial port is opened.

---JOG---

---MACHINE---

---TMC-SIMPLE---

---TMC-ADVANCED---

 Sequential TMC-DRIVER programming - registers are programmed in order and single register can be re-programmed multiple times during single driver setup.

# HARDWARE CHANGES

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/IMG_1b.jpg)

## RSENS
 Change Rsens resistors R022 according to this table:

![](https://raw.githubusercontent.com/0xDEADBEEF-ARM/ASAP-CNC/main/RSENS.png)
[1]

 For 2.0A rated stepper motor the 0.12 R (2.0A RMS) should be used. Then current should be scaled to match 2.0A peak current. If stepper motor used for application isn't getting hot, current can be scaled up. For more info check link [2].

## CLOCK
 For best performance feed TMC5160 driver with common clock source up to 18 MHz (16MHz optimal).
Remove R10 and connect to pads clock source (50% duty cycle).

# LINKS & SORURCES
[TMC5160-DATASEET]

 [1]
 https://www.analog.com/media/en/technical-documentation/data-sheets/TMC5160A_datasheet_rev1.18.pdf

 [2]
 https://help.stepperonline.com/en/article/how-to-set-the-current-on-stepper-driver-rms-or-peak-1d29t68/



