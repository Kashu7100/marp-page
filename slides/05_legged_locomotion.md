---
marp: true
title: 24 Jun 2024
size: 16:9
math: mathjax
theme: am_dark
paginate: true
headingDivider: [2,3]
footer: Kashu Yamazaki, 2024
---

<!-- _class: cover_b -->
<!-- _header: "" -->
<!-- _footer: "" -->
<!-- _paginate: "" -->
<!-- _backgroundImage: url('https://marp.app/assets/hero-background.svg') -->

# Robot Perception and Control

###### Legged Locomotion

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu

## Actuator Networks　[arxiv](https://arxiv.org/abs/1901.08652)
<!-- _class: cols-2 -->

<div class=ldiv>



<!-- RL research for legged robots **was** mainly limited to simulation, and only few simple examples had been deployed on real systems.  -->


</div>
<div class=rdiv>

![#center w:600](img/learn_motor_skills.png)

</div>

## Learning by cheating
Proposed two-stage training procedure, which first train a privileged agent and then using the agent as a teacher to train a purely vision-based system, for effective imitation learning [[1](https://arxiv.org/pdf/1912.12294.pdf)] [[code](https://github.com/dotchen/LearningByCheating)].  


![#center w:800](img/learn_by_cheat.png)

## Learning Locomotion over Challenging Terrain

[[1](https://arxiv.org/pdf/2010.11251.pdf)] [[code](https://github.com/leggedrobotics/learning_quadrupedal_locomotion_over_challenging_terrain_supplementary)]

## Learning Locomotion over Challenging Terrain

<!-- _class: cols-2 -->

<div class=ldiv>

</div>
<div class=rdiv>

![#center](img/locomotion.png)

</div>

## Perceptive locomotion for quadrupeds
Presented a three stage training and deploy method to perform zero-shot sim-to-real transfer [[1](https://arxiv.org/pdf/2201.08117.pdf)]. 
1. a **teacher policy**, which has access to privileged information, is trained to follow a random target velocity over randomly generated terrain with random disturbances.
1. a **student policy** is trained to reproduce the teacher policy’s actions without using this privileged information.
1. transfer the learned student policy to the physical robot and deploy it in the real world with onboard sensors.

## Training teacher policy

![#center w:1000](img/perceptive_1.png)

## Training student policy

![#center w:1000](img/perceptive_2.png)

## Deployment

![#center w:1000](img/perceptive_3.png)

## RMA: Rapid Motor Adaptation for Legged Robots

[[1](https://ashish-kmr.github.io/rma-legged-robots/rma-locomotion-final.pdf)]



<!-- _class: cols-2 -->

<div class=ldiv>

</div>
<div class=rdiv>

![#center](img/rma.png)

</div>


## Learning to Walk in Minutes
Presents a training setup that achieves fast policy generation for real-world robotic tasks by using massive parallelism on a single workstation GPU [[1](https://arxiv.org/pdf/2109.11978.pdf)] [[code](https://github.com/leggedrobotics/legged_gym)]. 

![#center](img/learn_to_walk_in_minutes.png)