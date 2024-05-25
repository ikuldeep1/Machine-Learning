# Kolmogorov-Smirnov Test

The Kolmogorov-Smirnov (K-S) test is a nonparametric test used to compare a sample distribution with a reference probability distribution (one-sample K-S test) or to compare two sample distributions (two-sample K-S test). It measures the maximum distance between the empirical distribution function of the sample and the cumulative distribution function of the reference distribution, or between the empirical distribution functions of two samples.

## Numerical Example

Let's consider a one-sample K-S test to see if a given sample comes from a standard normal distribution (mean = 0, standard deviation = 1).

### Sample Data
Suppose we have the following sample data:

```
Sample: [0.2, -0.3, 0.1, 0.4, -0.5]
```

### Steps:
1. **Sort the sample data**:

```
Sorted Sample: [-0.5, -0.3, 0.1, 0.2, 0.4]
```

2. **Calculate the empirical distribution function (EDF) at each point:**:
```
EDF(x) = (number of points ≤ x) / total number of points
```

#### For our sample:
```
EDF(-0.5) = 1/5 = 0.2
EDF(-0.3) = 2/5 = 0.4
EDF(0.1) = 3/5 = 0.6
EDF(0.2) = 4/5 = 0.8
EDF(0.4) = 5/5 = 1.0
```