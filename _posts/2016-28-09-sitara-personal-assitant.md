---
layout: post
title:  "Sitara Based Personal Assistant"
date:   2016-09-28
excerpt: "Current project focused on developing custom PCB board powered by TI Sitara ARM Cortex Processor. End goal to create smart assitant with built in Wifi, speakers and touch screen display "
project: true
feature: /assets/img/case_design_1.PNG
tag:
- PCB 
- Sitara
- Wifi
- Digital Design
comments: false
---
    
<center>The goal of this project is to expand PCB layout and embedded design skills using a TI Sitara ARM Cortex processor. End goal to create smart assitant with built in Wifi, speakers and touch screen display  </center>
     
## Inital Design Goals

For this project, I am desiring to design a custom PCB board that will be completely integrated with the following key features


- Wifi
- Bluetooth
- SD Card Reader
- DDR3L
- HDMI Port 
- Capacitive Touch Screen Interface
- USB x3
- Stereo Audio
- Audio AUX out
- Audio Microphone
- Status LED
- Linux based operating system

## System Level Design

The following is an early stage system level block design. 

![]({{ site.url }}/assets/img/Block Diagram - HL Design.png)

## Early Stage Physical Design

Designed using SketchUp, the following is an early stage physical design to estimate the board size and get and understanding of the physical requirements of the desired system. The end goal is a plug in device that is able to hang on a wall or sit on a desk. It has stereo audio using 2 independent speakers. It will also have the ability to drive an audio reciever using a headphone jack. A LCD display will be embedded in the device, allowing to display physical content to the end user. 

![]({{ site.url }}/assets/img/case_design_1.PNG)


#### Part Selection 

The following components are planned to be used in this project:


- TI Sitara ARM® Cortex®-A8 32-Bit - AM3358
- WiLink™ 8 single band combo 2x2 MIMO Wi-Fi®, Bluetooth® & Bluetooth Smart (Low energy) module - WL1835MOD
- Alliance Memory: IC SDRAM DDR3 128M X 16 96-FBGA - AS4C128M16D3L-12BIN
- IC HDMI TRANSMITTER 64-HVQFN - NXP TDA19988
- Closed Loop I2S Input Amplifier with Power Limiter and Integrated Headphone, PVDDmax of 16.5V - TAS5760LD 
- MEMS Microphones DIG MEMs Mic, BP w/ I2S output - SPH0645LM4H-B



