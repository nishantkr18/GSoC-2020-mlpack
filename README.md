# Addition of Rainbow and Soft Actor-Critic to RL codebase

## Abstract:
This summer, I'd like to add Rainbow [Hessel et al., 2017](https://arxiv.org/abs/1710.02298) and Soft Actor-Critic [Haarnoja et al., 2019](https://arxiv.org/abs/1812.05905) to the existing reinforcement learning codebase of **[mlpack](http://mlpack.org/)**, as I feel these are one of the most in-demand and recent algorithms, whose implementation in [mlpack](http://mlpack.org/) would be crucial.

Here are the details of what I expect to have accomplished at the end of the summer.

- Improving the current QLearning implementation.
- Implementing Rainbow as an improvement on DQN. This would include adding the following as extensions:
    - Dueling DQN
    - Noisy DQN
    - Categorical DQN
    - N-step DQN
- Writing test cases for each of the implementations
- Implementing Soft Actor-Critic (SAC) for continuous action space, along with its tests
- Creating detailed docs for all the above implementations
- Creating necessary environments, for proper testing of algorithms above (after discussing with mentors)


## Weekly Progress:
### [Week 1  - Layout for Dueling and Noisy DQNs](week-01/week-01.md)
### [Week 2 and 3  - Finishing Dueling and Noisy DQNs](week-02-and-03/week-02-and-03.md)
