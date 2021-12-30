---
layout: post
title: "2021-12-30-Probability interpretation of AUC"
date: 2021-12-30 13:08:00 +0800
categories: Note
tags: [Statistics, Other]
---

#### Probability interpretation of AUC

AUC stands for "**A**rea **U**nder the ROC **C**urve", where ROC means "**R**eceiver **O**perating **C**haracteristic". AUC measures the overall accuracy of a given classifier. 

![High bias](\img\2021-12-30-AUC.jpg)

The x axis of ROC plot is False Positive Rate (FPR). Specifically, $$FPR = \frac{FP}{FP+TN} = 1-Specificity$$. The y axis of ROC plot is True Positive Rate (TPR), aka sensitivity. By definition, $$TPR= \frac{TP}{TP+FN}$$. Each point on ROC is corresponded to a classification threshold. Given a classifier, exploring all possible classification threshold will generate a ROC.

For simplicity, let's consider a binary classification problem. 
$$
F_1Score=2\frac{PR}{P+R},
$$


[Wikipedia](https://en.m.wikipedia.org/wiki/Receiver_operating_characteristic ) has more details about ROC properties.

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

