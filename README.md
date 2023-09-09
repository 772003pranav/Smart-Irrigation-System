# Smart Irrigation System Readme

## Overview

This README file provides an overview and explanation of the code for a Smart Irrigation System using an Arduino and various components. The system is designed to monitor soil temperature and automatically control a water pump to irrigate the soil when necessary.

## Components Required
- Arduino board (e.g., Arduino Uno)
- Liquid Crystal Display (LCD)
- Temperature sensor (connected to A1)
- Motor driver (connected to pins 10 and 11)
- Red and Green LEDs (connected to pins 12 and 9, respectively)
- Buzzer (connected to pin 8)

## Libraries Used
The code relies on the "LiquidCrystal" library for interfacing with the LCD display. Ensure that this library is installed in your Arduino IDE.

## Code Structure

### `setup()`
- Initializes serial communication at a baud rate of 9600 for debugging purposes.
- Sets up the LCD display with the specified pin connections.
- Initializes pins for various components, including the LEDs, buzzer, motor driver, and temperature sensor.
- Clears the LCD display and displays initial information.

### `loop()`
This is the main loop of the program, where the system continuously monitors the soil temperature and takes action accordingly.

- Reads the analog value from the temperature sensor (connected to pin A1).
- Converts the analog value to temperature (in degrees) and displays it on both the serial monitor and the LCD.
- Checks if the soil temperature is greater than 50 degrees Celsius:
  - If the temperature is high, it indicates a need for irrigation.
  - Activates the water pump (motor driver) to irrigate the soil.
  - Turns on the red LED, indicating a warning.
  - Activates a buzzer to generate a sound.
  - Displays "ON" on the LCD.
  - Outputs relevant messages to the serial monitor.
- If the soil temperature is within an acceptable range (<= 50 degrees Celsius):
  - Deactivates the water pump.
  - Turns off the red LED and buzzer.
  - Turns on the green LED, indicating normal conditions.
  - Displays "OFF" on the LCD.
  - Outputs a message to the serial monitor indicating that the soil temperature is fine.

## Usage
1. Connect all the components as per the specified pin connections in the code.
2. Upload the code to your Arduino board using the Arduino IDE.
3. Open the serial monitor to view the real-time soil temperature readings and system status.
4. Observe the LCD display for temperature and system status.
5. The system will automatically activate the water pump and provide warnings when the soil temperature exceeds 50 degrees Celsius.
6. Adjust the temperature threshold in the code as needed for your specific application.

## Note
- Make sure to power the water pump and any other external components as required.
- Ensure that the temperature sensor is calibrated and provides accurate readings.
- Customize the code further to add more features or integrate additional sensors for a more comprehensive irrigation system.

**Caution:** Be cautious when working with electrical components and water. Ensure proper safety measures to avoid electrical hazards and water damage.
