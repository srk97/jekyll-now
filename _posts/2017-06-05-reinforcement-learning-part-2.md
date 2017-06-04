---
layout: post
title: Reinforcement Learning Part-2!
---

<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# Markov Decision Processes

MDPs describe an environment for reinforcement learning where the environment is fully observable.

Almost all RL problems can be formalised as MDPs

- Partially observable problems can be converted to MDPs

## Markov property

$$P[S_{t+1}|S_t] = P[S_{t+1}|S_1,S_2,...,S_t]$$

If the current state is known, history can be thrown away.

## State Transition Matrix

This is a matrix representing the probabilities of state transitions i.e switching from one state to another.

$$ P =   
        \begin{matrix}
        P_{11} & \cdots & P_{1n} \\\
        \vdots &  &  \\\
        P_{n1} & \cdots & P_{nn} \\\
        \end{matrix}
$$

## Markov Processes(Markov chain)

A Markov process is a sequence of random states $$S_1,S_2,...$$ with the Markov property.

A Markov Process is a tuple (S,P)

- S is a finite set of states
- P is a State Transition probability matrix

## Markov Reward Process

This is a Markov chain with values.

It is a tuple (S,P,R,$$\Gamma$$)

- R is a reward function $$R_s=E[R_{t+1}|S_t=s]$$

- $$\Gamma$$ is a discount factor that lies in [0,1].


## Return 

It is the total discounted reward from time step `t`

$$G_t = R_{t+1}+\GammaR_{t+2}+\cdots = \sum_{k=0}^\infty \Gamma^k R_{t+k+1}$$


