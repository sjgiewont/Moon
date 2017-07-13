---
layout: post
title:  "Delta Quad - An Implementation of a Quadruped Using Parallel Jointed Leg Architecture"
date:   2017-05-03
excerpt: "Research work investingating the ability to use parallel jointed legs in walking applications."
project: true
feature: /assets/img/delta_quad_cad.png
tag:
- PCB 
- MSP430
- Digital Design
comments: false
---
    
<center>Walking robots are in great demand due to their ability to navigate diverse terrains. Currently, many of the robotic legs in development are constructed using serial or prismatic joints. Such leg architectures have been proven capable but have high power requirements, are limited in overall motion and are slow. For this research work, a parallel jointed leg, Delta-Leg,that is capable of advanced locomotive gaits is developed. The mechanical design and kinematics of a physical working prototype are developed. The use of ANFIS (Adaptive Neural-Fuzzy Inference System) is utilized to describe the inverse kinematics and implement control of the robot. Four Delta-Legs are combined to produce a walking quadruped; Delta-Quad. A simulated model is generated to verify and test the walking capabilities of the Delta-Quad. A physical prototype is constructed to implement a basic omnidirectional walking gait. Both the simulated and physical Delta-Quad models are successful in omnidirectional locomotion. </center>

##Delta Leg

Below is an image of a single Delta-Leg. The various parts of the leg are described similar to a biological leg. The "hip" joints are actuated revolute joints. The "knee" and "ankle" joints are all free moving joints.

![]({{ site.url }}/assets/img/deltaleg_12_labeled.png)

The three actuated revolute joints work in parallel to allow the "toe" to be positioned dynamically within its workspace. A 3D representation of this workspace is shown in the image below. 
   
![]({{ site.url }}/assets/img/delta_leg_workspace.png)

## Inverse Kinematics

The inverse kinematics of each individual Delta-Leg are described as the "hip" positions (theta1, theta2, theta3) necessary to position the "toe" at a given point (X,Y,Z) in the Delta-Leg workspace. The forward kinematics are the exact opposite, describing the what posiiton (X,Y,Z) will be accomplished given an input of "hip" angles (theta1, theta2, theta3). The forward kinematics are much simplier to solve than the inverse kinemaitcs. Therefore, an ANFIS (Adaptive Neural-Fuzzy Inference System) is used to derive the inverse kinematics necessary for control of the leg. Using the forward kinematics as a training data set, the fuzzy neural network is trained to "learn" the inverse kinematics. This allows for very quick evaluation of the kinematics. 

##Delta-Quad

Four of these legs are then combined and attached to a common body/frame. This creates a quadruped (four legged robot, capable of walking) as seen below.

![]({{ site.url }}/assets/img/delta_quad_overview.png)

##V-REP

V-REP is a robotics simulation tool used to fully simulate the control, mechanics and overall operaiton of a robot in a simulated physical environment. A full V-REP model of the Delta-Leg and Delta-Quad is created. Using the Python API, each of the Delta-Leg joints are controlled individually. This allows walking gaits to be tested. Below is an image of the Delta-Quad model in V-REP. Further below are timelapse-screenshots of the Delta-Quad walking in V-REP. 

![]({{ site.url }}/assets/img/delta_quad_vrep.png)
![]({{ site.url }}/assets/img/delta_quad_walking_timelapse.png)



   