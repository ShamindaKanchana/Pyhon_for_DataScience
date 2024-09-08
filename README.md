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
