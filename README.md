# tennis-collab-compet-p3-drlnd

Deep reinforcement learning nanodegree project 3

[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif "Trained Agent"

# Introduction
This project is part of Udacity Deep Reinforcement Learning Nanodegree. In this project we will train 2 agents to play tennis using Unity ML environment.

![Trained Agent][image1]

# Objective of the project - 
In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single score for each episode.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

## State Space and Action Space- 

- The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation

- Each action is a vector with 2 numbers, corresponding to movement toward (or away from) the net, and jumping.

# Requirements - 

1. First requirement to run this project is to setup drlnd repository. Follow the instructions mentioned on their github repository - [link](https://github.com/udacity/deep-reinforcement-learning#dependencies)

2. After creating a new environment and installing drlnd repository and its dependencies, clone this repo and run the following command to install all the python libraries.

```bash
git clone https://github.com/milind97/tennis-collab-compet-p3-drlnd.git
cd tennis-collab-compet-p3-drlnd
pip install -r requirement.txt
```
3. After this you will also need Unity ML agents environment for the simulation to run. Download the environment from one of the links below.  You need only select the environment that matches your operating system

    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
    
    - (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    - (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment.  You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent.  (_To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the **Linux** operating system above._)
    
4. Place the downloaded file into "data" folder for this repository.

# Project Structure - 

- src
    - tennis_agent.py
    - tennis_model.py
- data
    - checkpoint_actor.pth
    - checkpoint_critic.pth
- Tennis.ipynb
- README.md
- Report.md
- requirements.txt


This repository contains 2 folders - 
1. `src` - This folder has all the required code to train the agent.
2. `data` - This folder contains the saved model weights for the trained agent.
3. Tennis.ipynb - This jupyter notebook has codes to train the agent using ddpg algorithm and to run the trained agent.
4. README.md - Contains intructions to use this repository
5. Report.md - Contains information about the algorithm used to train the agent.

# Steps to run it

1. Install all the dependencies and run the cells in Continuous_Control.ipynb jupyter notebook.



