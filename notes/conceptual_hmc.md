## Section 1: Computing Expectations by Exploring Probability Distributions

- When computing an integral with respect to some target probability distribution, linearity implies that we want to focus our resources on areas with the largest integrand.

- To identify such areas, we need to take into consideration both the density and the volume of the candidate area, especially in high dimensional spaces.

- In high dimensional spaces, the volume around the mode of the density function is small, and therefore, this region only has a relatively small contribution to the expectation.

- The set that achieves the best balance between volume and density is called the typical set

- As the number of dimensions increases, the typical set becomes narrower. This phenomenon is an example of the concentration of measure.

## Section 2: Markov Chain Monte Carlo

- When using a Markov chain to explore a probability density, we want to figure out whether it will be able to explore the typical set in a finite amount of time.

- Under ideal conditions, there are three phases in the exploration process of Markov chains:
    1. Convergence from the starting point to the typical set
    2. Initial exploration of the typical set
    3. Refinement of the initial exploration

- The Markov chains estimators are computed after the second phase has been reached. The first phase is used to warm-up the Markov chain.

- When the Markov chain encounters regions that are difficult to explore, it usually gets stuck there for a while. This can potentially introduce biases in the estimates.

- The Random Walk Metropolis algorithm uses a normal density as a jumping function. Its advantage is its simplicity, but it scales poorly with the number of dimensions.

## Section 3: The Foundations of Hamiltonian Monte Carlo

- In high dimensional spaces, the number of possible directions that the Markov chain can follow grows exponentially, which makes it hard for it to stay in the typical set.

- The gradient of the probability density contains useful information regarding which direction to follow. However, the gradient will generally lead us towards to mode of the density, which may not be aligned with the typical set. In this case, one must make some adjustments.

- The idea behind Hamiltonian Monte Carlo (HMC) is to lift the target density with a momentum parameter. Using a Hamiltonian function which depends on the momentum parameter, the parameters of the target density and captures the geometry of the typical set, we can generate trajectories in the new space and map them to the original space.

## Section 4: Efficient Hamiltonian Monte Carlo

- Without appropriately tuning the hyperparameters of HMC, it can fail easily. One must consider the interaction between the choice of hyperparameters and the target density.

- One of the properties of the Hamiltonian function is preserving the energy level of the system. This allows decomposing the space into energy level sets.

- The Hamiltonian Markov chain can be decoupled into two processes: the deterministic exploration of the energy level set, and the stochastic exploration of different energy levels. The efficiency of the chain can be analyzed along with those two dimensions.

- The choice of a conditional probability distribution over the momentum parameter should be made with the objective of making the energy level sets uniform to facilitate exploration, but also to ensure that the energy transition matches the marginal energy distribution.

- Integration time must be chosen to balance the tradeoff between taking advantage of coherent exploration and the computational cost of longer integration time. Integration exhibits diminishing returns with respect to time in terms of effective sample size.

## Section 5: Implementing Hamiltonian Monte Carlo in Practice

- When computing solutions to the Hamiltonian function or numerically integrating, errors can coherently add up and cause the chain to drift. To solve this problem, we can use a family of solvers called symplectic integrators.

- Symplectic integrators can fail in neighborhoods of high curvature. Fortunately, this problem is easy to diagnose.

- Using a lower step size for the integrator improves the numerical approximation but requires more computation.

- The choice of the order of the symplectic integrator can significantly affect the efficacy of HMC. However, automated adaption procedures have not yet been fully developed.

