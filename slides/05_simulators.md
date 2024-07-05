---
marp: true
title: 24 Jun 2024
size: 16:9
math: mathjax
theme: am_dark
paginate: true
headingDivider: [2,3]
footer: Kashu Yamazaki, 2024
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: cover_b -->
<!-- _header: "" -->
<!-- _footer: "" -->
<!-- _paginate: "" -->
<!-- _backgroundImage: url('https://marp.app/assets/hero-background.svg') -->

# Robot Perception and Control

###### Simulators

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu

## Simulators

![#center](img/simulators.png)

## Research oriented simulators

Popularized in robotics as sim2real research
- [**Gymnasium** (OpenAI Gym)](https://gymnasium.farama.org/): An API standard for single-agent reinforcement learning environments.
- [**MuJoCo**](https://mujoco.org/):
- [**NVIDIA Issac**](https://developer.nvidia.com/isaac-gym): GPU accelerated simulation: Gym (depricated), Sim, and Orbit.
- [**RaiSim**](https://github.com/raisimTech/raisimlib): physics engine for robotics and artificial intelligence research with easy to use C++ library.
- [**PyBullet**](https://pybullet.org/wordpress/):
- [**Drake** (MIT)](https://drake.mit.edu/): C++ toolbox started by the Robot Locomotion Group at the MIT and Toyota.
- [**Gazebo**](http://gazebosim.org/): part of ROS.

![bg right:30% w:250](https://gymnasium.farama.org/_images/lunar_lander.gif)
![bg vertical right:30% w:250](https://raisim.com/_images/anymals.png)
![bg vertical right:30% w:250](https://github.com/caelan/pddlstream/raw/d0eb256e88b8b5174fbd136a82867fd9e9cebc67/images/drake_kuka.png)


## Game engines as simulators

General purpose (physics simulation, rendering, etc.) game engines:
- [**Unity3D** (Unity Technologies)](https://unity.com/products/unity-engine): cross-platform game engine developed by Unity Technologies
    - **Barracuda**: neural network interface for Unity
- [**Unreal Engine** (Epic Games)](): 3D computer graphics and game engines developed by Epic Games
- [**CryEngine** (Crytek)]():
- [**Lumberyard** (Amazon)]():
- [**Stingray** (Autodesk)]():
- [**PhysX** (Nvidia)](https://www.nvidia.com/en-us/drivers/physx/physx-9-19-0218-driver/):

![bg right:30% w:250](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*fdQupctfwzssnwcE)

## Describing a Robot

## URDF 

URDF (Unified Robot Description Format) is a standard format based on XML used to describe a robot model in simulators. A URDF models a robot as a tree structure composed of **links** and **joints**. Links represent the robot's physical parts, while joints define how these parts move relative to each other, specifying their spatial relationships.

## Language in Simulator

