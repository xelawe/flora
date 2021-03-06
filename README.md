## flora

This arduino sketch implements an ESP32 BLE client for XIaomi Mi Flora Plant sensors, pushing the meaasurements to an MQTT server.

## Technical requirements

Hardware:
- ESP32
- Xiaomi Mi Plant Sensor (firmware revision >= 2.6.6)

Software:
- MQTT server

## Setup instructions

1) Copy config.h.example into config.h and update seetings according to your environment:
- WLAN SSID and password
- MQTT Server address
- MAC address of your Xiaomi Mi Plant sensor

2) Open ino sketch in Arduino, compile & upload. 

## Measuring interval

The ESP32 will perform a single connection attempt to the Xiaomi Mi Plant sensor, read the sensor data & push it to the MQTT server. The ESP32 will enter deep sleep mode after 30 seconds (can be configured in config.h) and sleep for one hour (also configurable in config.h), before repeating the exercise...

## Constraints

Some "nice to have" features are not yet implemented or cannot be implemented:
  - The sketch only works for a single Xiaomi Mi Plant sensore. If you have multiple of them, you'll need to change the sketch accordingly or run multiple ESP32 clients
  - Sensor Battery level: My sensor is brand new, so I was too lazy to implement this so far.
  - OTA updates: I didn't manage to implement OTA update capabilities due to program size constraints: BLE and WLAN brings the sketch up to 90% of the size limit, so I decided to use the remaining 10% for something more useful than OTA...
  - MQTT username & password
  
## Credits

Many thanks go to the guys at https://github.com/open-homeautomation/miflora for figuring out the sensor protocol.
  
