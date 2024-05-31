# Arduino Stepper Motor Control

Welcome to the Arduino Stepper Motor Control repository! This project demonstrates how to control a stepper motor using an Arduino.

## Table of Contents

- [Arduino Stepper Motor Control](#arduino-stepper-motor-control)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Hardware Requirements](#hardware-requirements)
  - [Software Requirements](#software-requirements)
  - [Circuit Diagram](#circuit-diagram)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Code Explanation](#code-explanation)


## Introduction

This project provides an example of how to control a stepper motor with an Arduino. Stepper motors are used in a variety of applications where precise positioning and repeatability are necessary.

## Hardware Requirements

- Arduino Uno (or any other compatible Arduino board)
- Stepper Motor (e.g., 28BYJ-48)
- ULN2003 Stepper Motor Driver
- Breadboard and jumper wires
- External power supply (if needed for the motor)

## Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)

## Circuit Diagram

Here is a basic circuit diagram for connecting a stepper motor to an Arduino using a ULN2003 driver:

```
       +5V  ---------------------+
                              |
Arduino Pin 8 -------------- IN1 (ULN2003)
Arduino Pin 9 -------------- IN2 (ULN2003)
Arduino Pin 10 ------------- IN3 (ULN2003)
Arduino Pin 11 ------------- IN4 (ULN2003)
                              |
                             COM (ULN2003)
                             |
       GND  -------------------+
```

## Installation

1. Open the Arduino IDE and navigate to the cloned directory.

2. Open the `stepper_motor` file.

3. Connect your Arduino board to your computer.

4. Select the correct board and port from the Arduino IDE.

5. Click the Upload button to upload the code to the Arduino.

## Usage

After uploading the code to the Arduino, the stepper motor will start rotating based on the parameters defined in the code. You can modify the code to change the speed and direction of the motor.

## Code Explanation

Here is a brief explanation of the code used to control the stepper motor:

```cpp
#include <Stepper.h>

// Define the number of steps per revolution for your motor
const int stepsPerRevolution = 2048; 

// Initialize the stepper library on pins 8 through 11
Stepper myStepper(stepsPerRevolution, 8, 10, 9, 11);

void setup() {
  // Set the speed of the motor (RPM)
  myStepper.setSpeed(15);
  // Initialize the Serial port
  Serial.begin(9600);
}

void loop() {
  // Step one revolution in one direction
  Serial.println("Clockwise");
  myStepper.step(stepsPerRevolution);
  delay(1000);

  // Step one revolution in the other direction
  Serial.println("Counterclockwise");
  myStepper.step(-stepsPerRevolution);
  delay(1000);
}
```

- **Include the Stepper library:** The `Stepper.h` library provides the necessary functions to control the stepper motor.
- **Define the steps per revolution:** This value depends on your specific motor.
- **Initialize the stepper motor:** Specify the motor pins and steps per revolution.
- **Set the motor speed:** Adjust the speed (in RPM) according to your needs.
- **Control the motor in the loop:** Rotate the motor in both directions with a delay in between.
