---
layout: post
title: "Notes about feed forward and back proporgation for neural network"
date: 2021-01-13 18:04:00 +0800
categories: Note
tags: [Matlab, Optimization, Machine Learning, Coursera]
---

Feed forward and back proporgation is widely used to train a neural network model. Specifically, **feed-forward** step passes the input into the model to calculate the value of neurons in each layer. After feed-forward, neuron values reversely give us the 'error' of each neuron and further the gradient of each parameters from far to near layers, which is called *back proporgation*.

![Neural Network Model(from Week5, Machine Learning in Coursera)](/img/2021-01-13-neural network model.png)

[column-row expansion equals the matrix multiplication](https://math.stackexchange.com/questions/1819403/proving-the-column-row-expansion-of-two-matrices-a-and-b-is-equal-to-the-pro)

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
