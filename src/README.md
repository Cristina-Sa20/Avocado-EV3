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
## Seguidor de pared avocado WRO.ev3

Seguidor de pared avocado WRO.ev3 is the final control program used for the WRO Future Engineers challenge. It integrates the routines required for the three competition rounds into a single EV3 program.
The program uses the robot's sensors and motors to execute the different movements required during the competition. Depending on the current round and the detected conditions, the program applies the corresponding control logic to navigate the field autonomously.
The three rounds are integrated into the same program rather than being stored as completely separate programs. This allows the team to use a single EV3 file while selecting or executing the appropriate routine for each competition situation.
The steering system is controlled through Motor C, while the drive motors provide forward movement. Sensor readings are continuously used to determine the robot's position and adjust its movement.
The control logic includes the parameters used during calibration, such as speed, kp, kd, and target, which determine how the robot responds to the detected conditions.



---



## Reproducibility

To reproduce our control system, the user should first assemble the robot according to the mechanical and electrical documentation provided in this repository. The sensors and motors must then be connected to the same ports used by the programs.

After the hardware configuration is complete, the corresponding `.ev3` program can be downloaded and opened using LEGO MINDSTORMS EV3 software. The `.bp` files can be used as a reference to understand the programming logic and reproduce or modify the routines.

The values of `speed`, `target`, `kp`, and `kd` must be configured according to the calibration of the robot. These parameters are important because changes in the robot's mechanical construction, sensor position, or motor behavior can affect the required control values.

Our different routines are the result of an iterative development process. Each version was tested on the field and modified according to the robot's behavior, allowing us to progressively improve stability, steering response, and reliability.

