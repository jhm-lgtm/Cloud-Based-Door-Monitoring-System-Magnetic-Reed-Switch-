# Cloud-Based-Door-Monitoring-System-Magnetic-Reed-Switch-
Designed to provide affordable and reliable perimeter security, this IoT setup utilizes magnetic reed sensors. Any break in the magnetic alignment (door opening) triggers a hardware interrupt on the ESP8266, which immediately transmits the event timestamp to a cloud dashboard. The system can activate local sirens and instant mobile push alerts.

# Firmware

This folder contains the firmware for the **Cloud-Based Door Monitoring System using a Magnetic Reed Switch**.

The firmware is developed for the **ESP8266 NodeMCU** and is responsible for monitoring the magnetic reed switch, detecting door open/close events, connecting to a Wi-Fi network, and transmitting door status to the configured cloud platform in real time.

## Features

* Real-time door status monitoring
* Magnetic reed switch event detection
* Wi-Fi connectivity using ESP8266
* Cloud data transmission
* Timestamp logging for door events
* Optional buzzer and LED indication
* Reliable and low-power operation

## Main File

* `Door_Monitoring_System.ino` – Main firmware source code for the ESP8266.

## Hardware

* ESP8266 NodeMCU
* Magnetic Reed Switch
* Magnet
* Optional Buzzer
* Optional LED Indicator
* 3.3V / 5V Power Supply

## Required Libraries

* ESP8266WiFi
* ArduinoJson
* Firebase ESP Client / Blynk / ThingSpeak libraries (depending on the cloud platform used)

## Upload Instructions

1. Install the ESP8266 Board Package in Arduino IDE.
2. Install all required libraries.
3. Open `Door_Monitoring_System.ino`.
4. Enter your Wi-Fi credentials and cloud configuration.
5. Select the correct ESP8266 board and COM port.
6. Upload the firmware to the ESP8266.
7. Open the Serial Monitor to verify the Wi-Fi connection and door status events.

## Notes

* Update the Wi-Fi SSID and password before uploading.
* Configure the cloud platform credentials (such as API keys or database URL) in the firmware.
* Verify that the reed switch is connected to the correct GPIO pin defined in the code.
