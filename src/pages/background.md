# Background


## Bayesian Optimisation
----
Optimisation method backed by a non-parametric stochastic process, usually a Gaussian Process. This GP models the objective function F(x). An acquisition function is then generated from the GP to describe the search strategy for the optima. Primarily used for black box functions with expensive sampling cost as it has a fast convergence rate.

### The Good
- Dealing with a black-box function, ie no gradient decent.
- Can achieve Optimisation on functions of high cost.
- Finds solution in a low number of samples.
- Primarily uses GPs, which allow for a large objective function space.
- Uses acquisition functions which allow for manipulation outside of GP.
- With infinite time (and some acquisition functions) will find the global optima.

### The Bad
- Heavily effected by curse of dimensionality
- Cannot know for sure if current solution is local or global
- Cannot measure distance from global optima.

Examples: Humans processes, Robotics, ML parameter learning.

## Gaussian Processes
---
The driving force of BO. The non-parametric model. Created from Kernel that describes covariance between points in the input space. The GP posterior distribution is a combination of the Kernel and previously observed samples.

### Kernels
The most important part of the GP. Describes covariance between points in input space. Squared Exponential default kernel for BO. (Matern 5/2 also used)


### Kernel Cookbook
Different rules for combining kernels. Equivalent to combining GPs. Will be important later why. Useful for input warping that allows the modelling of non-stationary functions. [Good examples here](http://www.cs.toronto.edu/~duvenaud/cookbook/).

## Acquisition functions
----
This is the search strategy for finding the optima. Has parallels to Bandit problems.
### PI
Probability of improvement. Compares the current best value with all possible search locations to produces a probability of improvement (*ignoring the size of improvement* ). Very prone to local optima. Uses the mean of the posterior.

### EI
Expected improvement. Similar to PI, uses mean of posterior incorporating the expected size of improvement. Again prone to local optima.

### Entropy Search
Minimise uncertainty in the location of optima. Difficult to formulate but provides a better exploration strategy due to less random search.

### UCB
Upper Confidence Bound. Coming from multi-armed bandit research, this function trades off between exploration and exploitation. Encoding optimism in unexplored areas (creating the category of Optimistic Algorithms).

## BO with constraint
----
Known areas of poor results. Prior knowledge. Bounding GP.

### Relationships in input space
Known areas of related space that are non-contiguous, thus badly represented by the parameter space. This is our problem. Area of related domain can allow for increased certainty over domains improving the search. Examples of this use conditional spaces creating graphs of connected variables that will be active or inactive dependant on neighbours.

## Domain Knowledge
----
Domain knowledge is unpopular area of ML. People are trying to remove such knowledge to allow for GAI. However in a search problem this auxiliary knowledge can aid our investigation of the parameter space similarly to how a human would approach a problem. Domain knowledge in this concept can come in two forms, Specification models (parametric models to imitate the objective functions) or Data describing relations/properties of input parameters. The later commonly stored as a relational database.

### Reference Models
Reference Models are essentially a simulation of the objective function. They are similar to the prior knowledge used by the GP. They have uses far beyond that of ML. For example testing software uses them to make sure the a program does as is required.

### Relational Data
Relational Data is often display as a graph, with nodes being objects and edges being some defined relation.

*(Many not be relevant to project anymore)* Some examples in the literature have shown promise, including StarAI and the research following. However most of the research in this field focuses on discovering new relations, ie recommending films that a users hasn't rated yet. This research [RelNN] describes a Neural Net structure to analyse properties of objects in a Relational Graph. It also models the discrete relations as continuous data. Also with some smart normalisation it avoids problems that plague other techniques such that results tend towards a binary nature 1 or 0.

## BO with Domain Knowledge
----
Also called multi-fidelity-BO Here we will discuss techniques previously used.

### State of the Art: Semi-parametric (BOAT)
Bayesian Optimisation Auto Tuners. Created for improving software performance, such as compiler garbage collection. Creates a user defined parametric model to simulated the objective function. This model improves the GPs interpolation, providing a predictor of the general trend. This combination improves the search strategy by removing areas of low value. However a mismatched model could also cause harm to the overall performance.

### State of the Art: Simulation kernel (Robotics)
Defines a GP-kernel that utilises information recorded when running the parameter setting in a simulation. This can include metrics that would difficult to measure physically. This technique is similar to BOAT as the simulation is a model for the objective function in the physical world. The kernel hyperparameters are then trained to model the differences between simulation and physical experiments.

## Gaussian Processes with Relational Knowledge
----
Here we will discuss techniques previously used.

### State of the Art: Multi-Relational Learning with Gaussian Processes
Using latent variables and linear combinations of GPs to describe relations between objects. Attempts to model distributions of unknown relations. The end goal of this research may not be useful, but the construction of GPs from relational data can be adapted for this project.


## Idea
---
F(x) is a combinations of gps from relations + some unknown relation that can be modelled. During BO we learn the combination. We also use this knowledge of the kernel/relations to create an acquisition function that has a concept of related spaces and can explore in an Entropy Search way.
Relational data is are objects and relations. The objects store some preset/information with respect to the input parameters. GPs for relations can be sum of all relations and some drop off between the current x and each objects property.

## Next step
---
Use toy example of Periodic F(x) and a relation between areas in F(x). Try and have the relations guide acquisition function to select areas that will reveal the most information.
