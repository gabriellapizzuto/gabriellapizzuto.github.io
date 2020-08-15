---
title: 'Real Robot Manipulation Datasets For Learning Dynamics'
date: 2020-08-14

tags:
  - robotics
  - datasets
  - dynamics
  - model learning
---

TL; DR: **Real robot datasets** are especially useful to benchmark and **evaluate** **model learning** techniques. Our efforts is to maintain a list of the available datasets for **learning forward and inverse dynamics of robotic manipulators** to encourage more reproducible research in robotics. 

## *Why do we need these?*

Dynamics models are key to achieve more compliant controllers. Benchmarking and evaluating data-driven dynamics learning models requires datasets that are available across platforms, and to date there is no such collection. 

## Forward Dynamics

For a robot with _N_ degrees of freedom (DoFs), the forward dynamics model is given by: 

$${\ddot q} = M^{-1}({q})({\tau} - h({q}, {\dot{q}}))$$

$\ddot q$ are the joint accelerations which the model will learn;

$M^{-1}({q})$ is the inverse of the inertia matrix;

$h({q}, {\dot q})$ comprises Coriolis and centripetal forces, friction and gravity;

$\mathbf{\tau}$ are the joint torques;

$q, \dot q$ are the respective joint positions, velocities and accelerations for each joint.

## Learning Forward Dynamics

Using a model learning approach, this is formulated through the following:

$$\ddot{q} = Forward Dynamics(q, \dot{q}, \tau )$$

Here, the _inputs_ are the _joint positions, velocities and torques_ and the _outputs_ are the learned _accelerations_. 

## Inverse Dynamics

For a robot with _N_ DoFs, the inverse dynamics model is given by: 

$$\mathbf{\tau} = M({q}){\ddot{q}} + h({q}, {\dot{q}})$$

$\mathbf{\tau}$ are the joint torques which the model will learn;

$M({q})$ is the inertia matrix;

$h({q}, {\dot q})$ comprises Coriolis and centripetal forces, friction and gravity;

$q, \dot q, \ddot q$ are the respective joint positions, velocities and accelerations for each joint.

## Learning Inverse Dynamics 

Using a model learning approach, this is formulated through the following:

$${\tau} = Inverse Dynamics(q, \dot{q}, \ddot{q})$$

Here, the _inputs_ are the _joint positions, velocities and accelerations_ and the _outputs_ are the learned _torques_. 

# Dataset 1: Transfer Dynamics Dataset

## Dataset Overview

The data was recorded from a 3 DoF torque-controlled real-robotic system. The control and observation rate is 1000 Hz, i.e. the time elapsed between t and t + 1 is 0.001 seconds. The system is run for multiple rollouts, each of which lasts 14 seconds, hence T = 14000. The control input corresponds to the three desired torques (Newton metres) sent to the motors of each joint at time index t. The observation is nine-dimensional and contains measured angles (radians), measured velocities (radians / seconds) and measured torques (Newton metres) at each joint. Two real-world datasets, one using open-loop controllers and one using closed-loop controllers. In the open loop case we sample trajectories of desired torques from Gaussian processes (GPs). In contrast, for feedback policies, we use PD control to track trajectories in joint space which are generated as a random superposition of sine waves.

![https://github.com/rr-learning/transferable_dynamics_dataset/raw/master/img/5.png](https://github.com/rr-learning/transferable_dynamics_dataset/raw/master/img/5.png)

## Paper Reference

[A Real-Robot Dataset for Assessing Transferability
of Learned Dynamics Models](https://www.is.mpg.de/uploads_file/attachment/attachment/589/ICRA20_1157_FI.pdf)

## Dataset Link

[https://github.com/rr-learning/transferable_dynamics_dataset](https://github.com/rr-learning/transferable_dynamics_dataset) 

# Dataset 2: Forward Dynamics Dataset Using KUKA LWR and Baxter

## Dataset Overview

Two recorded datasets gathered from two different robotic manipulators, the KUKA Light Weight Robot (LWR) and Rethink Robotics Baxter (one arm, equipped with a parallel gripper). The datasets contain trajectories generated during the execution of **pick and place tasks**. The pick and place locations were drawn randomly from two non-overlapping areas with size 50 × 50 cm each, as illustrated in the figure below. The robots were considered to have full executed a task by starting and finishing at the same location. The pick and place locations were randomly chosen.

![](/images/ds2.png){:height="900px" width="600px"}

For the forward dynamics, KukaDirectDynamics has 10 trajectories from Kuka LWR iwa, whereas BaxterDirectDynamics has 10 trajectories from Rethink Baxter robots. The rows represent the number of samples.

## Paper Reference

[A reservoir computing approach for learning forward dynamics of industrial manipulators](https://ieeexplore.ieee.org/document/7759116)

## Dataset Link

[https://bitbucket.org/athapoly/datasets/src/master/](https://bitbucket.org/athapoly/datasets/src/master/)

# Dataset 3: Inverse Dynamics Dataset Using UR10 and Baxter

## Dataset Overview

For the inverse dynamics, BaxterRand has 10 trajectories generated by point reaching movements of the Rethink Baxter robot, BaxterRhythmic has 10 trajectories generated by a circular movement of the Rethink Baxter robot, URpickNplace has 10 trajectories generated by pick n place of a 5 kg object for the Universal Robots UR10 manipulator. The rows represent the number of samples.

![](/images/ds2.png){}

## Paper Reference

[Real-time Deep Learning of Robotic Manipulator Inverse Dynamics](https://www.researchgate.net/publication/282851496_Real-time_Deep_Learning_of_Robotic_Manipulator_Inverse_Dynamics)

## Dataset Link

[https://bitbucket.org/athapoly/datasets/src/master/](https://bitbucket.org/athapoly/datasets/src/master/)

# Dataset 4: Inverse Dynamics Dataset Using KUKA

## Dataset Overview

The dataset is recorded from a real robot manipulation experiment, where a KUKA arm pushes flasks filled with 200, 300 and 400 milliliters of water. The different training set sizes range from100 to 100,000samples, whilst the number of test samples, range from 20 to 16,000. The dataset recorded consists of joint angles, joint velocities, joint accelerations as well as the joint torques in a teleoperation experiment using a mirroring of commands approach in a bimanual setting. The data is taken for the first five joints (d=5) of the arm. The remaining two wrist joints were hardly used in the experiment and hence were not recorded. The data is stored in .mat files with 20 trajectories for each .mat file. 

## Paper Reference

[Learning inverse dynamics models in O(n) time with LSTM networks](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8246965)

## Dataset Link

[http://robotics.com.de/ds/DATASETHumanoids2017Rueckert.zip](http://robotics.com.de/ds/DATASETHumanoids2017Rueckert.zip)
