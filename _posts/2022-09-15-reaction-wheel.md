---
layout: post
title: "Enhanced Quadruped Balance with Reaction Wheels"
---

| ![beam_walk](assets/img/quadruped/beam_walking_still.png) |
|:--:|
| <b> Fig.1 - An Unitree A1 quadruped performing a narrow beam walk with our custom reaction wheel actuator system</b>|

I worked on a team that investigated using reaction wheels to assist inertial stabilization for quadruped robots. Quadruped systems are inherently under-actuated systems during locomotion. They lose rotational control authority entirely during flight phases, and around the line of support when only two point-feet are on the ground. Typically, large body orientation error can only be eliminated by swtiching stance-foot configuration during locomotion. In nature, however, terrestial animals use a multitude of strategy to stabilize themselves through conserving angular momentums by swing their appendages such as tails or limbs. We brought similar capabilities to quadrupeal robots by using reaction wheel actuators to perform attitude control. My main contribution to this project is help formulating the control problem as well as implementing it on hardware. 

#### Approach
Inspired by both the standard centroidal dynamics model common in legged robotics and models of spacecraft commonly used in the aerospace community, we model the coupled quadruped-reaction-wheel system as a gyrostat, and simplify the dynamics to formulate the problem as a linear discrete-time trajectory optimization problem. We modify a standard centroidal model-predictive control (MPC) [algorithnm](https://github.com/ShuoYangRobotics/A1-QP-MPC-Controller) [1] to solve for both stance foot ground reaction forces and reaction wheel torques simultaneously. The MPC problem is then solved as a quadratic program online (implemented in C++) at 1000 hz.We demonstrate improved attitude stabilization both in simulation and on hardware compared to a quadruped without reaction wheels, and perform a challenging traversal of a narrow balance beam that would be extremely difficult for a standard quadruped. 

#### Narrated Video Summary
<iframe width="560" height="315" src="https://www.youtube.com/embed/pJVMX1-3rIk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


#### Biliography
[1] J. Di Carlo, P. M. Wensing, B. Katz, G. Bledt and S. Kim, "Dynamic Locomotion in the MIT Cheetah 3 Through Convex Model-Predictive Control," 2018 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2018, pp. 1-9, doi: 10.1109/IROS.2018.8594448.