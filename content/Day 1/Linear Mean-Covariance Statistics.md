
# Why the Mean-Covariance Framework?

### Statistical Decision Problem
- A **statistical decision problem** consists of a state space $\mathcal{S}$, the action space $\mathcal{A}$, and the loss function $\mathcal{l}$
- With this problem, the optimal action $\alpha$ under the Bayesian approach is $$\alpha^{\text{Bayes}} = \text{argmin}_\alpha \mathbb{E}\left[l(S, \alpha)\right]= \text{argmin}_\alpha \int l(x, \alpha) dF^*(x)$$
- However, this requires knowing the underlying distribution $F^*(x)$ which is usually unknown and difficult to completely estimate
- Many real-world examples use SDPs such as portfolio optimization. Here we can take $\mathcal{S}$ as the possible portfolios (with risk, position, capital limits), $\mathcal{A}$ are sets of trades, $\mathcal{l}$ is our utility function, and the underlying distribution is the (unknown) distribution of future returns

### Probabilistic Framework
- In the probabilistic framework, we assume we are working with the full distribution $F_X$
- This distribution contains all the information about the random variable but can be challenging to evaluate and estimate
- In the real world, we usually don't know what $F_X$ is and estimating can be difficult if not impossible, since we only have empirical data
- Within the probabilistic framework, we can consider arbitrary transformations of the RV: $Y = f(X)$

## Mean-Covariance Framework
- It is a lot easier to find just the mean and covariance of the distribution empirically
- The first two moments of the distribution (the mean and covariance) describe the distribution well (though not completely)
	- To see this, take the [characteristic function](https://en.wikipedia.org/wiki/Characteristic_function_(probability_theory)) of the distribution, $\phi_X(t)$
	- The characteristic function is equivalent the the pdf/cdf of the distribution: both entirely describe the distribution
	- Taylor expanding gives us $\phi_X(t) = \sum_{k=0}^{\infty} \frac{(it)^k}{k!} \mathbb{E}\left[X^k\right]$ where $\mathbb{E}\left[X^k\right]$ is the $k$-th moment
	- Note that the contribution of the $k$-th moment decreases as $\mathcal{O}\left(\frac{1}{k!}\right)$
	- Hence, the first two moments mostly, though not entirely, describe the distribution
	- Thus, it is a lot easier (and still very useful) to use the mean-covariance framework instead of the probabilistic framework
- N.B:. ***This does not only apply to Gaussian distributions***. It applies to any distribution with finite mean and covariance. This is what makes mean-covariance framework so powerful
- We only want to consider transformations that conserve the mean and covariance of the random variable. One can show these are exactly **affine transformations**: $Y = a + bX$
	- Due to this equivalence, it is best to view affine transformations as exactly the transformations that preserve the MC 
- This is opposed to the probabilistic framework where we consider general transformations, $Y = f(X)$
- We can geometrically visualize the mean-covariance as an ellipse, where the origin of the ellipse is the mean, and the eigenvectors of the covariance matrix describe the principal axes of the ellipse:

	![[mc_ellipse.png]]

- The z-score of an observation tells us how far from the center of a distribution an observation is: $$ z_X(x) = \frac{x - \mathbb{E}(X)}{\mathbb{SD}(x)}$$
- Affine transformation conserve z-scores (i.e an outlier remains an outlier after an affine transformation). One example is a transformation from return space to dollar space
	- A geometric visualization of this: ![[affine_equivariance.mp4]]
- There are two equivalent ways we can find the mean-covariance of an empirical distribution:
	- The mean-covariance that minimizes the z-score (algebraic):
		![[min_z_score.mp4]]
	- The mean-covariance that results in the minimal volume ellipse (geometric):
		![[min_volume.mp4]]

Thus we have two frameworks for SDPs: mean-covariance (MC) and probabilistic.
	![[mc_vs_prob_framework.png]]


### Linear Projection
- In the probabilistic framework, we have conditional distributions $f(x | z)$, the distribution of $X$ given that $Z=z$. This gives us the distribution of $X$ given that $Z=z$ and the joint distribution $f(x,z)$
- The counterpart in the mean-covariance framework is the linear projection operator: $X || Z$. This gives us the mean-covariance of $X$ given that $Z=z$ and the joint mean-covariance of $\{X, Z\} \sim \left\{\mu_{X,Z}, \sigma^2_{X, Z}\right\}$   
- The geometric visualization of linear projection is
	![[linear_projection.png]]
	- It effectively splits the space into two dimensions: the dimension representing the projection of $X$ onto $Z$ (i.e. the best approximation of $X$ given $Z$), and the dimension representing the residuals ($X - \mathbb{E}\left[X || Z \right]$)
- Note that the linear projection operator is an affine transformation
- The linear projection operator gives us the mean & covariance of $X$ given $Z=z$ and the joint distribution of the two
	- Mean is the linear projection and covariance is covariance matrix of residuals
- Similar to conditional distributions, we also have a MC analogue of independence
	- In the probabilistic framework, we say to RVs are **independent** ($X \perp\!\!\!\perp Z$) if the realization of one does not affect the distribution of the other (i.e. the joint CDF is separable: $F_{X,Y} = F_X(x)F_Y(y)$)
	- In the MC framework, two RVs are **uncorrelated** if their cross-covariance is zero ($X \perp\!\!\!\perp_{MC} Z \Leftrightarrow \mathbb{CV}\left[X,Z\right] = 0$)
	- Note that this happens if and only if the expectations of the RVs are separable: $\mathbb{E}\left[XZ\right] = \mathbb{E}\left[X\right]\cdot\mathbb{E}\left[Z\right]$ 
	- Also, if two RVs, $X \perp\!\!\!\perp_{MC} Z$, are uncorrelated then given an affine map $f$, the corresponding transformations are also uncorrelated: $f(X) \perp\!\!\!\perp_{MC} f(Z)$
