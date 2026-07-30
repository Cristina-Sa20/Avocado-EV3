# Team Avocado - WRO Future Engineers 2026

# Engineering Materials

This repository contains the engineering materials of Team Avocado for the World Robot Olympiad (WRO) Future Engineers 2026 category.

The purpose of this repository is to document the complete engineering process followed during the design, construction, programming, testing, and improvement of our autonomous vehicle. Our objective is to make the project understandable and reproducible for judges, participants, and anyone interested in autonomous robotics.

---

# Team Information

**Team Name:** Avocado

**Institution:** Universidad Marítima Internacional de Panamá (UMIP)

**Category:** WRO Future Engineers 2026

## Team Members

- Hillary Cerrud (20 years old)
- Maria Salazar (19 years old)
- Alan Saldaña (20 years old)

---

# Project Description

Team Avocado developed an autonomous vehicle capable of navigating the official WRO Future Engineers track without human intervention.

The vehicle is designed to complete both the Open Challenge and the Obstacle Challenge by combining different sensors with autonomous control algorithms. Throughout the development process, the team focused on achieving a reliable, stable, and reproducible robot capable of adapting to different track conditions while maintaining smooth steering and accurate navigation.

The robot continuously collects information from its sensors, processes that information using the EV3 controller, and makes real-time decisions to maintain its trajectory and avoid obstacles.

---

# Hardware Design

The robot was designed using LEGO Mindstorms EV3 components combined with a steering system based on the Ackermann principle.

Our design priorities were:

- Mechanical stability
- Reliable steering
- Easy maintenance
- Modular construction
- Fast replacement of components

The chassis allows quick access to motors, sensors, and cables during testing and competition.

---

# Main Controller

The robot uses a LEGO Mindstorms EV3 intelligent brick as its central controller.

The EV3 is responsible for:

- Reading sensor data
- Processing navigation algorithms
- Controlling steering
- Controlling propulsion
- Correcting the vehicle trajectory

---

# Drive System

The vehicle uses rear-wheel drive powered by two EV3 Medium Motors.

This configuration provides:

- Stable acceleration
- Balanced weight distribution
- Better traction
- Independent motor control

---

# Steering System

The steering system follows the Ackermann steering principle.

A third EV3 Medium Motor controls the steering mechanism, allowing smooth turns while reducing wheel slipping during curves.

This configuration improves turning accuracy and increases vehicle stability.

---

# Sensors

The robot incorporates several sensors that work together.

## Ultrasonic Sensor

The ultrasonic sensor detects obstacles placed on the competition track.

It is mounted on a dynamic support that increases its field of view and allows better obstacle detection.

Its measurements are used to determine when the vehicle should begin obstacle avoidance maneuvers.

## Color Sensor

The color sensor detects the black guide lines of the WRO field.

These detections help the robot:

- Maintain lane position
- Detect reference points
- Improve navigation consistency

## Gyro Sensor

The gyro sensor measures the robot's rotation angle.

This information allows:

- Heading correction
- Straight-line stabilization
- More accurate turning
- Reduction of accumulated steering error

## Pixy2 Camera

-Function: Detects the red and green pillars on the competition field.

-Location: Mounted at the front of the robot to maximize the field of view.

-Reason for selection: Provides fast and reliable real-time color recognition, allowing the robot to identify the pillar color before executing a turn.

-Role in the robot:

🟢 Green pillar → Left turn

🔴 Red pillar → Right turn

-Advantage: Reduces processing time compared to image processing and improves navigation accuracy during obstacle avoidance.

---

# Software

The software was developed specifically for the WRO Future Engineers challenges.

The program continuously executes a control loop where sensor information is acquired, processed, and used to calculate the appropriate steering and motor commands.

The software is organized into modules to facilitate maintenance and future improvements.

The source code is located inside the `/src` directory.

---

# Repository Structure

The repository is organized following the official WRO Future Engineers guidelines.

## src

Contains all software used by the robot.

This includes navigation algorithms, sensor management, steering control, motor control, and autonomous decision making.

## schemes

Contains wiring diagrams showing how every electronic component is connected.

These diagrams allow another team to reproduce the electrical configuration.

## models

Contains CAD models and files used for manufacturing custom mechanical parts.

If no custom parts are required, this folder documents the mechanical design.

## t-photos

Contains official photographs of the team.

## v-photos

Contains photographs of the vehicle from every required angle.

## video

Contains links to the official demonstration videos.

---

# Robot Construction

The robot was assembled using LEGO structural components combined with a steering mechanism based on Ackermann geometry.

Particular attention was given to:

- Center of gravity
- Cable organization
- Sensor positioning
- Accessibility for maintenance

The modular design allows damaged components to be replaced quickly without rebuilding the complete vehicle.

---

# Testing

The robot was tested repeatedly before competition.

The testing process included:

- Straight-line driving
- Cornering accuracy
- Gyroscope calibration
- Color sensor verification
- Obstacle detection
- Steering adjustment
- Complete laps

After every testing session, software and mechanical adjustments were performed to improve consistency.

---

# Future Improvements

Future versions of the robot may include:

- Improved obstacle detection algorithms
- Better steering calibration
- Faster decision-making routines
- More efficient cable management
- Improved mechanical rigidity

---

# Demonstration Videos

Open Challenge

(Link)

Obstacle Challenge

(Link)

---

# Acknowledgements

We thank the Universidad Marítima Internacional de Panamá for supporting our participation in the World Robot Olympiad 2026 and encouraging engineering innovation through robotics.
