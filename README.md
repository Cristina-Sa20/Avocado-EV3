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

# 1.Hardware Design

The robot was designed using LEGO Mindstorms EV3 components from LEGO´s base and expansion sets, combined with some 3D printed materials and as a third-party element a Pixy Camera.

Our design priorities were:

- Mechanical stability
- Reliable steering
- Easy maintenance
- Modular construction
- Fast replacement of components
- Reliable chasis structure

Our chassis allows us a quick access to motors, sensors, and cables during testing and competition. We focused on an easy access to the different components of the robot maintaining a steady and reliable structure.

## 1.1 Hardware Mechanisms

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

## 1.2 Pros and Cons

| Pros | Cons | Opción B |
| :--- | :---: | ---: |
| Precise correction to maintain between each wall | Would take 2 different ports leaving nothing for the camera or gyro |
| Could be connected to 1 port using a multiplexer| We couldnt afford a multiplexer and time was running.
 | 

             

1 movable ultrasonic

            Pros                                                              Cons
- 1 port only and would have to buy multiplexer                                - Could only focus on 1 wall at a time
- Just 1 input for PD control leaving it easier to design the PD               - Could be imprecise the moving of the sensor throught the runs.

After a week of evaluation we came down to the conclusion that we where going to use the movable ultrasonic sensor, the clock was ticking for the regional competition so buying a multiplexer wasnt really and option at that time.

After building it we decided to still use the ultrasonic sensor to know and help the robot locate itself in the field, we wanted it to be as autonomous as it could be, and it ended up being almost the same as having 2 ultrasonic sensor, we just trades 1 sensor slot for about 7 seconds that the robot uses doing the reading at the beginning of the rounds.

---

# 2.Main Controller

The robot uses a LEGO Mindstorms EV3 intelligent brick as its central controller.

The EV3 is responsible for:

- Reading sensor data
- Processing navigation algorithms
- Controlling steering
- Controlling propulsion
- Correcting the vehicle trajectory

---

# 3.Drive System

The vehicle uses rear-wheel drive powered by two EV3 Medium Motors.

This configuration provides:

- Stable acceleration
- Balanced weight distribution
- Better traction
- Independent motor control

---

# 4.Steering System

The steering system follows the Ackermann steering principle.

A third EV3 Medium Motor controls the steering mechanism, allowing smooth turns while reducing wheel slipping during curves.

This configuration improves turning accuracy and increases vehicle stability.

---

# 5.Sensors

The robot incorporates several sensors that work together.

## 5.1 Ultrasonic Sensor

The ultrasonic sensor detects obstacles placed on the competition track.

It is mounted on a dynamic support that increases its field of view and allows better obstacle detection.

Its measurements are used to determine when the vehicle should begin obstacle avoidance maneuvers.

## 5.2 Color Sensor

The color sensor detects the black guide lines of the WRO field.

These detections help the robot:

- Detect reference points
- Improve navigation consistency

## 5.3 Gyro Sensor

The gyro sensor measures the robot's rotation angle.

This information allows:

- Heading correction
- Straight-line stabilization
- More accurate turning
- Reduction of accumulated steering error

## 5.4 Pixy2 Camera

-Function: Detects the red and green pillars on the competition field.

-Location: Mounted at the front of the robot to maximize the field of view.

-Reason for selection: Provides fast and reliable real-time color recognition, allowing the robot to identify the pillar color for the robot to make a decision for the turn.

-Role in the robot:

Green pillar → Left turn

Red pillar → Right turn

-Advantage: Reduces processing time compared to image processing.

---

# 6. Software

The software was developed specifically for the WRO Future Engineers challenges.

The program continuously executes a control loop where sensor information is acquired, processed, and used to calculate the appropriate steering and motor commands.

The software is organized into modules to facilitate maintenance and future improvements.

---

# 7.Repository Structure

## 7.1 src

## 7.2 schemes

## 7.3 models

## 7.4 t-photos

## 7.5 v-photos

## 7.6 video
---

# 8.Robot Construction

The robot was assembled using LEGO structural components combined with a steering mechanism based on Ackermann geometry.

Particular attention was given to:

- Solid structure
- Center of gravity
- Sensor positioning
- Fast replacement components

The modular design allows damaged components to be replaced quickly without rebuilding the complete vehicle.

---

# 9.Testing

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

## 9.1 Test workflow

Our goal in every practice was to correct our mistakes. During the first few weeks of practice, we didn’t use any notes at all — we did everything from memory — but this method yielded mediocre results, as mistakes we thought we’d already corrected kept cropping up again.

Seeing this, we started taking notes: in a notebook, we wrote down the test number, the direction (clockwise/counterclockwise), recorded values such as speed and direction, and wrote brief explanations of how the robot behaved in each round, with the goal of achieving greater precision. However, this method was a bit confusing because the entries weren’t organized properly, so it was easy to mix up the tests in terms of clockwise and counterclockwise movements, but there was a noticeable improvement in the way the robot moved. 

We continued using this method until after the first competition, when we decided to create tables in our notes listing the speed, kp, and kd values, and began timing the runs. However, we also had a separate table with the same values from the second method (speed, lap description, and direction). Using the third method—with two tables—is where we’ve seen the best results, correcting errors more quickly than with the first two methods. We decided to include pk, and kd and quredtos are important components of the calibration.

## 9.2 Test demonstration

This section will provide a general explanation, using a comparative table, of how these practices have evolved.

| Test | Result| 
| :--- | :---: | 
| **Prototype 1** | Out of 10 laps, only 5 were completed correctly | 
| **Soporte** | Comunidad | 
| **Almacenamiento** | 5 GB | 




---

# Future Improvements

---
# Demonstration Videos

---

# Acknowledgements

We thank the Universidad Marítima Internacional de Panamá for supporting our participation in the World Robot Olympiad 2026 and encouraging engineering innovation through robotics.
