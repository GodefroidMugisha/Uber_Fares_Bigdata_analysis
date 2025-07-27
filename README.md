# Uber Rides Data Analysis - Power BI & Python

## Overview

This project analyzes Uber ride data using both **Power BI** and **Python**, focusing on descriptive statistics, data visualization, and key correlations. It is designed as an academic assignment for the course **"Introduction to Big Data."**

## Objectives

* Explore and preprocess Uber rides data.
* Generate descriptive statistics: mean, median, mode, standard deviation, quartiles, and identify outliers.
* Visualize patterns in fare amounts, ride timings, and distances.
* Build an interactive dashboard in Power BI.
* Capture documentation and screenshots for transparency.

## Tools Used

* **Power BI** (for data visualization and dashboard creation)
* **Python** (for statistical analysis and optional visualizations)
* **Jupyter Notebook / Power BI Python Scripts**

## Dataset

* File: `uber.csv`
* Fields: `pickup_datetime`, `fare_amount`, `trip_distance`, `passenger_count`, etc.

## Descriptive Statistics (Python)

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
from scipy import stats

# Load data
df = pd.read_csv("uber.csv")

# Drop NA and check structure
df.dropna(inplace=True)

# Descriptive statistics
print(df['fare_amount'].describe())
print("Median:", df['fare_amount'].median())
print("Mode:", df['fare_amount'].mode()[0])
print("Std Dev:", df['fare_amount'].std())

# Quartiles and range
Q1 = df['fare_amount'].quantile(0.25)
Q3 = df['fare_amount'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR)

# Outlier detection
outliers = df[(df['fare_amount'] < (Q1 - 1.5 * IQR)) | (df['fare_amount'] > (Q3 + 1.5 * IQR))]
print("Outliers found:", outliers.shape[0])
```

## Visualizations (Python)

```python
# Distribution of Fare
sns.histplot(df['fare_amount'], bins=50, kde=True)
plt.title("Fare Amount Distribution")
plt.show()

# Scatter plot: Fare vs Distance
plt.figure(figsize=(8, 6))
sns.scatterplot(x='trip_distance', y='fare_amount', data=df)
plt.title("Fare vs Trip Distance")
plt.show()
```

## Power BI Visuals

* **Line Chart**: Fare trend over time
* **Column Chart**: Rides by hour/day
* **Heatmap**: Avg fare by hour/day using Matrix visual with conditional formatting
* **Scatter Plot**: Fare vs Distance with passenger count as bubble size

### Visual Construction Summary

* Data was loaded and transformed in Power BI using `Transform Data` option.
* New columns for **hour** and **day\_of\_week** were created using:

  * `Add Column > Date > Hour`
  * `Add Column > Date > Day`
* Visuals were created using standard visualizations under the Power BI ribbon.

## Screenshot Documentation

📸 Included screenshots in my GitHub repo:

* CSV data loading step
* Power BI transformation (e.g., creating hour column)
* Each visualization step (line chart, column chart, matrix heatmap, scatter plot)
* Final dashboard layout

##Link to the PowerBi document in drive:
https://drive.google.com/drive/folders/1_7B_g7M0zdpiYv5iKpk8Jpj523WZYkkD?usp=drive_link

