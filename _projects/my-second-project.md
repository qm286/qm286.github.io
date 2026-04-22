---
title: High School Robotics Projects - Local Competition
layout: project
year: May 2022 - August 2024
project-url:
excerpt: Integrating embedded firmware on robots, IMU sensing, DC / brushless motor control, PCB design, and mechanical prototyping. Worked with Arduino Mega, STM32, SPI, I2C, PWM generation, electrical wiring, and system-level debugging.
project-image:
tags: [Embedded Firmware, Robotics, STM32, Arduino, IMU, PID Control, PCB Design, 3D Printing, Sensors, Prototyping]
order: 1
comments: true
---

- I programmed Arduino Mega and STM32 microcontrollers to read IMU and remote-controller data via SPI and I2C, then used that data for chassis motion and turret actuation.
- I implemented PID control for drivetrain motion, tuning the parameters to reduce drift and improve control stability.
- I modified MPU6050 internal registers through I2C to adjust the sensor sample rate for real-time control requirements, and programmed timer/counter registers to generate PWM signals for motor drivers and stepper control.
- I designed a 2-layer PCB shield in Altium with I2C/UART/SPI ports, reducing wiring time during prototyping by about 50%.
- I designed and 3D-printed custom robot parts, organized the wiring harness to reduce motor-induced noise, and helped lead a sub-team of three students to finish the project faster.