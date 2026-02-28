---
title: Building an Autonomous Line Following & Obstacle Avoiding Robot
date: 2025-11-28 20:00:00
layout: post
categories: [Embedded Systems]
tags: [Robotics, Arduino, Line Following, Ultrasonic, Control System]
toc: true
---

# 🤖 Autonomous Line Following & Obstacle Avoiding Robot

![Project Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Language](https://img.shields.io/badge/Language-C%2B%2B%20%2F%20Arduino-blue?style=for-the-badge)
![Hardware](https://img.shields.io/badge/Hardware-Arduino%20Uno%20%2B%20L293D-orange?style=for-the-badge)

---

## 📖 Introduction — The First Time My Code Moved

There is a special moment in every embedded engineer’s journey.

It’s the moment when your code stops being lines on a screen —  
and starts moving something in the real world.

For me, that moment was this robot.

This 2WD Autonomous Line Following & Obstacle Avoiding Robot was developed during my freshman year at HCMUTE. At first glance, it might look like a simple Arduino project. But behind it lies the integration of sensing, control logic, real-time decision-making, and hardware stability — all running on a small 8-bit microcontroller.

This was my first step into building systems that can:

- Sense the environment  
- Process information  
- Make decisions  
- Act autonomously  

---

## 🚀 System Overview

The robot operates in two intelligent modes:

### 1️⃣ Line Following Mode  

Using three TCRT5000 infrared sensors, the robot detects a black line on a white surface and continuously adjusts its trajectory.

### 2️⃣ Obstacle Avoidance Mode  

When an object is detected within a safety threshold using the HC-SR04 ultrasonic sensor, the robot switches behavior, scans the surroundings with a servo-mounted sensor, and selects the safest direction.

This dual-behavior architecture mimics how autonomous systems layer reactive control with environmental awareness.

---

<div align="center">
  <img width="783" height="865" alt="Image" src="https://github.com/user-attachments/assets/b19ad3b1-68bb-4d9a-ab6a-2e98bd905440" />
  &nbsp;
  <img width="751" height="819" alt="Image" src="https://github.com/user-attachments/assets/f416d7b6-39aa-43cf-a866-815bf3777b4b" />
  <br><br>
  <img width="801" height="819" alt="Image" src="https://github.com/user-attachments/assets/a593ed22-a1fd-4fed-b917-654105f57e17" />
</div>


---

## 🛠️ Hardware Architecture

At the core of the system is the **Arduino Uno R3**, handling sensor acquisition and motor control through an L293D Motor Shield.

| Component           | Specification                     | Quantity |
| :------------------ | :-------------------------------- | :------: |
| **MCU**             | Arduino Uno R3                    |    1     |
| **Driver**          | L293D Motor Shield                |    1     |
| **Motors**          | DC Gear Motors (Yellow, 1:48)     |    2     |
| **Line Sensors**    | TCRT5000 IR Sensor (3-Channel)    |    1     |
| **Distance Sensor** | HC-SR04 Ultrasonic                |    1     |
| **Servo**           | SG90 Micro Servo                  |    1     |
| **Power**           | 18650 Li-ion Batteries (3.7V x 2) |    2     |
| **Regulator**       | LM2596 Buck Converter (5V Out)    |    1     |
| **Chassis**         | Acrylic 2WD Smart Car             |    1     |

One of the most important lessons here was power integrity.  
DC motors generate noise and voltage drops. Without proper regulation, sensor readings become unstable. The LM2596 buck converter ensured consistent 5V supply and system reliability.

---

## 🔌 Pin Configuration

### Line Tracking Sensors

| Position           | Arduino Pin |
| :----------------- | :---------: |
| Left Sensor (SL)   |   **A5**    |
| Middle Sensor (SM) |   **A4**    |
| Right Sensor (SR)  |   **A3**    |

### Obstacle Avoidance Modules

| Component      |  Pin   | Connected To |
| :------------- | :----: | :----------: |
| **HC-SR04**    |  Trig  |    **A1**    |
|                |  Echo  |    **A0**    |
| **Servo SG90** | Signal |  **Pin 9**   |

---

## 🧠 Control Logic — Where Intelligence Happens

### 🔹 Line Following

Instead of implementing a full PID controller, I designed a lightweight correction-based logic:

- Middle detects line → Move forward  
- Left detects line → Reduce left motor speed  
- Right detects line → Reduce right motor speed  

This approach balances responsiveness with limited MCU resources.

---

### 🔹 Obstacle Avoidance

When:

The robot:

1. Stops immediately  
2. Reverses slightly  
3. Rotates the ultrasonic sensor  
4. Measures left and right clearance  
5. Turns toward the safer direction  

This behavior is implemented using a Finite State Machine (FSM), ensuring structured and predictable transitions between movement states.

---

## ⚙ Engineering Challenges

This project exposed me to real-world embedded problems:

- Motor-induced electrical noise  
- Sensor calibration under varying light conditions  
- Timing conflicts between servo movement and motor control  
- Trade-offs between algorithm complexity and hardware limitations  

These are problems you don’t fully understand until hardware starts behaving unexpectedly.

---

## 🎯 Why This Project Matters

This robot was more than a class assignment.

It was the first time I built a system that:

- Interacts with the physical world  
- Makes autonomous decisions  
- Demonstrates real-time embedded behavior  

It marked the beginning of my interest in building full-stack embedded systems — from low-level firmware to intelligent IoT architectures.

---

## 👤 Author

**Nguyen Phu Huu**  
Electronics & Telecommunications Technology – HCMUTE  

---

## 🎓 Acknowledgments

Special thanks to **Lecturer Phan Van Ca** for his guidance in the *Introduction to ECET* course.

---

## 📝 License

This project is open-source and available under the [MIT License](https://github.com/HuuzNg312/Autonomous-Line-Following-Obstacle-Avoiding-Robot)
