# Deep Recurrent Q-learning for Partially Observable MDPs



**Briefly summarize**

1. **Problem**: Deep Reinforcement Learning has limited memory and rely on being able to perceive the complete game screen at each decision point.

2. **Solution**: Add recurrency to a Deep Q-Network(DQN) by replacing the first post-convolutional fully-connected layer with a recurrent  Long Short Term Memory(LSTM).

3.  **Benefits**: DQN's performance declines when given incomplete state observations, However, DRQN is capable of handing partial observability , and that when trained with full observations and evaluated with partial observations, DQRN better handles the loss of the information than dose DQN.

   

#### Introduction:

##### 1. Deep Q- learning:

Q-Learning (Watkins and Dayan 1992) is a model-free
off-policy algorithm for estimating the long-term expected
return of executing an action from a given state. These estimated returns are known as Q-values. A higher Q-value indicates an action a is judged to yield better long-term results
in a state s. Q-values are learned iteratively by updating the
current Q-value estimate towards the observed reward plus
the max Q-value over all actions a' in the resulting state s'：

Q（s,a) : = Q(s,a)+ α（r + γ max Q(s', a') - Q(s, a))

![image](https://github.com/XXXXX-HZ/Note-for-Key-Papers-in-Deep-RL/blob/main/img/2.24.2021/image-20210227115101459.png)；



##### 2.Partial Observability

A POMDP can be described as a 6-tuple（S,A,P,R,Ω,O). 
the states, actions, transitions, and rewards as before, except
now the agent is no longer privy to the true system state
and instead receives an observation o∈Ω with the probability distribution o~O(s).

In the general case, estimating a Q-value from an observation
can be arbitrarily bad since Q(o,a|θ)≠Q(s,a|θ). DRQN can narrow the gap Q(o,a|θ) and Q(s,a|θ).

##### 3. DRQN Architecture



<img src="C:\Users\ZXH18\OneDrive\Desktop\新建文件夹\2.24.2021\image-20210227131514029.png" alt="image-20210227131514029" style="zoom:50%;" />

#####  4. Stable Recurrent Updates

1.Bootstrapped Sequential Updates

2.Bootstrapped Random Updates

##### 5.Conclusion

Real-world tasks often feature incomplete and noisy state
information, resulting from partial observability.

when trained with partial observations, DRQN can generalize its policies to the case of complete observations. despite seeing only a single frame at each step, is still capable integrating information across frames to detect relevant information such as velocity of on-screen objects.
