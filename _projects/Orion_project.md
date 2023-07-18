---
layout: page
title: Formula Student Driverless
description: Orion Racing India
img: assets/img/orion-car.jpg
importance: 4
category: work
---
<h2>Introduction</h2>

As I reflect on my time as a Driverless Vehicle Engineer at Orion Racing India, a Formula Student Team, I can't help but feel an overwhelming sense of pride and fulfillment. It was an experience that not only allowed me to delve into the fascinating world of autonomous vehicles but also provided the perfect platform to lean about and apply algorithms to various subsystems of our driverless prototype. In this blog post, I'll take you through my incredible journey, the challenges we faced, and the innovative algorithms that powered our driverless vehicle.

<h2>What is Orion Racing India?</h2>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/orion-logo.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Testing Days.
</div>


Orion Racing India or ORI is a student racing team, made entirely of engineering students trying educational experience by taking on a project of designing & developing a single seater formula style car, to participate at international design competition like Formula Student and Formula Bharat. Situated at the K.J. Somaiya College of Engineering, Mumbai, the team consists of 50+ passionate students from various engineering disciplines driven to work on various projects within ORI itself to achieve our final goal of building a reliable electric race car.


<h2>The First Glimpse into Real Robotics</h2>

In 2021, we started a sub-team to focus on the driverless part of the competition. It marked my first foray into real-world robotics. The opportunity to work on a driverless vehicle prototype with a team of talented and like-minded individuals excited me beyond words. Little did I know that this journey would be an immersive learning experience that would shape my passion for robotics and autonomous systems.

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.html path="assets/img/orion-setup.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.html path="assets/img/orion-test.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Testing Days.
</div>


<h2>Talking about our Tech Stack</h2>

<h3>Perception and Object Detection</h3>

Developing a robust perception system that had object (cone) detection capabilities was the first step in developing the Driverless Software. We had access to Kinect Stereo Cameras and 4-channel 3D LiDARs, so we experimented with both a Camera-based and LiDAR-based approaches. For the Camera-based approach we trained YOLOv5 over the FPOCO Cone Dataset. On the LiDAR-based front we followed a pipeline which involved distorion-correction,ground-removal, and clustering to get cone-positions. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    <iframe width="100%" height="315" src="https://www.youtube.com/embed/tJ52P60bIUg?start=2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </div>
</div>
<div class="caption">
    Perception System in work.
</div>

<h3>Mapping and Localization Algorithms</h3>

One of the fundamental challenges in building a driverless vehicle is ensuring accurate mapping and localization. We adopted a variation of Simultaneous Localization and Mapping (SLAM) algorithm called EKF-SLAM which uses cone-position aka landmarks obtained from the Perception stack to build a map. There are a total of 2 steps in the EKF SLAM implementation:
1. <b>Prediction Step</b>
This involves the localizing step in SLAM. Finding the coordinates of the car with respect to origin where we consider origin to be the initial position of car. We design the map with that respect and we can accordingly trace the car’s trajectory with this step.

2. <b>Correction Step</b>
This involves the consideration of landmarks/obstacles in the map and how to map it. This involves the working using the observation matrix, the car’s previous coordinates and yaw angle.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
    <iframe width="100%" height="315" src="https://www.youtube.com/embed/tJ52P60bIUg?start=48" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </div>
</div>
<div class="caption">
    SLAM subsytem
</div>

<h3>Path-Planning and Trajectory Tracking</h3>

In our pursuit of creating a robust and efficient autonomous driving prototype at Orion Racing India, we relied on cutting-edge algorithms for every aspect of our driverless vehicle's functionality. One of the key components of our system was path planning, which involved charting a safe and optimized course for our driverless vehicle to navigate. To achieve this, we harnessed the potential of the Voronoi Algorithm - an innovative and versatile approach that transformed our path planning capabilities.

The Voronoi Algorithm, originally used in diverse fields like computer graphics and computational geometry, found a perfect application in autonomous driving. Our objective was to identify the most feasible and collision-free path for our vehicle amidst complex and dynamic environments. The algorithm's ability to create a Voronoi diagram by partitioning the environment into regions based on proximity to obstacles and targets proved to be the key to unlocking this potential.

To complement our Voronoi-based path planning, we employed the Pure-Pursuit Controller for trajectory tracking. Once the global path was established using the Voronoi Algorithm, the Pure-Pursuit Controller took over, guiding our vehicle to follow the planned trajectory accurately. This controller used the concept of "look-ahead" points, where the vehicle continuously adjusted its steering angle to reach a specific point on the path, ensuring smooth and precise trajectory tracking.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
    <iframe width="100%" height="315" src="https://www.youtube.com/embed/tJ52P60bIUg?start=177" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
    </div>
</div>
<div class="caption">
    Voronoi Planner, Pure-Pursuit Controller
</div>

