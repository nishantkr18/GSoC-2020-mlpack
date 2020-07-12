# Week 6 and 7

  29th June - 12th July , 2020. Due to end semester examinations, I had to take a week (22nd to 28th June) off.

## Important changes:

We all know that the action space for an environment can either be continuous or discrete in gym-based environments. Initially, `Action` for each discrete environment was stored as a struct, containing an `enum` representing the action. On the other hand, continuous environments was stored as a double array, again inside a struct. Some classes like the Random and Prioritized replay, which should work for both continuous and discrete, should be reusable. And, since `State` was also being used as a class, so to maintain consistency, I made `Action` as a class as well. This required some 'backward incompatible' changes, addressed in some parts of q_learning and rl_components tests.

I also create a 'dummy' environment so that we can use lab.mlpack.org to train as well as test the agent using simulation, directly from gym, in the form of gym_tcp_api. Initially we had to train an agent on mlpack's implementation of [environments](https://github.com/mlpack/mlpack/tree/master/src/mlpack/methods/reinforcement_learning/environment), then to show the rendering of the agent solving the environment, we used gym_tcp_api; here's the [link](https://github.com/mlpack/examples/pull/90). This meant that for each env we wanted to test on, it had to be implemented in mlpack's list of environment implementations, so that we could train the agent on it.
But now, with the dummy environment, one can specify the dimensions of the state and action spaces as static members of the `DiscreteActionEnv` aka 'dummy' class, and with that, be able to use all environments of gym_tcp_api. So the mlpack's implementations would only be used as tests for the algorithms.

## Work done:
- Started the first week by adding Soft Actor-Critic, starting with its definition. Also added implementations of constructor and episode functions. This took some time.
- Added Step function for SAC in mlpack.
- Added support for continuous action space in replay methods.
- Started adding gym_tcp_api by making sort of a "dummy" environment, which just stores the type of state and action for discrete environments. With the SAC implementation complete, I plan on adding the 'dummy' env support for continuous actions as well.
- Trained an agent completely using gym_tcp_api, i.e. without using mlpack's env implementation. Although it was a bit slow to train from the simulator(gym_tcp_api), but at the end, the agent was able to balance the pole! (tested only on CartPole for now)
- made corresponding changes in async learning test, for changes made in action of each env.
- Added simple feedforward test for SAC, and added update mechanism for critic networks.
- Changed sampled rewards and terminal to be saved as row vectors instead of column, to avoid confusions and make one line computations like `nextQ = sampledRewards +  config.Discount() * (1 - isTerminal) % arma::min(Q1, Q2);` possible.

## Problems faced:

Figuring out a common way of dealing with discrete and continuous action spaces, while also making the DiscreteActionEnv and other envs compatible simultaneoudsly for q_learning, was a bit challenging.

## Lastly:

After a tiring week of writing assignments, I finally watched 'Dark', after being suggested by so many people! Just after watching season 1, I knew what I had to gift myself on my birthday. So, I quickly got hold of season 2 and 3, stored them on my external hard-drive and told my sister to hide it away, only to give it in November. And by that time, I'm hoping to learn (or atleast make proper sense of) german, as the english dubbing of Dark is not that great :/

If u still didn't get the hint, I strongly suggest u to watch Dark! It was so intriguing, I was forced to learn a new language to take the full essence of it!

Anyway, thanks for reading, and have a good one ;)