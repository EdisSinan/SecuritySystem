# STM32-Based Security System

This project is a security system implemented on an STM32 microcontroller. It integrates RFID authentication, ultrasonic distance sensing, a keypad for password entry, and a buzzer for alerts. The system is designed to provide a robust security mechanism by combining multiple authentication methods and real-time monitoring.

---

## Features

- **RFID Authentication**: Uses the MFRC522 RFID module to authenticate users via RFID cards.
- **Ultrasonic Distance Sensing**: Measures distance using an HC-SR04 ultrasonic sensor to detect proximity.
- **Keypad Password Entry**: A 4x4 keypad allows users to enter a password for additional authentication.
- **Buzzer Alerts**: A buzzer provides audible feedback for system events such as unauthorized access or successful authentication.
- **LED Indicators**: An LED indicates the system's status (e.g., armed or disarmed).
- **Modular Design**: The code is modular, making it easy to extend or modify functionality.

---

## Hardware Requirements

- STM32 Microcontroller (e.g., STM32F4)
- MFRC522 RFID Module
- HC-SR04 Ultrasonic Sensor
- 4x4 Matrix Keypad
- Buzzer
- LED
- Jumper Wires
- Breadboard (optional)

---

## Software Requirements

- STM32CubeIDE or any compatible IDE
- STM32 HAL Library
- Libraries for MFRC522, Keypad, and Buzzer

---

## Setup and Configuration

### Hardware Connections

1. **RFID Module (MFRC522)**:
   - Connect the SPI pins (MOSI, MISO, SCK, NSS) to the STM32.
   - Connect the RST pin to a GPIO pin on the STM32.

2. **Ultrasonic Sensor (HC-SR04)**:
   - Connect the TRIG pin to a GPIO output pin.
   - Connect the ECHO pin to a GPIO input pin.

3. **4x4 Keypad**:
   - Connect the rows and columns to GPIO pins on the STM32.

4. **Buzzer**:
   - Connect the buzzer to a PWM-capable GPIO pin.

5. **LED**:
   - Connect the LED to a GPIO pin via a current-limiting resistor.

### Software Configuration

1. **Clock Configuration**:
   - Set up the system clock using the RCC (Reset and Clock Control) module.

2. **Peripheral Initialization**:
   - Initialize SPI for the RFID module.
   - Configure GPIO pins for the ultrasonic sensor, keypad, buzzer, and LED.
   - Set up timers for PWM (buzzer) and distance measurement.

3. **Libraries**:
   - Include the `stm32f4_rc522.h` library for RFID functionality.
   - Include the `MY_Keypad4x4.h` library for keypad input.
   - Include the `buzzer.h` library for buzzer control.

---

## Code Overview

### Main Functionality

1. **RFID Authentication**:
   - The system continuously checks for an RFID card.
   - If a valid card is detected, the system grants access and disables the alarm.

2. **Ultrasonic Distance Sensing**:
   - The system measures the distance using the ultrasonic sensor.
   - If an object is detected within a predefined range (e.g., 10 cm), the system triggers the alarm.

3. **Keypad Password Entry**:
   - If the alarm is triggered, the user can enter a 4-digit password using the keypad.
   - If the password is correct, the system disables the alarm.

4. **Buzzer and LED Feedback**:
   - The buzzer provides audible feedback for system events.
   - The LED indicates the system's status (e.g., ON for armed, OFF for disarmed).

### Key Functions

- **`MFRC522_Request()`**: Requests an RFID card.
- **`MFRC522_Anticoll()`**: Handles RFID card collisions.
- **`Keypad4x4_ReadKeypad()`**: Reads input from the 4x4 keypad.
- **`BUZZER_Go()`**: Activates the buzzer with a specific frequency and duration.
- **`HAL_GPIO_WritePin()`**: Controls the LED and ultrasonic sensor.

---

## Usage

1. **Power On**:
   - The system initializes and enters the main loop.

2. **RFID Authentication**:
   - Present a valid RFID card to grant access.

3. **Proximity Detection**:
   - If an object is detected within the predefined range, the system triggers the alarm.

4. **Password Entry**:
   - Use the keypad to enter the 4-digit password to disable the alarm.

5. **System Feedback**:
   - The buzzer and LED provide real-time feedback on the system's status.

---

## Example Workflow

1. The system starts in the "armed" state (LED ON).
2. An object is detected within 10 cm, triggering the alarm (buzzer sounds).
3. The user enters the correct password on the keypad.
4. The system disables the alarm (LED OFF, buzzer stops).

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Thanks to the STMicroelectronics team for the STM32 HAL Library.
- Thanks to the developers of the MFRC522 and Keypad libraries.

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

---

## Contact

For any questions or support, please contact [Your Name] at [your.email@example.com].

---

This README provides a comprehensive overview of the project, including setup instructions, usage, and a description of the code. Feel free to customize it further to suit your needs!