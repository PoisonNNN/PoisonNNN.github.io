---
title: math
tags: a
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---

A Post with Header Image, See [Page layout](https://tianqi.name/jekyll-TeXt-theme/samples.html#page-layout) for more examples.

<!--more-->

$Q1$ :

由二项式定理可知：$(x+y)^n=\sum\limits_{k=0}^n\binom{n}{k}x^ky^{n-k}$

易知 $x^5y^{13}$ 是 $(x+y)^{18}$ 的第五项

$\therefore$  $x^5y^{13}$ 的系数是 $\binom{18}{5}3^5(-2)^{13}$

$\because 8+9 \neq 18$

$\therefore (x+y)^{18}$ 中不存在 $x^8y^9$

----

$Q2$ ：

$3^n=(1+2)^n$

由二项式定理可知

$3^n=(1+2)^n=\sum\limits_{k=0}^n\binom{n}{k}1^k2^{n-k}=\sum\limits_{k=0}^n\binom{n}{k}1^{n-k}2^k=\sum\limits_{k=0}^n\binom{n}{k}2^k$

推广：对于任意实数 $r$ 求 $\sum\limits_{k=0}^n\binom{n}{k}r^k$

$\sum\limits_{k=0}^n\binom{n}{k}r^k=\sum\limits_{k=0}^n\binom{n}{k}r^k1^{n-k}$

有二项式定理可知

$\sum\limits_{k=0}^n\binom{n}{k}r^k=\sum\limits_{k=0}^n\binom{n}{k}r^k1^{n-k}=(1+r)^n$

---

$Q3$ :

由二项式定理可知

$\sum\limits_{k=0}^n(-1)^k\binom{n}{k}3^{n-k}=(-1+3)^n=2^n$

---

$Q4$ :

由二项式定理可知

$\sum\limits_{k=0}^n(-1)^k\binom{n}{k}10^{k}=\sum\limits_{k=0}^n\binom{n}{k}(-10)^{k}=\sum\limits_{k=0}^n\binom{n}{k}(-10)^{k}1^{n-k}=(-10+1)^n=(-9)^n$

---

$Q5$ :

$\binom{n}{k}$ 即为在 $n$ 个球里面取 $k$ 个的方案数。

$\binom{n-3}{k}$ 即为在 $n$ 个球里面钦定 $3$ 个球都不取，取 $k$ 个的方案数。

左边 $\binom{n}{k}-\binom{n-3}{k}$ 即为在 $n$ 个球中钦定的 $3$ 个球，这 $3$ 个球里至少取一个，取 $k$ 个的方案数。

及钦定的三个球分别为 $a,b,c$ 。

1. 必选 $a$ 球。则方案数为 $\binom{n-1}{k-1}$ 。

2. 必选 $b$ 球。

   这里要考虑到在必选 $a$ 球的情况会存在选了 $b$ 球的情况，所以为了不重复也不能选 $a$ 球。

   所以方案数为 $\binom{n-2}{k-1}$ 。

3. 必选 $c$ 球。

   同理，前两种情况中也会有选到了 $c$ 球的情况，所以为了去重也不能取 $a$ , $b$ 球。

   所以方案数为 $\binom{n-3}{k-1}$ 。

综上所述，总方案数为 $\binom{n-1}{k-1}+\binom{n-2}{k-1}+\binom{n-3}{k-1}$ 。

所以 $\binom{n}{k}-\binom{n-3}{k}=\binom{n-1}{k-1}+\binom{n-2}{k-1}+\binom{n-3}{k-1}$ 。

---

$Q6$ :

1. 当 $n$ 为奇数。

   $\because \binom{n}{k}=\binom{n}{n-k}$

   $\therefore \binom{n}{k}^2=\binom{n}{n-k}^2$


   $\therefore \sum\limits_{k=0}^n(-1)^k\binom{n}{k}^2=(-1)^0\binom{n}{0}^2+(-1)^1\binom{n}{1}^2+...+(-1)^{n-1}\binom{n}{n-1}^2+(-1)^{n}\binom{n}{n}^2$

   $=\binom{n}{0}^2-\binom{n}{1}^2+\binom{n}{2}^2-...+\binom{n}{n-1}^2-\binom{n}{n}^2$ 

   $=\binom{n}{0}^2-\binom{n}{n}^2+\binom{n}{1}^2-\binom{n}{n-1}^2+...+\binom{n}{\lfloor \frac{n}{2} \rfloor}^2-\binom{n}{\lceil \frac{n}{2} \rceil}^2 = 0$

2. 当 $n$ 为偶数。

   
