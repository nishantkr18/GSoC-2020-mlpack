# Week 2 and 3

  8th June - 21st June , 2020

## Work done
- Added a common function(agentTest) for tests in QLearning.
- Added C51's layout as a separate network in `q_networks`, with Predict and Forward functions completed.
- Added the calculation for target distribution in C51, along with the Backward function.
- Made separate training functions for categorical and non-categotical versions of dqn, thus ensuring maximum reuse of code.
- Initially I thought of creating a separate replay method for N-step, but later found a way to addon changes to `RandomReplay` and `PrioritizedReplay`. Now multi-step can be enabled by just passing `n` as a last parameter, while initializing the replay method.

## Problems faced

A rather interesting issue that got unnoticed was the way noisy layers were addressed in noisy implementations of simple and dueling dqn. The layers had a special function (called `ResetNoise`) to be called after each update step. So, we had to somehow refer to all the noisy layers for that. For this, we were using a list of Layer pointers. This was a problem, since when we copied over the learningNetwork to targetNetwork in q_learning, both the networks referred to the same noisy layers. This bug was resolved by storing just the indices where the noisy layers were used, and calling `ResetNoise` on each noisy layer using `boost::get<>`.

Apart from that, the target distribution calculation for C51 dealt with a good amount of matrix manupilations, which got a bit confusing in the begining, but was very satisfying in the end, when it got over.

By the way, the c51 implementation doesn't converge. I searched a lot, but couldnt find what the error was. I even made a pytorch implementation to compare the algo with. The same workflow converges on pytorch, but doesn't in mlpack. We are still investigating what the cause might be. Here's the [link](https://github.com/mlpack/mlpack/pull/2454).

## Lastly:

By now, I'm pretty sure that most colleges, especially ours, are going to conduct their next semester completely online. I guess it'll be a new experience altogether! I'm not sure when's the next time we are going to see our college...

This week, I saw two great movies, both incredible in their respective genres.
The 'Green Mile' had a very profound effect on me. 
'Knives Out' is a recent film, and I was surprised why I hadn't heard of it earlier, considering the above average ratings and familiar artists. Anyways, I guess it can be counted among the best mystery movies that I've seen.

Btw, I recently found out that watching unboxing videos can feel quite satisfying sometimes..

Thanks for reading, and have a good one ;)