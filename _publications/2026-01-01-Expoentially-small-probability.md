---
title: "Exponentially Small Probabilities"
collection: publication
category: manuscripts
permalink: /publication/2026-01-01-Expoentially-small-probability
excerpt: '这篇短文主要是梳理概率方法的工具。'
date: 2026-01-01
venue: '讨论班讲义资料'
paperurl: 'https://ThreeLu.github.io/files/paper3.pdf'
citation: 'Your Name, You. (2024). &quot;Paper Title Number 3.&quot; <i>GitHub Journal of Bugs</i>. 1(3).'
---

# Exponentially Small Probabilities

---

## Chernoff Bound

### Begin at Markov's Inequality
**A common feature**: With large probability, $X \approx \mathbb{E}X$  
We will estimate $\mathbb{P}(X\ge \mathbb{E}X + t)$ that decrease exponentially as $t \rightarrow \infty$.

> **Theorem (Markov's Inequality)**  
> Let $X \ge 0$ be a random variable, for any $a \ge 0$, we have
> $$
> \mathbb{P}(X \ge a) \le \frac{\mathbb{E}X}{a}.
> $$

### Bernstein's Method (1924)
For any $u \ge 0$, we have
$$
\mathbb{P}(X \ge \mathbb{E}X + t) = \mathbb{P}(e^{uX} \ge e^{u(\mathbb{E}X + t)}) \le \frac{\mathbb{E}e^{uX}}{e^{u(\mathbb{E}X + t)}}.
$$
If we consider $X = X_1 + X_2 + \cdots + X_n$ where $X_i \sim \operatorname{Be}(p_i)$, we have
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le \exp\left\lbrace -u\left( \sum_{i=1}^{n}p_i + t  \right)\right\rbrace \cdot \prod_{i=1}^{n} (1 - p_i + e^u \cdot p_i).
$$
Moreover, if $X \sim \operatorname{Bi}(n,p)$, i.e. $p_i = p (i \in \{1,2,\cdots, n\})$, we have
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le \exp\{-u(np + t)\} \cdot (1 - p + e^u \cdot p)^n.
$$
If $t > (1 - p)n = n - np$, i.e. $np + t > n$, the probability is $0$ as $n \rightarrow \infty$.

### Chernoff Bound
If $t \le (1 - p)n$, choose $u$ such that
$$
e^u = \frac{(1 - p)(np + t)}{( n - np - t)p}.
$$
Therefore, we have the Chernoff Bound (1952).

> **Lemma (Chernoff Bound, initial version)**  
> Let $X \sim \operatorname{Bi}(n,p)$, for any $t \ge 0$, we have 
> $$
> \mathbb{P}(X \ge \mathbb{E}X + t) \le  
> \begin{cases}
>  \left( \frac{np}{np + t} \right)^{np + t} \cdot \left(  \frac{ n - np}{n - np - t}\right)^{n - np - t}, & 0 \le t \le n - np \\
>  0, & t > n - np	
> \end{cases}.
> $$

A large but simpler bound?

### $\varphi(x) = (1 + x) \log x - x$, for $x \ge -1$
Let $\varphi(x) = (1 + x) \log x - x$ (for $x \ge -1$), we have:
- $\varphi(x) \ge 0$ for any $x$; $\varphi(0) = 0$.
- $\varphi'(x) = \log(1 +x)$, thus 
  $$
  \varphi(x) \ge \frac{x^2}{2}, \quad \forall -1 \le x \le 0.
  $$
- Since $\varphi(0) = \varphi'(0) = 0$ and 
  $$
  \varphi''(x) = \frac{1}{1 + x} \ge \frac{1}{(1 + x \slash 3 )^3} = \left( \frac{x^2}{2(1 + x \slash 3)} \right)''. 
  $$ 
  thus
  $$
  \varphi(x) \ge \frac{x^2}{2(1 + x \slash 3)}.
  $$

### A Large But Simpler Bound
Let $\lambda = np$, so we can rewrite 
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le
\left( \frac{\lambda}{\lambda + t} \right)^{\lambda + t} \cdot \left(  \frac{ n - \lambda}{n - \lambda - t}\right)^{n - \lambda - t}, \quad 0 \le t \le n - \lambda
$$
as
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le \exp \left\lbrace -\lambda \varphi\left( \frac{t}{\lambda} \right) - (n - \lambda) \varphi\left( \frac{-t}{n - \lambda} \right) \right\rbrace, \quad 0 \le t \le n - \lambda.
$$
Replacing $X$ by $n - X$ and we obtain also
$$
\mathbb{P}(X \le \mathbb{E}X - t) \le \exp \left\lbrace -\lambda \varphi\left( \frac{-t}{\lambda} \right) - (n - \lambda) \varphi\left( \frac{t}{n - \lambda} \right)   \right\rbrace, \quad 0 \le t \le \lambda.
$$
Thus we have 
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le \exp \left\lbrace -\lambda \varphi\left( \frac{t}{\lambda} \right) \right\rbrace, \quad \mathbb{P}(X \le \mathbb{E}X - t) \le \exp \left\lbrace -\lambda \varphi\left( \frac{-t}{\lambda} \right)   \right\rbrace, \quad t \ge 0.
$$

### Chernoff Bound
Using $\varphi(x) \ge x^2\slash (2(1 + x \slash 3))$, we have 
$$
\exp \left\lbrace -\lambda \varphi\left( \frac{t}{\lambda} \right) \right\rbrace \le \exp \left\lbrace -\frac{t^2}{2(\lambda +t \slash 3) }\right\rbrace, \quad \exp \left\lbrace -\lambda \varphi\left( \frac{-t}{\lambda} \right) \right\rbrace \le \exp \left\lbrace -\frac{t^2}{2\lambda }\right\rbrace.
$$
Therefore, we have the Chernoff Bound.

> **Lemma (Chernoff Bound)**  
> If $X \in \operatorname{Bi}(n,p)$ and $\lambda = np$, we have
> $$
> \begin{aligned}
> 	\mathbb{P}(X \ge \mathbb{E}X + t) &\le \exp \left\lbrace -\frac{t^2}{2(\lambda +t \slash 3) }\right\rbrace, \quad t\ge 0 \\
> 	 \mathbb{P}(X \le \mathbb{E}X - t)  &\le \exp \left\lbrace -\frac{t^2}{2\lambda }\right\rbrace, \quad t \ge 0
> \end{aligned}.
> $$

### The exponents in the Estimates
$$
\mathbb{P}(X \ge \mathbb{E}X + t) \le \exp \left\lbrace -\frac{t^2}{2(\lambda +t \slash 3) }\right\rbrace, \quad t\ge 0.
$$
When $t$ is small (i.e., $t \le \lambda$), the exponent is $\Theta(t^2)$.  

When $t$ is large:  
In particular, let $t = \varepsilon \mathbb{E}X$, we have
$$
\mathbb{P}(X - \mathbb{E}X \ge \varepsilon \mathbb{E}X) \le \exp \left\lbrace -\mathbb{E}X\cdot  \varphi\left( \frac{\varepsilon\mathbb{E}X}{\mathbb{E}X}  \right)  \right\rbrace = \exp \left\lbrace - \varphi(\varepsilon) \right\rbrace \le\exp \left\lbrace -\frac{\varepsilon^2}{3}\mathbb{E}X \right\rbrace. 
$$
since $\varphi(-\varepsilon) > \varphi(\varepsilon) \ge \varepsilon^2 \slash 3$ when $\varepsilon \le 2 \slash 3$. Therefore, we have the Chernoff Bound.

### Chernoff Bound (Final Version)
> **Theorem (Chernoff Bound)**  
> If $X \sim \operatorname{Bi}(n,p)$ and for any $0 < \varepsilon <  3 \slash 2$, we have 
> $$
> \mathbb{P}(|X - \mathbb{E}X| \ge \varepsilon \mathbb{E}X) \le 2\exp \left\lbrace -\frac{\varepsilon^2\mathbb{E}X }{3}\right\rbrace.
> $$ 

For $X \sim \operatorname{Be}(p_i)$ and $X \sim H(n,M,N)$, Chernoff Bound still works.  

Single variable $\rightarrow$ More variables ?

### McDiarmid's Inequality for $n$ Independent Trials
> **Definition ($C$-Lipschitz)**  
> $X$ is called $C$-Lipschitz if $|X(\omega) - X(\omega')| \le C$ whenever $\omega$ and $\omega'$ differ in at most 1-coordinate.

> **Theorem (McDiarmid's Inequality)**  
> Let $X$ be $C$-Lipschitz random variable on a product probability space with $n$ coordinates. Then, for any $t > 0$,
> $$
> \mathbb{P}(|X - \mathbb{E}X| > \gamma \mathbb{E}X) \le 2\exp \left\lbrace -\frac{\gamma^2 \mathbb{E}X^2}{nC^2}  \right\rbrace.
> $$

If $\mathbb{E}X = o(\sqrt{n})$, McDiarmid's inequality doesn't work. **The dependency on $n$!**

### Talagrand's Inequality
> **Theorem (Talagrand's Inequality)**  
> Let $X$ be a non-negative random variable determined by $n$ independent trials, and satisfying the following for some $r, c > 0$.
> 1. $X$ is $C$-Lipschitz.
> 2. For any $s$, and sample $\omega$ with $X(\omega) > s$, there are $\le rs$ indices of $\omega$, so that for all other samples $\omega'$ that agree with $\omega$ on those $\le rs$ indices, $X(\omega') > s$ also.
> 
> Then, for all $t > \sqrt{ \mathbb{E}X }$, if $\mathbb{E}X$ is sufficiently large and $\beta < 1 \slash 8c^2r$, we have:
> $$
> \mathbb{P}(|X - \mathbb{E}X| \ge t) \le 2\exp \left\lbrace -\frac{ \beta t^2 }{\mathbb{E}X}\right\rbrace.
> $$

When $t = \varepsilon \mathbb{E}X$, RHS is $2\exp \{-\beta \varepsilon^2 \mathbb{E}X\}$, not dependent on $n$. **How about dependent trials?**

### Azuma's Inequality
> **Lemma (Azuma's Inequality)**  
> Let $X$ be a random variable determined by not necessarily independent outcomes of $n$ trials, $T_1, T_2, \cdots, T_n$, such that for any $i \in [n]$, and any two possible sequences of outcomes $t_1, \cdots, t_{i-1}, t_i$ and $t_1, \cdots, t_{i-1}, t_i'$, we have 
> $$
> \left| \mathbb{E} \left( X \mid \bigcap_{j = 1}^i T_j = t_j \right) - \mathbb{E} \left( X \mid \bigcap_{j = 1}^{i - 1} T_j = t_j, T_i = t_i' \right)  \right| \le c_i.
> $$
> then 
> $$
> \mathbb{P}(|X - \mathbb{E}X| > t) \le 2\exp \left\lbrace - \frac{t^2}{\sum\limits_{i = 1}^n c_i^2} \right\rbrace. 
> $$
