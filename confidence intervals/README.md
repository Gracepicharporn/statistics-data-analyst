# 📊 Confidence Intervals

## 📌 Project Overview

This project explores **confidence intervals** using real-world **Air Quality Index (AQI)** data from the U.S. Environmental Protection Agency (EPA).

The analysis focuses on six states where Ripple Renewable Energy (RRE) operates:

* 🇺🇸 California
* 🇺🇸 Florida
* 🇺🇸 Michigan
* 🇺🇸 Ohio
* 🇺🇸 Pennsylvania
* 🇺🇸 Texas

The goal is to summarize AQI levels, visualize their distributions, and construct a **95% confidence interval** for the state with the highest observed mean AQI.

---

## 🎯 Objectives

* 📋 Explore and summarize the AQI dataset
* 📊 Calculate mean AQI for RRE states
* 📦 Visualize AQI distributions using boxplots
* 🔎 Compare state-level AQI measurements against a policy threshold of **10**
* 📐 Construct a **95% confidence interval**
* 🧠 Understand sample statistics, standard error, margin of error, and confidence intervals

---

## 🗂️ Dataset

The dataset contains national **Air Quality Index (AQI)** measurements by state.

The activity assumes that the available data represents a **random sample from a larger population**. All observations in this dataset were collected on **January 1, 2018**.

### 📈 Dataset Summary

| Statistic     | Value |
| ------------- | ----: |
| Observations  |   260 |
| Unique States |    52 |
| Mean AQI      |  6.76 |
| Median AQI    |     5 |
| Minimum AQI   |     0 |
| Maximum AQI   |    50 |

The dataset is not equally represented across states. For example, California has 66 observations, while some states have only one observation.

---

## 🧹 Data Exploration

The analysis uses:

* `pandas.describe()`
* `value_counts()`
* `groupby()`
* `mean()`
* `shape`

These methods were used to understand the structure of the dataset, AQI distribution, and the number of observations available for each state.

---

## 📊 Mean AQI by RRE State

The mean AQI was calculated for the six states where RRE operates.

| State             |  Mean AQI | Observations |
| ----------------- | --------: | -----------: |
| 🇺🇸 California   | **12.12** |           66 |
| 🇺🇸 Florida      |      5.50 |           12 |
| 🇺🇸 Michigan     |      8.11 |            9 |
| 🇺🇸 Ohio         |      3.33 |           12 |
| 🇺🇸 Pennsylvania |      2.90 |           10 |
| 🇺🇸 Texas        |      2.70 |           10 |

California had the highest observed mean AQI among the RRE states, followed by Michigan.

---

## 📦 AQI Distribution with Boxplots

A **Seaborn boxplot** was used to visualize the distribution of AQI values across the six RRE states.

```python
import seaborn as sns

sns.boxplot(
    x=aqi_rre["state_name"],
    y=aqi_rre["aqi"]
)
```

The visualization helps compare:

* 📍 Median AQI
* 📏 Interquartile range
* 🔺 Potential outliers
* 📊 Overall AQI distribution

The policy threshold of **10** provides a reference point for interpreting the observed AQI distributions.

---

## 📐 Confidence Interval

Because California had the highest observed mean AQI, the confidence interval analysis focused on California.

### Sample Mean

The California sample mean was:

**12.1212**

```python
sample_mean = aqi_ca['aqi'].mean()
```

### 🎯 Confidence Level

A **95% confidence level** was selected.

```python
confidence_level = 0.95
```

For a 95% confidence level, the activity uses a z-value of:

**1.96**

### 📏 Standard Error

The standard error was calculated as:

**0.8987**

```python
standard_error = aqi_ca['aqi'].std() / np.sqrt(aqi_ca.shape[0])
```

### 📐 Margin of Error

The margin of error was:

**1.7615**

```python
margin_of_error = standard_error * z_value
```

---

## 📊 95% Confidence Interval

The confidence interval was calculated using:

```python
lower_ci_limit = sample_mean - margin_of_error
upper_ci_limit = sample_mean + margin_of_error
```

### Result

**95% Confidence Interval:**

**[10.36, 13.88]**

The same interval was also calculated using `scipy.stats.norm.interval()`.

---

## 🧠 Key Concepts

### 🔹 Sample Mean

The average AQI calculated from the observed sample.

### 🔹 Confidence Level

The selected level of confidence used to construct the interval. This project uses **95%**.

### 🔹 Standard Error

A measure of the variability of the sample mean.

### 🔹 Margin of Error

Calculated using:

```text
Margin of Error = z × Standard Error
```

### 🔹 Confidence Interval

Calculated as:

```text
Lower Limit = Sample Mean − Margin of Error

Upper Limit = Sample Mean + Margin of Error
```

---

## 💡 Key Takeaways

* 📊 California had the highest observed mean AQI among the six RRE states.
* 📦 Boxplots provided a visual comparison of AQI distributions across states.
* 📐 A 95% confidence interval for California's population mean AQI was estimated as **[10.36, 13.88]** based on the sample.
* 🔄 Changing the confidence level changes the width of the confidence interval.
* 🕐 The dataset represents measurements from a single date, which is an important limitation when interpreting the results.

---

## 🛠️ Tools & Technologies

* 🐍 Python
* 🐼 Pandas
* 🔢 NumPy
* 📊 Seaborn
* 📈 Matplotlib
* 🧮 SciPy
* 📓 Jupyter Notebook

---

## 🧠 Skills Demonstrated

* 📊 Descriptive statistics
* 🔍 Exploratory data analysis
* 📦 Data visualization
* 📐 Confidence interval construction
* 🧮 Statistical inference
* 📏 Standard error calculation
* 📊 Margin of error calculation
* 🐍 Python data analysis
* 📈 Statistical interpretation

---

## 🔄 Analysis Workflow

```text
📥 Load EPA AQI Dataset
        ↓
🔍 Explore Dataset
        ↓
🇺🇸 Filter RRE States
        ↓
📊 Calculate Mean AQI
        ↓
📦 Create Boxplot
        ↓
🔎 Identify Highest Mean AQI
        ↓
📐 Calculate Standard Error
        ↓
📏 Calculate Margin of Error
        ↓
🎯 Construct 95% Confidence Interval
        ↓
🧠 Interpret Results
```

---

## 📁 Project Structure

```text
confidence-intervals/
│
├── 📓 Explore_Confidence_Intervals.ipynb
├── 📄 README.md
└── 📊 c4_epa_air_quality.csv
```

> 💡 If the dataset is provided by Coursera and redistribution is restricted, keep the CSV out of the GitHub repository and include only the notebook and README.

---

## 🎓 Learning Outcome

This project demonstrates how **confidence intervals can be used to estimate population parameters from sample data**.

It also reinforces the relationship between:

**Sample Mean → Standard Error → Margin of Error → Confidence Interval**

---

## 📚 Reference

* [Seaborn Boxplot Documentation](https://seaborn.pydata.org/generated/seaborn.boxplot.html)

---

## 👤 Author

**Grace**

📊 Data Analytics | 🐍 Python | 📈 Statistics | 🤖 Google Advanced Data Analytics

