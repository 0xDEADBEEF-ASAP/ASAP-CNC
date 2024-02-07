# ASAP-CNC (project is under early stage of developement)

# What? Why? How?

ASAP-CNC is complete, minimalistic, written from scratch system that can control up to 5 axis in real time.

All released software out there uses step/dir signals. ASAP-CNC use TMC5160 in MODE 1 instead, (with embedded motion controller) without step/dir signals (only SPI interface).

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




