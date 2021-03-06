## Deterministic Policy Gradient Algorithms

#### 1. Problem solve

Due to the partial randomness of the stochastic policy, the method of stochastic policy has low efficiency and large variance. The deterministic policy method is more efficient than the stochastic policy in sampling. However, there is no way to explore the environment, so the off-policy method can only be used to carry out.

#### 2.Motivation

For continuous actions, the **Stochastic PG** in the past requires the expectation of reward in state S and action A, that is, the **sampling of state S and state A at the same time**, while the **Deterministic PG** does not need to sample action A, it **only needs to sample the state**, so the efficiency is greatly improved. so the key problem is what's the difference between Stochastic PG and Deterministic PG, how do we get Deterministic PG.

#### 3.Implemention

1.perfomence objective: (maximizes the cumulative discounted reward)

![1](C:\Users\ZXH18\OneDrive\Desktop\img\3.6.2021\1.png)

2.**Stochastic PG**

And then we take the derivative of (1)

![2](C:\Users\ZXH18\OneDrive\Desktop\img\3.6.2021\2.png)



2.1 On-policy

The PG algorithm(2) does not change, the same calculation of the gradient.



The true action-value Q is actually estimated with the future reward. Each calculation of Q requires the use of the current strategy to interact with the environment to the termination state, which costs too much, so we can use another network to estimate Q, so there are two networks, one actor, and one critic.



2.2 Off-policy

**Off-policy means that the strategy used for data training is not the same as the current strategy to be updated**. Suppose the strategy used for data is β, while the current strategy to be trained is π. Importance sampling is used here to obtain the new strategy gradient

![3](C:\Users\ZXH18\OneDrive\Desktop\img\3.6.2021\3.png)

**importance sampling**： In  sampling, states and actions can only meet the distribution in the data set, that is, the distribution of actions is about β , while the gradient required in our objective function is about π, so the expectation about β can be obtained by multiplying and excluding one β at the same time. importance sampling.

3.**Deterministic PG** 

3.1 On-policy

The critic uses Sarsa updates to estimate the action-value function.

![4](C:\Users\ZXH18\OneDrive\Desktop\img\3.6.2021\4.png)

3.2 Off-policy

Basically the same, except for selecting  the different state in Q (Note that: The difference between 11 and 16)

![5](C:\Users\ZXH18\OneDrive\Desktop\img\3.6.2021\5.png)

