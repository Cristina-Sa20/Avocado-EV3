Control software
====
In this commit, we will explain in detail the different routines, algorithms, control logics, and main programs developed for our robot. We will describe how the software is organized and how each part works together to control the robot’s movement, sensor readings, decision-making, and overall performance.

We will also include the main strategies used during the development process, as well as the adjustments and improvements made through testing. This section aims to provide a clear overview of our programming approach and make the control system easier to understand and reproduce.

# Programming Structure

Our programming was divided into three main versions, corresponding to the different competition rounds and the strategies we developed throughout the testing process. Instead of creating completely independent programs for each round, we reused and modified existing routines and constants, such as SeguidorDePared2, to improve the robot's performance and adapt it to different situations on the field.

The src folder contains the different programs used during the development of the robot. Since our goal is to make the project reproducible, we included both the .ev3 files used by the LEGO EV3 software and the .bp files containing the programming blocks. We also added explanations for the main programs to make their purpose and operation easier to understand.
