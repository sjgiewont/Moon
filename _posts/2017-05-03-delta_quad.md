---
layout: post
title:  "Delta Quad - An Implementation of a Quadruped Using Parallel Jointed Leg Architecture"
date:   2017-05-03
excerpt: "Research work investingating the ability to use parallel jointed legs in walking applications."
project: true
feature: /assets/img/deltaquad_12_full_12.png
tag:
- Robotics 
- Delta-Quad
- BeagleBone Black
- PCB
- Machine Learning
- ANFIS
- 3D Printing
- IoT
- Blynk
comments: false
---
    
Walking robots are in great demand due to their ability to navigate diverse terrains. Currently, many of the robotic legs in development are constructed using serial or prismatic joints. Such leg architectures have been proven capable but have high power requirements, are limited in overall motion and are slow. For this research work, a parallel jointed leg, Delta-Leg,that is capable of advanced locomotive gaits is developed. The mechanical design and kinematics of a physical working prototype are developed. The use of ANFIS (Adaptive Neural-Fuzzy Inference System) is utilized to describe the inverse kinematics and implement control of the robot. Four Delta-Legs are combined to produce a walking quadruped; Delta-Quad. A simulated model is generated to verify and test the walking capabilities of the Delta-Quad. A physical prototype is constructed to implement a basic omnidirectional walking gait. Both the simulated and physical Delta-Quad models are successful in omnidirectional locomotion.

## Delta Leg

Below is an image of a single Delta-Leg. The various parts of the leg are described similar to a biological leg. The "hip" joints are actuated revolute joints. The "knee" and "ankle" joints are all free moving joints.

![]({{ site.url }}/assets/img/deltaleg_12_labeled.png)

The three actuated revolute joints work in parallel to allow the "toe" to be positioned dynamically within its workspace. A 3D representation of this workspace is shown in the image below. 
   
![]({{ site.url }}/assets/img/delta_leg_workspace.png)

## Inverse Kinematics

The inverse kinematics of each individual Delta-Leg are described as the "hip" positions (theta1, theta2, theta3) necessary to position the "toe" at a given point (X,Y,Z) in the Delta-Leg workspace. The forward kinematics are the exact opposite, describing the what posiiton (X,Y,Z) will be accomplished given an input of "hip" angles (theta1, theta2, theta3). The forward kinematics are much simplier to solve than the inverse kinemaitcs. Therefore, an ANFIS (Adaptive Neural-Fuzzy Inference System) is used to derive the inverse kinematics necessary for control of the leg. Using the forward kinematics as a training data set, the fuzzy neural network is trained to "learn" the inverse kinematics. This allows for very quick evaluation of the kinematics. 

## Delta-Quad

Four of these legs are then combined and attached to a common body/frame. This creates a quadruped (four legged robot, capable of walking) as seen below.

![]({{ site.url }}/assets/img/delta_quad_overview.png)

## V-REP

V-REP is a robotics simulation tool used to fully simulate the control, mechanics and overall operaiton of a robot in a simulated physical environment. A full V-REP model of the Delta-Leg and Delta-Quad is created. Using the Python API, each of the Delta-Leg joints are controlled individually. This allows walking gaits to be tested. Below is an image of the Delta-Quad model in V-REP. Further below are timelapse-screenshots of the Delta-Quad walking in V-REP. 

![]({{ site.url }}/assets/img/delta_quad_vrep.PNG)

![]({{ site.url }}/assets/img/delta_quad_walking_timelapse.png)

## Walking Gait

To test the walking capabilites of the Delta-Quad, a parabolic step trajectory is used as shown in the image below. The parablic step function is capable of stepping in any height, length, direction and speed. 

![]({{ site.url }}/assets/img/step_trajectory.png)

Using the parabolic step, a lateral sequence gait is used to demonstrate walking. This gait, divides a single step into four sequences of all equal timing. Three of the four sequences include the dragging back portion of the step. The fourth sequence includes the stepping forward 

![]({{ site.url }}/assets/img/walking_gait_timing.png)

## The Mechanical Build

The base one of the Delta-Legs is 3D printed with ABS plastic. This allows a rigid yet light weight base to mount three RoBoard RS-1270 digital servo motors.

![]({{ site.url }}/assets/img/servo_base_mechanical.png)

The "tibia" portion of the Delta-Leg is constucted usign a threaded rod and a piece of aluminum U-Channel that swivels around the threaded rod. 

![]({{ site.url }}/assets/img/tibia_assembly.png)

The "knee" assembly includes a custom 3D printed knee joint that freely swivels around the aluminum joint. Together, this creates a pseudo spherical joint that allows the "leg" to move in any degree of motion. 

![]({{ site.url }}/assets/img/knee_assembly.png)

Below is a final mechanical assembly of an entire Delta-Leg. As it can be seen, most of the parts are 3D printed. This allows the leg to be light weight and low cost. 

![]({{ site.url }}/assets/img/delta_leg_assembly_2.png)

Each of the Delta-Legs are attached to a platform. The platform consists of aluminum U-Channel, 3D printed joints and a polycarbonate sheet. As it can be seen in the first image below, when the servos are on, the legs are able to hold up the weight of the entire robot. 

![]({{ site.url }}/assets/img/delta_quad_final.png)

## Delta-Quad System 

The Delta-Quad servo commands are derived using a BeagleBone Black. The BeagleBone Black calculates the inverse kinematics and trajectory planning. The corresponding servo commands are sent to a microcontroller which is capable of driving all 12 PWM signals simultaneously. A custom designed PCB board is used to provide clean power to all 12 servos. The servos and BeagleBone Black can be powered via a wired power supply or a mobile battery. Commands are sent to the Delta-Quad using a mobile app called Blynk. Blynk is a cloud based IoT platform that allows custom commands to be sent to a cloud server. The cloud requests are then received via the BeagleBone Black over a WiFi connection using a Python API. The entire control system is illustrated below. 

![]({{ site.url }}/assets/img/system_diagram_1.png)

## Final Results

The Delta-Quad was able to walk in both simulation and the mechanical prototype. While the walking may not have been perfect, this could eaisly be perfected by applying a control algorithm to allow the robot to maintain better balance while walking. Below is a quick video overviewing the results. 

<iframe width="1280" height="720" src="https://www.youtube.com/embed/JdKztPnUPYI?rel=0" frameborder="0" allowfullscreen></iframe>