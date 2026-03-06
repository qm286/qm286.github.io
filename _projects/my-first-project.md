---
title: Trip range estimator for electricity scooters
layout: project
year: June 2025 - August 2025
project-url: https://github.com/qm286/Decode-E-scooter-Battery
excerpt: I built a device to estimate the trip range based on real-time data. I collected the speed directly from motor (through software-based filter with 99.9% accuracy). I also reverse-engineered the data protocol from battery mainboard (byte by byte) to get battery-related data. 
project-image: 
tags: [Low-level C Programming, Signal Analysis, Reverse-Engineering, Android OS, Bluetooth GATT, ESP32, Saleae Logic]
comments: true
---

I built a device to estimate the trip range based on real-time data. This device consist of an ESP32 microcontroller (MCU), a RS485-TTL communication module.
- The ESP32 MCU with built-in Bluetooth hardware layer sends the scooter data (speed, remaining battery, trip estimation) to an Android OS device via "BLE-notify" method. 
- The MCU also collect battery data via RS485-TTL modules and speed data directly from motor by pulse-counting method. Its program has filter algorithm so that 98% of glitch noise will be dismissed.
- The RS485-TTL communcation module was in charge of communicating (in the RS485 protocol) between the MCU and the Battery Management System (BMS) circuit board.

I collected the speed directly from motor (through software-based filter with 99.9% accuracy). 
- I analyzed them using the Logic Analyzer from Saleae Logic. 
- The signal was from Hall sensor, since the Hall-effect caused glitch noise every 50 nanoseconds, so I developed an algorithm that filtered out 100% of noise, leaving fresh digital signal streaming.

I also reverse-engineered the data protocol from battery mainboard (byte by byte) to get battery-related data. 
- The BMS product model is JK-BD6A20s10p, manufactured by the Chengdu Jikong, came without datasheet / register map to extract data. 
- I decoded the datastreaming between its and their official software called JK-BMS, using third-party app called Serial Port Monitor. I recorded many bytes and translated them back to the battery-related specification.