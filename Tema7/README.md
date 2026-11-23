
# Tema 7 – Bayesian Inference

## Exercise 1 – Population Size Estimation

### Objective

The goal is to estimate the total number of animals in a population using capture-recapture data.

We have:
- Initially captured and marked animals: M = 20
- Animals in the second capture: n = 15
- Marked animals found in the second capture: Y = 4

We use a Hypergeometric likelihood and a Discrete Uniform prior for the population size N, between 20 and 200.

### Results and Interpretation

The posterior distribution gives the estimated total population size.

The obtained results are:
- Posterior mean: 103.74
- Posterior median: 97
- 95% HDI: [45, 181]
- Classical estimate: 75

The posterior mean is higher than the classical estimate. The 95% HDI shows the interval containing the most credible values for the population size.

The estimated probability that the population contains more than 100 animals is:

P(N > 100 | Y = 4) = 0.465

This means that, according to the posterior distribution, the probability that the population is larger than 100 animals is approximately 46.5%.

The posterior predictive distribution estimates the number of marked animals in a new capture of 15 animals. Unlike the posterior distribution of N, it also includes the randomness of a new capture.

### Graphs

- `grafice/ex1_a_posterior_N.png` – Posterior distribution of the population size.
- `grafice/ex1_d_predictive.png` – Posterior predictive distribution for a new capture.

---

## Exercise 2 – Comparison of Two Treatments

### Objective

The goal is to compare the recovery times of two treatments, A and B.

The recovery times are modeled using Exponential distributions.

We use independent Gamma prior distributions for the rate parameters:

λA, λB ~ Gamma(2, 4)

### Results and Interpretation

We estimate the posterior distributions of the rate parameters λA and λB.

The mean recovery times are calculated as:

Mean A = 1 / λA

Mean B = 1 / λB

We use the posterior distributions to compare the mean recovery times of the two treatments.

In point C, we calculate the probability that treatment B has a lower mean recovery time than treatment A.

In point D, we use posterior predictive distributions to compare two new patients, one treated with A and one treated with B.

These probabilities are different because point C compares the mean recovery times of the treatments, while point D compares individual recovery times.

Individual recovery times are random. Therefore, even if treatment B has a lower mean recovery time, a new patient treated with B is not guaranteed to recover faster.

### Graphs

- `grafice/ex2_b_posterior_means.png` – Posterior distributions of the mean recovery times for treatments A and B.

---

## Exercise 3 – Gradual Rate Change

### Objective

The goal is to model the gradual change in the number of daily support requests over 30 days.

We use a Poisson distribution:

Yt | λt ~ Poisson(λt)

The event rate changes over time according to a logistic function:

λt = λ1 + (λ2 - λ1) / (1 + exp(-k(t - τ)))

The model estimates four parameters:
- λ1 – initial event rate.
- λ2 – final event rate.
- τ – approximate time of the transition.
- k – speed of the transition.

### Results and Interpretation

The posterior distributions of τ and k help us understand when the transition occurs and how quickly the event rate changes.

The estimated probability that the final rate is greater than the initial rate is:

P(λ2 > λ1 | Data) = 1.0

This means that all posterior samples indicate a higher final event rate than the initial event rate.

The graph comparing observed data and the estimated event rate shows an increasing trend over the 30 days.

The posterior predictive distribution generates possible values for the number of daily requests. We compare these values with the observed data to evaluate how well the model describes the gradual increase.

Some differences between predicted and observed values are normal because the daily number of requests is random and follows a Poisson distribution.

### Graphs

- `grafice/ex3_b_posterior_tau_k.png` – Posterior distributions of τ and k.
- `grafice/ex3_c_lambda_t.png` – Observed data and estimated event rate.
- `grafice/ex3_d_predictive.png` – Observed data compared with posterior predictive values.

---

## PyMC Sampling Configuration

The following sampling configuration was used:

| Parameter | Exercises 1 and 2 | Exercise 3 |
|---|---:|---:|
| Chains | 4 | 4 |
| Draws per chain | 2000 | 2000 |
| Tuning steps | 1000 | 2000 |

Each chain generates 2000 posterior samples, resulting in 8000 posterior samples in total for each model.

The random seed was set to 42 to make the results reproducible.

---


