---
layout: post
title:  "Galois Cohomology and the Artin-Schreier Theorem"
date:   2026-09-10 00:00:00 -0400
categories: Galois-Cohomology
---

Let $F$ be a field. The Artin-Schreier theorem (not to be confused with Artin-Schreier theory, which is related but not the same thing) is basically the following equivalence:

 - $G_F$ is a finite group
 - $G_F\cong \mathbb{Z}/2\mathbb{Z}$

there's more you can prove about the characteristic of $F$ being $0$ and about $F$ being orderable, but this statement contains the majority of the difficulty of the proof of the Artin-Schreier theorem.

This is one of those theorems where I was always a little embarrassed about how little I understood the proof. Its pretty influential and its proof affected subjects I really like (primarily anabelian geometry and Kummer theory). Ignoring the obvious main contributing factor of my laziness, I think part of the reason I didn't care for it is that proofs of it just don't look that interesting. There's a lot of grinding through explicit calculations with elements.

But this summer I was forced to confront my lack of understanding. I suggested it as a topic for a project on Galois theory for Mickey Wong, a rising first-year at Cambridge, at the [Ross Mathematics Program](https://rossprogram.org/). As usual with Mickey, he asked some really good questions to try and understand this proof instead of settling with "it works because we screwed around with elements for long enough and got the result." This led to a series of extremely productive conversations between the two of us about this theorem and some more conceptual approaches to its proof, and I'd like to share some of these ideas here.

The main tool I will use is Galois cohomology, and I have tried to rephrase as much as possible in terms of Galois cohomology. I have not been able to completely remove elements without resorting to overpowered machinery (see the last section), but I do think the perspectives I've given here are the most helpful I've seen. The idea I hope to emphasize is that the groups $\mathbb{Z}/n\mathbb{Z}$ for $n\neq 1,2$ behave cohomologically in a way that is impossible for an absolute Galois group to behave.

## The Characteristic $p$ Case

First assume $F$ is characteristic $p$ and $G_F=\mathbb{Z}/p\mathbb{Z}$. We will prove this is impossible (in fact it is even impossible for $p=2$). To do this, we will use the following fact from Galois cohomology:

**Theorem:** Let $F$ be a field of characteristic $p$. Then $H^i(F,\mathbb{F}_p)=0$ for $i>1$.

*Proof.* This follows from additive Hilbert $90$. We consider the Artin-Schreier exact sequence

$$0 \to \mathbb{F}_p \to \overline{F} \xrightarrow{x^p-x} \overline{F} \to 0.$$

If we apply Galois cohomology to this sequence and look around $H^{i}(F,\mathbb{F}_p)$ in the long exact sequence, we get

$$H^{i-1}(F,\overline{F}) \to H^{i}(F,\mathbb{F}_p) \to H^{i}(F,\overline{F})$$

by additive Hilbert $90$, the groups on the left and right vanish for $i>1$, so by properties of exact sequences the middle group must also vanish. $\square$

Now we go back to assuming that $G_F=\mathbb{Z}/p\mathbb{Z}$. By the cocycle description of group cohomology, its easy to see that $H^1(G_F,\mathbb{F}_p)=\mathbb{F}_p$, but then by cyclicity of $G_F$ and vanishing of the Herbrand quotient for finite modules, we obtain $\mid H^2(G_F,\mathbb{F}_p)\mid=\mid H^1(G_F,\mathbb{F}_p)\mid \neq 0$, a contradiction. $\square$

Its worth noting that the restriction on the behavior of $G_F$ for a characteristic $p$ field $F$ that I just presented is actually very strong. In [NSW] Corollary 6.1.3 and Theorem 6.1.4, it is used to deduce the cohomological dimension bound $\text{cd}_p(G_F)\leq 1$ and that the pro-$p$ completion $G_F(p)$ is a free pro-$p$ group.
## Kummer Theory and the Behavior of $2$

For the case of characteristic not dividing $p$, the approach is based on Kummer theory instead of Artin-Schreier theory (as you should expect.) This means we should be understanding the action of $G_F$ on $\mu_{p^n}$. This means we will need a little more consideration of elements than in the previous case, because that's the only way we can figure out what that Galois action literally is.

As a first observation, we know that $\mu_p\subseteq F$, since otherwise we would have $[F(\mu_p):F]\nmid p$. Next, we'd like to know if $\mu_{p^2}\subseteq F$. This will be our first input from the structure of $\mathbb{Z}/p\mathbb{Z}$. The group $H^1(G_F,\mu_{p^2})$ has to have exponent dividing $p$ because $\mid G_F\mid=p$, and the order of a group kills its cohomology.

This fact is very interesting when you consider the Kummer isomorphism $H^1(F,\mu_{p^2})\cong F^\times/F^{\times p^2}$. Since $\overline{F}/F$ is a Kummer extension, there is an element $x\in F$ without a $p$th root, so this group is certainly nontrivial. Just think of this purely group theoretically: we have an abelian group $A$ such that $A/pA$ is nontrivial but $A/p^2A$ is still $p$-torsion.

This implies that for any $x\in F$, there exists a $y\in F$ with $x^p=y^{p^2}$. Choosing $x$ to not be a $p$th power and taking $p$th roots, we get $x=\zeta_p y^p$, and this would imply that $x^{1/p}=\zeta_{p^2}y$, but that cannot be an element of $F$ by our assumption on $x$. Therefore $\zeta_{p^2}\not \in F$. The fact that $\mu_{p^2}\not \subseteq F$ is the last fact about elements of $F$ that we'll need.

*Remark.* You can do the argument in the above paragraph with pure homological algebra and tor groups, and while it is a good strategy, I excluded it because its not really about Galois cohomology, so it just makes this less accessible. I recommend it as an exercise, though.

Ok, now that we have $\mu_{p^2}\not \subseteq F$, there are two ways to conclude. They both take advantage of [The first cause of $p=2$ strangeness](https://connorlane04.github.io/algebraic-number-theory,/galois-cohomology/2024/12/26/Why-is-2-Poorly-Behaved.html). The first directly considers the cohomology of $\mathbb{Z}/p\mathbb{Z}$ and is "finitary", whereas the second doesn't use any more cohomology but is 
"infinitary".

**Method 1.** Since $\mu_{p^2}\not \in F$, we get an injection $G_F \to \text{Aut}(\mu_{p^2})=(\mathbb{Z}/p^2\mathbb{Z})^\times$. By our previous discussion, we have $H^1(G_F,\mu_{p^2})\neq 0$, so in abstract group-theoretic terms what we have is a subgroup $G=G_F$ of $(\mathbb{Z}/p^2\mathbb{Z})^2$ and the nonvanishing of $H^1(G,\mathbb{Z}/p^2\mathbb{Z})$. But cohomology groups of this group have been computed in complete generality. See this result in [NSW]

> **9.1.4 Lemma** Let $p$ be a prime number, $m\geq 1$ a natural number, and let $G\subseteq (\mathbb{Z}/p^m\mathbb{Z})^\times$ be a subgroup. Let $A$ be the $G$-module which is isomorphic to $\mathbb{Z}/p^m\mathbb{Z}$ as an abelian group and on which $G$ acts in the canonical way. Then
>  $$\hat{H}^i(G,A)=0\quad \text{ for all }i\in \mathbb{Z},$$
> unless $p=2$, $m>1$, and $-1\in G$, in which case 
> $$\hat{H}^i(G,A)\cong \mathbb{Z}/2\mathbb{Z}\quad \text{ for all }i\in \mathbb{Z}.$$
Since the cohomology group is nontrivial for us, this implies $p=2$. $\square$

*Remark.* One interesting thing about this approach is that the lemma we applied, 9.1.4, is primarily used in the proof of the Grunwald-Wang theorem, and the exceptional case that is enabling the Artin-Schreier theorem is *exactly* that problem that causes the special case in the Grunwald-Wang theorem. We recall that the Grunwald-Wang theorem says either
 - If $K$ is a number field and $x\in K$, then $x$ is an $n$th power if it is an $n$th power in $K_{\mathfrak{p}}$ for all primes $\mathfrak{p}$ of $K$ outside a finite set $T$, unless you are in a niche special case involving $2$.
 - (Dualy) If $K$ is a number field, $T$ is a finite set of primes, and you specify abelian extensions $L_{\mathfrak{p}}/K_{\mathfrak{p}}$, then there is a global extension $L/K$ that realizes all of those local extensions, unless you are in a niche special case involving $2$.
For a description of what that special case is, see [NSW] Theorems 9.1.11 and 9.2.8.

**Method 2.** Consider the cyclotomic character, $\chi:G_F \to \text{Aut}\_{\mathbb{Z}}(\mu_{p^\infty})$. We know this homomorphism is nontrivial because $\mu_{p^2}\not \subseteq F$, and since $G_F$ is simple this in fact implies $G_F\subseteq \text{Aut}\_{\mathbb{Z}}(\mu_{p^\infty})$. But that latter group is isomorphic to $\mathbb{Z}_p^\times$, so we have

$$\mathbb{Z}/p\mathbb{Z}\subseteq \mathbb{Z}_p^\times.$$

We then use the structure theorem for $\mathbb{Z}_p^\times$:

$$\mathbb{Z}_p^\times \cong \begin{cases} \mu_{p-1} \times \mathbb{Z}_p & p>2 \\ \mu_2 \times \mathbb{Z}_p & p=2 \end{cases}$$

to deduce that this is possible if and only if $p=2$. $\square$

This argument is definitely more elegant that method 1, but it doesn't show the connection to Grunwald-Wang, so I included both. 
## The Norm Residue Isomorphism Theorem (yes really)

If you have enough Galois cohomology brain damage, then you might notice that there is a cohomological property of $\mathbb{Z}/2\mathbb{Z}$ that is not present for $\mathbb{Z}/p\mathbb{Z}$ for $p>2$, and Galois groups very often have this property.

**Proposition.** Let $G=\mathbb{Z}/p\mathbb{Z}$. Then the cup product pairing $\cup:H^1(G,\mathbb{F}_p)\times H^1(G,\mathbb{F}_p)\to H^2(G,\mathbb{F}_p)$ is nontrivial if and only if $p=2$.

**Proof.** By the vanishing of the Herbrand quotient, all groups in sight are isomorphic to $\mathbb{F}_p$. Also, the cup product is antisymmetric, so we have an antisymmetric pairing $\cup: \mathbb{F}_p \times \mathbb{F}_p \to \mathbb{F}_p$. By antisymmetree, $1\cup 1=-(1 \cup 1)$, so $2(1\cup 1)=0$, implying that $1\cup 1=0$ unless $p=2$. This tells us the pairing is trivial for $p>2$. Proving its nontrivial for $p=2$ is a calculation and omitted. $\square$

But ok, how do we use this? Well, there may be simpler ways to do this, but the only way I can think of is an atomic bomb: the norm residue isomorphism theorem. We'll need to introduce some $K$ theory, which is the reason I've had to use $F$ for a field instead of my beloved $K$.

**Definition.** Let $F$ be a field, the Milnor $K$-theory of $F$ is the graded algebra
$$K^M_\bullet(F)=T(F^\times)/\langle a \otimes (1-a)| a,1-a\in F^\times\rangle$$
where $T(F^\times)$ denotes the tensor algebra of $F$, the graded algebra where the $n$th graded piece is $(F^\times)^{\otimes n}$.

Our interest in this comes from the following extremely deep theorem:

**Theorem** (Voevodsky, 2008). There is an isomorphism of graded algebras
$$H^\bullet (F,\mu_p^{\otimes \bullet})\cong K^M_\bullet(F)/p.$$

This isomorphism is given by Kummer theory in degree $1$ but is much more complicated in all higher degrees.

The upshot, however, is that when $\mu_p\subseteq F$, this is an extremely strong restriction on the structure of $H^\bullet (G_F,\mu_p)\cong H^\bullet (G_F,\mathbb{F_p})$. From the definition of Milnor $K$-theory, we see that $K_*^M$ is generated in degree $1$, and this immediately gives us the contradiction we need: for $p>2$, we cannot have $H^\bullet (\mathbb{Z}/p\mathbb{Z},\mathbb{F}_p)$ be generated in degree $1$ because the lemma implies that the cup product is trivial in degree $1$! $\square$
