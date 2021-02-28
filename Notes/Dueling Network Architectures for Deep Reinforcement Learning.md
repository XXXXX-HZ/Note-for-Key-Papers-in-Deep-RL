## Dueling Network Architectures for Deep Reinforcement Learning

#### 1.motivation:

In many application scenarios, there are many different states of action corresponding to the same Q value.  In order to distinguish the influence of state and action on Q, Dueling DQN was designed.

#### 2. Dueling DQN:

The dueling architecture can learn which states
are (or are not) valuable, without having to learn the effect
of each action for each state.

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.26.2021/7.4.png)

The first path will output a **scalar**, and the scalar is called V(s), Because it depends on the input S, so it's called V(s), is a scalar

The second path will output a **vector**, which is called A(s, a), where each action has a value.



#### 3.Benefit

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.26.2021/7.5.png)

sometimes when you update Q value, you don't necessarily update V(s) and A(s, a) together. You just update V(s) , and Q will change. This is a more efficient method, because updating A is often cumbersome.

#### 4.Restriction

if V(s)= 0, then A is equal to Q, then you will not get any benefits from Dueling DQN. You will just be the same as the original DQN. In order to avoid this problem, you actually have to put some constraints on A, so that updating A is actually a hassle, and the network tends to want to solve the problem in terms of V(s)

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.26.2021/20190603000219408.png)

This is the final approach adopted in the original text, as shown in the above formula. To address this issue of identifiability, they can force the advantage function(A) estimator to have zero advantage at the chosen action. Note that while subtracting the mean in equation helps with identifiability, it does not change the relative rank of the A (and hence Q) values.

