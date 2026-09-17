# 🧪 Hypothesis Testing

## 📌 Project Overview

This project explores **hypothesis testing** using real-world **Air Quality Index (AQI)** data from the U.S. Environmental Protection Agency (EPA).

The analysis was completed for **Repair Our Air (ROA)**, an environmental think tank using AQI data to develop strategies for improving air quality in America.

The project applies statistical hypothesis tests to investigate three real-world questions involving California, New York, Ohio, and Michigan.

---

## 🎯 Objectives

* 📊 Explore and summarize AQI data
* 🧪 Formulate null and alternative hypotheses
* 📈 Perform two-sample t-tests
* 🔬 Perform a one-sample t-test
* 📉 Interpret p-values and t-statistics
* 📌 Use a **5% significance level**
* 🧠 Translate statistical results into practical findings

For two-sample comparisons, **Welch's t-test** was used by setting `equal_var=False`.

---

## 🗂️ Dataset

The dataset contains national **Air Quality Index (AQI)** measurements by state.

For this analysis, the data is assumed to be randomly sampled from a larger population.

### 📊 Dataset Summary

| Statistic    | Value |
| ------------ | ----: |
| Observations |   260 |
| States       |    52 |
| Mean AQI     |  6.76 |
| Median AQI   |     5 |
| Minimum AQI  |     0 |
| Maximum AQI  |    50 |

The dataset contains AQI measurements from **January 1, 2018** and includes state, county, city, site, carbon monoxide measurements, and AQI values.

---

## 🔍 Data Exploration

Initial exploration was performed using:

* `head()`
* `describe()`
* `value_counts()`
* `shape()`
* `mean()`

The analysis showed that the dataset contains observations from all 52 states, but the number of observations varies considerably between states.

California has **66 observations**, while New York and Ohio each have **10–12 observations** available for comparison.

---

# 🧪 Hypothesis Testing

The analysis uses a **5% significance level**:

```python
significance_level = 0.05
```

The hypothesis-testing workflow follows five main steps:

```text
1️⃣ Formulate hypotheses
        ↓
2️⃣ Set significance level
        ↓
3️⃣ Select statistical test
        ↓
4️⃣ Calculate p-value
        ↓
5️⃣ Draw conclusion
```

---

# 1️⃣ Los Angeles County vs. Rest of California

### ❓ Research Question

Is the mean AQI in **Los Angeles County** statistically different from the mean AQI in the rest of California?

### 🧠 Hypotheses

**Null Hypothesis (H₀):**

> There is no difference in mean AQI between Los Angeles County and the rest of California.

**Alternative Hypothesis (Hₐ):**

> There is a difference in mean AQI between Los Angeles County and the rest of California.

### 🧪 Test Used

A **two-sample Welch's t-test** was used because two independent groups were being compared.

```python
stats.ttest_ind(
    a=ca_la['aqi'],
    b=ca_other['aqi'],
    equal_var=False
)
```

### 📊 Result

| Statistic          |       Value |
| ------------------ | ----------: |
| t-statistic        |       2.111 |
| p-value            | **0.04984** |
| Significance level |        0.05 |

Since the p-value is slightly below **0.05**, the null hypothesis was rejected in the course analysis.

### 💡 Interpretation

The results indicate a statistically significant difference in mean AQI between **Los Angeles County and the rest of California** at the 5% significance level.

---

# 2️⃣ New York vs. Ohio

### ❓ Research Question

Does **New York have a lower AQI than Ohio**?

### 🧠 Hypotheses

**Null Hypothesis (H₀):**

> The mean AQI of New York is greater than or equal to that of Ohio.

**Alternative Hypothesis (Hₐ):**

> The mean AQI of New York is lower than that of Ohio.

### 🧪 Test Used

A **one-sided two-sample Welch's t-test** was performed.

```python
tstat, pvalue = stats.ttest_ind(
    a=ny['aqi'],
    b=ohio['aqi'],
    alternative='less',
    equal_var=False
)
```

### 📊 Result

| Statistic          |       Value |
| ------------------ | ----------: |
| t-statistic        |      -2.026 |
| p-value            | **0.03045** |
| Significance level |        0.05 |

Since the p-value is below **0.05**, the null hypothesis was rejected in the course analysis.

### 💡 Interpretation

At the 5% significance level, the analysis supports the conclusion that **New York has a lower mean AQI than Ohio**.

---

# 3️⃣ Michigan AQI vs. Policy Threshold

### ❓ Research Question

A proposed policy would affect states with a mean AQI of **10 or greater**.

Will Michigan's mean AQI be greater than 10?

### 🧠 Hypotheses

**Null Hypothesis (H₀):**

> The mean AQI of Michigan is less than or equal to 10.

**Alternative Hypothesis (Hₐ):**

> The mean AQI of Michigan is greater than 10.

### 🧪 Test Used

A **one-sample t-test** was used to compare Michigan's mean AQI against the threshold of 10.

```python
tstat, pvalue = stats.ttest_1samp(
    michigan['aqi'],
    10,
    alternative='greater'
)
```

### 📊 Result

| Statistic          |       Value |
| ------------------ | ----------: |
| t-statistic        |      -1.740 |
| p-value            | **0.93994** |
| Significance level |        0.05 |

Since the p-value is substantially greater than **0.05**, the null hypothesis was not rejected.

### 💡 Interpretation

At the 5% significance level, the analysis does **not provide sufficient evidence** that Michigan's mean AQI is greater than 10.

---

# 📊 Results Summary

| Hypothesis                         | Test                        |     p-value | Course Analysis   |
| ---------------------------------- | --------------------------- | ----------: | ----------------- |
| Los Angeles vs. Rest of California | Two-sample Welch's t-test   | **0.04984** | Reject H₀         |
| New York vs. Ohio                  | One-sided Welch's t-test    | **0.03045** | Reject H₀         |
| Michigan vs. 10                    | One-sided one-sample t-test | **0.93994** | Fail to reject H₀ |

---

## 🧠 Key Takeaways

* 🧪 Hypothesis testing provides a structured way to evaluate claims using sample data.
* 📊 **Los Angeles County** showed a statistically significant difference in mean AQI compared with the rest of California at the 5% significance level.
* 🗽 The analysis found evidence that **New York's mean AQI was lower than Ohio's**.
* 🌲 The Michigan test did not provide sufficient evidence that its mean AQI was greater than 10.
* 📉 A **p-value** helps determine whether the observed result provides enough evidence to reject the null hypothesis.
* 🔬 **Welch's t-test** was used for two-sample comparisons to account for potentially unequal variances.

---

## 🛠️ Tools & Technologies

* 🐍 Python
* 🐼 Pandas
* 🔢 NumPy
* 🧮 SciPy
* 📓 Jupyter Notebook
* 📊 Statistical Analysis

---

## 🧠 Skills Demonstrated

* 🧹 Data exploration
* 📊 Descriptive statistics
* 🧪 Hypothesis testing
* 📐 One-sample t-tests
* 📈 Two-sample t-tests
* 🔬 Welch's t-test
* 📉 P-value interpretation
* 📊 Statistical significance
* 🧠 Statistical reasoning
* 🐍 Python data analysis

---

## 🔄 Analysis Workflow

```text
📥 Load EPA AQI Dataset
        ↓
🔍 Explore Data
        ↓
🧹 Prepare Comparison Groups
        ↓
🧪 Formulate Hypotheses
        ↓
🎯 Set α = 0.05
        ↓
📐 Select Appropriate t-Test
        ↓
🧮 Calculate Test Statistic & p-value
        ↓
📊 Interpret Results
        ↓
💡 Communicate Findings
```

---

## 📁 Project Structure

```text
hypothesis-testing/
│
├── 📓 Explore_Hypothesis_Testing.ipynb
├── 📄 README.md
└── 📊 c4_epa_air_quality.csv
```

> 💡 If the CSV is provided by Coursera and redistribution is restricted, keep the dataset out of GitHub and include only your notebook and README.

---

## 🎓 Learning Outcome

This project demonstrates how **statistical hypothesis testing can be applied to real-world data to evaluate differences between groups and compare sample means against a defined threshold**.

It reinforces the relationship between:

**Hypotheses → Significance Level → Statistical Test → p-value → Conclusion**

---

## 👤 Author

**Grace Jenjaroenwong**

📊 Data Analytics | 🐍 Python | 📈 Statistics | 🤖 Google Advanced Data Analytics
