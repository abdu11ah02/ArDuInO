# Arduino IR Sensor with LED Project

This repository contains the code and schematics for a project that uses an IR sensor to control an LED with an Arduino.

## Table of Contents
- [Arduino IR Sensor with LED Project](#arduino-ir-sensor-with-led-project)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Components](#components)
  - [Setup](#setup)
  - [Code](#code)
  - [Usage](#usage)

## Overview

This project demonstrates how to use an infrared (IR) sensor with an Arduino to control an LED. When the IR sensor detects an object, it will turn on the LED.

## Components

- Arduino Uno
- IR Sensor
- LED
- Resistor (220 ohms for the LED)
- Breadboard
- Jumper wires


## Setup

1. Connect the IR sensor to the Arduino:
   - GND to GND
   - VCC to 5V
   - OUT to digital pin 2 (D2)

2. Connect the LED to the Arduino:
   - The anode (long leg) to digital pin 13 (D13) through a 220-ohm resistor
   - The cathode (short leg) to GND

## Code

Upload the following code to your Arduino:

```cpp
// Pin definitions
const int irSensorPin = 2;
const int ledPin = 13;

void setup() {
  // Initialize the LED pin as an output
  pinMode(ledPin, OUTPUT);
  
  // Initialize the IR sensor pin as an input
  pinMode(irSensorPin, INPUT);
}

void loop() {
  // Read the value from the IR sensor
  int sensorValue = digitalRead(irSensorPin);
  
  // If the sensor detects an object
  if (sensorValue == LOW) {
    // Turn on the LED
    digitalWrite(ledPin, HIGH);
  } else {
    // Turn off the LED
    digitalWrite(ledPin, LOW);
  }
}
```

## Usage

1. Connect your Arduino to your computer via USB.
2. Open the Arduino IDE and upload the provided code to your Arduino.
3. Open the Serial Monitor (optional) to observe the sensor readings.
4. Place an object in front of the IR sensor to see the LED light up.
