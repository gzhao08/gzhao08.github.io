---
layout: default
title: "ENPH 253/Robot Summer"
---

# ENPH 253/Robot Summer


- **Tools:** C++, Altium Designer
- **Concepts:** Robotics, Software, Electronic Design
- **Status:** Completed
- **Repo:** [ENPH-253---Pet-Saver](https://github.com/gzhao08/ENPH-253---Pet-Saver) 

## Background

Every summer, second year UBC Engineering Physics students take a course called ENPH 253 where students have 5 weeks to design, build, and use a robot in a competition. In my year (2025), our competition was to drive around a platform, collecting pet stuffies to "save" them from a fire. The competition platform looked like:

| ![img1]({{ '/assets/img/projects/enph-253/platform-2d.png' | relative_url }}) | ![img2]({{ '/assets/img/projects/enph-253/platform-3d.png' | relative_url }}) |

There is also a strip of black electrical tape that gives a generic path that the robot can follow as all the robots must be completely autonomous. You can find out more information about the competition and the EngPhys Project lab at  [https://projectlab.engphys.ubc.ca/enph-253-2025/](https://projectlab.engphys.ubc.ca/enph-253-2025/).

## H-Bridge Design

As we used (brushed) DC motors, we needed some way of controlling the direction and speed of the motor. Speed is an easier problem to solve as we can simply provide a PWM signal from the ESP-32 (the microcontroller we had access to) to a MOSFET connected to the battery and the motor. Direction however, required creating a more complicated circuit that was essentially a combination of 4 switches in an "H" configuration around the motor, hence the name "H-Bridge". A generic circuit diagram is shown below

<img src='\..\..\assets\img\projects\enph-253\h-bridge_generic.png' width="400">

Since we had no pmos in the lab, we had to make the circuit out of 4 nmos acting like switches. In order to bias the top switches into strong inversion, we need the gate to be above the battery voltage... The solution is to use a charge pump IC, in our case the LT1161 gate driver. 

<img src='\..\..\assets\img\projects\enph-253\LT1161.png' width="300">

Using the LT1161 IC, I made two different H-Bridge circuits. The first would be considered a more standard circuit, which uses the input and gate pins. The schematic, 2D, and 3D renders are shown below.

<img src='\..\..\assets\img\projects\enph-253\h-bridge-schematic.png' width="500">

<img src='\..\..\assets\img\projects\enph-253\h-bridge_pcb2D.png' width="500">

<img src='\..\..\assets\img\projects\enph-253\h-bridge_pcb3D.png' width="500">

The smaller MOSFETs are used to prevent shoot-through or essentially a situation where excess charge on the gates turn on unwanted transistors. Essentially they cross latch the gates and when one pair of gates are being actively driven, the others are actively pulled to ground.
As shown, this design is a very compact way to use the LT1161 in an H-Bridge and was the design we ended up using in the final robot.

The second design uses the timer pins on the LT1161 as enable pins.

<img src='\..\..\assets\img\projects\enph-253\schematic.png' width="500">

<img src='\..\..\assets\img\projects\enph-253\2D.png' width="500">

<img src='\..\..\assets\img\projects\enph-253\3D.png' width="500">



## Photos and videos from Robot Summer

When the PCBs first came:  
<img src='\..\..\assets\img\projects\enph-253\pcb_packaged.jpg' width="400">

First assembled H-Bridge:  
<img src='\..\..\assets\img\projects\enph-253\pcb_assembled.jpg' width="400">

Some line follow videos:  
<video controls src="\..\..\assets\img\projects\enph-253\line_follow1.mp4"></video>

<video controls src="\..\..\assets\img\projects\enph-253\line_follow2.mp4"></video>

First pet saved:  
<video controls src="\..\..\assets\img\projects\enph-253\pet1.mp4"></video>



