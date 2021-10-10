# Key Notes from Geocentric models

- [Key Notes from Geocentric models](#key-notes-from-geocentric-models)
  - [4.1 Why normal distributions are normal](#41-why-normal-distributions-are-normal)
  - [4.2 A language for describing models](#42-a-language-for-describing-models)
  - [4.3 Gaussian model of height](#43-gaussian-model-of-height)
  - [4.4 Linear prediction](#44-linear-prediction)
  - [4.5 Curves from lines](#45-curves-from-lines)
Linear regression is the geocentric model of applied statistics.

1. linear regression can usefully describe a very large variety of natural phenomena.
2. linear regression is a descriptive model that corresponds to many different process models. If we read its structure too literally, we’re likely to make mistakes.

## 4.1 Why normal distributions are normal

* Normal by addition
* Normal by multiplication
* Normal by log-multiplication
* By the ontological justification, the world is full ofGaussian distributions, approximately. One consequence of this is that statistical models based on Gaussian distributions cannot reliably identify micro-process. 
* The Gaussian is a member ofa family of fundamental natural distributions known as the *exponential family*. All of the members of this family are important for working science, because they populate our world.
* By the epistemological justification, the Gaussian represents a particular state of ignorance. It is the least surprising and least informative assumption to make. 
* This epistemological justification is premised on information theory and maximum entropy.

## 4.2 A language for describing models

Here’s the approach, in abstract/the general recipe.

(1) First, recognize a set of variables to work with. Observable: data. Unobservable (rates and averages): parameters.
(2) Define each variable in terms of the other variables or in terms of a probability distribution.
(3) The combination of variables and their probability distributions defines a joint generative model.

## 4.3 Gaussian model of height

1. The prior predictive simulation is an essential part becaus priors imply a joint prior distribution of individual heights. By simulating from this distribution, you can see what your choices imply about observable height. This helps **diagnose** bad choices. 
2. Bayes lets us proceed in these cases. But only if we use our scientific knowledge to construct sensible priors. Using scientific knowledge to build priors is not cheating. The important thing is that your prior not be based on the values in the data, but only on what you know about the data before you see it. 
3. The posterior’s peak will lie at the maximum a posteriori estimate (MAP), and we can get a useful image of the posterior’s shape by using
the quadratic approximation of the posterior distribution at this peak.
4. A variance-covariance matrix can be factored into two elements: (1) a vector of variances for the parameters and (2) a correlation matrix that tells us how changes in any parameter lead to correlated changes in the others. 

## 4.4 Linear prediction

1. The linear model strategy instructs the golem to assume that the predictor variable has a constant and additive relationship to the mean of the outcome. 
2. Plotting the implications of your models will allow you to inquire about things that are hard to read from tables:
(1) Whether or not the model fitting procedure worked correctly 
(2) The absolute magnitude, rather than merely relative magnitude, of a relationship between outcome and predictor
(3) The uncertainty surrounding an average relationship 
(4) The uncertainty surrounding the implied predictions of the model, as these are distinct from mere parameter uncertainty

## 4.5 Curves from lines

1. *Polynomial regression* uses powers of a variable—squares and cubes—as extra predictors. This is an easy way to build curved associations.
2. The first thing to do is to standardize the predictor variable.
3. The second way to introduce a curve is to construct something known as a spline.
4. B-splines build up wiggly functions from simpler less-wiggly components. Those components are called basis functions. 
5. They invent a series of entirely new, synthetic predictor variables. Each of these synthetic variables exists only to gradually turn a specific parameter on and off within a specific range of the real predictor variable. Each of the synthetic variables is called a basis function.
6. The splines in the previous section are just the beginning. A entire class of models, generalized additive models (GAMs), focuses on predicting an outcome variable using smooth functions of some predictor variables.

