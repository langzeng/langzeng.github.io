---
layout: post
title: "Probability interpretation of AUC"
date: 2021-12-30 13:08:00 +0800
categories: Note
tags: [Statistics, Other]
---

#### **Probability interpretation of AUC**

AUC stands for "**A**rea **U**nder the ROC **C**urve", where ROC means "**R**eceiver **O**perating **C**haracteristic". AUC measures the overall accuracy of a given classifier. 

![AUC](\img\2021-12-30-AUC.jpg)

The x axis of ROC plot is False Positive Rate (FPR). Specifically, $$FPR = \frac{FP}{FP+TN} = 1-Specificity$$. The y axis of ROC plot is True Positive Rate (TPR), aka sensitivity. By definition, $$TPR= \frac{TP}{TP+FN}$$. Each point on ROC is corresponded to a classification threshold. Given a classifier, exploring all possible classification threshold will generate a ROC.

For simplicity, let's consider a binary classification problem. The class prediction depends on variable $$X$$. Given a threshold $$T$$, the instance will be classified as "positive" if $$X>T$$, and "negative" otherwise. 

![Binary classification](\img\2021-12-30-ROC_curves.png)

Suppose $$X$$ follows a probability density $$f_1(x)$$ if the instance is truly "positive", and $$f_0(x)$$ if otherwise. Then $$TPR(T)=\int_T^\infty f_1(x)\mathrm{d}x$$ and $$FPR(T)=\int_T^\infty f_0(x)\mathrm{d}x$$.

![TPR](\img\2021-12-30-TPR.jpg)

$$
\begin{align*} 
AUC&=\int_0^1TPR(FPR^{-1}(fpr))\mathrm{d}fpr\\
&=\int_\infty^{-\infty}TPR(t)[-f_0(t)\mathrm{d}t]\\
&=\int^\infty_{-\infty}TPR(t)f_0(t)\mathrm{d}t\\
&=\int^\infty_{-\infty}\int_t^\infty f_1(x)\mathrm{d}xf_0(t)\mathrm{d}t\\
&=\int^\infty_{-\infty}\int_\infty^\infty I(x>t)f_1(x)\mathrm{d}xf_0(t)\mathrm{d}t\\
&=P(X_1>X_0),
\end{align*}
$$

where $$X_0$$ has density $$f_0$$ and $$X_1$$ has density $$f_1$$. That is "when using normalized units, the area under the curve (often referred to as simply the AUC) is equal to the probability that a classifier will rank a randomly chosen positive instance higher than a randomly chosen negative one (assuming 'positive' ranks higher than 'negative')".[[Reference](https://www.sciencedirect.com/science/article/pii/S016786550500303X?casa_token=DjoOWOyMz6oAAAAA:pRZWRsR-Qv4AO1Op9ZMCbIpUYtBUgv5Cd-4caeX0ND9ePTT5mH_OFqkLLhENNoeCdeL8mYVD4w)]

[Wikipedia](https://en.m.wikipedia.org/wiki/Receiver_operating_characteristic ) has more details about ROC properties.

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

