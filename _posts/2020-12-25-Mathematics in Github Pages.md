---
layout: post
title: "Mathematics in Github Pages"
date: 2020-12-25 20:02:51 +0800
categories: Github Pages
---

You can use an inline formula $$\forall x \in R$$ like this one

{% highlight ruby %}
$$\forall x \in R$$
{% endhighlight %}

$$
M = \left( \begin{array}{ccc}
x_{11} & x_{12} & \ldots \\
x_{21} & x_{22} & \ldots \\
\vdots & \vdots & \ldots \\
\end{array} \right)
$$

Add this script in your page:

{% highlight ruby %}
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
{% endhighlight %}

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
