## Prioritized experience replay

#### 1.problem:

In prior work, when we used to train your Q-network with sample data, experience transitions were **uniformly sampled** from a replay memory. However, this approach simply replays transitions
**at the same frequency** that they were originally experienced, regardless of their significance.

#### 2. Solution:

 Develop a framework for prioritizing experience, so as to replay **important transitions more frequently**, and therefore learn more
efficiently.

#### 3.Prioritized experience replay

1. Key idea: an RL agent can learn more effectively from some transitions than from others .In particular, they propose to more frequently replay transitions with high expected learning progress, as measured by the magnitude of their temporal-difference (TD) error, which is the difference between the output of the network and the target.
2. Advantage :making the most effective use of the replay memory for learning

#### 4. Prioritizing TD-Error

1.To avoid expensive sweeps over the entire replay memory, TD errors are only updated for the transitions that are replayed;

2.It greatly reduces useless attempts and accelerates the execution speed of the algorithm.

3.issues:

A low TD error on first visit may not be replayed for a long
time.

Sensitive to noise.

Greedy prioritization focuses on a small subset of the experience,This lack of diversity that makes the system prone to over-fitting.

#### 5.stochastic sampling method

1.Aimed at overcoming these issues.

2.Guarante a non-zero probability **even for the lowest-priority** transition. Concretely, we define the probability of sampling transition i as

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/3.1.2021/1.png)

where pi > 0 is the priority of transition i. The exponent α determines how much prioritization is used, with α = 0 corresponding to the uniform case. when α increase, the transition with large TD-error will have higher possibility to be sampled. 

#### 6.Annealing the bias

Prioritized replay introduces bias because it changes this
distribution in an uncontrolled fashion, and therefore changes the solution that the estimates will converge to (even if the policy and state distribution are fixed). We can correct this bias by using
importance-sampling (IS) weights:

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/3.1.2021/2.png)
