# Recap
![[Pasted image 20250708084353.png]]

Suppose we transform a distribution $X \sim F_X$ via a general distribution. We can not necessarily find the resulting distribution 

Can always write any CDF as a convex combination [2.1.1]:
![[Pasted image 20250708085523.png]]

(TODO: Write out $F^{ac}$, $F^{disc}$, ...). How does this connect to rest of lecture?


In probabilistic framework, we can use the push-forward to find CDF of transformation. This is oftentimes intractable (unlike in the MC framework) [2.3.3]


[54.5]
It is easy to get the push-forward of scenario-probabilities [54.5.3]



# Approaches to ML

Goal: build relationship between input and continuous outputs.
In unsupervised: discover endogenous
RL Goal: perform design of experiments
Go over [Intro 33 and 33.1]

Learning [33.3.1]
Inference [33.3.2]

# Supervised Learning: Regression

Point vs Probabilistic Regression [Intro 34]
[34.3]
![[Pasted image 20250708095402.png]]

Think of regression as SDP:
$\mathcal{l}(\{x,z\}, \mathcal{v}) = \mathbb{E}^f \left\{-\ln f_{\mathcal{v}} (X|Z)\right\}$ where $\{x,z\}$ is the state and $\mathcal{v}$ are the actions

### Point Regression
[34.1.2], [50.2.3]

Gradient descent depends on the underlying (unknown) distribution. Stochastic gradient descent uses sampling as a substitute for the distribution.
[50.2.4]

"Notice that the update for Newton’s method ([50.48](https://www.arpm.co/lab/optimization-tools.html#x311-1494003r48)) is the same as the algorithm for the gradient descent ([50.43](https://www.arpm.co/lab/optimization-tools.html#x311-1493015r43)), except that the scalar γ"

[34.1.4 (particularly the polynomial basis part)]
Need to regularize (ridge, lasso) to avoid overfitting

Trees [34.1.6]
Fit trees via CART

NNs [34.1.7]

### Probabilistic Regression
[34.3 Intro - 34.3.3]. Once we have the loss, we can use the same optimization techniques as point regression

# Classification
[35.1 Intro - 35.1.5]

# Autoencoders
Generalization of PCA. [36.1 Intro]
Other than PCA, one special case of Autoencoders is k-means clustering [36.1.2]

# Optimal Transport
#### Copulas

[4 intro - 4.2]
Joint = Copula + Marginal
So copulas are useful for understanding independence


#### Optimal Transport
Monge Problem [38.1.2]
In general, Monge Problem has no solution (DNE)

Kantorovich solved this by taking a stochastic transformation instead of a deterministic transformation (we are taking the argmin over the coupling in Kantorovich). Can solve numerically via linear programming

Wasserstein Distance [38.3]


#### Probabilistic Causality
Nonlinear probabilistic counterpart of linear causality modeling is probabilistic causality. [40 intro]

Causal Bayesian Networks [40.2, 37.4],
Use DAG to model chain of events (causes/effects) 
Can convert to probabilistic graphic model [37.4.1]

In Causal BNs, the arrows represent causality. 
