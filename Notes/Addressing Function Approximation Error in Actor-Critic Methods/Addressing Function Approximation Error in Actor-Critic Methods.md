## Addressing Function Approximation Error in Actor-Critic Methods

#### 1.Problem

Overestimation bias is a property of Q-learning in which the
maximization of a noisy value estimate induces a consistent
overestimation.

Due to overestimation bias, this accumulated error can cause arbitrarily bad states to be estimated as high value, resulting in suboptimal policy updates and divergent behavior.

DDPG（ actor- critics + DQN) also have Overestimation problem.

#### 2.Solution

##### 2.1 Clipped Double Q-Learning for Actor-Critic

Target function in Double DQN:

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/3.9.2021/1.png)

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/3.9.2021/2.png)



**Clipped Double Q-learning**:  compare biased estimate Q1,  upper-bound the less biased value estimate Q2, taking the minimum between the two estimates, to give the target update of our Clipped Double Q-learning algorithm.



Note that:     Y : target function      Q: value function 

**Result**:  While this update rule may induce an **underestimation bias**, this is far preferable to overestimation bias, as unlike overestimated actions, the value of **underestimated actions will not be explicitly propagated** through the policy update.

##### 2.2 Target Networks and Delayed Policy Updates

Target Network: without target networks, the divergence that occurs is the result of policy updates with a high variance value estimate.



**Delayed Policy Updates**: In this way, when the policy is updated, the TD error should be minimized first, so that the policy will not be affected by the error when it is updated, resulting in high variance.





##### 2.3  Target Policy Smoothing Regularization

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/3.9.2021/3.png)

By adding a small amount of random noise to the target
policy.

Where the added noise is clipped to keep the target **close to**
**the original action**
