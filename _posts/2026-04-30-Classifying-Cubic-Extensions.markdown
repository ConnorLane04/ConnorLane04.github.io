---
layout: post
title:  "Classifying Cubic Extensions"
date:   2026-04-30 00:00:00 -0400
categories: Galois-Cohomology
---

Kummer theory doesn't get enough respect. To prove this I will classify all cubic extensions (not necessarily Galois) of an arbitrary field (not necessarily containing $\mu_3$, possibly characteristic $3$). This way I can finally justify reading 800 pages of Galois cohomology.

In terms of prerequisites, a solid understanding of Galois cohomology (say at the level needed for CFT) should suffice. I maybe use one trick that's a little more advanced than that, which is keeping track of how a quotient $G/H$ acts on the cohomology groups $H^i(H,A)$, especially when I change the $G/H$-structure of $A$. But I explicitly point this out when its used. I also use Tate twists.

First, let's recall the classification of quadratic extensions so we can understand why cubic extensions are harder.

---- 

Let $F$ be a field. To classify the quadratic extensions of $F$, we can use either Kummer theory (if $\text{Char}(F)\neq 2$) or Artin-Schreier theory (if $\text{Char}(F)=2$). In the $\text{Char}(F)\neq 2$ case, we have an isomorphism by Kummer theory

$$\text{Hom}(G_F,\mu_2)\simeq F^\times/F^{\times 2}$$

which implies that there is a bijection

$$\text{Quadratic extensions of }F\leftrightarrow\text{order 2 subgroups of }F^\times/F^{\times 2}$$

Similarly, if $\text{Char}(F)=2$, then Artin-Schreier theory gives us the relevant classification. Define $\wp:F\to F$ by $\wp(x)=x^2-x$. Then we have

$$\text{Hom}(G_F,\mathbb F_2)\simeq F/\wp(F)$$

which implies that there is a bijection

$$\text{Quadratic extensions of }F\leftrightarrow\text{order 2 subgroups of }F/\wp(F).$$

Together, these give a classification of quadratic extensions of $F$ for any field $F$.


----

The next integer after $2$ is $3$, so what happens if we try to classify all cubic extensions of $F$? Let's assume for a moment that $\text{Char}(F)\neq 3$, so we will use Kummer theory instead of Artin-Schreier theory. There are two obstacles to generalizing the results for quadratic extensions:
- We can't apply Kummer theory blindly in case $\mu_3\not \subseteq F$
- There are nongalois cubic extensions to worry about.
However, we actually can work around both of these problems and obtain a classification. 

Let's work around the first bullet point first. 

**Lemma 1:** Let $F$ be a field of characteristic $\neq p$, and assume $\mu_p\not \subseteq F$. Then

$$\text{Hom}(G_F,\mathbb Z/p\mathbb Z)\simeq (F(\mu_p)^\times/F(\mu_p)^{\times p}(-1))^{\text{Gal}(F(\mu_p)/F)}$$

where $A(n)$ is the $n$th Tate twist of $A$. 

**Proof:** By the Inflation-Restriction exact sequence, we have

$$0\to H^1(F(\mu_p)/F,\mathbb Z/p\mathbb Z)\to H^1(F,\mathbb Z/p\mathbb Z)\to H^1(F(\mu_p),\mathbb{Z}/p\mathbb{Z})^{\text{Gal}(F(\mu_p)/F)}\to H^2(F(\mu_p)/F,\mathbb Z/p\mathbb Z).$$

Since $[F(\mu_p):F]=p-1$ is coprime to $p=\vert\mathbb{Z}/p\mathbb{Z}\vert$, the first and last groups vanish, and we have 

$$H^1(F,\mathbb Z/p\mathbb Z)\simeq H^1(F(\mu_p),\mathbb{Z}/p\mathbb{Z})^{\text{Gal}(F(\mu_p)/F)}.$$

So we are reduced to computing the RHS of this isomorphism. However, since $\mu_p\subseteq F(\mu_p)$, we can pass Tate twists on exponent $p$ groups in and out of Cohomology, so we have

$$H^1(F(\mu_p),\mathbb{Z}/p\mathbb{Z})^{\text{Gal}(F(\mu_p)/F)}\simeq H^1(F(\mu_p),\mu_p)(-1)^{\text{Gal}(F(\mu_p)/F)}\simeq (F(\mu_p)^\times/F(\mu_p)^{\times p}(-1))^{\text{Gal}(F(\mu_p)/F)}$$

which completes the proof. $\square$

Now we know how to classify the Galois cubic extensions, so the next thing to do is classify the nongalois ones. The best way to do this is to stratify by Galois closure. Specifically, let $L/F$ be a cubic extension that is not Galois. Then the Galois closure $\tilde{L}/F$ is an $S_3$ extension, and has a unique quadratic subextension $\tilde{L}/K/F$. This field $K$ is called the discriminant root field of $L$, and is obtained from $F$ by adjoining the square root of the discriminant of any cubic polynomial whose splitting field is $\tilde{L}$. We will classify the cubic extensions one discriminant root field at a time.

By the Galois correspondence, the extension $\tilde{L}/F$ has not one, but three cubic subextensions. They correspond to the subgroups $\langle (12)\rangle$, $\langle (13)\rangle$, and $\langle (23)\rangle$ of $S_3$. Since these subgroups are conjugate, the fields are the conjugates of $L$ over $F$, and they are therefore all isomorphic. 

In conclusion, for any triple of isomorphic nongalois cubic extensions $L_1,L_2,L_3/F$, they all have an identical Galois closure $\tilde{L}=L_1K=L_2K=L_3K$, and the extension $\tilde{L}/K$ is a cubic Galois extension.

Since our goal is a full classification, we want to understand when a cubic Galois extension of $K$ comes from a cubic nongalois extension of $F$. A cubic extension $M/K$ corresponds to an order $3$ subgroup $H$ of $\text{Hom}(G_K,\mathbb{Z}/3\mathbb{Z})$. 

If $\text{Gal}(K/F)$ acts *trivially* on $H$, then $\text{Gal}(M/F)$ is an extension of $\text{Gal}(K/F)\cong \mathbb{Z}/2\mathbb{Z}$ by $\text{Gal}(M/F)\cong \mathbb{Z}/3\mathbb{Z}$ where $\mathbb{Z}/2\mathbb{Z}$ acts trivially on $\mathbb{Z}/3\mathbb{Z}$, and the only such extension is $\mathbb{Z}/6\mathbb{Z}$. This means the relevant cubic extension of $F$ was already Galois over $F$, so we discard this case. 

If $\text{Gal}(K/F)$ acts *nontrivially* on $H$, then the extension now has to be $S_3$, and we get three nongalois cubic extensions of $F$, which is exactly what we are looking for.

Finally, the last possibility is that $H$ is not $\text{Gal}(K/F)$-stable. In this case, the extension $M/F$ will not be Galois, so it is impossible for $M$ to arise as the Galois closure of a cubic extension of $F$, so we can discard this situation.

Putting all we have done so far together, we get the following result:

**Lemma 2:** Let $F$ be a field and $K$ be a quadratic extension of $F$. Then there is a natural bijection 

$$\text{Triples of conjugate nongalois cubic extensions of }F\text{ with discriminant root field }K \\
\updownarrow \\
\text{order 3 subgroups of }\text{Hom}(G_K,\mathbb{Z}/3\mathbb{Z})\text{ with a well-defined nontrivial Gal}(K/F)\text{ action}.$$

We now have two lemmas, one which handles the issue of Kummer theory without $\mu_3$, and another that handles nongalois extensions. Putting these together, we get a full classification:

**Theorem:** Let $F$ be a field. Suppose first that $\text{Char}(F)=3$ and define $\wp:F\to F$ by $\wp(x)=x^3-x$. Then we have bijections between
- Galois cubic extensions $L/F$ and order $3$ subgroups of $F/\wp(F)$
- Triples of conjugate nongalois extensions $L_1,L_2,L_3/F$ with discriminant root field $K$, and order $3$ subgroups $H\subseteq K/\wp(K)$ such that $\text{Gal}(K/F)$ stabalizes $H$ and acts nontrivially on it.

If instead $\text{Char}(F)\neq 3$ and $\mu_3\subseteq F$, then we have bijections between
- Galois cubic extensions $L/F$ and order $3$ subgroups of $F^\times/F^{\times 3}$
- Triples of conjugate nongalois extensions $L_1,L_2,L_3/F$ with discriminant root field $K$, and order $3$ subgroups $H\subseteq K^\times/K^{\times 3}$ such that $\text{Gal}(K/F)$ stabalizes $H$ and acts nontrivially on it.

Finally, if $\text{Char}(F)\neq 3$ and $\mu_3\not\subseteq F$, then we have bijections between
- Galois cubic extensions $L/F$ and order $3$ subgroups of $(F(\mu_3)^\times/F(\mu_3)^{\times 3}(-1))^{\text{Gal}(F(\mu_3)/F)}$
- Triples of conjugate nongalois extensions $L_1,L_2,L_3/F$ with discriminant root field $F(\mu_3)$ and order $3$ subgroups $H\subseteq F(\mu_3)^\times/F(\mu_3)^{\times 3}$ such that $\text{Gal}(K/F)$ stabalizes $H$ and acts trivially on it.
- Triples of conjugate nongalois extensions $L_1,L_2,L_3/F$ with discriminant root field $K\neq F(\mu_3)$ and order $3$ subgroups $H\subseteq (K(\mu_3)^{\times}/K(\mu_3)^{\times 3}(-1))^{\text{Gal}(F(\mu_3)/F)}$ such that $\text{Gal}(K/F)$ stabalizes $H$ and acts nontrivially on it.

----

### Notes
- I don't think this theorem is useful, I just wanted to flex my Galois theory muscles. 
- This is probably still doable for quartic extensions? I think it will get real annoying though. I don't think its possible for quintic extensions since $S_5$ is not solvable.
- With clever wording you can collapse many of the cases of this classification together. More precisely, you can reword the theorems using the degenerate cases that the discriminant root field of a Galois $L/F$ is $F$, and that $\text{Gal}(F(\mu_3)/F)$ is trivial when $\mu_3\subseteq F$. This turns the theorem in to being about subgroups of $K/\wp(K)$ with nontrivial $\text{Gal}(K/F)$ action, and subgroups of $(K(\mu_3)^\times/K(\mu_3)^{\times 3}(-1))^{\text{Gal(K(\mu_3)/K)}}$ with nontrivial $\text{Gal}(K/F)$-action. 
The reason I did not phrase the theorem like this is because my proof still uses casework. However, this does hint at the existence of a cleaner proof, see the next bullet point.
- If anyone can find a way to reprove this result in terms of the nonabelian cohomology exact sequence
$$0\to H^1(G_F,\mathbb{Z}/3\mathbb{Z})\to H^1(G_F,S_3)\to H^1(G_F,\mathbb{Z}/2\mathbb{Z})\to H^2(G_F,\mathbb{Z}/3\mathbb{Z})$$
I would be intrigued. The main thing I can't work out is how the "with nontrivial $\text{Gal}(K/F)$ action" comes in to play... I think its something to do with the extension $\mathbb{Z}/3\mathbb{Z}\to S_3\to \mathbb{Z}/2\mathbb{Z}$ having nontrivial action of the quotient on the subobject.
