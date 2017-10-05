---
title: "Dense Object Detection"
excerpt: "Course Project for CS698N at IIT Kanpur"
header:
  teaser: assets/images/yolo-1.png
sidebar:
  - title: "October 2016"
    image: assets/images/yolo-1.png
    image_alt: "Object Detection YOLO"
    text: "Course Project for CS698N: Recent Advances in Computer Vision"
  - title: "People Involved"
    text: "Prof. Gaurav Sharma, Siddharth Tanwar"
gallery:
  - url: /assets/images/yolo-2.png
    image_path: assets/images/yolo-2.png
    alt: "Mona Lisa with a cat"
  - url: /assets/images/yolo-3.png
    image_path: assets/images/yolo-3.png
    alt: "Planes in the sky"
  - url: /assets/images/yolo-4.png
    image_path: assets/images/yolo-4.png
    alt: "Horse and jockey"
---
Object Detection is one of the most important parts of computer vision. In this course project we studied the <a href="https://arxiv.org/abs/1506.02640">YOLO</a> (You Only Look Once) object detection framework, trained a scaled down version of the network with 8 convolutional+maxpool layers followed by 1 fully connected layer. We also improved YOLO's reported performance in cluttered scenes by increasing its grid resolution, which helped detect smaller objects with greater accuracy.<br>
We also concluded that having more than 2 bounding boxes per cell was detrimental to performance, probably because it led to more situations where the wrong box was being selected. 
A YOLO network pre-trained on ImageNet was also tested on the <a href="http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=2d">KITTI</a> object detection benchmark.

A presentation summarizing the work can be accessed here: <a href="/assets/documents/objectDetection_ppt.pdf">[Slides]</a><br>
Report available here: <a href="/assets/documents/objectDetection_report.pdf">[Report]</a>

{% include gallery caption="Some Results Obtained" %}

