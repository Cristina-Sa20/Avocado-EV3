# **Vehicle**

## **Prototype 1**

<p align="justify">
We designed this prototype with the goal of optimizing the placement of the motors, control unit, and sensors to ensure proper weight distribution and connections. 
The aim was to prevent cable strain, reduce wear and tear on the robot, and avoid disconnections. 
</p>

### Left Side View 

<p align="center">
  <img src="Photos/left.png" width="300">
</p>

<p align="justify">
In this view, we can see the location of the control unit, the motors, and some of the sensors; we can also see how these components are mounted on the chassis. Additionally, we can see the difference in the size of the front and rear tires. These were designed to distribute weight, provide better traction, and thus ensure greater stability. 
</p>

### Right Side View 

<p align="center">
  <img src="Photos/Right.png" width="300">
</p>

<p align="justify">
Here we can once again see the layout of the motors, sensors, and chassis structure, but now we can see components that were not visible from the left side. We can also get a better view of the wiring layout and the brackets used to hold the components in place.
</p>

### Front View 

<p align="center">
  <img src="Photos/front.png" width="300">
</p>

<p align="justify">
The front view provides a clear view of the sensors located at the front of the vehicle and their position, which is as centered as possible to facilitate more accurate calculations when calibrating distances and angles. It also provides a better view of the front wheel mechanism.
</p>

### Rear View 

<p align="center">
  <img src="Photos/Back.png" width="300">
</p>

<p align="justify">
The rear view shows the position of the wheels and the width of the vehicle, as well as how the motor cables are connected to the control unit. From this perspective, we can see the symmetry we strive to maintain in the robot and how we integrated the motors so that they would fit within the width of the chassis.
</p>

### Top View 

<p align="center">
  <img src="Photos/Top.png" width="300">
</p>

<p align="justify">
The top view mainly shows the control unit and the connections for both the sensors and the motors. Here you can see how the wiring was routed so that it does not interfere with the wheels, sensors, and motors when the vehicle executes the code.
</p>

### Botton View 

<p align="center">
  <img src="Photos/Botton.png" width="300">
</p>

<p align="justify">
From this perspective, we can see the vehicle’s mechanical components in detail, including both the front and rear wheels. The gear-driven transmission components and part of the mechanisms associated with steering and movement are visible, allowing us to understand how motion is mechanically transmitted and how it is integrated into the chassis.
</p>

## **Prototype 2**
<p align="justify">
Prototype 2 reflects the changes made to the robot after the regionals. In this case, we kept virtually the same structure and mechanics as Prototype 1, since they met the established objectives.
In the new version, we made six modifications: We changed the mechanics of the steering wheels, repositioned the rotation sensor, stabilized the control unit, repositioned the motor connected to the ultrasonic sensor, and added a camera.
</p>

### 1. Steering Motor
<p align="justify">
One problem we detected was that the steering wheels sometimes did not turn properly and were very unstable. Upon investigation, we realized that the gear connected to the motor was causing wear that prevented effective and coordinated movement of the steering mechanism. Therefore, we decided to remove the gears and connect the motor directly to the steering mechanism. Here, the motor was reoriented from a horizontal to a vertical position.
</p>

### 2. Gyroscope 
<p align="justify">
Here we noticed that sometimes, during practice, the compiler would show that the gyroscope was producing very large numbers that were out of the ordinary. This affected the correction, causing the vehicle to veer off course significantly or, in some cases, to drift gradually. We noticed that the gyroscope was in a position that didn’t keep it stable or still, so we decided to lower it and provide more support to keep it from moving.
</p>

### 3. Control Unit
<p align="justify">
We noticed that the control unit was asymmetrical and tilted; one side was higher than the other. Although we initially thought this wouldn’t cause any problems, we realized that it affected weight distribution and the tension in the connections. This tilt contributed to the robot’s deviation and erroneous turns due to the weight distribution, which affected the motors and the gyroscope.
</p>

### 4. Color Sensor
<p align="justify">
During the laps, the color sensor sometimes failed to detect colors accurately, and there were many problems if the area wasn’t well lit; moreover, calibration was very difficult because of this, and the values varied too much. To fix this, we decided to lower the color sensor slightly, and there was a significant improvement.
</p>

### 5. Ultrasonic motor and camera
<p align="justify">
For the obstacle course, we needed add and position the camera. We found that the best spot for it was right in the front center, but there it interfered with the motor connected to the ultrasonic sensor. So, we reoriented the motor from vertical to horizontal and added gears to keep the ultrasonic sensor in place, since it was working perfectly there. After making this change, we added some supports to stabilize the camera in the center.
</p>

## Prototype 2 - Photo Record

### Left Side View 

<p align="center">
  <img src="Photos 2/Left2.jpeg" width="300">
</p>

<p align="justify">
The integration of the built-in components is evident without significantly altering the original structure.

### Right Side View 

<p align="center">
  <img src="Photos 2/Rigth2.jpeg" width="300">
</p>

<p align="justify">
It allows you to visualize the layout of the components and their integration with the chassis.
</p>

### Front View 

<p align="center">
  <img src="Photos 2/Front2.jpeg" width="300">
</p>

<p align="justify">
The front view of the vehicle and the location of the sensing components are shown.
</p>

### Rear View 

<p align="center">
  <img src="Photos 2/Back2.jpeg" width="300">
</p>

<p align="justify">
This allows you to view the rear layout and the corresponding wiring for this version.
</p>

### Top View 

<p align="center">
  <img src="Photos 2/Top2.jpeg" width="300">
</p>

<p align="justify">
The general layout of the components and the wiring of the new configuration are shown.
</p>

### Botton View 

<p align="center">
  <img src="Photos 2/Botton2.jpeg" width="300">
</p>

<p align="justify">
It is evident that the main traction, steering, and undercarriage mechanisms remained the same as in Prototype 1.
</p>

