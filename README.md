# stm32f4-pcb-design-imu
Custom STM32F4-based 4-layers PCB featuring MPU-6050 IMU, USB power, LDO regulation, and SWD debugging


<img width="815" height="723" alt="image" src="https://github.com/user-attachments/assets/5c29c7ce-b4d2-4386-a68c-29f4505cbfa1" />




<img width="1191" height="849" alt="image" src="https://github.com/user-attachments/assets/2bf20c31-6fbb-4516-8117-5fd409733d84" />



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



# 2. Hardware Architecture

Core Components:

MCU: STM32F4 series
* IMU: MPU-6050 (accelerometer + gyroscope)

*Voltage Regulator: AMS1117-3.3 (5V → 3.3V)

*Clock Source: External 24 MHz oscillator


Power System:
* Input: 5V via USB connector (473460001)
* Regulation: AMS1117-3.3 LDO
* Output: 3.3V rail powering MCU and peripherals


Interfaces:
* USB
* SWD Debugging:
  * Connector: TC2030 Tag-Connect
  * Signals:
     * SWDIO
     * SWCLK
     * GND
    * 3.3V (reference)


IMU Interface (MPU-6050):
* Communication: I2C
* Pull-up resistors: Present on SDA and SCL lines
* Powered from 3.3V rail


Expansion Connector:
* JST 6-pin connector (SM06B-GHS-TB)
* Can be used for:
    * External sensors
    * UART / I2C / GPIO expansion


# 3. Boot Configuration:

* BOOT0 is tied to GND
   * MCU always boots from internal Flash
   * Prevents accidental boot into system bootloader


# 4. Clock Configuration:

* External 24 MHz oscillator connected to MCU


# 5. Pin Mapping

## Pin Mapping

| Function        | MCU Pin | Direction | Description                        |
|----------------|--------|-----------|--------------------------------------|
| I2C_SCL        | PB6    | Bidir     | I2C clock to MPU-6050 (pull-up)      |
| I2C_SDA        | PB7    | Bidir     | I2C data to MPU-6050 (pull-up)       |
| USB_VBUS       | -      | Input     | 5V input from USB connector          |
| USB_DN         | PA11   | Bidir     | USB differential data (-)            |
| USB_DP         | PA12   | Bidir     | USB differential data (+)            |
| SWDIO          | PA13   | Bidir     | SWD debug data                       |
| SWCLK          | PA14   | Bidir     | SWD debug clock                      |
| SW0            | PB3    | Bidir     | Serial Wire Output. Debug            |
| LED            | PB13   | Output    | Red LED                              |
| NRST           | NRST   | Input     | MCU negative reset                   |
| BOOT0          | BOOT0  | Input     | Boot configuration (Flash mode)      |
| HSE_IN         | PH0    | Input     | External 24 MHz oscillator input     |
| HSE_OUT        | PH1    | Output    | External oscillator output           |
| 3V3            | —      | Power     | Regulated 3.3V rail                  |
| GND            | —      | Ground    | Ground                               |
| JST_PIN_1      | -      | Power     | 3.3V                                 |
| JST_PIN_2      | PA4    | I/O       | Expansion connector                  |
| JST_PIN_3      | PA5    | I/O       | Expansion connector                  |
| JST_PIN_4      | PA6    | I/O       | Expansion connector                  |
| JST_PIN_5      | PA7    | I/O       | Expansion connector                  |
| JST_PIN_6      | -      | GND       | GND                                  |


# 6. Design Notes / Decisions

* Used I2C with pull-ups for reliable communication with IMU
* BOOT0 tied low for stable boot behavior
* Tag-Connect reduces connector footprint vs standard headers


# 7. Limitations / Future Improvements

* AMS1117 has high dropout and poor efficiency → consider switching regulator
* No ESD protection on USB


# 8. Files Included
* Schematic (PDF)
* PCB layout
* BOM
* Gerber Files
* Pick and Place



  
