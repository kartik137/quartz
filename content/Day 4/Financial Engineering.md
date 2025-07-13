
## $\mathbb{P}$ vs $\mathbb{Q}$
Back in the day, "give me a bunch of traded liquidity, take the derivatives and compute the pricing of the underlying". $\mathbb{Q}$: risk-neutral measure. Pricing in the present

![[p_vs_q.png]]

Q was much more popular before GFC. 

Back in day, P quants had much less advanced math (Q had math/physics degrees, P had MBAs). Now P is much more mathematically rigorous and requires math/physics backgrounds.


the probability measure which makes the normalized price process a martingale is referred to as “risk-neutral” (we use $\mathbb{Q}$ for this measure)
Risk management and portfolio management aim to forecast and improve the distribution of future returns. This real world probability distribution is typically denoted by $\mathbb{P}$

CAPM is used throughout P. 

![[fin_eng_flow.png]]
![[steps.png]]

Q world is basically just step 1

## Pricing (Step 1)

Payoff is $\Pi_{n,t}$ which is the sum of (change in price) + (cash flow). Cash flows are dividends for equities, coupons for fixed income.


3 axioms of linear pricing.
linearity is the most challenging (e.g. bulk discounts). Insurance doesn't use linearity but most quant finance uses linearity. Linearity means value of pfo is  sum of holdings. 

3 axioms give rise the the linear pricing eqn: $v = \mathbb{E}(S \times \Pi)$

$\mathbb{E} [S] = 1/(1+r)$. Since risk-free return is position, this expectation is strictly less than 1. This is why it is called the discount factor. 

**numeraire Radon-Nikodym derivative**
**numeraire probability measure**

56a.7.2
This is under Q since it's a risk-neutral measure.
the fundamental theorem of asset pricing, as it is the milestone of many standard models used in practice by Q-quants.

[56a.8.3] Definition Q-measure

P-measure defined in [56a.7.2]


## Capital Asset Pricing Model

$R_w = w'R$ where $w$ are the weights and $R$ is the vector of market returns, and $r$ is risk-free rate.
Define Sharpe ratio as $$ SR_w = (E[R_w - r])/SD(R_w-r)$$
Since expectation is linear and SD is invariant under constants. We get $$ SR_w = (E[R_w] - r)/SD(R_w)$$

Can define optimal weights as $w_{SR}$ as the argmax of the above.


Can regress to get $R-r = \alpha + \beta(R^{SR} -r) + \epsilon$ . Can take expectations of both sides. 

If we use the (unknown) optimal $R^{SR}$, then $\alpha = 0$ since you can capture all returns in factors. alphas are just unknown betas. We can think that CAPM isn't a model, it's an identity.


We use market indices (e.g S&P) as a proxy  for$R^{SR}$ since it is actually unknown.

Video 56a.17

### APT
APT is a multivariate generalization of CAPM


CAPM had no assumptions (beyond those of linear pricing theory). The multivariate generalization requires 2 assumptions.
1. Systematic-idiosyncratic
2. No arb


So far we've been analyzing historical data. Now we want to be forward looking.


## Risk Drivers Identification
Need to transform data from subject matter experts into something that can be consumed by statisticians (who don't know finance). This is called Risk drivers identifications

![[risk_drivers_identifications.png]]



What's with the name "risk driver identification"?


Now that the data can be processed by a statistician, we now move from modeling the past to predicting the future.

## Univariate 
![[univariate_quest_for_invariance.png]]
$X_t = m_t + P_t + Y_t$

iid shocks

Video 58a.1. MC ellipse will be a circle (necessary but not sufficient for iid-ness)

58a.1.3 + 58a.1.4


### Multivariate
![[multivariate.png]]
Similar to univariate but we have cointegration (video 58b.4) and it's very hard to use multivariate models (need marginal-copula)



### Repricing




# Appendix

Risk-free rate = US treasuries but... https://www.bloomberg.com/opinion/articles/2025-04-22/us-bonds-have-never-been-risk-free-and-never-will-be 

https://www.bloomberg.com/opinion/newsletters/2025-04-09/save-havens-may-not-be

Explanation of measures, and Randon-Nikodym. Link to Zitkovic's notes