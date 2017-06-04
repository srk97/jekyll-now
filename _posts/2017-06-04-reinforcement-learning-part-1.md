---
layout: post
title: Reinforcement Learning Part-1!
---

<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

## Intro

Deep learning mainly is of three types:

- Supervised Learning
- Unsupervised Learning
- Reinforcement Learning

**What makes Reinforcement Learning different from supervised and unsupervised learning?**	

- There is no supervisor i.e we don't have the ground truth
- There is a reward signal associated with an action the agent takes
- The data is non Independent and identically distributed.

	This stack-overflow [answer](https://stackoverflow.com/a/13058903/4989649) explains `i.i.d` data pretty well.	

	"Independent and identically distributed" implies an element in the sequence is independent of the random variables that came before it. In this way, an IID sequence is different from a Markov sequence, where the probability distribution for the $$n^{th}$$ random variable is a function of the previous random variable in the sequence (for a first order Markov sequence).


- Agent's actions affect the incoming data unlike other forms of learning.


## Rewards

A reward `R` is basically a scalar quantity that tells the agent how well it has performed. The ultimate goal of reinforcement learning is to maximize this cumulative reward.

This means that the greedy approach would not work. Evenif a specific action leads to an immediate "good" reward,It might actually be a bad move overall. So, actions have long term consequences. "Foresight" is required to perform better.


## Agent and Environment

- Agent executes action ---> Environment receives an action.

The action affects the environment thereby resulting in a new "state."

- Environment emits an observation ---> The agent receives the observation.

Based on the new observation, the environment emits a
reward that's received by the agent.

This cycle goes on for a number of time steps.

## History and State

- History is the sequence of observations,actions and rewards upto time `t`

- A state is any function of the history. `State` is used to determine what happens next.

## State

- **Environment State**
	
	$$S_t^e$$ is the environment's private representation. This also is the data that the environment uses to emit the next observation and reward.This state may or may not be visible to the agent

- **Agent state**	
	
	This is the agent's internal representation. It can be any function of the history i.e
	$$S_t^a = f(H_t)$$

## Information State (Markov State)	

A state $$S_t$$ is Markov iff 
$$P[S_{t+1}] = P[S_{t+1}|S_1,S_2,...,S_t]$$ 

This means that the future state is only dependent on the present state and nothing else. The states $$S_1,S_2,...S_{t-1}$$ are useless for the inference of the next state.


## Fully observable environments

The environment state is completely visible to the agent.

$$ O_t = S_t^a = S_t^e $$

This is a Markov Decision Process(MDP)

## Partially Observable environments

The agent has its own state representation.This can be 

- Complete History
- Beliefs of the environment state $$S_t^a = (P[S_t^e=S^1],P[S_t^e=S^2],...,P[S_t^e=S^n])$$
- Recurrent Neural Network $$S_t^a = \Sigma(S_{t-1}^aW_s+O_tW_o)$$ 

$$\Sigma$$  is the sigmoid function here.

This is a Partially Observable Markov Decision Process.


## RL agent components

- ## Policy
	It is a mapping from state to action
	- Deterministic policy: $$a = \Pi(s)$$
	- Stochastic policy: 
	$$\Pi(a|s) = P[A_t=a|S_t=s]$$

	Deterministic vs Stochastic Models

	- In deterministic models, the output is fully determined by the parameter values and the initial conditions.
	- Stochastic models possess inherent randomness.The same set of parameter values and initial conditions will lead to an ensemble of different outputs.
	More info [here](http://www4.stat.ncsu.edu/~gross/BIO560%20webpage/slides/Jan102013.pdf)


- ## Value Function
Value function is a prediction of future reward given the state. Actions,therefore are taken based on the value function's output.
$$v_\Pi(s) = E_\Pi[R_{t+1}+\Gamma R_{t+2}+\Gamma^2R_{t+3}+...|S_t=s]$$

$$\Gamma$$ is the discount here. In lecture-2 notes


- ## Model

A model predicts what the environment will do next.We could say it is a simulation of the environment.

- `P` predicts the next state

$$P_{ss'}^a = P[S_{t+1}=s'|S_t=s,A_t=a]$$

- `R` predicts the next reward

$$R_s^a = E[R_{t+1}|S_t=s,A_t=a]$$


## Categories of RL agents

- Model free
	- Policy and/or Value function
- Model Based	
	- Policy and/or Value function
	- Model

## Learning and Planning

- Reinforcement learning
The environment is initially unknown. Agent interacts with environment and improves its policy

- Planning
A model of the environment is known. The agent performs computations with its model and improves its policy.	

