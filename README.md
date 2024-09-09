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


## Central Limit Theorem (CLT)

The **Central Limit Theorem (CLT)** is a fundamental principle in statistics that states that, given a sufficiently large sample size, the sampling distribution of the sample mean will approach a normal distribution, regardless of the shape of the original population distribution. This is crucial for inferential statistics, allowing us to make predictions about population parameters based on sample data.

### Why is Central Limit Theorem Important?

- **Normality of Sample Means**: The CLT allows us to assume that the distribution of the sample means will be approximately normal, even if the original data is not. This normality is important for making confidence intervals and hypothesis tests.
  
- **Sample Size Consideration**: The larger the sample size, the closer the sample mean distribution will be to a normal distribution. For most data, a sample size of 30 or more is generally sufficient.

- **Practical Applications**: The CLT is used in many areas of data science, especially in A/B testing, hypothesis testing, and confidence intervals. It helps when dealing with unknown population distributions by relying on the sample means.

### Example in Python:

```python
import numpy as np
import matplotlib.pyplot as plt

# Generating a non-normal population distribution
population = np.random.exponential(scale=2, size=1000)

# Function to calculate the means of random samples
def sample_me

```



## Hypothesis Testing

**Hypothesis Testing** is a statistical method used to determine whether there is enough evidence in a sample of data to infer that a certain condition holds true for the entire population. It is a key process in statistical inference and decision-making.

### Definitions

- **Null Hypothesis (H₀)**: The null hypothesis is a statement of no effect or no difference. It serves as the default assumption that there is no significant effect or relationship between variables. It is the hypothesis that researchers aim to test against.

- **Alternative Hypothesis (H₁ or Ha)**: The alternative hypothesis is a statement that contradicts the null hypothesis. It proposes that there is a significant effect or difference. It is what researchers aim to support with evidence.

### Importance in Data Science

- **Decision-Making**: Hypothesis testing helps in making data-driven decisions by providing a structured method to test assumptions and claims. It is crucial for validating models, algorithms, and business strategies.

- **Model Evaluation**: In machine learning, hypothesis testing is used to evaluate the performance of models, such as comparing the effectiveness of different algorithms or determining if the observed performance metrics are statistically significant.

- **A/B Testing**: Used in A/B testing to compare two or more versions of a web page, product, or feature to determine which one performs better based on statistical evidence.

### Example in Python:

Here’s an example using Python to perform a hypothesis test with a sample dataset:

```python
from scipy import stats
import numpy as np

# Sample data
data_before = np.array([20, 22, 19, 24, 30, 29, 25, 23, 27, 28])
data_after = np.array([25, 27, 24, 28, 35, 33, 30, 29, 32, 31])

# Null Hypothesis (H₀): There is no difference in means between the two groups.
# Alternative Hypothesis (H₁): There is a significant difference in means between the two groups.

# Perform a t-test
t_stat, p_value = stats.ttest_ind(data_before, data_after)

print(f"T-statistic: {t_stat}")
print(f"P-value: {p_value}")

# Interpret the result
alpha = 0.05  # significance level
if p_value < alpha:
    print("Reject the null hypothesis: There is a significant difference between the two groups.")
else:
    print("Fail to reject the null hypothesis: There is no significant difference between the two groups.")


```
### Example01
A teacher claims that the mean socre of students in his class is greater than 82 with a standard deviation of 20. If a sample of 81 students was selected with a mean score of 90.

### Example02
#### Scenario
Imagine you work for an e -commerce company, and your team is responsible for analyzing customer purchase data. You want to determine whether a new website design has led to a significant increase in the average purchase amount compared to the old design.

#### Data
You have collected data from a random sample of 30 customers who made purchases on the old website design and 30 customers on the new website design .You have the sample means, sample standard deviations, and sample size for both groups.

Old design data=[45.2,42.8,38.9,43.5,41.0,44.6,40.5,42.7,39.8,41.4,44.3,39.7,42.1,40.6,43.0,42.2,41.5,39.6,44.0,43.1,38.7,43.9,42.0,41.9,42.8,43.7,41.3,40.9,42.5,41.6]
New Design data=[48.5,49.1,50.2,47.8,48.7,49.9,48.0,50.5,49.8,49.6,48.2,48.9,49.7,50.3,49.4,50.1,48.6,48.3,49.0,50.0,48.4,49.3,49.5,48.8,50.6,50.4,48.1,49.2,50.7,50.8]

Population std=2.5

### Hypothesis testing (T test)

### Example 01
A manufacturer claims that the avrage weight of potato chips is 150 grams. A sample of 25 bags is taken, and the average weight is found to be 148 grams, with a standard deviation of 5 grams. Test the manufacturers claim using a one-tailed test with a significance level of 0.05

### Example 02
A company wants to test whether a new training program improves the typing speed of its employees. The typing speed of 20 employees was recorded before and after the training program. The data is given below. Test at 5% level of significance whether the training program has an effect on the typing speed of the employees. 

Before=[50,60,45,65,55,70,40,75,80,65,70,60,50,55,45,75,60,50,65,70]
After=[60,70,55,75,65,80,50,85,90,70,75,65,55,60,50,80,65,55,70,75]


### Hypothesis testing (CHI SQR TEST)

### Example01
A study was conducted to investigate whether there is a relationship between gender and the preferred genre of music. A sample of 235 people was selected and the data collected is shown below. Test at 5% level of sign9ificance whether there is signinficance association between gender and music preference. 

|        | Pop | Hip hop  | Classical  | Rock   |
|------------|------------|------------|------------|------------|
| Male   | 40  | 45  | 25   | 10   |
| Female | 35  | 30  | 20   | 30   |


df=(row-1)(columns-1)=3
alfa=.05
