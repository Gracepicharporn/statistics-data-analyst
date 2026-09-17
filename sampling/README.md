# 📊 Explore Sampling

## 📌 Project Overview

This project explores **sampling techniques and sampling distributions** using Python and air-quality data from the Environmental Protection Agency (EPA).

The analysis demonstrates how random sampling can be used to work efficiently with datasets and how repeated sampling helps us understand the behavior of sample statistics. The project also applies the **Central Limit Theorem (CLT)** and calculates the **standard error** of the sample mean.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* 🔍 Explore and understand the dataset
* 📋 Calculate descriptive statistics
* 🎲 Perform random sampling **with replacement**
* 📐 Compare sample and population means
* 🔄 Create a sampling distribution using 10,000 random samples
* 📈 Visualize the sampling distribution
* 🧠 Apply the **Central Limit Theorem**
* 📏 Calculate the **standard error**
* 📊 Compare the sampling distribution with a normal distribution

---

## 🌎 Project Scenario

I worked as a member of an analytics team for the **Environmental Protection Agency (EPA)**.

The goal was to analyze **air quality related to carbon monoxide**, a major air pollutant. The dataset contains air-quality measurements from more than 200 monitoring sites across different states, counties, cities, and local sites.

---

## 📂 Dataset

The dataset used in this project is:

`c4_epa_air_quality.csv`

### 📋 Key Variables

| Column             | Description                                |
| ------------------ | ------------------------------------------ |
| `date_local`       | Date of the measurement                    |
| `state_name`       | State where the measurement was collected  |
| `county_name`      | County where the measurement was collected |
| `city_name`        | City associated with the monitoring site   |
| `local_site_name`  | Local monitoring site                      |
| `parameter_name`   | Pollutant being measured                   |
| `units_of_measure` | Measurement units                          |
| `arithmetic_mean`  | Mean carbon monoxide measurement           |
| `aqi`              | Air Quality Index                          |

The dataset contains **260 AQI measurements**.

---

## 🔎 Data Exploration

The initial descriptive statistics showed:

* 📊 **Population size:** 260 observations
* 📈 **Population mean AQI:** `6.757692`
* 📏 **Population standard deviation:** `7.061707`
* 🔢 **Minimum AQI:** `0`
* 🔢 **Maximum AQI:** `50`

The `aqi` column represents the **Air Quality Index**.

---

## 🎲 Sampling With Replacement

A random sample of **50 observations** was selected from the population using sampling with replacement.

```python
sampled_data = epa_data.sample(
    n=50,
    replace=True,
    random_state=42
)
```

### 🔑 Why Sampling With Replacement?

Sampling with replacement allows an observation to be selected more than once. This is why duplicate row indexes can appear in the resulting sample.

For example, row index `102` appeared twice in the sample because the observation was randomly selected more than once.

---

## 📐 Population Mean vs. Sample Mean

The population mean was:

**Population mean:** `6.757692`

The mean of the first random sample of 50 observations was:

**Sample mean:** `5.54`

The two values are different because of **sampling variability**.

The sample mean represents a point estimate of the population mean based on a smaller random sample rather than the entire dataset.

---

## 🔄 Sampling Distribution

To demonstrate the behavior of sample means, I generated:

**10,000 random samples**

with:

* 🎲 Sampling with replacement
* 📦 Sample size = 50
* 📊 Statistic = sample mean AQI

```python
estimate_list = []

for i in range(10000):
    estimate_list.append(
        epa_data['aqi'].sample(
            n=50,
            replace=True
        ).mean()
    )
```

The resulting sample means were stored in a new DataFrame.

```python
estimate_df = pd.DataFrame(
    data={'estimate': estimate_list}
)
```

---

## 🧠 Central Limit Theorem

The **Central Limit Theorem (CLT)** describes how the sampling distribution of the sample mean approaches a normal distribution when sufficiently large random samples are repeatedly drawn from a population.

In this project, 10,000 random samples of 50 observations were used to create a sampling distribution.

The mean of the sampling distribution was:

**Mean of sample means:** `6.765438`

This was very close to the population mean:

**Population mean:** `6.757692`

This demonstrates the relationship described by the Central Limit Theorem.

---

## 📈 Sampling Distribution Visualization

A histogram was created to visualize the distribution of the 10,000 sample means.

The analysis also compared the sampling distribution with a normal curve based on:

* Population mean
* Standard error

The visualization showed that the sampling distribution was well approximated by a normal distribution, consistent with the Central Limit Theorem.

---

## 📏 Standard Error

The standard error measures the **sample-to-sample variability of a statistic**, helping quantify how much a sample statistic may vary from the actual population value.

The standard error calculated from the initial sample of 50 was:

**Standard error:** `0.741323`

```python
standard_error = (
    sampled_data['aqi'].std()
    / np.sqrt(len(sampled_data))
)
```

---

## 💡 Key Findings

### 🔹 1. Sampling Creates Variability

A sample mean does not necessarily equal the population mean.

In this analysis:

* Population mean = **6.757692**
* First sample mean = **5.54**

The difference is a result of random sampling variability.

### 🔹 2. Sampling With Replacement Can Create Duplicates

Because observations were sampled with replacement, the same observation could appear multiple times in a sample.

### 🔹 3. The Sampling Distribution Approaches Normality

The distribution of 10,000 sample means was well approximated by a normal distribution, demonstrating the practical application of the Central Limit Theorem.

### 🔹 4. The Mean of Sample Means Approximates the Population Mean

The mean of the 10,000 sample means was approximately equal to the population mean:

> **6.765438 ≈ 6.757692**

This illustrates an important property of sampling distributions.

### 🔹 5. Standard Error Measures Sampling Variability

The standard error provided a numerical measure of how much the sample mean can vary from sample to sample.

---

## 🛠️ Tools & Technologies

* 🐍 **Python**
* 🐼 **Pandas**
* 🔢 **NumPy**
* 📊 **Matplotlib**
* 📈 **SciPy**
* 📉 **Statsmodels**
* 📓 **Jupyter Notebook**

---

## 🧠 Skills Demonstrated

* 📥 Data loading
* 🔍 Exploratory data analysis
* 📊 Descriptive statistics
* 🎲 Random sampling
* 🔄 Sampling with replacement
* 📐 Mean estimation
* 🧠 Central Limit Theorem
* 📊 Sampling distributions
* 📈 Data visualization
* 📏 Standard error calculation
* 📝 Statistical interpretation

---

## 🔄 Analysis Workflow

```text
📥 Load EPA Air Quality Data
        ↓
🔍 Explore Dataset
        ↓
📊 Calculate Descriptive Statistics
        ↓
📐 Calculate Population Mean
        ↓
🎲 Draw Random Sample of 50
        ↓
📊 Calculate Sample Mean
        ↓
🔄 Generate 10,000 Random Samples
        ↓
📈 Build Sampling Distribution
        ↓
🧠 Apply Central Limit Theorem
        ↓
📏 Calculate Standard Error
        ↓
📊 Compare With Normal Distribution
        ↓
💡 Interpret Results
```

---

## 📓 Project Notebook

The analysis was completed in a Jupyter Notebook:

**`Activity_Explore sampling.ipynb`**

The notebook contains the Python code, calculations, visualizations, and statistical interpretations from the lab.

---

## 🎓 Learning Outcome

This project strengthened my understanding of how **random sampling and sampling distributions** support statistical analysis.

It demonstrated how repeated sampling can be used to understand the behavior of sample means and how the **Central Limit Theorem** provides a foundation for approximating sampling distributions with a normal distribution.

---

## ⚠️ Disclaimer

This project was completed as part of the **Google Advanced Data Analytics Professional Certificate** coursework on Coursera.

The analysis is intended for educational and portfolio purposes. The dataset and scenario are used within the context of the course and should not be interpreted as a current assessment of real-world air quality conditions.

---

## 👤 Author

**Data Analytics Portfolio**

📌 Focus Areas:
`Python` • `Statistics` • `Sampling` • `Central Limit Theorem` • `Data Analysis` • `Data Visualization`

