---
layout: post
title:  "A proof of row rank == column rank"
date:   2020-09-26 19:23:33 +0200
---
As I was reading up on linear algebra lately, I was looking for a more intuitive proof of row rank == column rank than the one in Axler's book. This led me to Wardlaw's concise proof [1], which happens to use a matrix factorization.

For this proof, it will be helpful to use the notation that for a matrix $$S$$, $$s_{i, \cdot}$$ represents the ith row and $$s_{\cdot, j}$$ represents jth column.

Consider a $$m \times n$$ matrix $$A$$:
$$
A =
\begin{pmatrix}
a_{1,1} & a_{1,2} & \cdots & a_{1,n} \\
a_{2,1} & a_{2,2} & \cdots & a_{2,n} \\
\vdots  & \vdots  & \ddots & \vdots  \\
a_{m,1} & a_{m,2} & \cdots & a_{m,n}
\end{pmatrix}
$$

with $$\textrm{rank}_\textrm{col} = k$$.

Now consider the $$m \times k$$ matrix $$C$$, whose columns form a basis of the column space of $$A$$. Then each column of $$A$$ can be formed by taking a linear combination the columns of $$C$$, $$c_{\cdot,1},..,c_{\cdot,k}$$. Let $$R$$ be the $$k \times n$$ matrix whose ith column, $$r_{\cdot,i}$$ contains the coefficients of the linear combination to form the ith column of $$A$$. More concisely, $$A=CR$$.

$$
A=\color{magenta}C \color{cyan}R \color{black}=
\begin{pmatrix}
\color{magenta}
c_{1,\cdot} \\
\color{magenta}
c_{2,\cdot} \\
\vdots  \\
\color{magenta}
c_{m,\cdot}
\end{pmatrix}
\color{cyan}R \color{black}
=
\begin{pmatrix}
\color{magenta}
c_{1,\cdot}
\color{cyan}R \\
\color{magenta}
c_{2,\cdot}
\color{cyan}R \\
\vdots  \\
\color{magenta}
c_{m,\cdot}
\color{cyan}R
\end{pmatrix}
=
\begin{pmatrix}
\color{magenta}
c_{1,1}
\color{cyan}
r_{1,\cdot} +
\color{magenta}
c_{2,1}
\color{cyan}
r_{2,\cdot} +
\cdots
+
\color{magenta}
c_{k,1}
\color{cyan}
r_{k,\cdot}
\\
\color{magenta}
c_{1,2}
\color{cyan}
r_{1,\cdot} +
\color{magenta}
c_{2,2}
\color{cyan}
r_{2,\cdot} +
\cdots
+
\color{magenta}
c_{k,2}
\color{cyan}
r_{k,\cdot}
\\
\vdots  \\
\color{magenta}
c_{1,m}
\color{cyan}
r_{1,\cdot} +
\color{magenta}
c_{2,m}
\color{cyan}
r_{2,\cdot} +
\cdots
+
\color{magenta}
c_{k,m}
\color{cyan}
r_{k,\cdot}
\\
\end{pmatrix}
$$.

At this point, it should be clear that the rows of $$A$$ are linear combinations of the $$k$$ rows of $$R$$, which implies that the row space of $$A$$ has dimension at most $$k$$. It follows that $$\textrm{rank}_\textrm{row} \leq \textrm{rank}_\textrm{col}$$. Following the same steps with the transpose of $$A$$ leads to the reverse inequality, thus completing the equality and the proof.


[1] Wardlaw, William P. "Row rank equals column rank." *Mathematics Magazine* 78, no. 5 (2005): 316-318. [DOI](https://doi.org/10.1080/0025570X.2005.11953364) [PDF](https://www.jstor.org/stable/pdf/30044181.pdf)
