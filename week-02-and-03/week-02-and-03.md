# Week 2 and 3

  25th May - 7th June , 2020

## Work done

- Completed implementing backward function with gradient flow in Dueling Networks.
- Completed Forward and Backward pass for NoisyLinear implementation.
- Changed passing of the network along with other parameters to the QLearning agent, to pass by reference. This avoided the unnecessary copy/move operations. 
- After having made arrangements for deep copy of the network in Dueling DQN, the agent now works. So added tests for dueling netork.
- Added Reset for the noise and network parameters as described in the paper, in NoisyLinear implementation; added proper tests for Noisy Linear.
- Added NoisyDQN. Initially I thought of making it as a separate network, but then found a way to add `isNoisy` as a flag to both Simple and Dueling DQN. This would enable Noisy varients of both types to be created, with max code reusability. Finally added tests, and tuned hyperparameters to get it converged.


## Problems faced
- A major problem popped up in copying over the Dueling network. Since the network uses Concat and Sequential layers in the form of pointers while adding subnetworks, its difficult to directly copy over. Thats because it may still refer to the previous network.(Shallow copy). Ultimately I had to spend some time searching for proper ways to copy over networks and pointers(Deep Copy). And with that done, the agent converged on CartPole by running in one shot. That was awesome because I generally expect silly mistakes in my implementation. 😁
- Somehow, the Add function for the concat `concat.Add()` kept pointing to `mlpack::ann::Add` which was a different class. In the end, we had to remove one of the three overloaded `Add` member functions in `Concat` class. Errors in the test due to this change took some time to rectify.
- When adding noisy linear as a new layer type to `LayerTypes`, found out that there's a limit to the number of types you can define in `boost::varient`. (i guess 50) 


## Lastly:

SpaceX's launch was a delight to watch! It me led to watch **First Man**. I'd recommended that of u r into space stuff ;)

Number of people infected due to COVID is a concern, but people are recovering as well, so there is still hope.

Thanks for reading! Stay safe.