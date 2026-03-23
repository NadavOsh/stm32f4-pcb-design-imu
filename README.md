# stm32f4-pcb-design-imu
Custom STM32F4-based 4-layers PCB featuring MPU-6050 IMU, USB power, LDO regulation, and SWD debugging


<img width="815" height="723" alt="image" src="https://github.com/user-attachments/assets/5c29c7ce-b4d2-4386-a68c-29f4505cbfa1" />




# 1. Overview

This board is a custom embedded system built around the STM32F4 microcontroller, designed for motion sensing applications using an onboard IMU.

It includes:



* MCU: STM32F4 series (High-performance ARM Cortex-M4).

* Sensors: IMU MPU-6050 6-Axis Gyroscope & Accelerometer. Connected via I2C.

* Micro USB (Molex 473460001).
 
* Onboard AMS1117-3.3 LDO (5V to 3.3V regulation).

* JST-GH 6-pin (SM06B-GHS-TB) for external peripherals.

* Programming: Tag-Connect TC2030 (Plug-of-Nails™) SWD debugging interface.

* Configuration: BOOT0 hardwired to GND for normal flash boot.



  
