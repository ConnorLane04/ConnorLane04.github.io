Recall the following elementary proof of a very special case of QR:

Let $p$ be a prime. The group $\mathbb{F}_p^\times$ is cyclic of order $p-1$, so it has an element of order $3$ exactly when $p\equiv 1\bmod 3$. Therefore it contains the primitive third root of unity $\zeta_3=-\frac12-\frac{\sqrt{-3}}{2}$ exactly when $p\equiv 1\bmod 3$. But clearly it contains this element if and only if it contains $\sqrt{-3}$, so $\sqrt{-3}\in \mathbb{F}_p$ if and only if $p\equiv 1\bmod 3$. 

This is a favorite proof of mine. It is totally elementary, super quick, proves a very interesting fact, and still manages to be quite conceptual. There's nothing not to love about it. And it's been on my mind recently, as these sorts of ideas are core to how the [Ross Mathematics Program](https://rossprogram.org/) (where I am a counselor) proves the quadratic reciprocity theorem.

Fundamental to this argument is the consideration of the $3$ torsion of $\mathbb{G}_m$. Of course this is just an extremely fancy way to say $\zeta_3$, but I want to make the point that its about the torsion of a group scheme. From the perspective of class field theory, $\mathbb{G}_m$ gives an explicit CFT over $\mathbb{Q}$. So it makes sense that studying its torsion can lead to proofs of special cases of quadratic reciprocity, since QR is a special case of Artin reciprocity over $\mathbb{Q}$.

From this perspective it is natural to ask whether similar elementary arguments can be done using a CM elliptic curve to prove special cases of Artin reciprocity over $\mathbb{Q}(i)$. I claim the answer is yes, and in this blog post I will explain how to do so.

Our main subject will be the CM elliptic curve $E:y^2=x^3-x$. This has CM by $\mathbb{Z}[i]$, where multiplication by $i$ is given by $(x,y)\mapsto (-x,iy)$. However, we will never actually use this fact explicitly in our proof, as CM theory is far too advanced of machinery to count as an elementary proof. This curve has supersingular reduction at all primes $p\equiv 3\mod 4$, so in particular $a_p=0$ for such primes. This means the structure of $E(\mathbb{Z}[i]/p)=E(\mathbb{F}\_{p^2})$ will be particularly simple at such primes. This will give us a very simple "modular arithmetic criterion" for when $E[n]\subseteq E(\mathbb{F}\_{p^2})$ for varying values of $n$. From here, we will find the coordinates of an order $n$ point, and therefore we'll have a modular arithmetic criterion for when the coordinates of that point lie in $\mathbb{F}_{p^2}$.

With the strategy explained, here's the theorem we'll prove:

**Theorem**: Let $p\equiv 3\bmod 4$ be a prime. Then $p\equiv 4\bmod 5$ if and only if $5-10i$ is a square in $\mathbb{Z}[i]/p$

**Proof**: First, recall that $p$ is prime in $\mathbb{Z}[i]$ if and only if it is $\equiv 3\bmod 4$. This is Fermat's two square theorem and has several elementary proofs.

Next consider the two curves $E_+:y^2=x^3+x$ and $E_-:-y^2=x^3+x$. 

**Lemma 1**: $E_+(\mathbb{F}_p)$ and $E_-(\mathbb{F}_p)$ have $p$ affine points

**Proof of Lemma 1**: Let $P(x)=x^3+ x$. $P$ is an odd function. If $x\neq 0$, then $P(x)\neq 0$ since $i\not \in \mathbb{F}_p$. Furthermore, exactly one of $P(x)$ and $-P(x)=P(-x)$ is a square, so $y^2=P(x)$ and $-y^2=P(x)$ have exactly two solutions in total. Therefore, for every pair $(x,-x)$ of nonzero elements of $\mathbb{F}_p$, $y^2=P_{\pm}(x)$ has exactly $2$ solutions. There are $(p-1)/2$ such pairs, so there are $p-1$ solutions when $x\neq 0$. Adding in the only solution $(0,0)$ that has $x=0$, we get a total of $p$ solutions.$\quad\square$

**Lemma 2**: Let $n$ be an odd integer, $A_{\pm}$ be the $n$-torsion subgroup of $E_\pm(\mathbb{F}_p)$, and $B$ be the $n$-torsion subgroup of $E_+(\mathbb{F}_{p^2})$. Then $B\cong A_+\oplus A_-$.

**Proof of Lemma 2**: Recalling that $\mathbb{F}\_{p^2}=\mathbb{F}\_p[i]$, we write $\alpha=a+bi$, define $c:\mathbb{F}\_p[i]\to \mathbb{F}\_p[i]$ by $c(a+bi)=a-bi$. This is an automorphism of $\mathbb{F}\_p[i]$, and therefore it acts on $B$. Let $B\_{\pm}=\{Q=(x,y)\in B:c(Q)=\pm Q\}$. Then $B_+=A_+$, and we claim that $B_-\cong A_-$. To see this, take $(x,y)\in B_-$. Then since $-(x,y)=(x,-y)$, we see that $x\in \mathbb{F}\_p$ and $y\in i\mathbb{F}\_p$, and the isomorphism $B_-\cong A_-$ is given by $(x,y)\mapsto (x,y/i)$. So it suffices to prove that $B\cong B_+\oplus B_-$.

To prove this isomorphism, define the elements $e_+$ and $e_-$ given by $e_\pm=(1\pm c)/2$. Then we have a homomorphism $Q\mapsto (e_+Q,e_-Q)$ with inverse $(Q_+,Q_-)\mapsto (Q_++Q_-)$. This completes the proof.$\quad \square$

This actually gives us an explicit description of the group structure of $B$ for $n$ odd. Indeed, let $g=\text{gcd}(n,p+1)$. Then we claim that $B=(\mathbb{Z}/g\mathbb{Z})^2$. This is implied if $A_{\pm}\cong \mathbb{Z}/g\mathbb{Z}$. If say $A_+$ is not cyclic, then there is some prime $\ell|g$ such that $A_+[\ell]$ is at least two dimensional. But $A_-[\ell]$ is at least one dimensional, so this implies $B[\ell]$ is at least three dimensional, which is possible since $E[\ell]$ has cardinality $\ell^2$.

All in all, this gives an explicit description of the structure of $E_+(\mathbb{F}_{p^2})$ away from $2$, so we get a correspondence for odd $n$

$$E(\mathbb{F}_{p^2})\text{ has a primitive }n\text{ torsion point} \Longleftrightarrow n|p+1$$

Applying this in the case of $5$-torsion and using sage to compute the field of definition of the relevant points, we see via a few lines of sage code that a certain element of $E[5]$ has coordinates with minimal field of definition $\mathbb{Q}(i,\sqrt{5-10i})$.

```python
K.<i> = NumberField(x^2 + 1)
E= EllipticCurve(K, [1,0])
psi = E.isogenies_prime_degree(5)[0]
f = psi.kernel_polynomial()
f.factor()
```
```
x^2 - 2/5*i + 1/5
```

So therefore we get that $E[5]\subseteq E(\mathbb{F}\_{p^2})$ if and only if $\sqrt{1/5-(2/5)i}\in \mathbb{F}\_{p^2}$. This proves the result. $\quad \square$

----

I am not yet done working on this. I like this proof, but I want to be able to push elementary methods as far as possible. If you give yourself access to the fact that the Frobenius on $E$ is given by the reduction mod $p$ of an element of norm $p$ in $\mathbb{Z}[i]=\text{End}(E)$, then you can show that the behavior of $E(\mathbb{Z}[i]/\pi)$ for a split prime $\pi|p$ is determined by congruences on $\pi$. This can allow you to remove the hypothesis that $p\equiv 3\bmod 4$ from this theorem. But I don't know how to do this in an elementary way yet, so this is all we have. I think this should be possible in an elementary way, though. I just need to figure out how.
