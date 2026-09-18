# Mathematical Statistics — Homework 1

## Point Estimation

---

## Problem 1

Let \(X_1,X_2,\ldots,X_n\) be a random sample from a Bernoulli distribution:

| \(X_i\) | 0 | 1 |
|---|---:|---:|
| Probability | \(1-p\) | \(p\) |

Find the method of moments estimator and the maximum likelihood estimator of \(p\). For the sample

```text
0, 1, 1, 0, 1, 1, 1, 0, 0, 1
```

find the estimate of \(p\).

### Method of Moments

The first theoretical moment is

```math
E[X]=0(1-p)+1\cdot p=p.
```

The first sample moment is

```math
M_1=\bar X=\frac{1}{n}\sum_{i=1}^{n}X_i.
```

Equating the theoretical moment and the sample moment gives

```math
p=\bar X.
```

Therefore,

```math
\boxed{\hat p_{\mathrm{MM}}=\bar X}
```

### Maximum Likelihood Estimation

For one observation,

```math
f(x;p)=p^x(1-p)^{1-x},\qquad x\in\{0,1\}.
```

Hence the likelihood function is

```math
L(p)=\prod_{i=1}^{n}p^{x_i}(1-p)^{1-x_i}.
```

Collecting the powers of \(p\) and \(1-p\),

```math
L(p)=p^{\sum_{i=1}^{n}x_i}(1-p)^{n-\sum_{i=1}^{n}x_i}.
```

Taking logarithms,

```math
\ln L(p)
=
\left(\sum_{i=1}^{n}x_i\right)\ln p
+
\left(n-\sum_{i=1}^{n}x_i\right)\ln(1-p).
```

Differentiating,

```math
\frac{d}{dp}\ln L(p)
=
\frac{\sum_{i=1}^{n}x_i}{p}
-
\frac{n-\sum_{i=1}^{n}x_i}{1-p}.
```

Setting the derivative equal to zero,

```math
\frac{\sum x_i}{p}
-
\frac{n-\sum x_i}{1-p}
=0.
```

Multiplying by \(p(1-p)\),

```math
\left(\sum x_i\right)(1-p)
-
\left(n-\sum x_i\right)p
=0.
```

Therefore,

```math
\sum_{i=1}^{n}x_i-np=0,
```

so

```math
\boxed{
\hat p_{\mathrm{MLE}}
=
\frac{1}{n}\sum_{i=1}^{n}X_i
=
\bar X
}
```

Thus the method of moments estimator and the maximum likelihood estimator are the same:

```math
\boxed{\hat p_{\mathrm{MM}}=\hat p_{\mathrm{MLE}}=\bar X}
```

### Numerical Estimate

For the given sample,

```math
\sum_{i=1}^{10}x_i=6,
\qquad n=10.
```

Hence

```math
\boxed{\hat p=\frac{6}{10}=0.60}
```

---

## Problem 2

Let \(X_1,X_2,\ldots,X_n\) be a random sample from the distribution

| \(X_i\) | 0 | 1 | 3 |
|---|---:|---:|---:|
| Probability | \(1-p_1-p_2\) | \(p_1\) | \(p_2\) |

Find method of moments estimators of \(p_1\) and \(p_2\). For the sample

```text
0, 1, 3, 0, 1, 1, 1, 3, 3, 1
```

find the estimates of \(p_1\) and \(p_2\), and determine whether the estimators are unbiased.

### Step 1: First Theoretical Moment

```math
E[X]
=
0(1-p_1-p_2)+1\cdot p_1+3p_2
=
p_1+3p_2.
```

Thus

```math
\mu_1'=p_1+3p_2.
```

### Step 2: Second Theoretical Moment

```math
E[X^2]
=
0^2(1-p_1-p_2)+1^2p_1+3^2p_2
=
p_1+9p_2.
```

Thus

```math
\mu_2'=p_1+9p_2.
```

The corresponding sample moments are

```math
M_1=\frac{1}{n}\sum_{i=1}^{n}X_i,
```

and

```math
M_2=\frac{1}{n}\sum_{i=1}^{n}X_i^2.
```

Equating theoretical and sample moments,

```math
\begin{cases}
M_1=p_1+3p_2,\\
M_2=p_1+9p_2.
\end{cases}
```

Subtracting the first equation from the second,

```math
M_2-M_1=6p_2,
```

so

```math
\boxed{
\hat p_2
=
\frac{M_2-M_1}{6}
}
```

Substituting back,

```math
\hat p_1=M_1-3\hat p_2,
```

which gives

```math
\boxed{
\hat p_1
=
\frac{3M_1-M_2}{2}
}
```

Therefore,

```math
\boxed{
\hat p_1=\frac{3M_1-M_2}{2},
\qquad
\hat p_2=\frac{M_2-M_1}{6}
}
```

### Numerical Estimates

For the given sample,

```math
\sum_{i=1}^{10}x_i=14,
```

so

```math
M_1=\frac{14}{10}=1.4.
```

Also,

```math
\sum_{i=1}^{10}x_i^2=32,
```

so

```math
M_2=\frac{32}{10}=3.2.
```

Hence

```math
\hat p_1
=
\frac{3(1.4)-3.2}{2}
=
0.50,
```

and

```math
\hat p_2
=
\frac{3.2-1.4}{6}
=
0.30.
```

Thus

```math
\boxed{\hat p_1=0.50,\qquad \hat p_2=0.30}
```

### Unbiasedness

Because

```math
E[M_1]=E[X]=p_1+3p_2
```

and

```math
E[M_2]=E[X^2]=p_1+9p_2,
```

we have

```math
E[\hat p_1]
=
E\left[\frac{3M_1-M_2}{2}\right]
=
\frac{3E[M_1]-E[M_2]}{2}.
```

Therefore,

```math
E[\hat p_1]
=
\frac{3(p_1+3p_2)-(p_1+9p_2)}{2}
=
p_1.
```

Similarly,

```math
E[\hat p_2]
=
E\left[\frac{M_2-M_1}{6}\right]
=
\frac{E[M_2]-E[M_1]}{6},
```

so

```math
E[\hat p_2]
=
\frac{(p_1+9p_2)-(p_1+3p_2)}{6}
=
p_2.
```

Hence both estimators are unbiased:

```math
\boxed{E[\hat p_1]=p_1,\qquad E[\hat p_2]=p_2}
```

---

## Problem 3

Let \(X_1,X_2,\ldots,X_n\) be a random sample from the probability density function

```math
f(x;\theta)
=
\begin{cases}
(\theta+1)x^\theta, & 0<x<1,\\
0, & \text{otherwise},
\end{cases}
\qquad \theta>-1.
```

### (a) Maximum Likelihood Estimator

For observations \(x_1,\ldots,x_n\), the likelihood function is

```math
L(\theta)
=
\prod_{i=1}^{n}(\theta+1)x_i^\theta.
```

Therefore,

```math
L(\theta)
=
(\theta+1)^n
\left(\prod_{i=1}^{n}x_i\right)^\theta.
```

Taking logarithms,

```math
\ln L(\theta)
=
n\ln(\theta+1)
+
\theta\sum_{i=1}^{n}\ln x_i.
```

Differentiating with respect to \(\theta\),

```math
\frac{d}{d\theta}\ln L(\theta)
=
\frac{n}{\theta+1}
+
\sum_{i=1}^{n}\ln x_i.
```

Setting the derivative equal to zero,

```math
\frac{n}{\theta+1}
+
\sum_{i=1}^{n}\ln x_i
=0.
```

Thus

```math
\theta+1
=
-\frac{n}{\sum_{i=1}^{n}\ln x_i},
```

and the maximum likelihood estimator is

```math
\boxed{
\hat\theta_{\mathrm{MLE}}
=
-\frac{n}{\sum_{i=1}^{n}\ln X_i}-1
}
```

### (b) Method of Moments Estimator

The first theoretical moment is

```math
E[X]
=
\int_0^1 x(\theta+1)x^\theta\,dx.
```

Therefore,

```math
E[X]
=
(\theta+1)\int_0^1x^{\theta+1}\,dx
=
\frac{\theta+1}{\theta+2}.
```

Equating this to the first sample moment \(\bar X\),

```math
\bar X
=
\frac{\theta+1}{\theta+2}.
```

Solving for \(\theta\),

```math
\bar X(\theta+2)=\theta+1,
```

so

```math
\theta(1-\bar X)=2\bar X-1.
```

Hence

```math
\boxed{
\hat\theta_{\mathrm{MM}}
=
\frac{2\bar X-1}{1-\bar X}
}
```

### (c) Numerical Estimates

The sample is

```text
0.72, 0.41, 0.88, 0.55, 0.93, 0.67, 0.31, 0.79, 0.58, 0.84
```

Using logarithms rounded to three decimal places,

```math
\begin{aligned}
\ln(0.72)&\approx-0.329,\\
\ln(0.41)&\approx-0.892,\\
\ln(0.88)&\approx-0.128,\\
\ln(0.55)&\approx-0.598,\\
\ln(0.93)&\approx-0.073,\\
\ln(0.67)&\approx-0.400,\\
\ln(0.31)&\approx-1.171,\\
\ln(0.79)&\approx-0.236,\\
\ln(0.58)&\approx-0.545,\\
\ln(0.84)&\approx-0.174.
\end{aligned}
```

Thus

```math
\sum_{i=1}^{10}\ln x_i\approx-4.546.
```

Therefore,

```math
\hat\theta_{\mathrm{MLE}}
=
-\frac{10}{-4.546}-1
\approx1.20.
```

Hence

```math
\boxed{\hat\theta_{\mathrm{MLE}}\approx1.20}
```

For the method of moments,

```math
\bar x
=
\frac{0.72+0.41+0.88+0.55+0.93+0.67+0.31+0.79+0.58+0.84}{10}
=
0.668.
```

Therefore,

```math
\hat\theta_{\mathrm{MM}}
=
\frac{2(0.668)-1}{1-0.668}
\approx1.01.
```

Thus

```math
\boxed{
\hat\theta_{\mathrm{MLE}}\approx1.20,
\qquad
\hat\theta_{\mathrm{MM}}\approx1.01
}
```

---

## Problem 4

Consider a random sample \(X_1,X_2,\ldots,X_n\) from the shifted exponential density

```math
f(x)
=
\begin{cases}
\lambda e^{-\lambda(x-\theta)}, & x\ge\theta,\\
0, & x<\theta,
\end{cases}
```

where \(\lambda>0\).

### (a) Maximum Likelihood Estimators

For the sample \(x_1,\ldots,x_n\), the likelihood is

```math
L(\theta,\lambda)
=
\lambda^n
\exp\left[-\lambda\sum_{i=1}^{n}(x_i-\theta)\right],
```

provided that

```math
\theta\le x_{(1)},
```

where

```math
x_{(1)}=\min(x_1,\ldots,x_n).
```

For fixed \(\lambda\), the likelihood increases as \(\theta\) increases. Therefore the largest admissible value of \(\theta\) is the MLE:

```math
\boxed{\hat\theta_{\mathrm{MLE}}=X_{(1)}}
```

The log-likelihood is

```math
\ln L
=
n\ln\lambda
-
\lambda\sum_{i=1}^{n}(x_i-\theta).
```

Differentiating with respect to \(\lambda\),

```math
\frac{\partial}{\partial\lambda}\ln L
=
\frac{n}{\lambda}
-
\sum_{i=1}^{n}(x_i-\theta).
```

Setting this equal to zero gives

```math
\hat\lambda
=
\frac{n}{\sum_{i=1}^{n}(x_i-\theta)}.
```

Substituting \(\hat\theta_{\mathrm{MLE}}=X_{(1)}\),

```math
\boxed{
\hat\lambda_{\mathrm{MLE}}
=
\frac{1}{\bar X-X_{(1)}}
}
```

Therefore,

```math
\boxed{
\hat\theta_{\mathrm{MLE}}=X_{(1)},
\qquad
\hat\lambda_{\mathrm{MLE}}
=
\frac{1}{\bar X-X_{(1)}}
}
```

### (b) Method of Moments Estimators

For a shifted exponential random variable,

```math
E[X]=\theta+\frac{1}{\lambda}.
```

Also,

```math
\operatorname{Var}(X)=\frac{1}{\lambda^2}.
```

Using raw moments,

```math
E[X^2]-E[X]^2
=
\frac{1}{\lambda^2}.
```

Let

```math
M_1=\bar X,
\qquad
M_2=\frac{1}{n}\sum_{i=1}^{n}X_i^2.
```

Then

```math
M_2-M_1^2
=
\frac{1}{\lambda^2}.
```

Therefore,

```math
\boxed{
\hat\lambda_{\mathrm{MM}}
=
\frac{1}{\sqrt{M_2-M_1^2}}
}
```

Since

```math
M_1
=
\theta+\frac{1}{\lambda},
```

we obtain

```math
\boxed{
\hat\theta_{\mathrm{MM}}
=
M_1-\sqrt{M_2-M_1^2}
}
```

Thus,

```math
\boxed{
\hat\theta_{\mathrm{MM}}
=
\bar X-\sqrt{M_2-\bar X^2},
\qquad
\hat\lambda_{\mathrm{MM}}
=
\frac{1}{\sqrt{M_2-\bar X^2}}
}
```

### (c) Numerical Estimates

The data are

```text
3.1, 0.6, 2.5, 2.2, 5.4, 3.4, 10.3, 8.9, 17.8, 1.3
```

First,

```math
\bar x
=
\frac{55.5}{10}
=
5.55.
```

The smallest observation is

```math
x_{(1)}=0.6.
```

Therefore the maximum likelihood estimates are

```math
\hat\theta_{\mathrm{MLE}}=0.6,
```

and

```math
\hat\lambda_{\mathrm{MLE}}
=
\frac{1}{5.55-0.60}
\approx0.202.
```

Thus

```math
\boxed{
\hat\theta_{\mathrm{MLE}}=0.60,
\qquad
\hat\lambda_{\mathrm{MLE}}\approx0.202
}
```

For the method of moments,

```math
M_2
=
\frac{1}{10}\sum_{i=1}^{10}x_i^2
=
56.561.
```

Hence

```math
M_2-\bar x^2
=
56.561-(5.55)^2
=
25.7585.
```

Therefore,

```math
\sqrt{M_2-\bar x^2}
\approx5.0753.
```

Thus

```math
\hat\lambda_{\mathrm{MM}}
=
\frac{1}{5.0753}
\approx0.197,
```

and

```math
\hat\theta_{\mathrm{MM}}
=
5.55-5.0753
\approx0.475.
```

Therefore,

```math
\boxed{
\hat\theta_{\mathrm{MM}}\approx0.475,
\qquad
\hat\lambda_{\mathrm{MM}}\approx0.197
}
```

### (d) Validity of the Method of Moments Estimate

The parameter must satisfy

```math
\lambda>0
```

and, for the observed sample to lie inside the support,

```math
\theta\le x_{(1)}.
```

Here,

```math
\hat\lambda_{\mathrm{MM}}\approx0.197>0
```

and

```math
\hat\theta_{\mathrm{MM}}\approx0.475<0.60=x_{(1)}.
```

Therefore the method of moments estimate is a valid point in the parameter space:

```math
\boxed{\text{Yes, the method of moments estimate is valid.}}
```
