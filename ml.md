# Machine Learning (notes from '15)
**Supervised Learning**: Using already classified/regressed data learn and predict for any future dataset  
**Unsupervised Learning**: Based on a dataset find patterns and similarities and any new findings  
**Classification**: classify data into n-discrete sets, find a function that maps data to this discrete set  
**Regression**: classify data onto a continuous set; used for prediction of continuous variables pricing, temperature etc.  

### Algorithms  
- k-nearest neighbor
    - classify input based on k nearest neighbor values
    - really seems way too simple...
- classification trees
    - piecewise interpolation
    - diving n-dimensional fields into subsets that hold only one value, via minimizing the fraction of wrong classes in said region or the mean-square error
        - misclassification error and entropy: sum_y{ p(y) log(p(y)) }
        - use arbitrary manifolds for growing classification trees? as opposed to rectilinear grids? topology?
- random forests
    - in a high dimensional dataset start constructing a classification tree
        - at each node choose a random subspace of full dataset and split along those dimensions/features of the data to minimize error
        - bootstrapping over random tress (aka forests) to get reduced variance in ensemble function output
- neural networks

### Ways to solve problem aka minimize estimated loss aka find the conditional distribution (the big picture): Ch. 3. Supervised Learning  
Discriminative: 
- kNN
- random forest
- support vector machines  

Generative: 
- calculate conditional probabliltiy therefore estimated loss using bayesian rules and parameters: fit the distribution  

Exact inference: 
- multivariate gaussian distribution
- conjugate priors
- graphical models
- point estimate of theta (all parameters of dataset)
- maximum likelihood estimate, maximum a posteriori estimate (theta value that maximizes p(th|x,D)
- Optimization, Expectation Maximization, and Empirical bayes (point estimate for parts of theta)  

Deterministic approximations
- Laplace approximation
- Variational Methods
- Expectation Propagation  

Stochastic Approximations
- Markov Chain Monte Carlo (Gibbs, MH), Importance sampling (Particle filtering)

*Above methods are also applicable in unsupervised learning?*

Gradient descent: Cost function update algorithm: other options:
- conjugate gradient
- BFGS
- L-BFGS  

K-means  
- very simple algorithm
- randomly initialize k-points on actual training points and iterate k-means with several initializations to converge on global minimum
- run over several values of k to find the right number k (find least minimum cost k)
- mean normalization and feature scaling in n-dimensional data

Dimensionality reduction
- PCA in 2D, projection of data onto regressed curve dimension (or eigenvector plane aka subspace)
- PCA vs linear regression
    - minimize projection distance (orthogonal distance to projection onto subspace)
- Only use PCA when conventional method on full dataset is too slow

Anomaly detection
- create a library of good input and anomalous input
- calculate a p(x) for all good input
- find a tolerance e below which in the phase space any input will be anomalous
    - key assumption that all features/parameters are independent variables (not effective) that follow gaussian distribution
        - simple polynomial(power) or log manipulations can transform the input feature to have a gaussian distribution then plug it into anomaly detection theorem
- be creative with non-linear superposition of features
- don't need to be creative just calculate a covariance, independent variables computationally cheaper for large matrices

Mapreduce
- Useful for scaling to large datasets
- when taking the sum of large matrices is the bulk of the overhead
