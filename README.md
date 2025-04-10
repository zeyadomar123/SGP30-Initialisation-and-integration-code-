# SGP30-Initialisation-and-integration-code-
# RFID-Based CO₂ Monitoring System – STM32 Firmware

This repository contains the embedded C firmware developed for the STM32 microcontroller as part of the RFID-based CO₂ Environmental Monitoring System. The system measures indoor air quality using the SGP30 gas sensor and communicates the results to other devices via UART. This data can then be logged, written to an RFID tag using a separate ESP32-based RFID module, or used for machine learning predictions.

## Purpose

The main objective of this firmware is to enable real-time communication with the SGP30 CO₂ and TVOC sensor using I²C, and transmit readings via UART. The firmware is optimized for low-power operation and reliable I²C data acquisition, with fault handling and restart logic included for stability.

## Project Structure

- `main.c` – Core firmware containing sensor control logic and UART output
- `SGP30_ReadAirQuality()` – Reads CO₂ and TVOC data over I²C
- `I2C_Write()` and `I2C_Read()` – Handles low-level communication with the sensor
- `UART_Transmit()` – Sends formatted sensor data to connected device
- `MX_I2C1_Init()` & `MX_USART2_UART_Init()` – Peripheral configuration

## Hardware Connections

- **SGP30 Sensor (I²C)**
  - SDA → PB9
  - SCL → PB8
- **UART Output (to ESP32 or PC)**
  - TX → PA2
  - RX → PA3
- Operating Voltage: 3.3V (regulated by STM32)

## How to Build and Flash

1. Open the project in **STM32CubeIDE 1.17.0**.
2. Connect the STM32 NUCLEO board via USB.
3. Flash the code using the “Run” button in the IDE.
4. Open a serial monitor at 115200 baud to view CO₂ and TVOC output.

## UART Output Example

