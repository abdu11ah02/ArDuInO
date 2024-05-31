# Arduino Sonar Sensor Project

This repository contains the code and instructions for interfacing a sonar sensor with an Arduino. The sonar sensor can be used to measure distance to an object by using ultrasonic sound waves.

## Table of Contents

- [Arduino Sonar Sensor Project](#arduino-sonar-sensor-project)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Components](#components)
  - [Circuit Diagram](#circuit-diagram)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Code Explanation](#code-explanation)

## Introduction

This project demonstrates how to use a sonar sensor (HC-SR04) with an Arduino to measure distance. The sonar sensor sends out an ultrasonic pulse and measures the time it takes for the echo to return. This time is then converted into a distance measurement.

## Components

- Arduino (Uno, Mega, or any compatible board)
- HC-SR04 Ultrasonic Sonar Sensor
- Breadboard
- Jumper Wires

## Circuit Diagram

Below is the schematic for connecting the HC-SR04 sonar sensor to the Arduino:

```
HC-SR04        Arduino
VCC ---------- 5V
GND ---------- GND
TRIG --------- D9
ECHO --------- D10
```


## Installation


1. **Open the project in the Arduino IDE:**
    - Launch the Arduino IDE.
    - Open the `sonar_sensor.ino` file from the cloned repository.

2. **Install necessary libraries:**
    - Ensure you have the `NewPing` library installed. If not, you can install it via the Library Manager in the Arduino IDE:
      - Go to `Sketch` -> `Include Library` -> `Manage Libraries...`
      - Search for `NewPing` and install it.

## Usage

1. **Connect the components as per the circuit diagram.**
2. **Upload the code to your Arduino:**
    - Select the correct board and port in the Arduino IDE.
    - Click on the upload button to upload the code to the Arduino.

3. **Open the Serial Monitor:**
    - Go to `Tools` -> `Serial Monitor` or press `Ctrl+Shift+M`.
    - Set the baud rate to `9600`.

You should see the distance measurements being printed on the Serial Monitor.

## Code Explanation

Here is a brief explanation of the provided code:

```cpp
#include <NewPing.h>

#define TRIG_PIN 9
#define ECHO_PIN 10
#define MAX_DISTANCE 200

NewPing sonar(TRIG_PIN, ECHO_PIN, MAX_DISTANCE);

void setup() {
  Serial.begin(9600);
}

void loop() {
  delay(50);
  unsigned int uS = sonar.ping();
  Serial.print("Distance: ");
  Serial.print(uS / US_ROUNDTRIP_CM);
  Serial.println(" cm");
}
```

- **Libraries and Pin Definitions:**
  - `NewPing.h` library is included to simplify the sonar sensor interaction.
  - `TRIG_PIN` and `ECHO_PIN` are defined as 9 and 10, respectively.
  - `MAX_DISTANCE` is set to 200 cm, the maximum distance to measure.

- **Setup Function:**
  - Initializes the serial communication at 9600 baud rate.

- **Loop Function:**
  - Introduces a delay of 50 ms between measurements.
  - Uses `sonar.ping()` to send a ping and get the echo time in microseconds.
  - Converts the time to distance and prints it to the Serial Monitor.
