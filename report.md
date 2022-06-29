[image1]: ./data/tennis_required_episodes.png "Episode required"

[image2]: ./data/tennis_score_per_episode.png "Reward per episode"

# Introduction

1. The objective of this project was to train 2 agents to play tennis with each other for as long as possible.
2. Acceptance criteria was to 2 agents such that the max score between them is greator than +0.5 over 100 consecutive episodes.
3. I have used multi agent DDPG algorithm to train the agents till the average reward over 100 consecutive episodes cross 0.5.
4. This report contains brief desciption of the algorithm we have used for the training, the architecture and the hyperparameters used.
5. It also conatins he result of the trained agent, graph of reward vs episodes.

# General desciption of DDPG algorithm - 

- `Deep Deterministic Policy Gradient (DDPG)` is a reinforcement learning technique that combines both Q-learning and Policy gradients. 

- DDPG being an actor-critic technique consists of two models: Actor and Critic.
    - The actor is a policy network that takes the state as input and outputs the exact action (continuous), instead of a probability distribution over actions.
    - The critic is a Q-value network that takes in state and action as input and outputs the Q-value.

- DDPG trains simultaneously two networks: An actor (selects the optimal (deterministic) policy based on the current state) and a critic (approximates the value function of the state-action pair).
- One of the good resource to read can be found [here](https://towardsdatascience.com/deep-deterministic-policy-gradients-explained-2d94655a9b7b)
# Implementation

## 1. Neural Network achitecture used -

I tried a bunch of achitecture with 2 hidden layers and different number of neurons, but the architecture that worked the best was the following - 

1. I have used a multi layed neural network with 2 hidden layers of 128 neurons each.
2. I have introduced batch normalization before input to the fully connected layers.
3. Reduced noise at rate of 1e-6 so that agent tries random actions early on for exploration but then use less random actions later on.
4. The input layer takes a 24 dimensional vector corresponding to current state in environment while the output layer has 2 neurons corresponsing to a single action.
5. The most considerable improvement in peformance came after introducing noise from a normal distribution with mean 0 and std as 1 instead of range between 0 and 1.

## 2. Hyperparameters used

Tried all sorts of weight decay, different learning rates and different episol decay for reducing noise later on. These are the parameters that worked best - 

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

- I was able to achieve a average score of 0.51 over 100 consecutive episodes in 328 episodes.

![Episode required][image1]
- Reward per episode graph -

![Reward per episode][image2]


# Conclusion
1. I used a normal noise distribution and used Batchnormalization which gave the most significant boost in terms of performamce.
2. I tried a bunch of achitechture with more neurons, but the 128 layer achitecture was enough to pass the acceptance criteria.
2. These combinations seemed to work well and I was able to pass the acceptance criteria of +0.5 averaged reward in 100 consecutive episodes.

# Ideas for future work - 

1. I would like to try to pripritized replay buffer in current architecture. I feel like a there are very less time steps with positivev reward, would want to prioritize them.
2. I would like to explore more hyperparameters optimization such as updating 10 times after every 10 time steps. I have coded that already on the code.
3. I would then like to try more powerful algorithms like PPO, A2C, A3C and the recent D4PG algorithm.