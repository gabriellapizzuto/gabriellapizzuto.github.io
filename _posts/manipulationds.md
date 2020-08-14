---
title: 'Real Robot Manipulation Datasets For Learning Dynamics'
date: 2020-08-14

tags:
  - robotics
---


# Real Robot Manipulation Datasets For Learning Dynamics

---

TL; DR: **Real robot datasets** are especially useful to benchmark and **evaluate** **model learning** techniques. Our efforts is to maintain a list of the available datasets for **learning forward and inverse dynamics of robotic manipulators** to encourage more reproducible research in robotics. 

## *Why do we need these?*

Dynamics models are key to achieve more compliant controllers. Benchmarking and evaluating data-driven dynamics learning models requires datasets that are available across platforms, and to date there is no such collection. 

## Forward Dynamics

For a robot with N degrees of freedom (DoFs), the forward dynamics model is given by: 

$${\ddot q} = M^{-1}({q})({\tau} - h({q}, {\dot{q}}))$$

$\ddot q$ are the joint accelerations which the model will learn

$M^{-1}({q})$ is the inverse of the inertia matrix

$h({q}, {\dot q})$ comprises Coriolis and centripetal forces, friction and gravity

$\mathbf{\tau}$ are the joint torques

$q, \dot q$ are the respective joint positions, velocities and accelerations for each joint 

Using a model learning approach, this is formulated through the following:

$$\ddot{q} = Forward Dynamics(q, \dot{q}, \tau )$$

## Inverse Dynamics

For a robot with N DoFs, the inverse dynamics model is given by: 

$$\mathbf{\tau} = M({q}){\ddot{q}} + h({q}, {\dot{q}})$$

$\mathbf{\tau}$ are the joint torques which the model will learn

$M({q})$ is the inertia matrix

$h({q}, {\dot q})$ comprises Coriolis and centripetal forces, friction and gravity

$q, \dot q, \ddot q$ are the respective joint positions, velocities and accelerations for each joint 

Using a model learning approach, this is formulated through the following:

$${\tau} = Inverse Dynamics(q, \dot{q}, \ddot{q})$$

Here, the inputs are the joint positions, velocities and accelerations and the outputs are the learned torques. 

## Summary of Available Datasets

[Manipulation Datasets For Learning Dynamics](https://www.notion.so/e00899f707de491893528b12ca0c8e14)

# Dataset 1: Transfer Dynamics Dataset [Sine Waves] (ICRA 2020)

## Dataset Overview

The data was recorded from a 3  degree of freedom (DoF) torque-controlled real-robotic system. The control and observation rate is 1000 Hz, i.e. the time elapsed between t and t + 1 is 0.001 seconds. The system is run for multiple rollouts, each of which lasts 14 seconds, hence T = 14000. The control input corresponds to the three desired torques (Newton metres) sent to the motors of each joint at time index t. The observation is nine-dimensional and contains measured angles (radians), measured velocities (radians / seconds) and measured torques (Newton metres) at each joint. Two real-world datasets, one using open-loop controllers and one using closed-loop controllers. In the open loop case we sample trajectories of desired torques from Gaussian processes (GPs). In contrast, for feedback policies, we use PD control to track trajectories in joint space which are generated as a random superposition of sine waves.

![https://github.com/rr-learning/transferable_dynamics_dataset/raw/master/img/5.png](https://github.com/rr-learning/transferable_dynamics_dataset/raw/master/img/5.png)

[Dataset Properties](https://www.notion.so/855d1ac55f1e41529749c21207caa485)

## **Paper Reference**

[](https://www.is.mpg.de/uploads_file/attachment/attachment/589/ICRA20_1157_FI.pdf)

## Dataset Link

[https://github.com/rr-learning/transferable_dynamics_dataset](https://github.com/rr-learning/transferable_dynamics_dataset) 

# Dataset 2: Forward Dynamics Dataset on KUKA LWR and Baxter [Pick and Place] (IROS 2016)

## Dataset Overview

Two recorded datasets gathered from two different robotic manipulators, the KUKA Light Weight Robot (LWR) and Rethink Robotics Baxter (one arm, equipped with a parallel gripper). The datasets contain trajectories generated during the execution of **pick and place tasks**. The pick and place locations were drawn randomly from two non-overlapping areas with size 50 × 50 cm each, as illustrated in the figure below. The robots were considered to have full executed a task by starting and finishing at the same location. The pick and place locations were randomly chosen.

![%5BPolished%5D%20Manipulation%20Datasets%20For%20Learning%20Dyna%2074773c7f552b44589d576de7380494f6/Untitled.png](%5BPolished%5D%20Manipulation%20Datasets%20For%20Learning%20Dyna%2074773c7f552b44589d576de7380494f6/Untitled.png)

For the forward dynamics, KukaDirectDynamics has 10 trajectories from Kuka LWR iwa, whereas BaxterDirectDynamics has 10 trajectories from Rethink Baxter robots. The rows represent the number of samples. The columns comprise the following: 

[Dataset Properties](https://www.notion.so/212cacdd4cae476eaea4d920361cea43)

[Dataset Breakdown](https://www.notion.so/12863ff061ac42a098c34029620c296c)

## **Paper Reference**

[A reservoir computing approach for learning forward dynamics of industrial manipulators - IEEE Conference Publication](https://ieeexplore.ieee.org/document/7759116)

## Dataset Link

[Bitbucket](https://bitbucket.org/athapoly/datasets/src/master/)

# Dataset 3: Inverse Dynamics Dataset on UR10 and Baxter [Pick and Place] (IROS 2015)

## Dataset Overview

For the inverse dynamics, BaxterRand has 10 trajectories generated by point reaching movements of the Rethink Baxter robot, BaxterRhythmic has 10 trajectories generated by a circular movement of the Rethink Baxter robot, URpickNplace has 10 trajectories generated by pick n place of a 5 kg object for the Universal Robots UR10 manipulator. The rows represent the number of samples. The columns comprise the following:

[Dataset Breakdown](https://www.notion.so/6efff043aedb418bab2fc5b4fa6dddd2)

## **Paper Reference**

[(PDF) Real-time Deep Learning of Robotic Manipulator Inverse Dynamics](https://www.researchgate.net/publication/282851496_Real-time_Deep_Learning_of_Robotic_Manipulator_Inverse_Dynamics)

## Dataset Link

[Bitbucket](https://bitbucket.org/athapoly/datasets/src/master/)

# Dataset 4: Inverse Dynamics Dataset on KUKA [Object Manipulation with Various Loads] (Humanoids 2017)

## Dataset Overview

The dataset is recorded from a real robot manipulation experiment, where a KUKA arm pushes flasks filled with 200, 300 and 400 milliliters of water. The different training set sizes range from100 to 100,000samples, whilst the number of test samples, range from 20 to 16,000. The dataset recorded consists of joint angles, joint velocities, joint accelerations as well as the joint torques in a teleoperation experiment using a mirroring of commands approach in a bimanual setting. The data is taken for the first five joints (d=5) of the arm. The remaining two wrist joints were hardly used in the experiment and hence were not recorded. The data is stored in .mat files with 20 trajectories for each .mat file. 

![%5BPolished%5D%20Manipulation%20Datasets%20For%20Learning%20Dyna%2074773c7f552b44589d576de7380494f6/Untitled%201.png](%5BPolished%5D%20Manipulation%20Datasets%20For%20Learning%20Dyna%2074773c7f552b44589d576de7380494f6/Untitled%201.png)

## **Paper Reference**

[Learning inverse dynamics models in O(n) time with LSTM networks - IEEE Conference Publication](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8246965)

## Dataset Link

[](http://robotics.com.de/ds/DATASETHumanoids2017Rueckert.zip)
