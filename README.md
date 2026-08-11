# Overview of the robot, systems, and code

Radio RC Robot Car, Tank drive system. Run in Arduino C.

## Wiring + Other Images

KiCad schematic exported as images.

### Controller Wiring

![Wiring Diagram for RC Controller](SchematicPic.jpg)

### Car Wiring Diagram

To be added.

## Bill of Materials

### Controller

- Arduino Pro Mini
- NRF24L01 2.4GHz Transceiver Module
- I2C 0.96 inch screen module
- Joystick Module (2)
- Potentiometers (2)
- Switches (2)
- Connecting wires
- AA battery x 3
- AA battery x 3 holder

### Car

Car can be assembled with anything as long as there is a microcontroller, a good h-bridge motor driver (with HIGH-LOW-PWM code), motors in tank drive, an NRF module same as the one used in the controller, and a power source. If using lithium please be careful. An optional BOM is given below.

- ESP32 microcontroller
- NRF24L01 2.4GHz Transceiver Module
- TB6612FNG Dual Motor Driver Module
- AA battery x 4
- AA battery x 4 holder
- 6V N20 motors
- Connecting wires

## Instructions for use

### Libraries used
#### Controller
- <SPI.h>
- <Wire.h>
- <RF24.h>
- <nRF24L01.h>
- <Adafruit_GFX.h>
- <Adafruit_SSD1306.h>

#### Car
- <SPI.h>
- <RF24.h>
- <nRF24L01.h>

### Some details about the code

- The code is largely annotated and also self-explanatory at most points.
- The data package can be changed as per the user's wishes, however it must be changed at both points, controller and car.

## To Do

### Flaws to be fixed
- Currently, when suddenly increasing motor speed (by rapidly moving the joystick upward), I observe the bot moving in a pulsating manner as per any joystick position that can update in-between pulses. I suspect this is brownout caused by sudden increase in motor speed.
    - Therefore it is a loop... Motor speed increases -> ESP resets -> Motor speed 'starts' at 0 -> Immediately increases to earlier high speed (finger has not left joystick) -> Repeat.
    - However, I suspect that this is because I'm using alkaline batteries to power the bot. I could use: Lithium ion batteries / Separate power supply for microcontroller + Radio module. Will also attempt to fix this in code.
- In controller, RF_OK (checking condition of radio module) is only looked at at the beginning of the code. If the module is removed in-between, there is no update on the screen and the code attempts to function as usual.


### Repo To-Dos

- Atach SPI setup code
- Attach radio module setup code
- Attach videos: Pulsating, normal running
- Attach car schematics


