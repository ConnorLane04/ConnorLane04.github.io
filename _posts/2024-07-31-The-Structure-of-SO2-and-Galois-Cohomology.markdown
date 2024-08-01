---
layout: post
title:  "The Structure of SO_2 and Galois Cohomology"
date:   2024-07-31 01:58:18 -0400
categories: Galois-Cohomology
---

Let $K$ be a field, we can define the special orthogonal group $\text{SO}_2(K)$ as a matrix group

$$\text{SO}_2(K)=\left\{\begin{pmatrix}a & b \\ -b & a\end{pmatrix}\in \text{GL}_2(K):a^2+b^2=1\right\}.$$

One natural question to ask here is whether there is an alternative description of the group structure of $\text{SO}_2(K)$ under multiplication that are perhaps easier to get a grasp on. This turns out to have an answer but to say it we establish some terminology. We will say that $i\in K$ if the polynomial equation $x^2+1=0$ has a solution in $K$. In general, $i$ will always denote a solution to this polynomial equation. With this in mind, we can state the structure theorem for $\text{SO}_2(K)$.

**Theorem 1:** Let $K$ be a field. Then if $i\in K$, $\text{SO}_2(K)\cong K^\times$, the multiplicative group of $K$. If $i\not \in K$, then $\text{SO}_2(K)\cong K(i)^\times/K^\times$.

The proof of this theorem that I present will look slightly ad-hoc. However, it is all a reflection of Galois cohomology, and in the second half of this blog post I will use the solution to this problem to introduce some basic concepts in Galois cohomology.

*Proof of Theorem 1:* We will handle the case of $i\in K$ and $i\not \in K$ separately, as they are quite different.

**Case 1:** $i\in K$. In this case, we see that the condition $a^2+b^2=1$ factors as $(a+bi)(a-bi)=1$. Inspired by this, we will define a map $\varphi:K^\times\to \text{SO}_2(K)$ by letting $\varphi(x)$ be the solution to the system equations

$$
\begin{cases}
  a+bi=x, \\ a-bi=x^{-1}.
\end{cases}
$$

If we work out the solution to this system of equations, we get the following explicit form of $\varphi$

$$\varphi(x)=\left(\frac{x+x^{-1}}{2} \qquad \frac{x-x^{-1}}{2i}\right)$$

This map also has an inverse, given by $(a,b)\mapsto a+bi$. These are clearly seen to be inverses, so we just have to verify that $\varphi$ is actually a homomorphism. But this can be done by directly: for $x,y\in K^\times$, we have by computation

$$\begin{pmatrix}\frac{x+x^{-1}}{2} & \frac{x-x^{-1}}{2i} \\ -\frac{x-x^{-1}}{2i} & \frac{x+x^{-1}}{2} \end{pmatrix}\begin{pmatrix}\frac{y+y^{-1}}{2} & \frac{y-y^{-1}}{2i} \\ -\frac{y-y^{-1}}{2i} & \frac{y+y^{-1}}{2} \end{pmatrix}=\begin{pmatrix}\frac{xy+(xy)^{-1}}{2} & \frac{xy-(xy)^{-1}}{2i} \\ -\frac{xy-(xy)^{-1}}{2i} & \frac{xy+(xy)^{-1}}{2} \end{pmatrix}.$$

**Case 2:** $i\not \in K$. This case will take a bit more work, but we will also take a slightly more conceptual approach. We make the following observation: define a $2$-dimensional $K$-algebra $A$ by

$$A=\left\{\begin{pmatrix} a & b \\ -b & a\end{pmatrix}:a,b\in K\right\}$$

Note that we have a map $\text{det}:A\to K$, and $\text{SO}_2(K)=\text{Ker}(\text{det}:A^\times\to K^\times)$. Now, $A$ is isomorphic to a different object that might be more familiar: $K(i)$. We have an isomorphism $\varphi:K(i)\to A$ given by

$$a+bi\mapsto \begin{pmatrix}a & b \\ -b & a\end{pmatrix}.$$

This is an example of a general principle: if you have a degree $n$ field extension $L/K$, then for any $K$-basis of $L$ you can construct an embedding $L\hookrightarrow M_{n\times n}(K)$ by sending $\alpha$ to the matrix corresponding to the linear transformation $[\alpha]:L\cong K^n\to K^n$ given by multiplication by $\alpha$.

What does the determinant correspond to under this isomorphism? It turns out to be equal to the norm $N:K(i)\to K$, which is a map that takes $a+bi$ to $a^2+b^2$. This can also be defined by $N(x)=x\bar{x}$, where $\bar{x}=a-bi$ is the Galois conjugate of $x$ over $K$.

All this information can be combined in the following commutative diagram

<div align="center"><iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNCxbMCwwLCJLKGkpIl0sWzAsMSwiSyJdLFsxLDEsIksiXSxbMSwwLCJBIl0sWzAsMywiXFx2YXJwaGkiXSxbMCwxLCJOIiwyXSxbMywyLCJcXHRleHR7ZGV0fSJdLFsxLDIsIlxcdGV4dHtpZH0iXV0=&embed" width="304" height="304" style="border-radius: 8px; border: none;"></iframe></div>

All this tells us that we have an isomorphism $\text{Ker}(N:K(i)^\times\to K^\times)\cong \text{SO}_2(K)$. The upshot of this is that instead of studying matrices, we can just work with in the field $K(i)$. Now that we have this perspective, I want to introduce a group homomorphism that I will call $\delta$. This will map $K(i)^\times$ to $K(i)^\times$, and it is given by the formula

$$\delta(x)=\frac{x}{\bar{x}}.$$

I will leave verifying that $\delta$ is a group homomorphism as an exercise. It turns out that $\delta$ is the key to proving case 2.

**Lemma 1:** Via the first isomorphism theorem, $\delta$ induces an isomorphism from $K(i)^\times/K^\times$ to $\text{Ker}(N:K(i)^\times\to K^\times)$.

*Proof* There are three steps to this proof. First, we need to show that $\text{Ker}(\delta)=K^\times$, second we need to show that $\text{Im}(\delta)\subseteq \text{Ker}(N:K(i)^\times\to K^\times)$, and finally we need to show that $\text{Im}(\delta)\supseteq \text{Ker}(N:K(i)^\times\to K^\times)$.

For step one, we see that by definition $x\in \text{Ker}(\delta)$ if and only if $1=\delta(x)=x/\bar{x}$. But this implies that $x=\bar{x}$, which by the Galois correspondence implies $x\in K$. If you don't know Galois theory, we can also see this by writing $x=a+bi$ for $a,b\in K$, then $a+bi=x=\bar{x}=a-bi$ if and only if $b=0$, or $x\in K$.

Now for step two, we can do this by direct computation, verifying that $N(\delta(x))=1$:

$$N(\delta(x))=N\left(\frac{x}{\bar{x}}\right)=\frac{x}{\bar{x}}\overline{\frac{x}{\bar{x}}}=\frac{x}{\bar{x}}\frac{\bar{x}}{x}=1.$$

Now we have step three, our challenge is as follows: Suppose $y\in K(i)^\times$ such that $N(y)=1$. Can we construct an $x\in K(i)^\times$ such that $y=\delta(x)$? To do this, we will set $x=1+y$, then

$$\delta(x)=\frac{x}{\bar{x}}=\frac{1+y}{1+\bar{y}}=\frac{1+y}{1+y^{-1}}=\frac{1+y}{y^{-1}(y+1)}=y,$$

note that we are explicitly using the fact that $\bar{y}=y^{-1}$, which follows from $y\in \text{Ker}(N)$. There's actually one minor issue here, which is that if $y=-1$, then $x=0\not\in K(i)^\times$. But this is just a single case, so we can verify that $y=\delta(i)$ in this case.

Now we collect the properties that we have proven about $\delta$: it is a group homomorphism from $K(i)^\times$ to itself, with kernel $K^\times$ and image $\text{Ker}(N:K(i)^\times\to K^\times)$. By the first isomorphism theorem, this means that $K(i)^\times/K^\times$ is isomorphic to $\text{Ker}(N:K(i)^\times\to K^\times)$. By since we previously obtained an isomorphism $\varphi$ between $\text{Ker}(N:K(i)^\times$ and $K^\times)\cong \text{SO}_2(K)$. Putting this all together, we get $K(i)^\times/K^\times \cong \text{SO}_2(K)$. $\quad \square$

If you like, we can encode all of this information in an exact sequence

<div align="center"><iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNSxbMSwwLCJLXlxcdGltZXMiXSxbMCwwLCIxIl0sWzIsMCwiSyhpKV5cXHRpbWVzIl0sWzMsMCwiXFx0ZXh0e1NPfV8yKEspIl0sWzQsMCwiMSJdLFsxLDBdLFswLDIsIlxcaW90YSJdLFsyLDMsIlxcdmFycGhpXFxjaXJjXFxkZWx0YSJdLFszLDRdXQ==&embed" width="751" height="176" style="border-radius: 8px; border: none;"></iframe></div>

Here, the map $\iota$ is the inclusion map.

**Exercise:** Try proving case 1 in the style of case 2. Hint[^1]

### Adendum: Galois Cohomology

This section is completely unnecessary to a basic understanding of everything that proceeded it in the post. However, it does put everything done on a more conceptual ground and introduces a very important tool in number theory: Galois cohomology. See, what was actually done in the proof of case 2 was a very special case of a foundational result in Galois cohomology, called Hilbert's theorem 90, that I hope to introduce here. The following will assume familiarity with the Galois correspondence and modules.

Here's the setup: let $L/K$ be a finite Galois extension of fields, and let $G=\text{Gal}(L/K)$ be the Galois group of this extension. The first thing to realize that objects defined in terms of $L$ should be understood as having an action of $G$. This is a very general principle, but all we need here is that $L^\times$ is not just an abelian group, but a module over a (noncommutative) ring called $\mathbb{Z}[G]$.

What is $\mathbb{Z}[G]$? As a set, it is

$$\mathbb{Z}[G]=\left\{\sum_{g\in G}a_g[g]:a_g\in \mathbb{Z}\right\}$$

The $[g]$ are just symbols that satisfy a certain multiplication law, which is that $[g] [h]=[gh]$. The multiplication for all of $\mathbb{Z}[G]$ simply extends linearly.

How is $L^\times$ a $\mathbb{Z}[G]$ module? Well, the Galois group $G$ basically definitionally acts on $L$, so the $\mathbb{Z}[G]$-module structure comes from combining the action of $G$ and the natural $\mathbb{Z}$-module structure of any abelian group. More specifically, if $x\in L$ and a=\sum_{g\in G}a_g[g], Then

$$x^a=\prod_{g\in G}g(x)^{a_g},$$

n.b. that we are writing $L^\times$ multiplicatively, so we write the action of $\mathbb{Z}[G]$ is as an exponential. In general, we call modules over $\mathbb{Z}[G]$ *Galois modules*.

$\mathbb{Z}[G]$ has a certain two-sided ideal $I_G$, called the augmentation ideal. We define a ring homomorphism $\epsilon:\mathbb{Z}[G]\to \mathbb{Z}$ by

$$\epsilon \left(\sum_{g\in G}a_g[g]\right)=\sum_{g\in G}a_g,$$

then we define $I_G=\text{Ker}(\epsilon)$. Next, let $A$ be a multiplicative right $\mathbb{Z}[G]$-module. Define a map $N:A\to A$ by $N(a)=\prod_{g\in G}a^g$. Note that if $A=L^\times$, $N$ recovers the regular norm map of fields. Now we are ready to introduce our first Galois cohomology group. Let $A$ be a right $\mathbb{Z}[G]$-module, define

$$\hat{H}^{-1}(L/K,A)=\text{ker}(N)/(AI_G),$$

this is called the $-1$st Tate cohomology group of $A$ (Exercise: show that this is well defined, i.e. $AI_G\subseteq \text{Ker}(N)$.) I claim that we can restate Lemma 1, in particular the third step of the proof, as $\hat{H}^{-1}(K(i)/K,K(i)^\times)\cong 0$. If $c\in \text{Gal}(K(i)/K)$ is complex conjugation, then one can show that $I_G=(1-c)$ and $\delta$ is exponentiation by $1-c$. Putting these facts together, it turns out that $K(i)^\times I_G=\text{im}(\delta)$. Since Lemma 1 says that $\text{im}(\delta)=\text{Ker}(N)$, we get that $\hat{H}^{-1}(K(i)/K,K(i)^\times)=\text{ker}(N)/(K(i)^\times I_G)\cong 0$. This admits the following generalization:

**Theorem 2:** (Hilbert $90$) Let $L/K$ be a cyclic Galois extension of fields. Then $\hat{H}^{-1}(L/K,L^\times)\cong 0$.

This theorem was proven by Kummer in the $1850$s. (Hilbert's name is only on it because this was the $90$th theorem is his Zahlbericht.) This is not what will often be stated as Hilbert $90$ in many modern texts, instead they will state a generalization by Emmy Noether in the $1930$s, but this generalization is surprisingly unimportant for our story. (That does not, however, mean Noether's version is unimportant. It is in fact very important and is *the* foundational result in Galois cohomology.)

*Proof:* Let $y\in \text{Ker}(N)$ and let $G=\text{Gal}(L/K)=\langle \sigma \rangle\cong \mathbb{Z}/n\mathbb{Z}$. We wish to show that $y\in AI_G$. In this case, we can actually write $I_G$ as the principal ideal $(1-\sigma)$, so this is equivalent to showing that $y=x^{1-\sigma}$ for some $x$. I will introduce a rather unusual function $x(t)$ defined on $L$.

$$x(t)=\sum_{j=0}^{n-1}t^{\sigma^j} y^{1+\sigma +\cdots+\sigma^{j-1}}$$

Now, we want to find a formula for $x(t)^\sigma$.

$$x(t)^\sigma=\sum_{j=0}^{n-1}t^{\sigma^j\sigma} y^{(1+\sigma +\cdots+\sigma^{j-1})\sigma}=\sum_{j=0}^{n-1}t^{\sigma^{j+1}}y^{\sigma+\sigma^2+ \cdots+\sigma^{j}}=y^{-1}\sum_{j=0}^{n-1}t^{\sigma^{j+1}}y^{1+\sigma +\cdots+\sigma^{j}}$$

Now, if we inspect this sum, we notice that it is very similar to $x(t)$. In particular, its $j=0,1,\cdots,{n-2}$ terms correspond to the $j=1,2,\cdots,n-1$ terms of $a(x)$. If we look at the $j=n-1$ term, we get $t^{\sigma^n}y^{1+\sigma+\cdots+\sigma^{n-1}}$. But $\sigma^n=1$, so $x^{\sigma^n}=x$. Furthermore, $a^{1+\sigma+\cdots+\sigma^{n-1}}=N(a)=1$ by assumption, so the $j=n-1$ term of the sum on the right is equal to $y$, which is precisely the $j=0$ term of $x(t)$. The upshot of this is that

$$x(t)=\sum_{j=0}^{n-1}t^{\sigma^{j+1}}y^{1+\sigma +\cdots+\sigma^{j}}$$

so

$$x(t)^\sigma=y^{-1}x(t) \Longrightarrow y=x(t)/x(t)^h.$$

This almost implies that $y\in L^\times I_G$, except theres one technicality: the possibility that $x(t)$ is $0$. However, there is always some value of $t$ such that $x(t)\neq 0$. To show this, note that $x(t)$ is a nonzero linear combination of field automorphisms. But field automorphisms are known to be linearly independent (see for example Marcus Number Fields Ch. 4 Ex. 15.) so we are done. $\qquad \square$

This group, $\hat{H}^{-1}(L/K,A)$ is part of a series of infinite groups, $\hat{H}^i(L/K,A)$ for $i\in \mathbb{Z}$, called the Tate cohomology groups. There's also a similar series of groups $H^i(L/K,A)$, which are the regular Galois cohomology groups. Together, these form extremely refined invariants of a $\mathbb{Z}[G]$-module $A$ that can enable a ton of algebraic number theory and arithmetic geometry. Hopefully, the concrete problem of determining the structure of $\text{SO}_2(K)$ has helped motivate why some of these constructions are interesting. 

[^1]: In case 1, $K(i)$ makes no sense since $i$ is already in $K$. Instead you want to work with $K[x]/(x^2-1)$. What's the structure of this ring?
