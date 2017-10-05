---
title: "Obstacle Detection for Self-Driving Cars"
excerpt: "Used stereo vision to detect obstacles and free space on the road in front of autonomous vehicles in cluttered urban environments"
header:
  teaser: assets/images/obstaclestereo.jpg
sidebar:
  - title: "Aug - Nov 2014"
    image: assets/images/obstaclestereo.jpg
    image_alt: "Obstacle Detection for Self-Driving Vehicles"
    text: "Undergraduate Project"
  - title: "People Involved"
    text: "Prof. Gaurav Pandey and Siddharth Tanwar"
---
The objective of the project was to use stereo (depth) cameras to efficiently detect the free on-road space in front of a vehicle  faster than real-time. 
Using the property that the horizon would always be horizontal in the images observed, we used a column-based representation (similar to stixels) to represent obstacles which resulted in a great reduction in computational complexity. 
OpenCV was used extensively to build a disparity map and remove road and sky using erode-dilate/watershed algorithm. We averaged the frames to reduce random noise in the image, and then calculated columnar occupancy. 

A report summarizing the project can be found here: <a href="/assets/documents/ugp1_report.pdf">[Report]</a>
