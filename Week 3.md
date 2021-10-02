# Statistical Rethinking Chapter 3 Notes

- [Statistical Rethinking Chapter 3 Notes](#statistical-rethinking-chapter-3-notes)
  - [3.1 Sampling from the a grid-approximate posterior](#31-sampling-from-the-a-grid-approximate-posterior)
  - [3.2 Sampling to summarize](#32-sampling-to-summarize)
    - [3.2.1. Intervals of defined boundaries](#321-intervals-of-defined-boundaries)
    - [3.2.2. Intervals of defined mass](#322-intervals-of-defined-mass)
    - [3.2.3. Point estimates](#323-point-estimates)
  - [3.3 Sampling to simulate prediction](#33-sampling-to-simulate-prediction)
    - [3.3.1. Dummy data](#331-dummy-data)
    - [3.3.2. Model checking.](#332-model-checking)
      - [3.3.2.1. Did the software work?](#3321-did-the-software-work)
      - [3.3.2.2. Is the model adequate?](#3322-is-the-model-adequate)
  - [3.4 Summary](#34-summary)

The posterior distribution is a probability distribution. And like all probability distributions, we can imagine drawing samples from it. The sampled events in this case are parameter values. Most parameters have no exact empirical realization. The Bayesian formalism treats parameter distributions as relative plausibility, not as any physical random process. In any event, randomness is always a property of information, never of the real world. 

This chapter teaches you basic skills for working with samples from the posterior distribution. There are two reasons to adopt the sampling approach.

First, many scientists are uncomfortable with integral calculus, even though they have strong and valid intuitions about how to summarize data. 

Second, some of the most capable methods of computing the posterior produce nothing but samples, such as MCMC.

The most important thing for science to do requires thinking, not testing(statistics).

## 3.1 Sampling from the a grid-approximate posterior

1. You can see that the estimated density is very similar to ideal posterior you computed via grid approximation. If you draw even more samples, maybe 1e5 or 1e6, the density estimate will get more and more similar to the ideal.

2. That isn’t of much value. But next it is time to use these samples to describe and understand the posterior. That is of great value.

## 3.2 Sampling to summarize

1. Common questions include: 
   * How much posterior probability lies below some parameter value? 
   * How much posterior probability lies between two parameter values? 
   * Which parameter value marks the lower 5% of the posterior probability? 
   * Which range of parameter values contains 90% of the posterior probability?
   * Which parameter value has highest posterior probability?
These simple questions can be usefully divided into questions about (1) intervals of *defined boundaries*, (2) questions about intervals of *defined probability mass*, and (3) questions about *point estimates*. 

### 3.2.1. Intervals of defined boundaries

### 3.2.2. Intervals of defined mass

1. It is more common to see scientific journals reporting an interval of defined mass, usually known as a *confidence interval*. An interval of posterior probability, such as the ones we are working with, may instead be called a *credible interval*. We’re going to call it a *compatibility interval* instead.

2. Intervals of this sort, which assign equal probability mass to each tail, are very common in the scientific literature. We’ll call them percentile intervals (PI). These intervals do a good job of communicating the shape ofa distribution, as long as the distribution isn’t too asymmetrical. 

3. In terms of describing the shape of the posterior distribution—which is really all these intervals are asked to do—the percentile interval can be misleading. In contrast, we can use the 50% highest posterior density interval (HPDI) The HPDI is the narrowest interval containing the specified probability mass. 

4. The HPDI has some advantages over the PI. But in most cases, these two types of interval are very similar. They only look so different in this case because the posterior distribution is highly skewed. 

5. The HPDI also has some disadvantages. HPDI is more computationally intensive thanPI and suffers from greater simulation variance, which is a fancy way of saying that it is sensitive to how many samples you draw from the posterior.

6. Overall, if the choice of interval type makes a big difference, then you shouldn’t be using intervals to summarize the posterior.

### 3.2.3. Point estimates

1. One principled way to go beyond using the entire posterior as the estimate is to choose a *loss function*. A loss function is a rule that tells you the cost associated with using any particular point estimate. 

2. The two most common examples are the absolute loss, which leads to the median as the point estimate, and the quadratic loss $(d − p)^2$, which leads to the posterior mean as the point estimate. 

## 3.3 Sampling to simulate prediction

For what?

(1) Model design. 
(2) Model checking.
(3) Software validation. 
(4) Research design. 
(5) Forecasting. 

### 3.3.1. Dummy data

We will call simulated data from the model *dummy data*, to indicate that it is a stand-in for actual data. 

### 3.3.2. Model checking. 

Model checking means (1) ensuring the model fitting worked correctly and (2) evaluating the adequacy of a model for some purpose. Since Bayesian models are always *generative*, able to simulate observations as well as estimate parameters from observations, once you condition a model on data, you can simulate to examine the model’s empirical expectations.

#### 3.3.2.1. Did the software work? 

In the simplest case, we can check whether the software worked by checking for correspondence between implied predictions and the data used to fit the model i.e. *retrodictions*, as they ask how well the model reproduces the data used to educate it. It often catches silly mistakes, mistakes of the kind everyone makes from time to time.

#### 3.3.2.2. Is the model adequate?

1. It’s useful to also look for aspects of the data that are not well described by the model’s expectations. The goal is not to test whether the model’s assumptions are “true,” because all models are false. 
2. Rather, the goal is to assess exactly how the model fails to describe the data, as a path towards model comprehension, revision, and improvement.
3. We lose this information when we pluck out a single parameter value and then perform calculations with it. This loss of information leads to overconfidence.
4. So if you were to compute the sampling distribution of outcomes at each value of p, then you could average all of these prediction distributions together, using the posterior probabilities of each value of p, to get a posterior predictive distribution.
5. The independent assumption is questionable. If the assumption is violated, then the model may be mis-specified. But whether or not the mis-specification should lead us to try other models will depend upon our specific interests.
6. In the long run, even the wrong model will converge on the correct proportion. But it will do so more slowly than the posterior distribution may lead us to believe.

## 3.4 Summary

Our fundamental tool is samples of parameter values drawn from the posterior distribution. Working with samples transforms a problem of integral calculus into a problem of data summary. These samples can be used to produce intervals, point estimates, posterior predictive checks, as well as other kinds of simulations.
