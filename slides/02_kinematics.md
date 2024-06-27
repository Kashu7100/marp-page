---
marp: true
title: 24 Jun 2024
size: 16:9
math: mathjax
theme: am_dark
paginate: true
headingDivider: [2,3]
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: cover_b -->
<!-- _header: "" -->
<!-- _footer: "" -->
<!-- _paginate: "" -->
<!-- _backgroundImage: url('https://marp.app/assets/hero-background.svg') -->

# Robot Perception and Control

###### Kinematics and Control

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu


## Kinematics

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## Kinematics

Kinematics: study of a motion of the robot without considering the forces and torques producing the motion.

## Denavit–Hartenberg convention

The following four transformation parameters are known as D–H parameters:

- $a_i$: distance from $z_{i-1}$ to $z_i$ along $x_i$.
- $\alpha_i$: angle from $z_{i-1}$ to $z_i$ about $x_i$.
- $d_i$: distance from $x_{i-1}$ to $x_i$ along $z_i$.
- $\theta_i$: angle from $x_{i-1}$ to $x_i$ about $z_i$.

![bg right 100%](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Classic_DH_Parameters_Convention.png/568px-Classic_DH_Parameters_Convention.png)


## Denavit–Hartenberg convention

In this convention, coordinate frames are attached to the joints between two links such that one transformation is associated with the joint $[Z]$, and the second is associated with the link $[X]$. The coordinate transformations along a serial robot consisting of n links form the kinematics equations of the robot:

$$
[T] = [Z_1][X_1][Z_2][X_2]...[Z_n][X_n]
$$

Each transformation $[Z][X]$ can be implemented as a 4x4 matrix:

```python
def transform(a, alpha, d, theta):
    return Rz(theta) @ Tz(d) @ Tx(a) @ Rx(alpha)
```

## Forward Kinematics

Forward kinematics is the problem of finding the end-effector position and orientation of a robot manipulator given the joint angles and link lengths.

$$
x(t) = f(\theta(t))
$$

## Inverse Kinematics

Inverse kinematics (IK) is essentially the reverse operation of FK: computing configuration(s) to reach a desired workspace coordinate. Unlike forward kinematics, inverse kinematics cannot be solved in a closed-form expression (in general). If we can derive a closed-form expression through symbolic manipulations, we can use Analytical IK, otherwise we need to use numerical approach.

**Analytical IK**
- Once the equations are derived, solutions are very fast to compute.
- Often difficult or tedious to derive.
- Only applicable to non-redundant robots (# DOFs = # of task space dimensions).

**Numerical IK**
- need to define solution parameters or initial guesses
- More generalizable

## Jacobian

The Jacobian matrix is a matrix of partial derivatives that describes how the robot's configuration affects the robot's end-effector position. The Jacobian matrix is defined as:

$$
J = \frac{\partial x}{\partial \theta}
$$

where $x$ is the end-effector position and $\theta$ is the joint angles.