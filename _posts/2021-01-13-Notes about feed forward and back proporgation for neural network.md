---
layout: post
title: "Notes about feed forward and back proporgation for neural network"
date: 2021-01-13 18:04:00 +0800
categories: Note
tags: [Matlab, Optimization, Machine Learning, Coursera]
---

Feed forward and back proporgation is widely used to train a neural network model. Specifically, **feed-forward** step passes the input into the model to calculate the value of neurons in each layer. After feed-forward, neuron values reversely give us the 'error' of each neuron and further the gradient of each parameters from far to near layers, which is called **back proporgation**.

Below is a neural network model (img from Week5, Machine Learning in Coursera). 

<img src="/img/2021-01-13-neural network model.png" width="300">
<img src="/img/2021-01-13-Backproporgation.png" width="300">

Weights for layer l $$\mathbb{\theta}^{(l)} \in \mathbb{R}^{s_l\times s_{l+1}}$$. Design matrix $$X \in \mathbb{R}^{m\times n+1}$$ where m is the number of sample and n is the number of features. The first column of $$X$$ is all one. 

1. Feed-forward: calculate all $$(z^{(l)},a^{(l)}), z^{(l+1)}=\mathbf{\theta}^{(l)}a^{(l)}$$ and $$a^{(l+1)}=g(z^{(l+1)})$$ remember to add $$a_0^{l+1}=1$$.
1. $$\delta^{(L)}=a^{(L)}-y$$.
1. $$\delta^{(l)}=(\mathbf{\theta}^{l})^T\delta^{(l+1)}.*g'(z^{(l)})$$.
1. $$\Delta^{(l)}=\Delta^{(l)}+\delta^{(l+1)}(a^{(l)})^T$$. Remember to remove $$\delta_0^{(l+1)})$$.
1. $$\frac{\partial}{\partial \mathbf{\theta}^{l}_{ij}}J(\mathbf{\theta})=\frac{1}{m}\Delta^{(l)}_{ij}$$, while using regulization:
  1. $$\frac{\partial}{\partial \mathbf{\theta}^{l}_{ij}}J(\mathbf{\theta})=\frac{1}{m}\Delta^{(l)}_{ij}$$ for j=0.
  1. $$\frac{\partial}{\partial \mathbf{\theta}^{l}_{ij}}J(\mathbf{\theta})=\frac{1}{m}\Delta^{(l)}_{ij}+\frac{\lambda}{m}\mathbf{\theta}^{l}_{ij}$$ for j>0.

[column-row expansion equals the matrix multiplication](https://math.stackexchange.com/questions/1819403/proving-the-column-row-expansion-of-two-matrices-a-and-b-is-equal-to-the-pro)

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
