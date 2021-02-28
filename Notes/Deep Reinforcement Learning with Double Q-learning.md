# Deep Reinforcement Learning with Double Q-learning

#### 1. Problem

Q value is usually over estimate. because it includes a maximization step over estimated action values, which tends to
prefer overestimated to underestimated value.

#### 2. Innovation

They  constructed a new algorithm we call Double DQN which not only yields more accurate value estimates, but leads to much higher scores on several games. This also demonstrated that the overestimations of DQN were indeed leading to poorer policies and that it is beneficial to reduce them.

#### 3. Introduction:

1. Deep Q Networks

2. Double Q-Learning

3.  Overoptimize due to estimation errors

   In this section the author demonstrated that upward bias can be caused by any type of estimation error, whether from environmental noise, function approximation, non-stationarity, or any other source. In practice, since the true value is unknown, any method will create some inaccuracies in the learning process. The results of Thrun and Schwartz (1993) mentioned above give the upper limit of overestimation for Q-learning under specific Settings, and the lower limit of overestimation for Q-learning needs to be further deduced.

#### 4. Double DQN

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.27.2021/1.png)

The idea of Double Q-learning is to reduce overestimations by decomposing the max operation in the target into **action**
**selection** and **action evaluation**.

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.27.2021/2.png)

 The function Q: the one we use to update parameter, is action selector

The function Q‘：the target network,  is action evaluator.



#### 

