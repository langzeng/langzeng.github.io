---
layout: post
title: "Notes about model evaluation in Machine Learning"
date: 2021-01-15 16:53:00 +0800
categories: Note
tags: [Machine Learning, Coursera, Model evaluation, Debug]
---

Notes below are all coming from Machine Learning course in Coursera.

## Debugging a learning algorithm

While training a model, dataset is usually chopped to training set (to train the weight), cross validation set(or validation set, to tune parameters  e.g. $$\lambda$$, or model selection), test set(to test model performance after parameters being fixed on validation set) with proportion 60%, 20%, 20%. The cost values on the three sets are important for model evaluation and debugging:
$$
\Theta=argmin_{\Theta} (cost(\Theta,Training Set)+\lambda\times penalty(\Theta))
$$
$$
J_{train}(\Theta)=cost(\Theta,Training Set)
$$
$$
J_{cv}(\Theta)=cost(\Theta,Validation Set)
$$
$$
J_{test}(\Theta)=cost(\Theta,Test Set)
$$

### Bias and Variance

Bias (underfit) is the case when $$J_{train}(\Theta)$$ is high and $$J_{train}(\Theta)\approx J_{cv}(\Theta)$$.

Variance (overfit) shows low $$J_{train}(\Theta)$$ and $$J_{train}(\Theta)\gg J_{cv}(\Theta)$$.

![Bias and Variance](\img\2021-01-15-Bias and Variance.png)

### Learning curves

Plot $$J_{train}(\Theta)$$ and $$J_{cv}(\Theta)$$ v.s. training set size to  debug the bias or variance.

![High bias](\img\2021-01-15-High bias.png)

![High Variance](\img\2021-01-15-High variance.png)

![Idea Case](\img\2021-01-15-Ideal case.png)

"In practice, especially for small training sets, when you plot learning curves to debug your algorithms, it is often helpful to average across multiple sets of randomly selected examples to determine the training error and cross validation error. Concretely, to determine the training error and cross validation error for i  examples, you should first randomly select i examples from the training set and i examples from the cross validation set. You will then learn the parameters $$\theta$$ using the randomly chosen training set and evaluate the parameters $$\theta$$ on the randomly chosen training set and cross validation set. The above steps should then be repeated multiple times (say 50) and the averaged error should be used to determine the training error and cross validation error for i examples."

Six options given by Andrew are:

- Get more training examples (fixes high variance)
- Try smaller sets of features (fixes high variance)
- Try getting additional features (fixes high bias)
- Try adding polynomial features ($$x_1^2, x_2^2,x_1x_2$$, etc.) (fixes high bias)
- Try decreasing $$\lambda$$ (fixes high bias)
- Try increasing $$\lambda$$ (fixes high variance)

In short, add more features (compare to #examples) to fix high bias. Drop features (compare to #examples) to fix high variance.

## Error analysis

"It's not who has the best algorithm that wins. It's who has the most data". But getting more training examples should be the last choice since it's quite time-consuming. A useful test is that: given input $$X$$, can a human expert confidently predict y? If so, X contains enough information for y and next step should be adjusting the model (try more complex one?) rather than getting more training examples.

#### Recommended approach:

- Start with a simple algorithm that you can implement quickly. Implement it and test it on your cross-validation data.
- Plot learning curves to decide if more data, more features, etc. are likely to help.
- Error analysis: Manually examine the examples (in cross-validation set) that your algorithm made errors on. See if you spot systematic trend in what type of examples it is making errors on. Adjust the algorithm using your hypothesis and test the performance by numerical evaluation (cost, %error).

We should be careful with the error metrics. Sometimes percentage of error will fail, suppose only 10 patients have cancer out of 1000 patients in total (skewed classes), then a predictor "y=0" will have 1% error but it's unreasonable. So we need other metrics like recall (sensitivity) or precision (true positive rate). F1 score is good metrics given by:
$$
F_1Score=2\frac{PR}{P+R},
$$
which essentially is the harmonic mean of **R**ecall and **P**recision.

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

