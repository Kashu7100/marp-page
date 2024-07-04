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

###### Robot Perception in 3D

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu

## Homogeneous Transformations

Rigid motions can be represented in set of matrices of the following form so that composition of rigid motions can be reduced to matrix multiplication.

$$
\text{H} = \begin{bmatrix}
R & d \\
0 & 1
\end{bmatrix}, R \in SO(3), d \in \mathbb{R}^3
$$

This represents a homogeneous transformation matrix H, where R is a rotation matrix from the special orthogonal group SO(3), and d is a translation vector in 3D. The inverse transformation is given by:

$$
\text{H}^{-1} = \begin{bmatrix}
R^\intercal & -R^\intercal d \\
0 & 1
\end{bmatrix}
$$

## Homogeneous Transformations

The most general homogeneous transformation that we consider may be written as:

$$
\text{H}_{1}^{0} = \begin{bmatrix}
n_x & s_x & a_x & d_x \\
n_y & s_y & a_y & d_y \\
n_z & s_z & a_z & d_z \\
0 & 0 & 0 & 1 \\
\end{bmatrix} = \begin{bmatrix}
\mathbf{n} & \mathbf{s} & \mathbf{a} & \mathbf{d} \\
0 & 0 & 0 & 1 
\end{bmatrix} 
$$

Here, $\mathbf{n}$ is a vector representing the direction of $x_1$ ($x$ axis of new frame) in the original frame, $\mathbf{s}$ represents the direction of $y_1$, and $\mathbf{a}$ represents the direction of $z_1$. The vector $\mathbf{d}$ represents the position of the new origin in the original frame.


## Rotation Matrices

<!-- _class: cols-2 -->

<div class=ldiv>

Translation along the axis:

$$
\text{Trans}_{x,a} = \begin{bmatrix}
1 & 0 & 0 & a \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

$$
\text{Trans}_{y,b} = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & b \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

$$
\text{Trans}_{z,c} = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & c \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

</div>

<div class=rdiv>

Rotation around the axis:

$$
\text{Rot}_{x,\alpha} = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos \alpha & -\sin \alpha & 0 \\
0 & \sin \alpha & \cos \alpha & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

$$
\text{Rot}_{y,\beta} = \begin{bmatrix}
\cos \beta & 0 & \sin \beta & 0 \\
0 & 1 & 0 & 0 \\
-\sin \beta & 0 & \cos \beta & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

$$
\text{Rot}_{z,\gamma} = \begin{bmatrix}
\cos \gamma & -\sin \gamma & 0 & 0 \\
\sin \gamma & \cos \gamma & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
$$

</div>