# Laboratory 8

## Exercise 1 – Estimating the Total Number of Customers

### Model Description

The goal is to estimate the total number of customers (n) in a store, knowing the number of customers who bought a product (Y).

The model uses:
- A Poisson distribution with mean 10 as the prior for n.
- A Binomial distribution for the observed number of buyers Y.
- Theta represents the probability that a customer buys the product.

I analyzed six combinations:
- Y = 0, theta = 0.2
- Y = 0, theta = 0.5
- Y = 5, theta = 0.2
- Y = 5, theta = 0.5
- Y = 10, theta = 0.2
- Y = 10, theta = 0.5

For each combination, I used PyMC to generate posterior samples with:
- 4 chains
- 2000 draws per chain
- 1000 tuning steps

### Effect of Y

When Y increases from 0 to 5 and then to 10, the posterior distribution of n generally moves towards higher values.

This happens because a larger number of customers buying the product suggests that the total number of customers is also larger.

### Effect of Theta

For the same value of Y, a higher theta leads to a lower estimated total number of customers.

This happens because when the probability of buying the product is higher, fewer total customers are needed to obtain the same number of buyers.

### Conclusion

Both Y and theta influence the posterior distribution of n.

- A higher Y generally leads to a higher estimated number of customers.
- A higher theta generally leads to a lower estimated number of customers when Y stays constant.

The prior distribution, Poisson(10), also influences the final posterior distribution.
