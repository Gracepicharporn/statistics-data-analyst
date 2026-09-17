# 📊 Probability Distributions

This project explores **probability distributions, normal distribution, empirical rules, z-scores, and outlier detection** using air quality data from the **U.S. Environmental Protection Agency (EPA)**.

The analysis focuses on **Air Quality Index (AQI) data related to carbon monoxide (CO)** and demonstrates how statistical techniques can be used to understand the distribution of data and identify observations that may require further investigation.

---

## 🌎 Project Scenario

The project uses a modified dataset based on EPA air-quality monitoring data from more than 200 sites across the United States.

The goal is to analyze carbon monoxide air-quality measurements and determine:

* 📈 What type of probability distribution best describes the data?
* 📊 Does the data approximately follow a normal distribution?
* 📐 How does the empirical rule apply to the data?
* 🔢 How can z-scores be used to identify potential outliers?
* 🔍 Which sites may require additional investigation?

---

## 🎯 Project Objectives

The main objectives of this project were to:

* 🔎 Explore the structure of the dataset
* 📊 Visualize the distribution of AQI data
* 🔔 Determine whether the distribution is approximately normal
* 📐 Apply the empirical rule
* 🧮 Calculate mean and standard deviation
* 🔢 Calculate z-scores
* 🚨 Identify potential outliers
* 💡 Communicate statistical findings to stakeholders

---

## 📊 Dataset

The dataset contains **260 observations and 8 original variables** related to carbon monoxide air-quality measurements.

Important variables include:

| Variable           | Description                                |
| ------------------ | ------------------------------------------ |
| `date_local`       | Date of the observation                    |
| `state_name`       | State where the monitoring site is located |
| `county_name`      | County of the monitoring site              |
| `city_name`        | City associated with the site              |
| `local_site_name`  | Local monitoring site                      |
| `parameter_name`   | Air-quality parameter                      |
| `units_of_measure` | Measurement units                          |
| `aqi_log`          | Log-transformed AQI value                  |

A `z_score` column was also created during the analysis to measure how many standard deviations each observation is from the mean.

---

## 🔬 Analysis

### 📈 Distribution

A histogram was created to visualize the distribution of `aqi_log`.

The distribution showed a **slight right skew while maintaining an approximately bell-shaped form**, suggesting that the data could be treated as approximately normally distributed for the purposes of this analysis.

---

## 📐 Empirical Rule

The empirical rule states that for a normal distribution:

* **68%** of observations fall within 1 standard deviation of the mean
* **95%** fall within 2 standard deviations
* **99.7%** fall within 3 standard deviations

For this dataset:

| Standard Deviations | Expected |   Observed |
| ------------------- | -------: | ---------: |
| ±1 SD               |      68% | **76.15%** |
| ±2 SD               |      95% | **95.77%** |
| ±3 SD               |    99.7% | **99.62%** |

The results for ±2 and ±3 standard deviations are very close to the theoretical values expected for a normal distribution.

Overall, the data appears to be **approximately normally distributed**, although the ±1 standard deviation result differs somewhat from the theoretical 68%.

---

## 🔢 Z-Score Analysis

A z-score measures how far an observation is from the mean in terms of standard deviations.

The z-score was calculated using:

```python
data["z_score"] = stats.zscore(data["aqi_log"], ddof=1)
```

Observations with a z-score greater than **+3** or less than **−3** were examined as potential outliers.

### 🚨 Potential Outlier

The analysis identified one observation beyond ±3 standard deviations:

**West Phoenix, Arizona**

* `aqi_log`: **3.931826**
* `z_score`: **3.029044**

This observation is slightly more than three standard deviations above the mean.

---

## 💡 Key Findings

* 📊 The `aqi_log` distribution is approximately bell-shaped.
* 📐 The empirical rule provides evidence that the data is approximately normally distributed.
* 📈 **76.15%** of observations fall within one standard deviation of the mean.
* 📈 **95.77%** fall within two standard deviations.
* 📈 **99.62%** fall within three standard deviations.
* 🚨 One observation, **West Phoenix**, was identified as a potential outlier based on a z-score above +3.
* 🔍 The potential outlier could be investigated further to determine whether it represents an unusual measurement or an area requiring additional attention.

---

## 🛠️ Tools & Technologies

🐍 **Python**

🐼 **Pandas**

🔢 **NumPy**

📊 **Matplotlib**

📐 **SciPy**

📈 **Statsmodels**

📓 **Jupyter Notebook**

---

## 🧠 Skills Demonstrated

* Probability distributions
* Normal distribution
* Exploratory data analysis
* Data visualization
* Mean and standard deviation
* Empirical rule
* Z-score calculation
* Outlier detection
* Statistical interpretation
* Data-driven communication

---

## 🔄 Analysis Workflow

```text
📥 Import Data
      ↓
🔎 Explore Dataset
      ↓
📊 Visualize Distribution
      ↓
📈 Evaluate Normality
      ↓
📐 Apply Empirical Rule
      ↓
🔢 Calculate Z-Scores
      ↓
🚨 Identify Potential Outliers
      ↓
💡 Interpret Results
      ↓
📢 Communicate Findings
```

---

## 📓 Project Notebook

**Jupyter Notebook:**
`Activity_Explore probability distributions.ipynb`

---

## 📚 Reference

U.S. Environmental Protection Agency (EPA), Air Quality Data collected at outdoor monitoring sites across the United States.

---

## ⚠️ Disclaimer

The dataset used in this project has been modified for educational purposes. The analysis is intended to demonstrate statistical concepts and should not be interpreted as a complete assessment of real-world air quality conditions.

