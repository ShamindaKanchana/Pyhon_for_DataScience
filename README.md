# Python_for_DataScience

## Mean, Median, and Mode

In data science, the **mean**, **median**, and **mode** are fundamental statistical measures to describe the central tendency of a dataset.

- **Mean**: The average value of the data points.
- **Median**: The middle value when the data points are sorted.
- **Mode**: The most frequent value in the dataset.

### Example in Python:

```python
import numpy as np
from scipy import stats

# Example dataset
data = [12, 15, 12, 14, 16, 18, 19, 20, 12]

# Calculate mean, median, and mode
mean = np.mean(data)
median = np.median(data)
mode = stats.mode(data)[0][0]

print(f"Mean: {mean}")
print(f"Median: {median}")
print(f"Mode: {mode}")
```

## Skewness
Skewness is a measure of the asymmetry of the distribution of data points. In data science, it helps identify whether the data leans more towards the left or right of the mean. Understanding skewness is essential because many statistical models assume data to be normally distributed, and skewed data may need transformation for accurate analysis and predictions.

### Why is Skewness Important?
Positive Skewness (Right-skewed): The right tail is longer, indicating that more data points are concentrated on the left side of the distribution. This may indicate the presence of outliers on the right.

Negative Skewness (Left-skewed): The left tail is longer, indicating that more data points are concentrated on the right side of the distribution. This may indicate the presence of outliers on the left.

Practical Use in Data Science:
Modeling Impact: Skewed data can affect the performance of statistical models, especially those that assume normality, such as linear regression. Transforming skewed data (e.g., using log or square root transformations) can improve model accuracy.

Real-World Examples: Salary data is often positively skewed because a small number of high earners raise the mean salary, but most people earn closer to the median.


```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

# Example dataset with positive skewness
data_skewed = [10, 11, 12, 15, 19, 20, 25, 30, 50]

# Plot the distribution
sns.histplot(data_skewed, kde=True)
plt.title("Distribution with Positive Skewness")
plt.show()

# Calculate skewness
skewness = pd.Series(data_skewed).skew()
print(f"Skewness: {skewness}")

# Interpretation of skewness
if skewness > 0:
    print("The data is positively skewed (right-skewed).")
elif skewness < 0:
    print("The data is negatively skewed (left-skewed).")
else:
    print("The data is symmetric.")




```