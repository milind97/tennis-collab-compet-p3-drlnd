[image1]: ./data/tennis_required_episodes.png "Episode required"

[image2]: ./data/tennis_score_per_episode.png "Reward per episode"

# Introduction

1. The objective of this project was to train 2 agents to play tennis with each other for as long as possible.
2. Acceptance criteria were to train 2 agents such that the max score between them is greater than +0.5 over 100 consecutive episodes.
3. I have used a multi-agent DDPG algorithm to train the agents till the average reward over 100 consecutive episodes crosses 0.5.
4. This report contains a brief description of the algorithm we have used for the training, the architecture, and the hyperparameters used.
5. It also contains the result of the trained agent and the graph of reward vs episodes.

# General description of DDPG algorithm - 

- `Deep Deterministic Policy Gradient (DDPG)` is a reinforcement learning technique that combines both Q-learning and Policy gradients. 

- DDPG being an actor-critic technique consists of two models: Actor and Critic.
    - The actor is a policy network that takes the state as input and outputs the exact action (continuous), instead of a probability distribution over actions.
    - The critic is a Q-value network that takes in state and action as input and outputs the Q-value.

- DDPG trains simultaneously two networks: An actor (selects the optimal (deterministic) policy based on the current state) and a critic (approximates the value function of the state-action pair).
- One of the excellent resources to read can be found [here](https://towardsdatascience.com/deep-deterministic-policy-gradients-explained-2d94655a9b7b)
# Implementation

## 1. Neural Network architecture used -

I tried a bunch of architecture with 2 hidden layers and different numbers of neurons, but the architecture that worked the best was the following - 

1. I have used a multi-layer neural network with 2 hidden layers of 128 neurons each. I applied the “ReLU” activation function in the outputs of 1st 2 layers and the “tanh” activation function in the last layer.
2. I have introduced batch normalization before input to the fully connected layers.
3. Reduced noise at a rate of 1e-6 so that agent tries random actions early on for exploration but then uses fewer random actions later.
4. The input layer takes a 24-dimensional vector corresponding to the current state in the environment while the output layer has 2 neurons corresponding to a single action.
5. The most considerable improvement in performance came after introducing noise from a normal distribution with mean 0 and std as 1 instead of a range between 0 and 1.

## 2. Hyperparameters used

Tried all sorts of weight decay, different learning rates, and different epsilon decay for reducing noise later on. These are the parameters that worked best - 

- Max number of episodes - 500
- BUFFER_SIZE = 100000
- BATCH_SIZE = 128
- GAMMA = 0.99
- TAU = 0.001
- LR_ACTOR = 0.0001
- LR_CRITIC = 0.001
- WEIGHT_DECAY = 1e-06
- UPDATE_EVERY = 1
- EPSILON_DECAY = 1e-06
- EPS_START = 1.0

# Result (Reward per episode graph)

- I was able to achieve an average score of 0.51 over 100 consecutive episodes in 328 episodes.

![Episode required][image1]
- Reward per episode graph -

![Reward per episode][image2]


# Conclusion
1. I used a normal noise distribution and used Batchnormalization which gave the most significant boost in terms of performance.
2. I tried a bunch of architecture with more neurons, but the 128-layer architecture was enough to pass the acceptance criteria.
2. These combinations seemed to work well and I was able to pass the acceptance criteria of +0.5 averaged reward in 100 consecutive episodes.

# Ideas for future work - 

1. I would like to try prioritized replay buffer in the current architecture. I feel like there are very less time steps with positive rewards and maybe prioritizing them would produce better results.
2. I would like to explore more hyperparameters optimization such as updating 10 times after every 10-time step. I have coded that already on the code.
3. I would then like to try more powerful algorithms like PPO, A2C, A3C, and the recent D4PG algorithm.
