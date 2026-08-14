# Team Avocado - WRO Future Engineers 2026

# Engineering Materials

This repository contains the engineering materials of Team Avocado for the World Robot Olympiad™ (WRO®) Future Engineers 2026 category.

The purpose of this repository is to document the complete engineering process followed during the design, construction, programming, testing, and improvement of our autonomous vehicle. Our objective is to make the project understandable and reproducible for judges, participants, and anyone interested in autonomous robotics.


# Table of Contents

* [1. Presentation](#1-presentation)
  * [1.1 Teams Information](#11-teams-information)
  * [1.2 Project Description](#12-project-description)
  * [1.3 Demonstration Videos](#13-demonstration-videos)
* [2. Hardware Design](#2-hardware-design)
  * [2.1 Hardware Mechanisms](#21-hardware-mechanisms)
  * [2.2 Pros and Cons with 2 Ultrasonic](#22-pros-and-cons-with-2-ultrasonic)
  * [2.3 Pros and Cons with 1 Ultrasonic](#23-pros-and-cons-with-1-ultrasonic)
  * [2.4 Components](#24-components)
* [3. Mobility Management](#3-mobility-management)
  * [3.1 Main Controller](#31-main-controller)
  * [3.2 Drive System](#32-drive-system)
  * [3.3 Steering System](#33-steering-system)
* [4. Sensors](#4-sensors)
  * [4.1 Ultrasonic Sensor](#41-ultrasonic-sensor)
  * [4.2 Color Sensor](#42-color-sensor)
  * [4.3 Gyro Sensor](#43-gyro-sensor)
  * [4.4 Pixy2 Camera](#44-pixy2-camera)
* [5. Software](#5-software)
  * [5.1 Organization](#51-organization)
* [6. Repository Structure](#6-repository-structure)
  * [6.1 src](#61-src)
  * [6.2 schemes](#62-schemes)
  * [6.3 models](#63-models)
  * [6.4 t-photos](#64-t-photos)
  * [6.5 v-photos](#65-v-photos)
  * [6.6 video](#66-video)
* [7. Robot Construction](#7-robot-construction)
  * [7.1 Power and Voltage](#71-power-and-voltage)
* [8. Testing](#8-testing)
  * [8.1 Test Workflow](#81-test-workflow)
  * [8.2 Test Demonstration](#82-test-demonstration)
  * [8.3 Metrics Counterclockwise with Prototype 2](#83-metrics-counterclockwise-with-prototype-2)
  * [8.4 Boundary Cases](#84-boundary-cases)
* [9. Acknowledgements](#9-acknowledgements)

---
# 1.Presentation

## 1.1 Team Information

**Team Name:** Avocado

**Institution:** Universidad Marítima Internacional de Panamá (UMIP)

**Category:** WRO Future Engineers 2026

## Team Members

- Hillary Cerrud (20 years old)
- Maria Salazar (19 years old)
- Alan Saldaña (20 years old)
- Pepita (Robot- 3 months) The most important member.

  <img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/42f1640d-b047-4461-9aca-ed85e651d9a9" />


## 1.2 Project Description

Team Avocado developed an autonomous vehicle capable of navigating the official WRO Future Engineers track without human intervention.

The vehicle is designed to complete both the Open Challenge and the Obstacle Challenge by combining different sensors with autonomous control algorithms. Throughout the development process, the team focused on achieving a reliable, stable, and reproducible robot capable of adapting to different track conditions while maintaining smooth steering and accurate navigation.

The robot continuously collects information from its sensors, processes that information using the EV3 controller, and makes real-time decisions to maintain its trajectory and avoid obstacles.

## 1.3 Demonstration Videos

- First round open challenge:

  [![Watch video](https://img.youtube.com/vi/ajBkacQnERg/hqdefault.jpg)](https://youtube.com/shorts/ajBkacQnERg?feature=share)

Second Update

   [![Watch video](https://img.youtube.com/vi/UFrqMT3q9P4/maxresdefault.jpg)](https://youtu.be/UFrqMT3q9P4?si=ljdScA7mgKMssL3Y)

  
- Second round:

  
- Third Round Obstacle challenge: 

---

# 2.Hardware Design

The robot was designed using LEGO Mindstorms EV3 components from LEGO´s base and expansion sets, combined with some 3D printed materials and as a third-party element a Pixy Camera.

Our design priorities were:

- Mechanical stability
- Reliable steering
- Easy maintenance
- Modular construction
- Fast replacement of components
- Reliable chasis structure

Our chassis allows us a quick access to motors, sensors, and cables during testing and competition. We focused on an easy access to the different components of the robot maintaining a steady and reliable structure.

## 2.1 Hardware Mechanisms

Throught a lot of investigation, testing, evaluation and sketches we came down to this different mechanisms that were optimal and aligned with the vision we had for our robot:

- Ackerman Principle:
  At first we didn´t knew what ackerman principle was and how it worked in vehicles, the variations this principle had.
  We tested which one of it would be the one that fitted our robot and concluded that it was the Ackerman principle.



  After some testing we noticed different problems with our ackerman;

  1. Our steering was colliding with the robot´s chassis
     We ended up fixing this by putting 2 axles limiting the angle the steering could make, with this we still could make an optimal turn without the steering         and wheels colliding with our chassis.

  2. Our steering had too much backlash
     Our first prototype had its medium motor connected to the steering by a 90° with gears 1:1, it created to us 2 problems:
     
     -First, the gears and their backlash were making the robot had a bad steering when we didnt had any correction, the robot just running forward
       had a lot of trouble to not go to its right side.

     -The second problem it created was that the correction that our wallfollower or gyrostraight gave to the steering motor, had a delay and
      was mutliplying the error it accumulated.

    So our solution to this problem in the steering was to just delete the 90° 1:1 gears and just plug in directltly the motor to the steering, it made us change     part of the robot´s build but the correction and the smooth movement where completely worth it.


- Differential gear
  We decided to use differential gears because it was the mechanisim that most fitted the ackerman to help the robot have smooth turns, we ended up using
  the LEGO differential gear, we came to the conclusion that building one would useless because of how easy it would be for it to break when we had a relaible      one already.



- Moving Ultrasonic sensor
  We evaluated two different options for the ultrasonic sensor position that where:

  1. Using 2 ultrasonic sensors to read both walls at the same time
  2. Have only 1 ultrasonic sensor to read one wall at a time.
 
  Here are the Pros and Cons of each one
  2 ultrasonic

## 2.2 Pros and Cons with 2 ultrasonic

| Pros | Cons | 
| :--- | :---: |
| Precise correction to maintain between each wall | Would take 2 different ports leaving nothing for the camera or gyro |
| Could be connected to 1 port using a multiplexer| We couldnt afford a multiplexer and time was running.| 

             

## 2.3 Pros and Cons with 1 ultrasonic

| Pros | Cons | 
| :--- | :---: |
| 1 port only and would have to buy multiplexer | Could only focus on 1 wall at a time |
| Just 1 input for PD control leaving it easier to design the PD| Could be imprecise the moving of the sensor throught the runs.| 


After a week of evaluation we came down to the conclusion that we where going to use the movable ultrasonic sensor, the clock was ticking for the regional competition so buying a multiplexer wasnt really and option at that time.

After building it we decided to still use the ultrasonic sensor to know and help the robot locate itself in the field, we wanted it to be as autonomous as it could be, and it ended up being almost the same as having 2 ultrasonic sensor, we just trades 1 sensor slot for about 7 seconds that the robot uses doing the reading at the beginning of the rounds.

## 2.4 Components
The robot consists of a LEGO MINDSTORMS EV3 control system, three EV3 medium motors, an ultrasonic sensor, a colour sensor, a gyroscope, a Pixy2 camera, four wheels, an EV3 rechargeable battery and LEGO Technic structural components. Each component performs a specific function in the robot’s propulsion, steering, navigation, obstacle detection and control systems.

---
# 3. Mobility Management

## 3.1 Main Controller

The robot uses a LEGO Mindstorms EV3 intelligent brick as its central controller.

The EV3 is responsible for:

- Reading sensor data
- Processing navigation algorithms
- Controlling steering
- Controlling propulsion
- Correcting the vehicle trajectory


<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/24fbd5a3-4118-400f-88ea-1e4cbfaf9186" />

---

## 3.2 Drive System

The vehicle uses rear-wheel drive powered by two EV3 Medium Motors.

This configuration provides:

- Stable acceleration
- Balanced weight distribution
- Better traction
- Independent motor control


<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/fd2ab9c0-e092-40bb-ae14-d9954865237c" />

---

## 3.3 Steering System

The steering system follows the Ackermann steering principle.

A third EV3 Medium Motor controls the steering mechanism, allowing smooth turns while reducing wheel slipping during curves.

This configuration improves turning accuracy and increases vehicle stability.


<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/bf855d2f-2477-4fa9-b550-90d0ef3c7f2f" />

---

# 4.Sensors
This section explains the specifications of all sensors used for our robot.


## 4.1 Ultrasonic Sensor
We mainly use the ultrasonic sensor for 2 specific functions:

One of these functions is in PD correction, where the ultrasonic sensor detecs the nearest side wall and keeps the same distance it measured from the wall. 
The second function is to detect both walls to determine which quadrant of the canvas it is in, whether it's on the left, right, or in the middle. This allows the robot to know if it should adjust using the left wall or the right wall. 

¿Why did we decide to put it in that position?.

We decided to place it in that position to give it mobility since, due to the limited number of sensors, we needed it to be mobile to help with the robot's automation. We also preferred to use it at the front because this helps us correct faster during turns, allowing the PD to work better.

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/7413f9ae-dd6d-4344-86a1-62844ace468a" />


## 4.2 Color Sensor
The main function of the color sensor in the firs round is to count the blue and orange lines on the track to indicate how many sections the robot has gone through and when it's the last section so it can stop.
In the second lap of the first round, and also in the obstacle round, its function is so detect the first line, whether blue or orange, to tell the robot if it needs to turn left or right.

¿Why did decide to put it in that position? 

It´s  in that position because it's important that  this is the first input when the robot stars moving, since our robot's path heavily relies on floor  readings to determine the number of sections to travel, the turn direction, the robot's orientation, and the starting distance. So having the color sensor in the front is deal to receive this information as the first input.

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/702a3fb9-b5a4-4117-9ee8-860664435fd9" />


## 4.3 Gyro Sensor

The gyro sensor measures the robot's rotation angle.

This information allows:

- Heading correction
- Straight-line stabilization
- More accurate turning
- Reduction of accumulated steering error

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/46fcaa36-6cec-4f40-aac8-0108bf1b31d8" />


## 4.4 Pixy2 Camera
Its main function is to detect obstacles and the color of those obstacles in order to avoid them. If it reads green, it will dodge to the left, and if it reads red, it will dodge to the right. 

¿Why did we decide to put it in that position?

We placed it in that position because what we want with the camera is to be able to read the traffic light blocks inside the track from a good distance, but prioritizing that the reading is at an ideal distance to make maneuver. The main problem has been the angle since the camera must avoid reading outside the track because that could be harmful.

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/b794ad31-5a3d-48fc-9f57-cdeaeebc21ea" />


# 5. Software

The software was developed specifically for the WRO Future Engineers challenges.

The program continuously executes a control loop where sensor information is acquired, processed, and used to calculate the appropriate steering and motor commands.

The software is organized into modules to facilitate maintenance and future improvements.

## 5.1

---

# 6. Repository Structure

## 6.1 src

## 6.2 schemes

## 6.3 models

## 6.4 t-photos

In this file, you'll find photos of the team, a section titled “About Us,” and a description of our roles within the team.

## 6.5 v-photos

This file contains photos of the two prototypes of our autonomous vehicle, taken from different angles, along with a brief explanation.

## 6.6 video

When you open this file, you'll find some short videos and demonstration videos showing how the autonomous vehicle completes the competition rounds.
---

# 7.Robot Construction

The robot was assembled using LEGO structural components combined with a steering mechanism based on Ackermann geometry.

Particular attention was given to:

- Solid structure
- Center of gravity
- Sensor positioning
- Fast replacement components

The modular design allows damaged components to be replaced quickly without rebuilding the complete vehicle.



## 7.1 Power and voltage

| Component | Voltage | Current (mA)|
| :--- | :---: | ---: |
| **EV3 Rechargeable Battery / Charger** | 10 V | 700 mA |
| **Left Motor (EV3 Motor)** | 9 V |60 mA - 700 mA |
| **Right Motor (EV3 Motor)** | 9 V | 60 mA - 700 mA|
| **Pixy2 camara** | 5 V| 140 mA - 300 mA|
| **Color Sensor (LEGO EV3 / Arduino)**| 4.3 to 5 V| 15 mA - 30 mA|

---

# 8.Testing

The robot was tested repeatedly before competition.

The testing process included:

- Straight-line driving
- Cornering accuracy
- Gyroscope calibration
- Color sensor calibration in different ambients
- Obstacle detection
- Steering adjustment
- Complete laps
- Drift accummulated with each round

After every testing session, software and mechanical adjustments were performed to improve consistency.

## 8.1 Test workflow

Our goal in every practice was to correct our mistakes. During the first few weeks of practice, we didn’t use any notes at all — we did everything from memory — but this method yielded mediocre results, as mistakes we thought we’d already corrected kept cropping up again.

Seeing this, we started taking notes: in a notebook, we wrote down the test number, the direction (clockwise/counterclockwise), recorded values such as speed and direction, and wrote brief explanations of how the robot behaved in each round, with the goal of achieving greater precision. However, this method was a bit confusing because the entries weren’t organized properly, so it was easy to mix up the tests in terms of clockwise and counterclockwise movements, but there was a noticeable improvement in the way the robot moved. 

We continued using this method until after the first competition, when we decided to create tables in our notes listing the speed, kp, and kd values, and began timing the runs. However, we also had a separate table with the same values from the second method (speed, lap description, and direction). Using the third method—with two tables—is where we’ve seen the best results, correcting errors more quickly than with the first two methods. We decided to include pk, and kd and quredtos are important components of the calibration.

## 8.2 Test demonstration

This section will provide a general explanation, using a comparative table, of how these practices have evolved.

| Test | Result| 
| :--- | :---: | 
| **Prototype 1** | Out of 10 laps, only 5 were completed correctly | 
| **PID Change** | Out of 10 laps, only 4 were completed | 
| **Sensor Replacement** | 10 laps | 


## 8.3 Metrics Counterclockwise with prototype 2

| Laps | Velocity |Kd | Kp| Time | Description |
| :---:| :---: | :---:| :---:|:---:|:---:
|1| -60| 20| -60| 1:08|
|2| - 70| 20|-60|1:06|
|3| - 90|60|-60|1:05|
|4| -100|-120|-60|1:08|
|5| -100|-120|-45|1:05|
|6| -100|-120|-20|1:08|


## 8.4 Boundary cases

There are several borderline cases that, as the name suggests, are unlikely to happen, but if these occur, they could be the following.

If the pillars disappear, the robot would continue straight and go around not to detect any object, but with the probability that it will advance slowly compared to its normal speed.

If the camera fails, it would be the most extreme case and that you least want, but in that case we would choose to say STOP, since we are aware that we are not prepared for something like that.

If the color sensor stopped detecting the alteration that would be observed are the infinite revolutions, since with the color sensor we are guided by how many revolutions the robot must give and it can stop, but if this sensor the robot would enter a loop until it turned off manually.


---

# Acknowledgements

We thank the Universidad Marítima Internacional de Panamá for supporting our participation in the World Robot Olympiad 2026 and encouraging engineering innovation through robotics.
