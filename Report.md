# Report
This is the third project of [Deep Reinforcement Learning Nanodegree](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) program of Udacity. This code is based on the [repository](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum) of Udacity, and the modifications regarding the two agents were based on the [blog post](https://opensourcelibs.com/lib/deeprl-p3-collaboration-competition).

## Network
**Batch Normalization** : Both Actor and Critic networks were batch normalized to collect less correlated samples from the replay buffer.<br/>
**Double the Size of the Number of the Units** :In the Critic Network, the first and second fully connected layers receive double the size of states and actions to calculate the values of the two agents.<br/>

## Hyperparameters
### The parameters are based on the paper (Lillicrap et al., 2015), but modified a lot to increase the performance.
<pre>
BUFFER_SIZE = int(1e5)  # replay buffer size<br/>
BATCH_SIZE = 128        # minibatch size<br/>
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters<br/>
LR_ACTOR = 1e-5         # learning rate of the actor <br/>
LR_CRITIC = 1e-4        # learning rate of the critic<br/>
WEIGHT_DECAY = 0        # L2 weight decay<br/>
UPDATE_EVERY = 1        # skip training steps<br/>
num_agents = 1          # number of agents<br/>
EPS_START = 5.0         # initial value for epsilon in noise decay process in Agent.act()<br/>
EPS_EP_END = 300        # episode to end the noise decay process<br/>
EPS_FINAL = 0           # final value for epsilon after decay<br/>
LEARN_NUM = 1           # number of learning passes<br/>
</pre>

## Agent
To start the training more stabily, the initial parameters of the target networks of Actor and Critic were broadcasted to those of the local networks using a [pytorch function](https://pytorch.org/docs/stable/generated/torch.Tensor.copy_.html). When I did not implemented this part, the reward fluctuated from the negative to the positive scores in the beginning of the training. 

## Main(DDPG Algorithm)
I have started with the DDPG code to solve this project. To adapt it to train multiple agents, I have modified the algorithm so that each agent receives its own local observation. Thus, both agents were simultaneously trained through self-play. Each agent used the same actor network to select actions, and the experience was added to a shared replay buffer.

To enable for the two agents learn together, I reshaped the ``states`` size and the ``next_states`` size into the double (from 24 to 48) and fed it to the ``Agent`` module.

Referred to the [blog post](https://opensourcelibs.com/lib/deeprl-p3-collaboration-competition), I revised the DDPG algorithm with two separate agents (``agent_0`` and ``agent_1``) and concatenated their actions to fed it to the environement and ``Agent`` module.

## Result
The combination of the batch normalization, proper hyperparameters, and the initial weight stabilization, the agent reached the target score(+0.5) around 40 episodes.

## Ideas for Future Work
* For this project, I assigned separate agent to solve the multi agent problem. Next time, I want to solve it with many agents simultaneously.
