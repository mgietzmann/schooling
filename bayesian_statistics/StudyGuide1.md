# Study Guide 1

## General Questions that Need Answering

- What is the interpretation of a confidence interval?

If I repeated my experiment many times, I would expect the true parameter to fall within the confidence interval 95% of the time.
- What is the interpretation of a credible interval?

Given the data, there is a 95% probability that the true parameter falls within the credible interval.

- What is the multiple comparisons problem?
- Frequentists just maximize the likelihood. Bayesians find a posterior distribution.

- What is sensitivity (true positive rate) versus specificity (true negative rate)?

- Differences between informative, non-informative, and jeffreys priors.

- posterior, prior, and posterior predictive distributions

- preferences for bayesian or frequentist methods

- what does it mean for marginal distributions to be dependent

## Formulas:

- Bayes' Rule: $P(\theta|y) = \frac{P(y|\theta)P(\theta)}{P(y)}$
- Mean of a distribution: $E(\theta) = \int \theta \pi(\theta) d\theta$
- Variance of a distribution: $Var(\theta) = E(\theta^2) - E(\theta)^2$
- Covariance of two distributions: $Cov(\theta_1, \theta_2) = E(\theta_1\theta_2) - E(\theta_1)E(\theta_2)$
- Correlation of two distributions: $\rho(\theta_1, \theta_2) = \frac{Cov(\theta_1, \theta_2)}{\sqrt{Var(\theta_1)Var(\theta_2)}}$
- Covariance Matrix: $\Sigma = \begin{bmatrix} Var(\theta_1) & Cov(\theta_1, \theta_2) \\ Cov(\theta_1, \theta_2) & Var(\theta_2) \end{bmatrix}$
- Covariance Matrix as an Integral: $\int (\theta - E(\theta))(\theta - E(\theta))^T \pi(\theta) d\theta$



## Distributions

- Gaussian Distribution: $\pi(\lambda)=\text{Gamma}(a, b)=\frac{b^a}{\Gamma(a)}\lambda^{a-1}e^{-b\lambda}$
    - Mean: $E(\lambda)=\frac{a}{b}$
    - Variance: $Var(\lambda)=\frac{a}{b^2}$
    - Mode: $\frac{a-1}{b}$
- Poisson Distribution: $p(y|\lambda)=\frac{e^{-\lambda}\lambda^y}{y!}$
    - Mean: $E(y)=\lambda$
    - Variance: $Var(y)=\lambda$
    - Mode: $\lfloor \lambda \rfloor$
- Binomial Distribution: $p(y|n, \theta)=\binom{n}{y}\theta^y(1-\theta)^{n-y}$
    - Mean: $E(y)=n\theta$
    - Variance: $Var(y)=n\theta(1-\theta)$
    - Mode: $\lfloor (n+1)\theta \rfloor$
- Beta Distribution: $\pi(\theta)=\text{Beta}(\alpha, \beta)=\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}\theta^{\alpha-1}(1-\theta)^{\beta-1}$
    - Mean: $E(\theta)=\frac{\alpha}{\alpha+\beta}$
    - Variance: $Var(\theta)=\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$
    - Mode: $\frac{\alpha-1}{\alpha+\beta-2}$
- Normal Distribution: $\pi(\mu)=\text{Normal}(\mu_0, \tau_0^2)=\frac{1}{\sqrt{2\pi\tau_0^2}}e^{-\frac{(\mu-\mu_0)^2}{2\tau_0^2}}$
    - Mean: $E(\mu)=\mu_0$
    - Variance: $Var(\mu)=\tau_0^2$
    - Mode: $\mu_0$
    - 95% Credible Interval: $\mu_0 \pm 1.96\tau_0$
- Inverse Gamma Distribution: $\pi(\omega)=\text{Inv-Gamma}(\alpha, \beta)=\frac{\beta^\alpha}{\Gamma(\alpha)}\omega^{-\alpha-1}e^{-\frac{\beta}{\omega}}$
    - Mean: $E(\omega)=\frac{\beta}{\alpha-1}$ for $\alpha>1$
    - Variance: $Var(\omega)=\frac{\beta^2}{(\alpha-1)^2(\alpha-2)}$ for $\alpha>2$
    - Mode: $\frac{\beta}{\alpha+1}$ for $\alpha>1$


## Conjugate Priors

- Poisson-Gamma: $\lambda \sim \text{Gamma}(\alpha, \beta)$, $y|\lambda \sim \text{Poisson}(\lambda)$, then $\lambda|y \sim \text{Gamma}(\alpha+\sum_i y_i, \beta+n)$
- Binomial-Beta: $\theta \sim \text{Beta}(\alpha, \beta)$, $y|\theta \sim \text{Binomial}(n, \theta)$, then $\theta|y \sim \text{Beta}(\alpha+y, \beta+n-y)$
- Normal Normal: $y \sim \text{Normal}(\theta, \sigma_0^2), \pi(\theta)=\text{Normal}(\mu_0, \tau_0^2)$, then $\theta|y \sim \text{Normal}(\mu_n, \tau_n^2)$ where $\mu_n=\frac{\frac{\mu_0}{\tau_0^2}+\frac{n \bar{y}}{\sigma_0^2}}{\frac{1}{\tau_0^2}+\frac{n}{\sigma_0^2}}$ and $\tau_n^2=\left(\frac{1}{\tau_0^2}+\frac{n}{\sigma_0^2}\right)^{-1}$
- Normal Inverse Gamma: $y \sim \text{Normal}(\mu, \sigma^2), \sigma^2 \sim \text{InverseGamma}(\alpha, \beta)$ then $\sigma^2|y \sim \text{InverseGamma}\left(\alpha+\frac{n}{2}, \beta+\frac{1}{2}\sum_i(y_i-\mu)^2\right)$



