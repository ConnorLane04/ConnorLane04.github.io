---
layout: post
title:  "The Structure of SO_2 and Galois Cohomology"
date:   2024-07-31 01:58:18 -0400
categories: Galois-Cohomology
---

The prime number $2$ is famously an exceptional case in many theorems from number theory.

![Paper]({{ site.url }}{{ site.baseurl }}/downloads/2isbad.png)

A while ago, I set out to "understand" why $2$ is such a terrible case, and after over a year of thinking of this problem and seeing its various incarnations, I think I finally have an answer that satisfies me. I believe most instances of $2$ being poorly behaved come down to one of three reasons, which I hope to explain. Interestingly, not all of these reasons have anything to do with $2$ being a small number, which suggests there is more to this than the common reasoning that $2$ is simply too small to behave well.

I hope to explain these reasons in increasing order of complexity. For the first reason, familiarity with elementary number theory and the $p$-adics should suffice. For the second reason, experience with algebraic number theory and arithmetic geometry will be useful. For the third case, I will assume knowledge of Galois cohomology and class field theory.

Consider the following three theorems:

**Theorem A:** Let $G=(\mathbb{Z}/m\mathbb{Z})^\times$ be the multiplicative group of units mod $m$. Then $G$ is cyclic if and only if $m=p^n$ for some prime $p\neq 2$ and $n\geq 0$, or if $m=2,4$. 

**Theorem B:** Let $K=\mathbb{Q}(\sqrt{D})$ for a squarefree integer $D\neq 1$. Then $p$ is ramified in $K/\mathbb{Q}$ if and only if $p\mid D$, or if $p=2$ and $D\not \equiv 1\bmod 4$.

**Theorem C:** Let $K$ be a number field and $\text{scd}_p(K)$ denote the (strict) $p$-cohomological dimension of the absolute Galois group $G_K=\text{Gal}(\bar{K}/K)$. (I.e. For a profinite group $G$, $\text{scd}_p(G)$ is the smallest $n$ such that the $p$-part of $H^i(G,A)$ is trivial for any $i\geq n$ and any $G$-module $A$.) Then $\text{scd}_p(G_K)=2$ unless $p=2$ and $K$ has a real place, in which case $\text{scd}_p(G_K)=\infty$. 

I claim that the poor behavior of $2$ in each of these cases comes down to three different reasons, which I will call reason $A$, reason $B$, and reason $C$.

Before I begin, I would like to give a word of warning: because my focus is on explaining the reason for this poor behavior than the technical details of these theorems, all proofs will only be sketched. 

### Reason A: The structure of $\mathbb{Z}_p^\times$ and the $p$-adic exponential

Let $m$ be a positive integer. The Chinese remainder theorem allows us to decompose $(\mathbb{Z}/m\mathbb{Z})^\times$ into factors from each prime

$$(\mathbb{Z}/m\mathbb{Z})^\times\cong \prod_{p\mid m} (\mathbb{Z}/p^{\nu_p(m)}\mathbb{Z})^\times.$$

Here, $\nu_p$ is the $p$-adic valuation, which takes $m$ to the exponent of $p$ in its prime factorization. Using this idea, we can (this is not completely trivial) reduce the proof of **Theorem A** to just verifying it on prime powers. So, let $p^k$ be a prime power, and we want to see when $(\mathbb{Z}/p^k\mathbb{Z})^\times$ is cyclic. In one elementary solution to this, you end up showing that when $p>2$, $(1+p)$ is an element of exact order $p^{k-1}$. You do this by applying the binomial theorem to $(1+p)^{p^n}$ and then using some results on the divisibility of binomial coefficients.

What goes wrong for $p=2$? Well, in the method I am familiar with, this comes down to the following fact:

$$\nu_p\left(\binom{p}{2}\right)=\begin{cases}1 & p>2 \\ 0 & p=2\end{cases}.$$

I find this explanation unsatisfying because it basically is a computational coincidence. So instead, I will discuss an alternative proof using the $p$-adic exponential.

Let $\mathbb{Z}_p$ be the $p$-adic integers, $\mathbb{Z}_p^\times$ the units of the $p$-adic integers, and $U^1_p\subseteq \mathbb{Z}_p^\times $ the set of $x\in \mathbb{Z}_p$ with $x\equiv 1\bmod p$. (This notation $U^1_p$ is slightly nonstandard, but I want to make the dependence on $p$ very explicit.) There is a very important isomorphism $\mathbb{Z}_p^\times\cong \mu_{p-1}\times U^1_p$, where $\mu_{p-1}\subseteq \mathbb{Z}_p$ is the group of $p-1$st roots of unity. This reduces studying $\mathbb{Z}_p^\times$ to studying $U^1_p$, which we will now attempt to do. The $p$-adic logarithm is a homomorphism $\log_p:(U_1,\times)\to (\mathbb{Z}_p,+)$ given by a power series:

$$\log_p(1+x)=x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots,$$

this converges for all $1+x\in U^1_p$, or equivalently $\| x-1\|_p<1$. The $p$-adic logarithm is an extremely useful tool for studying $U_1$ because it turns out to almost be an isomorphism. Its near-inverse is given by the $p$-adic exponential $\exp_p$ 

$$\exp_p(x)=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots.$$

Now, $\exp_p$ has a pretty terrible radius of convergence. Unlike $\log$ which had radius of convergence $1$, the $p$-adic exponential has radius of convergence $|x|_p<p^{-1/(p-1)}.$ What does this translate to in practice? Well, let $q=p$ if $p>2$ and $q=4$ if $p=2$. It turns out that $\exp_p(x)$ is defined exactly when $x\in q\mathbb{Z}_p$. Since $\exp_p$ and $\log_p$ invert each other *formally*, they define an isomorphism

$$\mathbb{Z}_p\cong q\mathbb{Z}_p=\text{Domain}(\exp_p)\cong \text{Im}(\exp_p)\subseteq U^1_p$$

What exactly is the image of $\exp_p$ then? Well, it turns out that it is exactly $1+q\mathbb{Z}_p$. When $p>2$, we then obtain $\text{Im}(\exp_p)=U^1_p$, but when $p=2$, because $q\neq p$ in this case we get $\text{Im}(\exp_p)\subsetneq U^1_p$. If we then account for this difference, we can obtain the following structure theorem for $U^1_p$

$$(\ast)\qquad \qquad U^1_p\cong \begin{cases}\mathbb{Z}_p & p>2 \\ \mathbb{Z}_p \times (\mathbb{Z}/2\mathbb{Z}) & p=2\end{cases}.$$

You can use this result to find the structure of $\mathbb{Z}_p^\times$ for all $p$, and then reducing mod $p^k$, you can find the structure of $(\mathbb{Z}/p^k\mathbb{Z})^\times$ and prove **Theorem A**.

So, following this proof technique, the "original sin" of $2$ in this case was the fact that we needed to introduce $q$. Specifically, the region of convergence of $\exp_p$ behaved qualitatively different for $p=2$ as it did for $p>2$. If you look at the details of the radius of convergence computation, the key point is that the size of $p$ influences how quickly $\nu_p(n!)$ grows. Because of this, I do believe that this specific type of poor behavior can be explained by "$2$ is small." That being said, I think it is useful to think of the problem here coming from $(*)$. This is because $(\ast)$ alone can explain a lot of times $2$ is weird. One example of this is the lifting the exponent (LTE) lemma:

**Lemma 1 (LTE):** Let $p$ be a prime, $x,y$ integers, and $n>0$ a positive integer. Then $\nu_p(x^n-y^n)=\nu_p(x-y)+\nu_p(n)$, unless $p=2$ and $n$ is even, in which case $\nu_p(x^n-y^n)=\nu_p(x-y)+\nu_p(x+y)+\nu_p(n)-1$.

Like **Theorem A**, LTE can be proven by using $(\ast)$, and once again the two different structures of $U^1_p$ are the sole cause of the two different behaviors. In general, just about any difference between $p=2$ behavior and $p>2$ behavior for theorems about the ring structure of $(\mathbb{Z}/p^k\mathbb{Z})$ can be explained by $(\ast)$.

This problem has more advanced appearances: it is unavoidable in algebraic number theory and it especially shows up in Iwasawa theory. However, I think this slightly more elementary discussion (at least elementary relative to Iwasawa theory) illustrates the point well enough.

### Reason B: The set of bad primes of a problem

After doing enough algebraic number theory and arithmetic geometry, one begins to notice that almost every type of object or question you can ask comes with some finite set of "bad primes," with bad being defined in various ways.

- Given an extension of number fields $L/K$, there is a finite list of primes $\{\mathfrak{p}_i\}$ of $K$ that ramify in $L$.
- Given an elliptic curve $E/\mathbb{Q}$ with reductions $E_p$ mod $p$, there is a finite list of primes $\{p_i\}$ such that $E_{p_i}$ is not an elliptic curve. These are the primes of bad reduction.
- Given a space of modular forms $M_k(\Gamma)$ for a congruence subgroup $\Gamma$, there is a finite set of primes $\{p_i\}$, the primes dividing the level $N$ of $\Gamma$, such that the Hecke operators $U_{p_i}$ need not commute. 

Now, suppose we have a family of problems $X(n)$ for varying $n\in \mathbb{Z}_{>0}$. It turns out that quite often, the set of bad primes of the problem $X(n)$ is precisely the primes dividing $n$. I claim that frequently a theorem $T$ where it looks like $2$ is an exceptional case is the solution to an $X(2)$, and there is some generalization of $T$, $T'(n)$ (so that $T'(2)=T$) that solves $X(n)$. And moreover, $X(n)$ has the property that its set of primes is exactly the set of primes dividing $n$. Therefore, the only reason that $2$ is exceptional in $T$ is because it is the set of bad primes for $X(2)$.

Let me demonstrate this on **Theorem B**. I will define a problem $X(n)$, parametrized by a squarefree number $n$.[^1]

**Problem $X(n)$:** For an $n$th power free $D\in \mathbb{Z}$, when is a prime $p$ of $\mathbb{Q}$ ramified in the extension $\mathbb{Q}(\sqrt[n]{D})/\mathbb{Q}$?

Observe that $X(2)$ is exactly the problem that **Theorem B** solves. This problem admits the following solution, whose proof is omitted. (It is a lot of involved Kummer theory and local arguments.)

**Theorem $B'(n)$:** For $n$th power free $D\in \mathbb{Z}$, $p$ is ramified in $\mathbb{Q}(\sqrt[n]{D})/\mathbb{Q}$ if and only if $p\nmid D$ or if $p\mid n$ and $a\not \equiv 1\bmod p^2$.

This demonstrates the general principle of reason B: we have a generalization of **Theorem B**, which we call **Theorem $B'(n)$**, such that $B=B'(2)$, and such that $p$ is a "bad prime" of $B(n)$ whenever $p|n$. Note that in this case, I am considering a bad prime to be one where the statement involves a congruence condition. This decision is even further justified by the proof of this theorem, where most of the work comes from proving the $p|n$ case.

Another place where this reason comes up a lot is in arithmetic geometry. Specifically, we are often interested in curves of some type $K$ over finite fields $\mathbb{F}_q$. For example, we may consider $K=\text{quadratic forms}$. In this case, $2$ is often such a bad prime to the point where we do not even attempt to state the theorems over $\mathbb{F}_{2^n}$. If we do state them, the theory is often so different that we do not even bother to try and develop it in a unified way. (See for example the theory of orthogonal groups of finite fields.) In these cases, the class of curves $K$ often has $2$ as a bad prime. For example, instead of considering quadratic forms we could consider homogeneous polynomials of degree $n$, and we would find that in these cases, the fields $\mathbb{F}_{p^r}$ for $p|n$ would be the hard ones to handle.

I think this reason is so pervasive because often problems in number theory are so fickle that the general $n$ case is incomparable in difficulty to the $n=2$ case. Because of this, we do not really think about the fact that we are working in a special case when we are doing the $n=2$ case. For example, **Theorem B** can be proven by anyone who knows the definition of the terms involved, while **Theorem $B'(n)$** requires a decent level of fluency in algebraic number theory. For geometric problems, the situation is often even worse. Quadratic forms are almost completely understood number-theoretically, however higher degree polynomials are still a complete mystery to us.

This reason is then also tied into the fact the $2$ is small, but more for a meta reason. That being that we study the small cases of problems before attacking the general case, so we're likely to study the $n=2$ case, and therefore have $2$ in the set of bad primes.

### Reason C: The algebraic closure of $\mathbb{R}$

Let $K$ be a number field with absolute Galois group $G_K$, $S$ the set of all places of $K$, and $S_\infty$ the set of all infinite places. For $\mathfrak{p}\in S$, denote by $K_{\mathfrak{p}}$ the completion of $K$ at $\mathfrak{p}$. By fixing a prime $\mathfrak{P}$ of $\bar{K}$ lying over $\mathfrak{p}$, we can identify the decomposition group $G_{\mathfrak{P}}\subseteq G_K$ with the local Galois group $G_{K_{\mathfrak{p}}}$. The philosophy of Galois cohomology is that we should study $K$ by studying $G_K$, and we know that a decent amount of the structure of $G_K$ is influenced by the structure of the subgroups $G_{K_\mathfrak{p}}$. 

So, what do these subgroups look like? Well for $\mathfrak{p}$ finite they behave very uniformly. We always have $\text{scd}_p(G_{K_{\mathfrak{p}}})=2$ for all primes $p$. This is a really useful result and is deeply related to local class field theory. Now let $\mathfrak{p}\in S_\infty$. Here we have two cases. If $K_\mathfrak{p}=\mathbb{R}$, then $G_{K_{\mathfrak{p}}}=C_2$. If $K_{\mathfrak{p}}=\mathbb{C}$, then $G_{K_{\mathfrak{p}}}=1$. This second case is no problem: we have a bunch of trivial subgroups and they obey $\text{scd}_p(G_{K_{\mathfrak{p}}})=0$. However, if $K_{\mathfrak{p}}=\mathbb{R}$, then we have a major issue: $\text{scd}_2(G_{K_{\mathfrak{p}}})=\infty$.

I claim this is a unique reason that $2$ is poorly behaved: for a real prime $\mathfrak{p}$, the group $G_{\mathfrak{p}}\cong \text{Gal}(\mathbb{C}/\mathbb{R})\cong C_2$ has $\text{scd}_2(C_2)=\infty$. Taking any $G_{K_{\mathfrak{p}}}$ module $A$ with $H^i(G_{\mathfrak{p}},A)\neq 0$, we can use Shapiro's lemma to obtain a $G_K$ module $B=\text{ind}^{G_{\mathfrak{p}}}_{G_K}A$ with $H^i(G_K,B)\cong H^i(G_{\mathfrak{p}},A)\neq 0$.

I will briefly sketch how the proof of **Theorem C** diverges for $p=2$ and $K$ having a real place. The key step in the proof is obtaining $H^3(G_L,\mu_p)=0$ for all extensions of number fields $L/K$. To do this, you consider the Kummer exact sequence

<div align="center"><iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNSxbMCwwLCIwIl0sWzEsMCwiXFxtdV9wIl0sWzIsMCwiXFxiYXJ7S31eXFx0aW1lcyJdLFszLDAsIlxcYmFye0t9XlxcdGltZXMiXSxbNCwwLCIwIl0sWzAsMV0sWzEsMl0sWzIsM10sWzMsNF1d&embed" width="668" height="176" style="border-radius: 8px; border: none;"></iframe></div>

If we take $G_L$ cohomology of this, we obtain

<div align="center"><iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNCxbMCwwLCJIXjIoR19MLFxcYmFye0t9XlxcdGltZXMpIl0sWzEsMCwiSF4yKEdfTCxcXGJhcntLfV5cXHRpbWVzKSJdLFsyLDAsIkheMyhHX0wsXFxtdV9wKSJdLFszLDAsIkheMyhHX0wsXFxiYXJ7S31eXFx0aW1lcykiXSxbMCwxLCJbcF0iXSxbMSwyXSxbMiwzXV0=&embed" width="803" height="147" style="border-radius: 8px; border: none;"></iframe></div>

Now we make heavy use of class field theory, specifically Albert-Brauer-Hasse-Noether. One first obtains $H^3(G_L,\bar{K}^\times)=0$ (which holds independent of the behavior of infinite primes) by considering the exact sequence $0\to \bar{K}^\times \to I\to C$, where $I$ and $C$ are the absolute ideles and absolute idele class group. This then implies that $H^3(G_L,\mu_p)=H^2(G_L,\bar{K}^\times)/pH^2(G_L,\bar{K}^\times)$, so we are done if we can show $H^2(G_L,\bar{K}^\times)$ is $p$-divisible. 

Using ABHN, we can reduce this to the $p$-divisibility of $H^2(G_{L_{\mathfrak{P}}},\bar{K}^\times_{\mathfrak{P}})$ for all primes $\mathfrak{P}$ of $L$. The $p$-divisibility of this group is then related to $p$-cohomological dimension of $G_{L_{\mathfrak{p}}}$: if $\text{scd}_p (G_{L_{\mathfrak{P}}})=2$ then it is $p$-divisible. But if this is not the case, there are no guarantees. If $L$ has real primes (which is only possible if $K$ has real primes,) then you do have local Galois groups with cohomological dimension greater than $2$, and these factors are what prevent you from showing $H^2(G_L,\bar{K}^\times)$ is $p$-divisible.

This specific reason has a couple remarkable properties. First, there is no place where you can point to and say "here, $2$ was too small." That means that simply saying that $2$ is too small does actually miss out on some cases. Secondly, this problem is not really native to places lying over $2$, and is instead a manifestation of a local phenomenon happening at infinity. 

### Ruminations

While I feel like I have a good understanding to the question of "why is $2$ bad," I'm sure there is more out there, so if you find an instance that isn't of one of these three types (or is one of these types in a unique way) please send it my way. 

There's a sense in which reason A is a special case of reason B, but I don't think its complete so I still consider them distinct. Specifically, let $K=\mathbb{Q}(\zeta_p)$ and $\pi=1-\zeta_p$ be the unique prime lying over $p$. Then the local fields $K_{\pi}$ behave remarkably similarly. In particular, their $1$-units all decompose as $\text{im}(\exp_p)\oplus \mu_p$. If you consider this family of local fields, then a lot of the weird behavior for $2$ gets generalized. This is a perspective I find particularly useful in Iwasawa theory, where I often think of $\mathbb{Q}_p(\zeta_p)$ as being like $\mathbb{Q}_2$. 

This analogy is not perfect, however. For example, the cyclotomic $\mathbb{Z}_p$-extension of $\mathbb{Q}_p(\zeta_p)$ is $\mathbb{Q}_p(\zeta_{p^\infty})$ for $p>2$, but for $p=2$ its $\mathbb{Q}_p(\zeta_{p^\infty}+\zeta_{p^\infty}^{-1})$. (This discrepancy is ironically caused by reason $A$, but this time being applied to the Galois groups $\text{Gal}(\mathbb{Q}_p(\zeta_{p^\infty})/\mathbb{Q}_p(\zeta_p))\cong U^1_p$.)

Nonetheless, I hope this topic was interesting to you.

[^1]: The reason I restrict to the squarefree case is because, ironically, reason A starts to affect this theorem for squarefull $n$.
