---
title: "Disparate Image Matching"
excerpt: "Course Project for EE604: Image Processing at IIT Kanpur"
header:
  teaser: assets/images/dude-matching.jpg
sidebar:
  - title: "November 2016"
    image: assets/images/dude-matching.jpg
    image_alt: "Disparate Image Matching"
    text: "Course Project for EE604: Image Processing at IIT Kanpur"
  - title: "People Involved"
    text: "Prof. Tanaya Guha, Siddharth Tanwar, Ayush Shakya"
gallery:
  - url: /assets/images/dude-graffiti.png
    image_path: assets/images/dude-graffiti.png
    alt: "Graffiti"
  - url: /assets/images/dude-madrid.png
    image_path: assets/images/dude-madrid.png
    alt: "Madrid"
  - url: /assets/images/dude-vatican.png
    image_path: assets/images/dude-vatican.png
    alt: "Vatican"
---
Finding corresponding points between two images is a fundamental step for image matching, 3D reconstruction, object tracking, recognition and depth estimation. Disparate images of the same scene like those captured at different times of day, in different centuries or different modalities (painting v/s image) have historically been very challenging for image matching algorithms.

We implemented a recently proposed duality descriptor, <a href="http://ieeexplore.ieee.org/abstract/document/7532369/">DUDE</a>, which, combined with the multi-modal image detector outperformed algorithms like SIFT, SYMD and J-SPEC at much lower computational cost, while also being highly repeatable. 

A presentation summarizing the work can be accessed here: <a href="/assets/documents/imageMatching_ppt.pdf">[Slides]</a><br>

{% include gallery caption="Some Results Obtained" %}

