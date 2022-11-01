---
layout: post
title: "Autonomous River Profiling with ASV"
---

| ![q_boat](assets/img/river/q_boat.JPG) |
|:--:|
| <b> Fig.1 - Our autonomous teledyne Q-Boat mapping a section of the Kern River</b>|


I worked on a team that collaborated with scientists from Caltech Geological and Planetary Science Department to accurately map rivers with robots. Most rivers have the tendency to change course and self-adjust their topography, and the current method of mapping rivers relies on people to manually collect depth data with Acoustic Doppler Current Profiler (ADCP) sensor on a boat. This project was inspired by the possibility to map river with robots with an ADCP instead of with human. For this project, I developed:

1. A nested PID controller that steers an under-actuated ASV on a predefined straight-line across a river with rapid current.
2. A Kalman Filter based strategy for fusing multiple ASV sensor measurements to construct 3D estimate of velocity and depth profile.

#### Transect Controller
Assuming the robot is facing upstream, I designed a controller that utilizes a double PID error feedback loop that minimizes 1. the distance error between the ASV and the transect line, and 2. the desired transect velocity along the transect line. We were able to implement this controller and tested in a river running at 1.5 meter per second. In the following video, the robot is traversing up the Kern River in Bakersfield. It makes one horizontal transect of the river at a set interval. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/4V8n4J1TdNQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### River Mapping with ADCP
While the ASV is traversing the river, the ADCP captures a depth measurement and a set of water velocity measurements at a set of discrete depth points. We then discretized the river into a 2D grid and the water body into a 3D lattice structure. A Kalman filter is then used to interpolate and update a window of cells at the location where the measurement is taken. 

| ![parametric](assets/img/river/lawnmower_parametric.png) |
|:--:|
| <b> Fig.2 - Parametric plot of a lawnmower river survey</b>|

| ![depth](assets/img/river/lawnmower_filtered.png) |
|:--:|
| <b> Fig.3 - Filtered river depth profile</b>|
 
| ![velocity](assets/img/river/transect_cross.png) |
|:--:|
| <b> Fig.3 - Cross-section velocity profile </b>|

<!-- #### Lagrange

Lagrange is a minimalist Jekyll blog theme that I built from scratch. The purpose of this theme is to provide a simple, clean, content-focused blogging platform for your personal site or blog.

Feel free to check out <a href="https://lenpaul.github.io/Lagrange/" target="_blank">the demo</a>, where you’ll also find instructions on <a href="https://lenpaul.github.io/Lagrange/journal/getting-started.html">how to use install</a> and use the theme.

#### Millennial

Millennial is a minimalist Jekyll blog theme that I built from scratch. The purpose of this theme is to provide a simple, clean, content-focused publishing platform for a publication or blog.

Feel free to check out <a href="https://lenpaul.github.io/Millennial/" target="_blank">the demo</a>, where you’ll also find instructions on <a href="https://lenpaul.github.io/Millennial/documentation/getting-started.html">how to use install</a> and use the theme.

#### Jekyll Starter Kit

The Jekyll Starter Kit is a simple framework for starting your own Jekyll project using all of the best practices that I learned from building my other Jekyll themes.

Feel free to check out <a href="https://github.com/LeNPaul/jekyll-starter-kit" target="_blank">the GitHub repository</a>, where you’ll also find instructions on how to use install and use the theme. -->
