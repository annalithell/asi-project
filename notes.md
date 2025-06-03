**This file contains notes taken while reading the original paper. Not an official part of the project submission, only used as a tool when developing the code and writing the report.**

# Notes from the paper
## Abstract
The authors of the paper introduce the development of a new theoretical framework, casting dropout training in deep neural networks (NNs) as approximate Bayesian inference in deep Gaussian processes. Their interpretation of the results presented in the paper suggest that a model's weights can be approximately integrated by dropout.

The paper shows a considerable improvement in predictive log-likelihood and RMSE (Root Mean Square Error - determines how far predictions fall from measured true values using Euclidean distance) compared to other methods when using MNIST dataset for regression and classification tasks.

As a direct result of this theory, it is possible to model uncertainty with dropout NNs using existing deep learning tools as Bayesian models. This allows us to implement bayesian probability in practice without a prohibitive computational cost.

These findings are important, as standard deep learning tools for regression and classification do not capture model uncertainty, a desirable charateristic when classifying new data a model have no previous knowledge about. For example, if a model is trained exclusively on pictures of cats and dogs and is then presented with a picture of an ostrich, we want the model to produce a result stating a low probability of the ostrich being a cat or dog.

## Introduction
Problems with standard deep learning tools for regression and classification: they do not capture model uncertainty.

Classification: Predictive probabilities obtained at the end of the pipeline (the softmax output) are erroneously interpreted as model confidence.

What is softmax function? converts raw output scores (aka logits) into probabilities by taking the exponential of each output and normalizing the value by dividing with the sum of all exponentials. Output values then range between (0,1) - can be interpreted as probability.

Dropout used in NNs can be interpreted as a Bayesian approximation of a well know probabilistic model: the Gaussian Process (GP).

Dropout is usually a way to avoid over-fitting in deep learning.

## Conclusions

This paper...

- introduce a link between Gaussian processes and dropout
- develop tools necessary to represent uncertainty in deep learning
- perform exploratory (= to discover more about something) assessment of uncertainty properties obtained from dropout NNs and convnets on regression and classification tasks
- show that model uncertainty is indispensible (= absolutely necessary) for classification tasks
- show improvement in predictive log likelihood and RMSE compared to existing state of the art methods.
- give a quantitative assessment of model uncertainty in the context of reinforcement learning.

**Dropout as a Bayesian Approximation**

Paper show that...

- Neural network with arbitrary depth and non-linearities with dropout applied before every weight layer = approximation of probabilistic deep Gaussian process
- results can be applied to variants of dropout (like drop-connect, multiplicative Gaussian noise).
- the dropout objective effects and minimize the Kullback-Leibler divergence (= how much a model probability distribution Q is different from a true probability distribution P) between an approximate distribution and the posterior of a deep Gaussian Process
