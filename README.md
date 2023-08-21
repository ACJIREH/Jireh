Engineering materials
====

This repository contains engineering materials of a self-driven vehicle's model participating in the WRO Future Engineers competition in the season 2022.

## Content

* `t-photos` contains 2 photos of the team (an official one and one funny photo with all team members)
* `v-photos` contains 6 photos of the vehicle (from every side, from top and bottom)
* `video` contains the video.md file with the link to a video where driving demonstration exists
* `schemes` contains one or several schematic diagrams in form of JPEG, PNG or PDF of the electromechanical components illustrating all the elements (electronic components and motors) used in the vehicle and how they connect to each other.
* `src` contains code of control software for all components which were programmed to participate in the competition
* `models` is for the files for models used by 3D printers, laser cutting machines and CNC machines to produce the vehicle elements. If there is nothing to add to this location, the directory can be removed.
* `other` is for other files which can be used to understand how to prepare the vehicle for the competition. It may include documentation how to connect to a SBC/SBM and upload files there, datasets, hardware specifications, communication protocols descriptions etc. If there is nothing to add to this location, the directory can be removed.

## Introduction

I. Code Objective:

Our objective in developing this code is to equip the vehicle with the ability to navigate autonomously on a track, utilizing ultrasonic sensors and a servo to make decisions and adjust its movement.

II. Code Structure:

We present the code in several key sections:

Library Imports: Here, we import the necessary libraries to control the servo, I2C communication, and the LCD screen.
Variable Declarations: We define variables that store relevant values such as distances, speeds, and angles.
Custom Functions: We create custom functions, such as the one measuring ultrasonic distance and those managing data presentation on the LCD screen.
Initial Configuration: In the setup() function, we configure pins and establish initial values.
Main Loop: The main logic of the vehicle resides here:
We read distances using ultrasonic sensors.
We control vehicle movement using motors and a servo.
We update information on the LCD screen.

III. Key Functions:

We highlight some important functions:

fnc_ultrasonic_distance: Measures distances using an ultrasonic sensor and returns values in centimeters.
forward, turn_right, turn_left, reverse: Functions controlling vehicle movement and the servo.
data_on_track, data_in_calculation: Functions presenting relevant information on the LCD screen.

IV. Development Process:

To build and use this code:

Set up the development environment, such as the Arduino IDE.
Connect components like ultrasonic sensors, motors, and the LCD screen as per the code's specifications.
Write and edit the code in the Arduino IDE.
Compile the code and load it onto the vehicle's microcontroller using a programming cable.
Upon powering the vehicle, it will follow the code's instructions and autonomously move along the track.

V. Conclusions:

The presented code is the backbone of our autonomous vehicle.
It enables the vehicle to make informed decisions based on data collected by its sensors.
The precise integration of functions, variables, and decisions transforms it into an efficient and capable autonomous system.

## How to prepare the repo based on the template

_Remove this section before the first commit to the repository_

1. Clone this repo by using the `git clone` functionality.
2. Remove `.git` directory
3. [Initialize a new public repository on GitHub](https://github.com/new) by following instructions from "create a new repository on the command line" section (appeared after pressing "Create repository" button).
