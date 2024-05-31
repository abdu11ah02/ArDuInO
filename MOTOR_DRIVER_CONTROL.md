# Arduino Motor Driver Control

Welcome to the Arduino Motor Driver Control project! This repository contains the code and documentation for controlling a motor driver using an Arduino.

## Table of Contents
- [Arduino Motor Driver Control](#arduino-motor-driver-control)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Features](#features)
  - [Hardware Requirements](#hardware-requirements)
  - [Software Requirements](#software-requirements)
  - [Installation](#installation)
  - [Usage](#usage)
    - [Wiring Diagram](#wiring-diagram)
    - [Example Commands](#example-commands)
  - [Code Explanation](#code-explanation)
  - [Troubleshooting](#troubleshooting)

## Introduction
This project demonstrates how to control a motor driver using an Arduino. It includes code for basic operations like starting, stopping, and changing the direction of the motor.

## Features
- Control motor speed
- Change motor direction
- Start and stop the motor

## Hardware Requirements
- Arduino (e.g., Uno, Mega, Nano)
- Motor driver (e.g., L298N, L293D)
- DC motor
- External power supply (if required by the motor)
- Jumper wires
- Breadboard

## Software Requirements
- [Arduino IDE](https://www.arduino.cc/en/software)

## Installation

1. Open the Arduino IDE.
2. Load the project by navigating to `File` -> `Open` and selecting the `.ino` file from the cloned repository.

## Usage
1. Connect the motor driver to the Arduino according to the wiring diagram provided below.
2. Upload the code to your Arduino.
3. Use the serial monitor to send commands to the motor driver.

### Wiring Diagram
```
  Arduino     Motor Driver
  --------    ------------
  5V         -> VCC
  GND        -> GND
  D3         -> IN1
  D4         -> IN2
  D5 (PWM)   -> ENA
  Motor A    -> Motor terminals
```

### Example Commands
- `start`: Starts the motor
- `stop`: Stops the motor
- `speed 100`: Sets the motor speed to 100 (0-255)
- `direction forward`: Sets the motor direction to forward
- `direction backward`: Sets the motor direction to backward

## Code Explanation
Here is a brief overview of the main parts of the code:

```cpp
const int motorPin1 = 3;
const int motorPin2 = 4;
const int enablePin = 5;

void setup() {
    pinMode(motorPin1, OUTPUT);
    pinMode(motorPin2, OUTPUT);
    pinMode(enablePin, OUTPUT);
    Serial.begin(9600);
}

void loop() {
    if (Serial.available() > 0) {
        String command = Serial.readString();
        processCommand(command);
    }
}

void processCommand(String command) {
    if (command == "start") {
        digitalWrite(motorPin1, HIGH);
        digitalWrite(motorPin2, LOW);
        analogWrite(enablePin, 255); // Full speed
    } else if (command == "stop") {
        analogWrite(enablePin, 0); // Stop the motor
    } else if (command.startsWith("speed")) {
        int speed = command.substring(6).toInt();
        analogWrite(enablePin, speed);
    } else if (command == "direction forward") {
        digitalWrite(motorPin1, HIGH);
        digitalWrite(motorPin2, LOW);
    } else if (command == "direction backward") {
        digitalWrite(motorPin1, LOW);
        digitalWrite(motorPin2, HIGH);
    }
}
```

## Troubleshooting
- Ensure all connections are correct.
- Verify the motor driver and motor are powered correctly.
- Check the serial monitor for any error messages.
