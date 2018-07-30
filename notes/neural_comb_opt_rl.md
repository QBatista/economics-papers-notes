## Key points

- Traditional methods for solving combinatorial optimization problems usually rely on search heuristics that need to be adapted to the problem at hand.

- This paper introduces two approaches which combine reinforcement learning and neural networks to solve such problems: RL pretraining and active search.

- RL pretraining uses a training set to optimize an RNN that parametrizes a stochastic policy using the expected reward as an objective.

- Active search starts from a random policy and iteratively optimizes the RNN parameters on a test instance.

- It is possible to combine these two approaches, which yielded better results in the experiments conducted by the authors.

- These approaches are potentially useful for problems for which designing heuristics is difficult.

- The results achieved in this paper are still far from state-of-the-art performance, but it offers a novel method in a direction that is very promising.