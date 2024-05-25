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

3. **Calculate the CDF of the reference distribution at each point. For the standard normal distribution, we use the cumulative distribution function (CDF) of the normal distribution.**:
```
CDF(-0.5) ≈ 0.3085
CDF(-0.3) ≈ 0.3821
CDF(0.1) ≈ 0.5398
CDF(0.2) ≈ 0.5793
CDF(0.4) ≈ 0.6554
```

4. **Compute the absolute differences between the EDF and the CDF at each sample point and find the maximum difference (D):**:
```
|EDF(-0.5) - CDF(-0.5)| = |0.2 - 0.3085| = 0.1085
|EDF(-0.3) - CDF(-0.3)| = |0.4 - 0.3821| = 0.0179
|EDF(0.1) - CDF(0.1)| = |0.6 - 0.5398| = 0.0602
|EDF(0.2) - CDF(0.2)| = |0.8 - 0.5793| = 0.2207
|EDF(0.4) - CDF(0.4)| = |1.0 - 0.6554| = 0.3446
```

#### Maximum Difference (D) = 0.3446

5. **Determine the critical value from the K-S table based on the sample size (n = 5) and the significance level (e.g., α = 0.05)**:

#### Let's implement this in Python:

### Python code

```
import numpy as np
from scipy import stats

# Sample data
data = np.array([0.2, -0.3, 0.1, 0.4, -0.5])

# Perform the Kolmogorov-Smirnov test
d_statistic, p_value = stats.kstest(data, 'norm', args=(0, 1))

print(f"D-statistic: {d_statistic}")
print(f"P-value: {p_value}")

# Interpret the result
alpha = 0.05
if p_value < alpha:
    print("Reject the null hypothesis: The sample does not come from a standard normal distribution")
else:
    print("Fail to reject the null hypothesis: The sample comes from a standard normal distribution")
```

### Explanation of the Code
- 1. **Import necessary libraries: numpy for numerical operations and scipy.stats for statistical functions.**
- 2. **Define the sample data.**
- 3. **Use kstest from scipy.stats: This function computes the K-S test for a sample against a reference distribution.**:
 - **'norm' specifies the standard normal distribution.**
 - **args=(0, 1) specifies the parameters of the normal distribution (mean = 0, standard deviation = 1)**
- 4. **Print the D-statistic and p-value.**
- 5. **Interpret the p-value**: If the p-value is less than the significance level (α = 0.05), we reject the null hypothesis that the sample comes from the specified distribution.

### Interview Question
Question: Explain the Kolmogorov-Smirnov test and write a Python function to perform a two-sample K-S test, comparing two given samples. Provide an example of how to use this function.

Answer:

- 1. **Explanation**:

- The K-S test compares the empirical distribution functions of two samples.
- It computes the maximum distance (D) between these EDFs.
- A large D suggests that the two samples come from different distributions.

- 2. **Python Function for Two-Sample K-S Test:**:
