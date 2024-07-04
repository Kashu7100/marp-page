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

###### Introduction

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu


## Logistics

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## Logistics


**Lectures**

- Time: 00:00 - 00:00 (CST), MWF / TuTh
- Location: JBHT 000 (in person)

**Office Hours**

- Instructor: By appointment via email
- TA: 00:00 - 00:00 (CST), MWF


## Logistics

**Grading Policy**

- HWs (30%): 5 home works
- Quizzes (10%): 5 quizzes each worth 20 points
- Midterm (30%): $\max(0.2 \cdot \sum(\text{quizzes}) + 0.8 \cdot \text{midterm}, \text{midterm})$
- Final Project (30%): project report + presentation

A: 90\% ~ , B: 80\% ~ 90 \%, C: 70\% ~ 80 \%, D: 60\% ~ 70 \%

**Submission Policy**
- HWs: $-5\%$ penalty / day from the total points of the assignment after due.
- Final Project: No late submission.

**Every submission is due midnight (11:59 pm) on the date specified.**

## Robot Learning

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 1. Robot Learning

<!-- _class: cols-3 -->

<div class=ldiv>

![#center](https://external-preview.redd.it/is-this-frame-manipulation-or-is-it-really-so-smooth-and-v0-MzJubGJyMWVoMDhkMaFyv-3Y5k43E2ChZcsZFS5twhklMNSV5hWfTTSt6JHp.png?format=pjpg&auto=webp&s=14dea71abc16375868dcc892fbb5ba6ee18b2413)
![#center](https://www.roboticvision.org/annualreport2019/wp-content/uploads/2020/04/CON-NA-Panda-arm-2-scaled.jpg)

Manipulation

</div>

<div class=mdiv>

![#center](https://i.ytimg.com/vi/nipH-yl8lR0/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLCNEgkxyZ614AutrlwM9lfdA6O8Aw)
![#center](https://i.ytimg.com/vi/8sO7VS3q8d0/maxresdefault.jpg)

Locomotion
</div>

<div class=rdiv>

![#center](https://www.inceptivemind.com/wp-content/uploads/2021/02/Spot-Robot-Arm.jpg)
![#center](https://interestingengineering.com/_next/image?url=https%3A%2F%2Fcms.interestingengineering.com%2Fwp-content%2Fuploads%2F2024%2F06%2FUntitled-design-35.png&w=1200&q=75)

Mobile Manipulation

</div>


## 1.1 What is Robot Learning?

**Robot learning** is a research field at the intersection of **machine learning** and **robotics**. It studies techniques allowing a robot to acquire novel skills or adapt to its environment through learning algorithms.


- *Sensing*: observe the physical world through multimodal senses
- *Perception*: acquiring knowledge from sensor data
- *Action*: act on the environment to execute task / acquire new observation

>A key challenge in Robot Learning is to close the **perception-action loop**.

![bg right:35% w:90%](https://cdn-wordpress-info.futurelearn.com/info/wp-content/uploads/f338ce63-774c-4034-9278-3f3a2593c68b-768x768.png)

## 1.2 When Should Robots Learn?

Robots should be designed to learn in situations where pre-existing knowledge or established protocols are insufficient or non-existent, requiring them to discover knowledge from data:

- High Environmental Uncertainty
- Significant Variation in Observations
- Lack of Reliable Priors
- Complex or Unstructured Environments
- Continuous Improvement

<!-- _class:  bq-red -->
> Learning is **NOT** the solution to every problem in robotics.
>
> When the task can be modeled without knowledge from data, learning algorithm is not required (and learning algorithm tend to perform worse).


## 1.3 How to make robots learn?

These days, many robot learning methods are based on **deep neural networks** with various learning algorithms (supervised learning, unsupervised learning, reinforcement learning, etc.).


![#center](https://www.mathworks.com/solutions/artificial-intelligence/ai-robotics/_jcr_content/mainParsys/band_copy_1227855798/mainParsys/pictogram.adapt.full.medium.svg/1712662010437.svg)

## Multi-modality Sensory

<!-- _class: cols-3 -->

<div class=ldiv>

![#center h:180](https://www.repairerdrivennews.com/wp-content/uploads/2018/01/velodyne-vlp-16-puck.jpg)
LiDAR sensor
![#center h:180](https://static.bhphoto.com/images/multiple_images/images500x500/1598955319_IMG_1410725.jpg)
Stereo Depth sensor

</div>

<div class=mdiv>

![h:180](https://m.media-amazon.com/images/I/61Th+lc12aL._AC_UF894,1000_QL80_.jpg)
RGBD camera, Microphone 
![#center h:180](https://www.researchgate.net/publication/308860567/figure/fig5/AS:413685446135814@1475641704716/IMU-sensor-with-a-scheme-of-the-measured-Euler-angles.png)
IMU (Gyro/Acceleration/Barometer)

</div>

<div class=rdiv>

![h:180](https://www.robotics247.com/images/article/BeBop_Sensors_01.jpg)
Tactile sensor
![#center h:180](https://www.roboct-global.com/uploads/202226482/high-torque-robot-joint-module02185840434.jpg)
Joint Position/Velocity/Torque

</div>

## Deep Learning

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 2.1 Basics

## Backpropagation 

## MLP

## CNN

## RNN

![#center w:900](https://miro.medium.com/v2/resize:fit:1194/1*B0q2ZLsUUw31eEImeVf3PQ.png)

## Scaled Dot product Attention

An attention mechanism where the dot products are scaled down by $\sqrt{d_k}$. 
* Motivated by the concern when the input is large, the softmax function may have an extremely small gradient, hard for efficient learning.

* Calculate *similarity* from $Q$ and $K$, and scale $V$ by the similarity.

* Can be viewed as **differentiable dictionary**.

$$
\text{Attention}(Q, K, V) = \text{softmax}\left( \frac{QK^\boldsymbol{\top}}{\sqrt{d_k}}\right)V
$$

![bg right:30% w:100%](img/dot_prod_attn.png)

## Multi-Head Attention (MHA)

A module for attention mechanisms which runs through an attention mechanism several times in parallel. 

$$
h_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)
$$
$$
\text{MultiHead}(Q, K, V) = [h_0\dots h_n]W
$$

- The multiple attention heads allows for attending to parts of the sequence differently.
- When $Q, K, V = X$, this is called **self-attention**.
- Only a small subset of heads appear to be important for the translation task. Especially the encoder self-attention heads, can be removed without seriously affecting performance [[1](https://arxiv.org/pdf/1905.09418.pdf)].

![bg right:30% w:80%](img/multi-head-attention.png)

## Masked Multi-Head Attention

Masking of the unwanted tokens can be done by setting them to $-\infty$. The binary mask $M \in \{0, -\infty \}$ is added to the attention scores so that attention weight will be zero on those unwanted tokens.

$$
\text{Attention}(Q, K, V) = \text{softmax}\left( \frac{QK^\boldsymbol{\top} + M}{\sqrt{d_k}}\right)V
$$

Sample implementation:
```python
qkv = to_qvk(x) # to_qvk = nn.Linear(dim, dim_head * heads * 3, bias=False)
q, k, v = tuple(rearrange(qkv, 'b t (d k h) -> k b h t d ', k=3, h=num_heads))
scaled_dot_prod = torch.einsum('b h i d , b h j d -> b h i j', q, k) * scale
scaled_dot_prod = scaled_dot_prod.masked_fill(mask, -np.inf)
attention = torch.softmax(scaled_dot_prod, dim=-1)
out = torch.einsum('b h i j , b h j d -> b h i d', attention, v)
out = rearrange(out, "b h t d -> b t (h d)")
```

## Self-Attention vs Cross-Attention

**Self-Attention**: all of the $K, V,$ and $Q$ come from the same input source. 
* Each position in the encoder can attend to all positions in the previous layer of the encoder.

**Cross-Attention**: the $K, V$ come from the reference source and the $Q$ come from the querying source.
* This allows every position in the decoder to attend over all positions in the input sequence.
* One way to realize cross-modal fusion.

![bg right:30% w:95%](img/self_cross_attn.png)

## Inductive Bias

![#center w:700](img/ib.png)

**Inductive bias (IB)** is the assumption(s) of data that the model holds [[1](https://towardsdatascience.com/recent-developments-and-views-on-computer-vision-x-transformer-ed32a2c72654)].
* **CNN**: information in the data is locally aggregated. (strong IB)
* **RNN**: the data is highly correlated with the previous time. (strong IB)
* **Self Attention**: just correlating all features with each other. (weak IB)

## Resources: Books

<!-- _class: cols-2 -->

<div class=ldiv>

![#center h:400](https://m.media-amazon.com/images/I/A10G+oKN3LL._AC_UF1000,1000_QL80_.jpg)

*Deep Learning*
by Ian Goodfellow, Yoshua Bengio, Aaron Courville

</div>

<div class=rdiv>

![#center h:400](https://m.media-amazon.com/images/I/4109zaBEgJL._AC_UF1000,1000_QL80_.jpg)

*Modern Robotics: Mechanics, Planning, and Control*
by Kevin M. Lynch, Frank C. Park

</div>

## Resources: Online Materials

- [CS391R (UT Austin) by Yuke Zhu](https://www.cs.utexas.edu/~yukez/cs391r_fall2023/syllabus.html): lecture slides