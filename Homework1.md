## Problem 1

For a Bernoulli random variable,

$$
P(X=0)=1-p,\qquad P(X=1)=p.
$$

### Method of Moments

The first theoretical moment is

$$
E[X]=0(1-p)+1\cdot p=p.
$$

The first sample moment is

$$
M_1=\bar X=\frac1n\sum_{i=1}^nX_i.
$$

Equating the theoretical and sample moments gives

$$
p=\bar X.
$$

Therefore,

$$
\boxed{\hat p_{MM}=\bar X}.
$$

### Maximum Likelihood Estimation

The likelihood function is

$$
L(p)=\prod_{i=1}^np^{x_i}(1-p)^{1-x_i}
=p^{\sum x_i}(1-p)^{n-\sum x_i}.
$$

Hence,

$$
\ln L(p)
=
\left(\sum x_i\right)\ln p
+
\left(n-\sum x_i\right)\ln(1-p).
$$

Differentiating,

$$
\frac{d}{dp}\ln L(p)
=
\frac{\sum x_i}{p}
-
\frac{n-\sum x_i}{1-p}.
$$

Setting the derivative equal to zero gives

$$
\sum x_i=np,
$$

and therefore

$$
\boxed{\hat p_{MLE}=\frac1n\sum_{i=1}^nX_i=\bar X}.
$$

For the given sample,

$$
0,1,1,0,1,1,1,0,0,1,
$$

we have

$$
\sum x_i=6,\qquad n=10.
$$

Thus,

$$
\boxed{\hat p=\frac6{10}=0.60}.
$$

Therefore,

$$
\boxed{\hat p_{MM}=\hat p_{MLE}=\bar X,\qquad \hat p=0.60}.
$$

---

## Problem 2

The distribution is

$$
P(X=0)=1-p_1-p_2,\qquad
P(X=1)=p_1,\qquad
P(X=3)=p_2.
$$

The first theoretical moment is

$$
E[X]=p_1+3p_2.
$$

The second theoretical moment is

$$
E[X^2]=p_1+9p_2.
$$

Let

$$
M_1=\frac1n\sum_{i=1}^nX_i,
\qquad
M_2=\frac1n\sum_{i=1}^nX_i^2.
$$

The method of moments equations are

$$
p_1+3p_2=M_1,
$$

$$
p_1+9p_2=M_2.
$$

Subtracting the equations gives

$$
6p_2=M_2-M_1,
$$

so

$$
\boxed{
\hat p_{2,MM}
=
\frac{M_2-M_1}{6}
}.
$$

Then

$$
\boxed{
\hat p_{1,MM}
=
\frac{3M_1-M_2}{2}
}.
$$

For the sample

$$
0,1,3,0,1,1,1,3,3,1,
$$

we obtain

$$
M_1=\frac{14}{10}=1.4
$$

and

$$
M_2=\frac{32}{10}=3.2.
$$

Therefore,

$$
\boxed{\hat p_1=0.50},
\qquad
\boxed{\hat p_2=0.30}.
$$

For unbiasedness,

$$
E[M_1]=p_1+3p_2,
\qquad
E[M_2]=p_1+9p_2.
$$

Thus,

$$
E[\hat p_2]
=
\frac{E[M_2]-E[M_1]}6
=
p_2.
$$

Also,

$$
E[\hat p_1]
=
\frac{3E[M_1]-E[M_2]}2
=
p_1.
$$

Therefore,

$$
\boxed{E[\hat p_1]=p_1,\qquad E[\hat p_2]=p_2}.
$$

Both estimators are unbiased.

---

## Problem 3

The pdf is

$$
f(x;\theta)=(\theta+1)x^\theta,
\qquad0<x<1,
$$

where \(\theta>-1\).

### Maximum Likelihood Estimation

The likelihood function is

$$
L(\theta)
=
(\theta+1)^n
\prod_{i=1}^nx_i^\theta.
$$

Therefore,

$$
\ln L(\theta)
=
n\ln(\theta+1)
+
\theta\sum_{i=1}^n\ln x_i.
$$

Differentiating,

$$
\frac{d}{d\theta}\ln L(\theta)
=
\frac{n}{\theta+1}
+
\sum_{i=1}^n\ln x_i.
$$

Setting this equal to zero gives

$$
\boxed{
\hat\theta_{MLE}
=
-\frac{n}{\sum_{i=1}^n\ln X_i}-1
}.
$$

Furthermore,

$$
\frac{d^2}{d\theta^2}\ln L(\theta)
=
-\frac{n}{(\theta+1)^2}<0,
$$

so the critical point is a maximum.

### Method of Moments

The first theoretical moment is

$$
E[X]
=
(\theta+1)
\int_0^1x^{\theta+1}\,dx
=
\frac{\theta+1}{\theta+2}.
$$

Equating this with \(\bar X\),

$$
\bar X=\frac{\theta+1}{\theta+2}.
$$

Solving for \(\theta\),

$$
\boxed{
\hat\theta_{MM}
=
\frac{2\bar X-1}{1-\bar X}
}.
$$

For the given sample,

$$
\bar x=0.668.
$$

Using logarithms rounded to three decimal places,

$$
\sum_{i=1}^{10}\ln x_i\approx-4.546.
$$

Hence,

$$
\hat\theta_{MLE}
=
-\frac{10}{-4.546}-1
\approx1.20.
$$

Also,

$$
\hat\theta_{MM}
=
\frac{2(0.668)-1}{1-0.668}
\approx1.01.
$$

Therefore,

$$
\boxed{\hat\theta_{MLE}=1.20},
\qquad
\boxed{\hat\theta_{MM}=1.01}.
$$

---

## Problem 4

The shifted exponential pdf is

$$
f(x)
=
\begin{cases}
\lambda e^{-\lambda(x-\theta)},&x\geq\theta,\\
0,&x<\theta.
\end{cases}
$$

### Maximum Likelihood Estimation

The likelihood is positive only if

$$
\theta\leq X_{(1)},
$$

where

$$
X_{(1)}=\min(X_1,\ldots,X_n).
$$

For fixed \(\lambda\), the likelihood increases with \(\theta\), so

$$
\boxed{\hat\theta_{MLE}=X_{(1)}}.
$$

The log-likelihood is

$$
\ln L
=
n\ln\lambda
-
\lambda\sum_{i=1}^n(x_i-\theta).
$$

Differentiating with respect to \(\lambda\),

$$
\frac{\partial\ln L}{\partial\lambda}
=
\frac n\lambda
-
\sum_{i=1}^n(x_i-\theta).
$$

Thus,

$$
\boxed{
\hat\lambda_{MLE}
=
\frac{n}{\sum(X_i-X_{(1)})}
=
\frac1{\bar X-X_{(1)}}
}.
$$

For the given sample,

$$
X_{(1)}=0.6,
\qquad
\bar x=5.55.
$$

Therefore,

$$
\boxed{\hat\theta_{MLE}=0.60}
$$

and

$$
\boxed{
\hat\lambda_{MLE}
=
\frac1{5.55-0.60}
=
0.2020
}.
$$

### Method of Moments

For the shifted exponential distribution,

$$
E[X]
=
\theta+\frac1\lambda
$$

and

$$
Var(X)=\frac1{\lambda^2}.
$$

Since

$$
Var(X)=E[X^2]-E[X]^2,
$$

the method of moments gives

$$
M_2-M_1^2=\frac1{\lambda^2}.
$$

Therefore,

$$
\boxed{
\hat\lambda_{MM}
=
\frac1{\sqrt{M_2-M_1^2}}
}
$$

and

$$
\boxed{
\hat\theta_{MM}
=
\bar X-\sqrt{M_2-\bar X^2}
}.
$$

For the sample,

$$
M_1=5.55,
$$

$$
M_2=56.561.
$$

Thus,

$$
M_2-M_1^2
=
25.7585.
$$

Hence,

$$
\hat\lambda_{MM}
=
\frac1{\sqrt{25.7585}}
\approx0.1970
$$

and

$$
\hat\theta_{MM}
=
5.55-\sqrt{25.7585}
\approx0.4747.
$$

Therefore,

$$
\boxed{
\hat\theta_{MM}\approx0.475,
\qquad
\hat\lambda_{MM}\approx0.197
}.
$$

The method of moments estimates are valid because

$$
\hat\lambda_{MM}>0
$$

and

$$
\hat\theta_{MM}=0.4747<0.6=X_{(1)},
$$

so all observed values satisfy \(x_i\geq\hat\theta_{MM}\).
