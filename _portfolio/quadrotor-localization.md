---
title: "Quadrotor Localization"
excerpt: "Course Project for EE698G: Mobile Robotics at IIT Kanpur"
header:
  teaser: assets/images/quads-nayan.jpg
sidebar:
  - title: "November 2016"
    image: assets/images/quads-nayan.jpg
    image_alt: "Nayan AUV by Aarav Unmanned Systems"
    text: "Course Project for EE698G: Mobile Robotics"
  - title: "People Involved"
    text: "Prof. Gaurav Pandey, Siddharth Tanwar"
---
The objective of the project was to implement the entire software pipeline required to autonomously fly a development-stage quadrotor and land it on a location specified by an ArUco marker. 
We used the Nayan quadrotor which has an Odroid-XU4 on-board computer running Lubuntu 14.04 for high-level control, and a twin cortex M4 processor with a Real-Time OS for the flight controller (HLP+LLP).
The quadrotor was fit with a monocular downward-facing camera, a PX4Flow optical flow sensor, and an IMU. 
The Robot Operating System (ROS) was used to create the interface between the high-level controller and sensors, while the flight controller itself communicated solely with the high-level controller.

ArUco marker detection was done with a publicly available open-source library which integrates into ROS. We implemented rotation compensation to get a robust estimate of the rotation using data from both IMU and ArUco marker detection library. All the incoming data was then passed into an Unscented Kalman Filter to get a stable estimate of the location of the quadrotor with respect to the marker.

A presentation which summarizes the project can be found here: <a href="/assets/documents/quadrotor_ppt.pdf">[Slides]</a>
