# Box-Cox Plot

## Overview

The Box-Cox transformation is a family of power transformations used to stabilize variance and make the data more normally distributed. It is particularly useful in situations where the assumption of normality is required, such as in linear regression. The Box-Cox transformation is defined as:

\[ y(\lambda) =
  \begin{cases} 
   \frac{y^\lambda - 1}{\lambda} & \text{if } \lambda \neq 0 \\
   \ln(y) & \text{if } \lambda = 0
  \end{cases}
\]

where \( y \) is the data and \( \lambda \) is the transformation parameter.

A Box-Cox plot helps to determine the best value of \( \lambda \) for the transformation. The optimal \( \lambda \) is the one that maximizes the log-likelihood function.

## Numerical Example

Let's consider a simple dataset:

\[ \text{data} = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] \]

We'll apply the Box-Cox transformation and generate a Box-Cox plot to find the optimal \( \lambda \).

## Python Code

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Sample data
data = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

# Box-Cox transformation and finding the optimal lambda
data_transformed, lambda_optimal = stats.boxcox(data)

# Plotting the Box-Cox plot
lambdas = np.linspace(-2, 2, num=100)
log_likelihoods = [stats.boxcox_llf(l, data) for l in lambdas]

plt.figure(figsize=(10, 6))
plt.plot(lambdas, log_likelihoods, 'b-')
plt.axvline(lambda_optimal, color='r', linestyle='--')
plt.xlabel('Lambda')
plt.ylabel('Log-Likelihood')
plt.title('Box-Cox Plot')
plt.grid(True)
plt.show()

print(f'Optimal lambda: {lambda_optimal}')
