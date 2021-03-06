## CONTINUOUS CONTROL WITH DEEP REINFORCEMENT LEARNING

#### 1. Problem

DQN can only handle discrete and low-dimensional action spaces.

#### 2. Motivation

To solve complex tasks from unprocessed, high-dimensional, sensory input

#### 3. Method

Combine the actor-critic approach with insights from the recent success of Deep Q Network(DQN).

Deep DPG (DDPG) can learn competitive policies for all of
our tasks using low-dimensional observations (e.g. cartesian coordinates or joint angles) using the same hyper-parameters and network structure.

#### 4.Implemention

![1](C:\Users\ZXH18\OneDrive\Desktop\img\3.7.2021\1.png)

The algorithm uses the actor-critic method in DQN2014 to build two neural networks, one actor function network ,one critic network.

Update critic:

The smaller the value of Loss function is, The closer Y and critic network Q. (See the function). So we have better Q.

Update the actor policy.

The better weight U we have, the higher expected J we will have.



