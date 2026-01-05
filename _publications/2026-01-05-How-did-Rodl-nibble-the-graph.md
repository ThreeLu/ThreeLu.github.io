---
title: "How did Rodl nibble the graph"
collection: publication
category: manuscripts
permalink: /publication/2026-01-05-How-did-Rodl-nibble-the-graph
excerpt: '这篇文章主要通过Alon书上的例子解释Rodl Nibble方法的实际操作过程。'
date: 2026-01-05
venue: '讨论班讲义资料'
citation: "Noga Alon's Book."
---
> **Theorem 1**    For every integer $r \ge 2$ and $n \ge 2$, $D^{-1} \ll \gamma \ll \varepsilon, k^{-1} \le 1$, every $r$-uniform hypergraph $H = (V,E)$ with $|V| = n$ and $d(v) > 0$ for every $v \in V$, which satisfies the following conditions: 
>
> 1. All but at most $\gamma n$ vertices $x$ has $d(x) = (1 \pm \gamma) D$; 
> 2. $d(x) < kD$, for all $x \in V$; 
> 3. $d(x,y) < \gamma D$, for any two distinct vertices $x,y \in V$. 
>
> contains a cover of all but at most $(1 + \varepsilon)(\frac{n}{r})$ edges. 

We use the following lemma to establish the nibble process. 

> **Lemma 1** (nibblecover)   For every integer $r \ge 2$ and $n \ge 2$, $D^{-1} \ll \delta \ll \delta', \varepsilon, K^{-1} \le 1$, for every $n$-vertex $r$-uniform hypergraph $H = (V,E)$ which satisfies that:
>
> 1. All but at most $\delta n$ vertices $x$ has $d(x) = (1 \pm \delta) D$;
> 2. $d(x) < KD$, for all $x \in V$;
> 3. $d(x,y) < \delta D$, for any two distinct vertices $x,y \in V$.     
>
> contains an edge set $E'$ with the following properties:
>
> (1) $|E'| = (\varepsilon \frac{n}{r}) (1 \pm \delta')$;  
>
> (2) Denote that  $$V' = V - \bigcup_{e \in E'} e.$$ The cardinality 
> $$|V'| = ne^{-\varepsilon}(1\pm \delta').$$
> (3) For all but at most $\delta'|V'|$ vertices in $V'$, 
> $$d_{G[V']}(x) = De^{-\varepsilon(r - 1)}(1 \pm \delta').$$

Lemma 1 shows that, if we begin with an almost regular graph, we can choose some special edges which can cover almost $\varepsilon n$ vertices and make the remaining graph almost regular.  

**Proof (Proof of Theorem 1, Informal Version)**  

Briefly speaking, we want to use Lemma 1 many times to obtain an edge set $E_1, E_2, \cdots, E_t$ from $E'$ of every step. Thus we have a vertex set sequence $V = V_0 \supseteq V_1 \supseteq \cdots \supseteq V_{t - 1} \supseteq V_t$. The remaining vertices are covered trivially (i.e., every vertex is contained into an edge). Therefore, it is sufficient to give an upper bound of $|E_1| + |E_2| + \cdots +|E_t| + |V_t|$.  

The main questions we should consider are as follows:

- Q1) Why is it possible to complete the proof by just one nibble? How can we choose $t$?  
- Q2) The order of the parameter between different results using Lemma 1. 

![fig the-nibble-lemma](_publications/fig_the-nibble-lemma.png)

**Figure 1**: Proof of Theorem 1 

Schematic diagram of the nibble process for Theorem 1, showing the sequence of vertex sets $V_0=V \supseteq V_1 \supseteq V_2 \supseteq \dots \supseteq V_t$. Clearly $|V_0| = |V| = n$. 

By Lemma 1, the parameter hierarchy is $D^{-1} \ll \gamma \ll \delta_1, \varepsilon_1,k_1^{-1} $, and $H$ contains an edge set $E_1$ with $|E_1| = (\varepsilon_1 \frac{n}{r})(1 \pm \delta_1)$ and the remaining vertex set $V_1$ with $|V_1| = ne^{-\varepsilon_1}(1 \pm \delta_1)$. 

Furthermore, consider the remaining hypergraph $H_1 = (V_1, E-E_1)$: for all but at most $\delta_1 |V_1|$ vertices $x$, $d_{H_1}(x) = De^{-\varepsilon_1(r - 1)}(1 \pm \delta_1)$.  To digress for a moment: if we stop now (i.e., cover every vertex in $H_1$ with an edge in $E - E_1$), the number of edges we need is 
$$|E_1| + |V_1| \le \frac{\varepsilon_1 n}{r}(1 + \delta_1) + ne^{-\varepsilon_1}(1 + \delta_1) = \frac{n}{r} \cdot \left( (1 + \delta_1) \cdot \left( \varepsilon_1  + re^{-\varepsilon_1} \right)   \right).$$

Now we check the parameters of Theorem 1. For any given $r,n,k,\varepsilon$, there exist $\gamma$ and $D$ such that we need a cover with at most $(1 + \varepsilon) \frac{n}{r}$ edges. The result above involves $r,n,k, \delta_1, \varepsilon_1$ (with $r,n,k$ matching Theorem 1), and $\delta_1, \varepsilon_1$ must satisfy: $$(1 + \delta_1) \cdot \left( \varepsilon_1  + re^{-\varepsilon_1} \right) = 1 + \varepsilon. \tag{1}$$ 

The reason we cannot complete the proof with only one nibble is that Equation (1) cannot hold when $\varepsilon$ is sufficiently small: the function $f(x) = x + re^{-x} \ge x + 2e^{-x} \ge 1.693 > 1 + \varepsilon$. Thus we need to nibble multiple times (with carefully chosen parameters) to resolve this. The error term $re^{-x}$ will be replaced with $rx$ to fix this issue.    

**Proposition**   If $\delta_1 < \delta_2$ and all but $\le \delta_1n$ vertices $x$ satisfy $d(x) = D(1 \pm \delta_1)$, then all but $\le \delta_2n$ vertices $x$ satisfy $d(x) = D(1 \pm \delta_2)$.  

Resuming our main discussion: we now show how to nibble twice. Recall that applying Lemma 1 with new parameters $\delta_2, k_2, \varepsilon_2$ (and $D_1^{-1} \ll \gamma_1 \ll \delta_2, \varepsilon_2, k_2^{-1}$) implies that every $r$-uniform hypergraph $H = (V,E)$ satisfying: 
1. All but $\le \gamma_1|V|$ vertices $x$ have $d_{H}(x) = D_1 \cdot (1 \pm \gamma_1)$; 
2. $d_{H}(x) < k_2 \cdot D_1$ for all $x \in V$; 
3. $d_{H}(x, y) < \gamma_1 D_1$ for any two distinct $x,y \in V$, 

contains a special edge set $E'$ with parameters $\delta_2$ and $\varepsilon_2$.

 **Claim**   The parameter dependency is: 
$$D^{-1} \ll \gamma \ll \delta_1, \varepsilon_1, k_1^{-1} \ll D_1^{-1} \ll \gamma_1 \ll \delta_2, \varepsilon_2, k_2^{-1}.$$

 **Remark**. Briefly speaking, parameters are chosen from right to left, while the hypergraph nibbling proceeds from left to right. 

**Step 1.** **Parameter Dependency**

Lemma 1 can be interpreted as a function $f(\delta, k,\varepsilon)$ that outputs the conditions required for nibbling with parameters $\delta,k,\varepsilon$.   For any $\delta_2, \varepsilon_2, k_2$, $f(\delta_2, \varepsilon_2, k_2) = \{D_1, \gamma_1\}$ means a $(1 \pm \gamma_1)$-regular hypergraph satisfies the conditions for the second nibble. To construct such a hypergraph, set $\gamma_1 = \delta_1$. For any $\varepsilon_1, k_1$ (no prior constraints on these), $f(\delta_1, \varepsilon_1, k_1) = \{D, \gamma\}$ means a $(1 \pm \gamma)D$-regular hypergraph satisfies the conditions for the first nibble. Thus the parameter hierarchy is: 
$$D^{-1} \ll \gamma \ll \delta_1, \varepsilon_1, k_1^{-1} \ll D_1^{-1} \ll \gamma_1 \ll \delta_2, \varepsilon_2, k_2^{-1}.$$

**Step 2.** **Nibble Order** 

Since $\gamma$ and $D^{-1}$ are sufficiently small, applying Lemma 1 to $H$ yields an edge set $E_1$ and leaves a $(1 \pm \delta_1)De^{-\varepsilon_1(r - 1)}$-regular hypergraph $H_1$. Let $D_1 = De^{-\varepsilon_1(r - 1)}$. We verify the second and third conditions for the second nibble: 

- $d(x) < k_1D < k_2D_1 = k_2De^{-\varepsilon_1(r-1)}$; 
- $d(x,y) < \gamma D < \delta_1 D_1 = \delta_1 De^{-\varepsilon_1(r - 1)}$. 

This imposes two constraints on $\delta_1$ and $k_1$:
$$k_1 < e^{-\varepsilon_1(r - 1)}k_2\quad \text{ and } \quad \gamma < \delta_1 e^{-\varepsilon_1(r - 1)}.$$

There is a minor contradiction with $\gamma$: since $\gamma \ll \delta_1$, we cannot directly bound $\delta_1$ below by $\gamma$. However, we can strengthen $f(\delta, k,\varepsilon)$ to $f'(\delta, k, \varepsilon) = \{D, \min \{\gamma, \delta e^{-\varepsilon(r - 1)}\}\}$ (parameters must be re-chosen accordingly), as the proposition holds for $\gamma$ and all smaller values.    

Thus we obtain a $(1 \pm \delta_1)D_1$-regular hypergraph that satisfies Lemma 1's conditions for the second nibble. We can nibble $E_2$ from $H_1$ and leave a $(1 \pm \delta_2)D_1$-regular hypergraph $H_2$ (we do not need $H_2$ for the proof). Note that $\varepsilon_1$ has no constraints in the nibble process, so we set $\varepsilon_1 = \varepsilon_2 := \varepsilon$.  

For a fixed $t$, we nibble $t$ times to get edge sets $E_1, E_2, \cdots, E_t$. The parameter hierarchy generalizes to:
$$D^{-1}\ll \gamma \ll \delta_1, k_1^{-1} \ll \delta_2, k_2^{-1} \ll \cdots \ll \delta_t, k_t^{-1}; \varepsilon.$$

For the vertex set $V_i$ remaining after the $i$-th nibble: 
$$|V_i| = |V_{i - 1}|e^{-\varepsilon}(1 \pm \delta_i) = |V_0|e^{-i\varepsilon}\prod_{j = 1}^i(1 \pm \delta_j) \quad (1 \le i \le t).$$

The size of the edge set $E_i$ (nibbled in the $i$-th step) is bounded by: 
$$|E_i| = \frac{\varepsilon|V_{i - 1}|}{r}(1 \pm \delta_i) = \frac{\varepsilon n}{r} e^{-(i - 1)\varepsilon} \prod_{j = 1}^i(1 \pm \delta_j)^2 \quad (1 \le i \le t).$$

The detailed proof can be found in Section 4.7 of Noga Alon's book.






