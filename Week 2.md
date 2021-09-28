# Statistical Rethinking Chapter 2  Notes

- [Statistical Rethinking Chapter 2  Notes](#statistical-rethinking-chapter-2--notes)
  - [2.1 The garden of forking data](#21-the-garden-of-forking-data)
    - [2.1.1. Counting possibilities](#211-counting-possibilities)
    - [2.1.2. Combining other information](#212-combining-other-information)
    - [2.1.3. From counts to probability](#213-from-counts-to-probability)
  - [2.2. Building a model](#22-building-a-model)
    - [2.2.1. A data story.](#221-a-data-story)
    - [2.2.2. Bayesian updating](#222-bayesian-updating)
    - [2.2.3. Evaluate](#223-evaluate)
  - [2.3 Components of the model](#23-components-of-the-model)
    - [2.3.1. Variables](#231-variables)
    - [2.3.2. Definitions](#232-definitions)
      - [2.3.2.1. Observed variables](#2321-observed-variables)
      - [2.3.2.2. Unobserved variables](#2322-unobserved-variables)
    - [2.3.3. A model is born](#233-a-model-is-born)
  - [2.4 Making the model go](#24-making-the-model-go)
    - [2.4.1. Bayes’ theorem](#241-bayes-theorem)
    - [2.4.2. Motors](#242-motors)
    - [2.4.3. Grid approximation](#243-grid-approximation)
    - [2.4.4. Quadratic approximation](#244-quadratic-approximation)
    - [2.4.5. Markov chain Monte Carlo](#245-markov-chain-monte-carlo)

1. All statistical modeling has these **two frames**: the small world of the model itself and the large world we hope to deploy the model in. **Navigating** between these two worlds remains a central challenge of statistical modeling. The challenge is greater when we **forget the distinction**.
2. The *small world* is the self-contained logical world of the model. 
   1. All possibilities are **nominated**. 
   2. It is important to be able to verify the model’s logic, making sure that it performs as **expected** under favorable assumptions. 
   3. Bayesian models have some advantages in this regard, as they have reasonable claims to optimality: **No alternative model** could make better use of the information in the data and support better decisions, assuming the small world is an accurate description of the real world.
3. The *large world* is the broader context in which one deploys a model. 
   1. There may be events that were **not imagined** in the small world. 
   2.  the model is always an **incomplete representation** of the large world, and so will make mistakes, even if all kinds of events have been properly nominated. 
   3.  The **logical consistency** of a model in the small world is **no guarantee** that it will be optimal in the large world. 

Passing back and forth between these two worlds allows both formal methods, like Bayesian inference, and informal methods, like peer review, to play an indispensable role.

4. Bayesian analysis provides a general way to discover relevant information and process it logically. Just don’t think that it is the only way.


## 2.1 The garden of forking data

1. A Bayesian analysis is a garden of forking data, in which alternative sequences of events are cultivated. 

2. This approach provides a quantitative ranking of hypotheses, a ranking that is maximally conservative, given the assumptions and data that go into it. The approach cannot guarantee a correct answer, on large world terms. But it can guarantee the best possible answer, on
small world terms, that could be derived from the information fed into it.

### 2.1.1. Counting possibilities

Take ALL paths/possible ways to reach the result.

### 2.1.2. Combining other information

1. Update information if we already know the previous outcomes. We can use multiplication if all events are independent.

2. The structure of the model and the scientific context always provide information that allows us to do better than ignorance.

### 2.1.3. From counts to probability

1. When we don’t know what caused the data, potential causes that may produce the data in more ways are more plausible.

* A conjectured proportion of blue marbles, p, is usually called a parameter value. It’s just a way of indexing possible explanations of the data.
* The relative number of ways that a value p can produce the data is usually called a likelihood. It is derived by enumerating all the possible data sequences that could have happened and then eliminating those sequences inconsistent with the data.
* The prior plausibility of any specific p is usually called the prior probability. 
* The new, updated plausibility of any specific p is usually called the posterior probability.

## 2.2. Building a model

To get the logic moving, we need to make assumptions, and these assumptions constitute the model. Designing a simple Bayesian model benefits from a design loop with three steps. 
(1) Data story: Motivate the model by narrating how the data might arise. 
(2) Update: Educate your model by feeding it the data.
(3) Evaluate: All statistical models require supervision, leading to model revision.

### 2.2.1. A data story.

Bayesian data analysis usually means producing a story for how the data came to be. This story may be *descriptive*, specifying associations that can be used to predict outcomes, given observations. Or it may be causal, a theory of how some events produce other events. Typically, any story you intend to be causal may also be descriptive. But many descriptive stories are **hard to interpret causally**.

### 2.2.2. Bayesian updating

1. A Bayesian model begins with one set of plausibilities assigned to each of these possibilities. These are the prior plausibilities. Then it updates them in light of the data, to produce the posterior plausibilities. This updating process is a kind of learning, called *Bayesian updating*. 

2. **There’s no free lunch**, when it comes to learning about the world. A Bayesian golem must choose an initial plausibility, and a non-Bayesian golem must choose an estimator. Both golems pay for lunch with their assumptions.

### 2.2.3. Evaluate

Bayesian machine guarantees perfect inference within the small world. No other way of using the available information, beginning with the same state of information, could do better. There are still at least two cautious principles. 

1. First, the model’s certainty is no guarantee that the model is a good one. This is because the inferences are conditional on the model. 

2. Second, it is important to supervise and critique model’s work. When something is irrelevant to the machine, it won’t affect the inference directly. But it may affect it indirectly, because the data will depend upon order. So it is important to check the model’s inferences in light of aspects of the data it does not know about.

My thoughts: I would like to draw our attention to a proportion of *Looking Awry* written by Slavoj Zizek:

> Which is why the detective's artifice lies not simply in his capacity' to grasp the possible meaning of "insignificant details," but perhaps even more in his capacity to apprehend absence itself (the nonoccurrence of some detail) as meaningful—it is perhaps not by chance that the most famous of all Sherlock Holmes's dialogues is the following from "Silver Blaze":
> 
>"Is there any point to which you wish to draw my attention?"
"To the curious incident of the dog in the night."
"The dog did nothing in the night."
"That was the curious incident," remarked Holmes.
> 
> This is how the detective traps the murderer: not simply by perceiving the traces of the deed the murderer failed to efface, but by perceiving **the very absence of a trace as itself a trace**.

3. For now, note that the goal is not to test the truth value of the model’s assumptions. We know the model’s assumptions are never exactly right, in the sense of matching the true data generating process.

4. Failure to conclude that a model is false must be a failure of our imagination, not a success of the model.
    
5. Moreover, models do not need to be exactly true in order to produce highly precise and useful inferences. All manner of small world assumptions about error distributions and the like can be violated in the large world, but a model may still produce a perfectly useful estimate. This is because models are essentially information processing machines, and there are some surprising aspects of information that cannot be easily captured by framing the problem in terms of the truth of assumptions.

6. The objective is to check the model’s adequacy for some purpose. This usually means asking and answering additional questions, beyond those that originally constructed the model, depending upon the scientific context. 

## 2.3 Components of the model

### 2.3.1. Variables

In a scientific context, variables include things we wish to infer, such as proportions and rates, as well as things we might observe, the data.  

### 2.3.2. Definitions

Once we have the variables listed, we then have to define each of them. In defining each, we build a model that relates the variables to one another. 

#### 2.3.2.1. Observed variables

In conventional statistics, a distribution function assigned to an observed variable is usually called a *likelihood*. 

#### 2.3.2.2. Unobserved variables

1. The distributions we assign to the observed variables typically have their own variables. In the binomial above, there is *p*, the probability of sampling water. Since *p* is not observed, we usually call it a parameter. Even though we cannot observe *p*, we still have to define it. In future chapters, there will be more parameters in your models. In statistical modeling, many of the most common questions we ask about data are answered directly by parameters:

* What is the average difference between treatment groups?
* How strong is the association between a treatment and an outcome? 
* Does the effect of the treatment depend upon a covariate?
* How much variation is there among groups?

2. For every parameter you intend your Bayesian machine to consider, you must provide a distribution of prior plausibility, its *prior*. A Bayesian machine must have an initial plausibility assignment for each possible value of the parameter, and these initial assignments do useful work. 

3. There is a school of Bayesian inference that emphasizes choosing priors based upon the personal beliefs of the analyst. While this *subjective Bayesian* approach thrives in some statistics and philosophy and economics programs, it is rare in the sciences.

4. The fact that statistical inference uses mathematics does not imply that there is only one reasonable or useful way to conduct an analysis. Engineering uses math as well, but there are many ways to build a bridge.

5. None of this should be understood to mean that any statistical analysis is not inherently subjective. It’s just that priors and Bayesian data analysis are no more inherently subjective than are likelihoods and the repeat sampling assumptions required for significance testing.

6. If you don’t have a strong argument for any particular prior, then try different ones. Because the prior is an assumption, it should be interrogated like other assumptions: by altering it and checking how sensitive inference is to the assumption.  

### 2.3.3. A model is born

## 2.4 Making the model go

A Bayesian model can update all of the prior distributions to their purely logical consequences: the *posterior distribution.* For every unique combination of data, likelihood, parameters, and prior, there is a unique posterior distribution.

### 2.4.1. Bayes’ theorem 

The mathematical definition of the posterior distribution arises from *Bayes’ theorem*. 

### 2.4.2. Motors

The action of this motor can be thought of as *conditioning* the prior on the data. 

In this book, you’ll meet three different conditioning engines, numerical techniques for computing posterior distributions:
(1) Grid approximation 
(2) Quadratic approximation
(3) Markov chain Monte Carlo (MCMC)

### 2.4.3. Grid approximation

1. While most parameters are *continuous*, capable of taking on an infinite number of values, it turns out that we can achieve an excellent approximation of the continuous posterior distribution by considering only a finite grid of parameter values. 

2. Just multiply the prior probability of p′ by the likelihood at p′. Repeating this procedure for each value in the grid generates an approximate picture of the exact posterior distribution.

3. In most of real modeling, grid approximation isn’t practical. The reason is that it scales very poorly, as the number of parameters increases.

### 2.4.4. Quadratic approximation

1. A useful approach is quadratic approximation. Under quite general conditions, the region near the peak of the posterior distribution will be nearly Gaussian—or “normal”—in shape. This means the posterior distribution can be usefully approximated by a Gaussian distribution. A Gaussian distribution is convenient, because it can be completely described by only two numbers: the location of its center (mean) and its spread (variance).

2. The logarithm of a Gaussian distribution forms a parabola. And a parabola is a quadratic function.

3. Find the posterior mode. Once you find the peak of the posterior, you must estimate the curvature near the peak.

### 2.4.5. Markov chain Monte Carlo

1. Markov chainMonte Carlo (MCMC), which is a family of conditioning engines capable of handling highly complex models.
