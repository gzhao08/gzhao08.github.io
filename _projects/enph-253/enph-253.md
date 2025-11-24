---
layout: default
title: "ENPH 253/Robot Summer"
---

# ENPH 253/Robot Summer


- **Tools:** C++, Altium Designer
- **Concepts:** Robotics, Software, Electronic Design
- **Status:** Completed

## Background

Every summer, second year UBC Engineering Physics students take a course called ENPH 253 where students have 5 weeks to design, build, and use a robot in a competition. In my year (2025), our competition was to drive around a platform, collecting pet stuffies to "save" them from a fire. The competition platform looked like:

| ![img1]({{ 'assets\img\projects\enph-253\platform-2d.png' | relative_url }}) | ![img2]({{ 'assets\img\projects\enph-253\platform-3d.png' | relative_url }}) |

There is also a strip of black electrical tape that gives a generic path that the robot can follow as all the robots must be completely autonomous.

## H-Bridge Design

As we used (brushed) DC motors, we needed some way of controlling the direction and speed of the motor. Speed is an easier problem to solve as we can simply provide a PWM signal from the ESP-32 (the microcontroller we had access to) to a MOSFET connected to the battery and the motor. Direction however, required creating a more complicated circuit that was essentially a combination of 4 switches in an "H" configuration around the motor, hence the name "H-Bridge". A generic circuit diagram is shown below

<img src='\..\..\assets\img\projects\enph-253\h-bridge_generic.png' width="400">

Since we had no pmos in the lab, we had to make the circuit out of 4 nmos acting like switches. In order to bias the top switches into strong inversion, we need the gate to be above the battery voltage... The solution is to use a charge pump IC, in our case the LT1161 gate driver. 

<img src='\..\..\assets\img\projects\enph-253\LT1161.png' width="300">

Using the LT1161 IC, I made two different H-Bridge circuits. The first would be considered a more standard circuit, which uses the input and gate pins.

## Photos and videos from Robot Summer




