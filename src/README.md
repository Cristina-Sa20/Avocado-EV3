Control software
====
In this commit, we will explain in detail the different routines, algorithms, control logics, and main programs developed for our robot. We will describe how the software is organized and how each part works together to control the robot’s movement, sensor readings, decision-making, and overall performance.

We will also include the main strategies used during the development process, as well as the adjustments and improvements made through testing. This section aims to provide a clear overview of our programming approach and make the control system easier to understand and reproduce.

# Programming Structure

Our programming was divided into three main versions, corresponding to the different competition rounds and the strategies we developed throughout the testing process. Instead of creating completely independent programs for each round, we reused and modified existing routines and constants, such as SeguidorDePared2, to improve the robot's performance and adapt it to different situations on the field.

The src folder contains the different programs used during the development of the robot. Since our goal is to make the project reproducible, we included both the .ev3 files used by the LEGO EV3 software and the .bp files containing the programming blocks. We also added explanations for the main programs to make their purpose and operation easier to understand.

### Programming Versions and File Formats

The repository contains both **`.bp`** and **`.ev3`** versions of our programs.

The **`.bp` files** are included so that the programming logic can be inspected and documented in the repository. They allow the main routines, variables, equations, conditions, and control algorithms to be reviewed.

The **`.ev3` files** are the programs used with the LEGO MINDSTORMS EV3 software. These files can be downloaded and opened in the EV3 programming environment to reproduce the corresponding program on the robot.

Some programs are therefore represented by both formats. The `.bp` version is provided mainly for transparency and documentation, while the `.ev3` version allows the program to be directly opened and used in the EV3 environment.

The repository also contains different versions of the wall-following program, including `seguidor de pared 1.ev3`, `seguidor de pared 2.ev3`, and `seguidor de pared avocado.ev3`. These files represent different iterations developed during testing.

## Main Control Logic

Our control system is based mainly on a **PD (Proportional-Derivative) control algorithm**. This algorithm allows the robot to continuously compare the desired value (`target`) with the current sensor or motor position and calculate a correction to keep the robot's movement stable.

The main variables used throughout our routines are:

* **`target`** – The desired sensor value or reference position that the robot tries to maintain.
* **`speed` / `Speed`** – The power applied to the main driving motor.
* **`kp`** – Proportional gain. It determines how strongly the robot reacts to the current error.
* **`kd`** – Derivative gain. It determines how strongly the robot reacts to changes in the error, helping reduce sudden oscillations.
* **`error`** – The difference between the desired condition and the current measured condition.
* **`lasterror`** – The previous error value, used to calculate the derivative component.
* **`correction`** – The value calculated by the PD controller.
* **`correction1`** – The final correction applied to the steering motor.
* **`C`** – The tachometer value obtained from Motor C, which provides information about the steering position.
* **`S1` and `S2`** – Intermediate values used to compare the steering position with the sensor-based reference.

The basic control equation used in our programs is:

`correction = (kp × error) + (kd × (error - lasterror))`

The calculated correction is then converted into a motor power value:

`correction1 = 1 - correction`

This value is sent to **Motor C**, which controls the steering mechanism, while **Motor B** controls the forward movement of the robot.

---

## 1. `SeguidorDePared`

`SeguidorDePared` is one of our basic wall-following routines. The robot moves forward using Motor B while continuously reading Sensor 1 and comparing its value with the target.

At the same time, Motor C provides the current steering position through its tachometer. These two values are compared to calculate the error:

`error = S1 - S2`

The PD controller then calculates the required steering correction. This allows the robot to continuously adjust its direction instead of using only fixed left and right movements.

This routine represents one of the foundations of our wall-following strategy and was later modified to create improved versions.

Source code:

C = MotorC.GetTacho() MotorB.SetPower(Speed) S1 = C S2 = (target - Sensor.ReadPercent(1)) × 8 error = S1 - S2 Correction = (kp × error) + (kd × (error - lasterror)) Correction1 = 1 - Correction Motor.StartPower("c", Correction1) lasterror = error

Files:

seguidorDePared.bp — View the programming logic.

seguidor de pared 1.ev3 — EV3 program available for download in the src folder.
---

## 2. `SeguidorDePared2`

`SeguidorDePared2` is an improved version of the wall-following routine. It follows the same general PD control structure, but the sensor-based value and the steering position are organized as:

`S1 = (Sensor.ReadPercent(1) - target) × 8`

`S2 = C`

The error is calculated from the difference between these two values, and the resulting correction is applied to Motor C.

The main purpose of this version was to obtain a more consistent relationship between the sensor reading and the steering angle while the robot was moving.

Source code:

C = MotorC.GetTacho() MotorB.SetPower(Speed) S1 = (Sensor.ReadPercent(1) - target) × 8 S2 = C error = S1 - S2 correction = (kp × error) + (kd × (error - lasterror)) correction1 = 1 - correction Motor.StartPower("c", correction1) lasterror = error

Files:

SeguidorDePared2.bp — View the programming logic.
seguidor de pared 2.ev3 — EV3 program available for download in the src folder.

---

## 3. `SSdeg`

`SSdeg` uses the same basic PD control strategy but is executed for a defined amount of motor rotation rather than continuously.

The routine begins by initializing the main control variables and setting the sensor mode. The robot then moves forward while:

`Motor.GetCount("b") <= degrees`

This allows the routine to control the robot for a specific distance or movement duration based on Motor B's tachometer count.

During this movement, Sensor 1 and Motor C are continuously compared, and the PD controller adjusts the steering motor.

This routine was useful when we needed a controlled movement over a specific number of degrees.

Source code:

While Motor.GetCount("b") <= degrees C = MotorC.GetTacho() MotorB.SetPower(speed) S1 = (Sensor.ReadPercent(1) - target) × 8 S2 = C error = S1 - S2 correction = (kp × error) + (kd × (error - lasterror)) correction1 = 1 - correction Motor.StartPower("c", correction1) lasterror = error EndWhile

Files:

SSdeg.bp — View the programming logic.
SSdeg.ev3 — EV3 program available for download in the src folder.

---

## 4. `SSdePared2`

`SSdePared2` combines the wall-following condition with the PD steering correction.

The routine continuously checks the value of **Sensor 2** and only performs the control loop while the sensor value is within the defined ranges:

`v > 50 and v < 90 or v > 135 and v < 180`

While this condition is true, Motor B moves the robot forward and Motor C adjusts the steering according to the PD controller.

This routine was developed to handle specific situations on the competition field where the robot needed to follow a wall while also checking an additional sensor condition.

Source code:

While v > 50 and v < 90 or v > 135 and v < 180 v = Sensor.ReadPercent(2) C = MotorC.GetTacho() MotorB.SetPower(speed) S1 = (Sensor.ReadPercent(1) - target) × 8 S2 = C error = S1 - S2 correction = (kp × error) + (kd × (error - lasterror)) correction1 = 1 - correction Motor.StartPower("c", correction1) lasterror = error EndWhile

Files:

SSdePared2.bp — View the programming logic.
SSdePared2.ev3 — EV3 program available for download in the src folder.

---

## 5. `CSDEG`

`CSDEG` is another movement routine based on a predefined number of degrees:

`While Motor.GetCount("b") <= degrees`

During this movement, Motor B provides forward motion while Motor C controls the steering. The routine compares the tachometer position of Motor C with the sensor-based reference and calculates the steering correction using the PD controller.

The main difference between this routine and `SSdeg` is the way the intermediate values are organized:

`S1 = C`

`S2 = (Sensor.ReadPercent(1) - target) × 8`

This represents another iteration of our control strategy, developed through testing and adjustments.

Source code:

While Motor.GetCount("b") <= degrees C = MotorC.GetTacho() MotorB.SetPower(speed) S1 = C S2 = (Sensor.ReadPercent(1) - target) × 8 error = S1 - S2 correction = (kp × error) + (kd × (error - lasterror)) correction1 = 1 - correction Motor.StartPower("c", correction1) lasterror = error EndWhile

Files:

CSDEG.bp — View the programming logic.
CSDEG.ev3 — EV3 program available for download in the src folder.

---

## 6. `CSDePared`

`CSDePared` is a wall-following routine that combines a sensor condition with PD steering control.

The program continuously checks Sensor 2 and executes the control logic only when its value falls within the specified ranges:

`v > 50 and v < 90 or v > 135 and v < 180`

While the condition is satisfied, Motor B moves forward and Motor C continuously adjusts the steering.

Unlike `SSdePared2`, the relationship between the sensor value and the motor tachometer is reversed:

`S1 = C`

`S2 = (target - Sensor.ReadPercent(1)) × 8`

This difference changes the direction and behavior of the calculated error and was part of our testing process to determine which configuration provided the best performance.

Source code:

While v > 50 and v < 90 or v > 135 and v < 180 v = Sensor.ReadPercent(2) MotorB.SetPower(Speed) C = MotorC.GetTacho() S1 = C S2 = (target - Sensor.ReadPercent(1)) × 8 error = S1 - S2 Correction = (kp × error) + (kd × (error - lasterror)) Correction1 = 1 - Correction Motor.StartPower("c", Correction1) lasterror = error EndWhile

Files:

CSDePared.bp — View the programming logic.
CSDePared.ev3 — EV3 program available for download in the src folder.

---



## Reproducibility

To reproduce our control system, the user should first assemble the robot according to the mechanical and electrical documentation provided in this repository. The sensors and motors must then be connected to the same ports used by the programs.

After the hardware configuration is complete, the corresponding `.ev3` program can be downloaded and opened using LEGO MINDSTORMS EV3 software. The `.bp` files can be used as a reference to understand the programming logic and reproduce or modify the routines.

The values of `speed`, `target`, `kp`, and `kd` must be configured according to the calibration of the robot. These parameters are important because changes in the robot's mechanical construction, sensor position, or motor behavior can affect the required control values.

Our different routines are the result of an iterative development process. Each version was tested on the field and modified according to the robot's behavior, allowing us to progressively improve stability, steering response, and reliability.

