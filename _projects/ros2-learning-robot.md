---
title: ROS2 Mobile Robot — IMU/Encoder Odometry & Motor Control
layout: project
year: 2026 - Present
project-url: https://github.com/qm286/ros2-learning-robot
excerpt: Built a differential-drive mobile robot from scratch on a Raspberry Pi 5 running ROS2 Jazzy — IMU/encoder sensor fusion for odometry, PID-based closed-loop motor control, and hardware-level GPIO/I2C debugging, all in Python.
project-image: assets/images/projects/ros2-learning-robot/thumb1.jpg
thumbnails:
  - assets/images/projects/ros2-learning-robot/thumb1.jpg
  - assets/images/projects/ros2-learning-robot/thumb2.jpg
  - assets/images/projects/ros2-learning-robot/thumb3.jpg
images:
  - src: assets/images/projects/ros2-learning-robot/placeholder.jpg
    caption: Photo coming soon — replace with a real robot/hardware shot
tags: [ROS2, Python, Raspberry Pi, IMU, Wheel Odometry, PID Control, I2C, GPIO, Differential Drive, Sensor Fusion]
order: 3
comments: true
---

- Designed and deployed a set of modular ROS2 nodes (`imu_node`, `odom_node`, `motor_driver_node`) in Python for a differential-drive robot running Ubuntu Server 24.04 / ROS2 Jazzy on a Raspberry Pi 5.
- Interfaced a BNO055 9-DOF IMU over I2C at a non-default address (ADR pin pulled high), publishing orientation data verified at 30Hz on real hardware; repositioned the sensor 10cm above the chassis, cutting motor-induced magnetometer noise by ~84%.
- Implemented wheel odometry combining IMU heading with quadrature encoder data (223 ticks/rev, 65mm wheels) through a complementary filter, publishing `/odom` and the `odom→base_link` TF at a verified 20Hz, with heading and twist sign conventions matching REP-103.
- Built a PID-based motor controller (TB6612FNG driver) for closed-loop wheel-speed regulation plus a heading-hold correction loop compensating for physical drivetrain imbalance; verified straight-line, reverse, and in-place pivot motion on hardware.
- Root-caused a reverse/pivot drift bug to a missing runtime dependency between two concurrently-running nodes rather than a kinematics or encoder-sign error — isolated it by cross-checking wheel setpoints against differential-drive kinematics before finding the real cause.
- Diagnosed and documented a GPIO resource conflict (`lgpio.error: GPIO busy`) between two nodes sharing encoder pins, and scoped out the node-splitting fix needed to resolve it.
