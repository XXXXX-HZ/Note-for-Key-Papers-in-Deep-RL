## Playing Atari with Deep Reinforcement Learning

#### 1.Innovation:

The first to combine deep learning model to successfully learn control policies directly from high-dimensional sensory input using reinforcement learning.

#### 2. Introduction:

DL: required large amounts of hand labelled training data; Assume the data samples to be independent; assume a fixed underlying distribution.

RL: must be able to learn from a scalar reward signal that is frequently sparse, noisy and delayed; Encounter sequences of highly correlated states;data distribution changes as the algorithm learns new behaviours.

From the above , three problems need be solved when combining RL and DL:

What if there is no label?
What if the sample correlation is too high?
What if the target distribution is not fixed?



#### 3.Solution:

The model is a convolutional neural network, trained with a variant of Q-learning, whose input is raw pixels and whose output is a value function estimating future rewards.

CNN+ Q-learning = Deep Q network

Q-learning algorithm, with stochastic gradient descent to update
the weights. (use reward to create label)

To alleviate the problems of correlated data and non-stationary distributions, we use an experience replay mechanism  which randomly samples previous transitions, and thereby
smooths the training distribution over many past behaviors.



#### 4.Deep Reinforcement learning

 ![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.25.2021/image-20210227214429707.png)

Experience Replay:

we store the agent’s experiences at each time-step,  ![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.25.2021/image-20210227220546854.png) in a data-set  ![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.25.2021/image-20210227220858477.png) , pooled over many episodes into a replay memory. During the inner
loop of the algorithm, we apply Q-learning updates, or minibatch updates, to samples of experience, drawn at random from the pool of stored samples. After performing experience replay, the agent selects and executes an action according to  greedy policy. 

