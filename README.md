# Sleep Health and Lifestyle Analysis

> **Data Analysis Essentials – Cornerstone Project**

A Python-based exploratory and statistical analysis of the **Sleep Health and Lifestyle Dataset**, focusing on the relationships between sleep duration, sleep quality, stress, physical activity, occupation, health indicators, and sleep disorders.

---

## 👥 Team Information

**University:** Aditya University  
**Department:** Computer Science and Engineering  
**Course:** Data Analysis Essentials  
**Project Type:** Cornerstone Project  
**Team Number:** _Add team number_  
**Team Name:** _Add team name_  
**Guide:** Mr. K. Ashok Teja, Assistant Professor, CSE Department

### Team Members

| Name | Roll Number |
|---|---|
| M. Pruthviraj Srinivas | 25B11CS534 |
| E. Tejeshwanth | 25B11CS254 |
| S. Bhavitha | 25B11CS868 |
| K. Arun Kumar | 26B12CS104 |

> **Note:** Individual responsibilities/contributions should be added here before final submission because they were not specified in the supplied project materials.

---

## 📌 Project Overview

Sleep is an essential part of a healthy lifestyle, and sleep patterns can be influenced by multiple lifestyle, occupational, and health-related factors.

This project uses **Python, Pandas, NumPy, Matplotlib, Seaborn, Plotly, SciPy, and Statsmodels** to transform raw sleep-health data into meaningful analytical insights.

The analysis follows an end-to-end workflow:

```text
Raw Dataset
     ↓
Data Loading
     ↓
Initial Exploration
     ↓
Data Cleaning
     ↓
Data Preprocessing
     ↓
Exploratory Data Analysis
     ↓
Statistical Analysis
     ↓
Visualization
     ↓
Insights
     ↓
Conclusion
```

The notebook is designed for **Google Colab** and performs setup, initial exploration, data cleaning, EDA, statistical analysis, and an insights summary.

---

## 🎯 Problem Statement

Sleep health is affected by several interconnected lifestyle, occupational, and health-related factors. Looking at individual records or performing manual comparisons makes it difficult to identify patterns across multiple variables.

The core problem addressed by this project is:

> **Identify meaningful relationships between lifestyle factors and sleep health using data-driven analysis rather than relying only on assumptions or manual observation.**

### Key Questions

The project investigates:

1. How does stress relate to sleep duration?
2. Does physical activity relate to sleep quality?
3. Does occupation influence sleep patterns?
4. Which groups show different occurrences of sleep disorders?
5. Can lifestyle and occupational variables be used to explain or predict sleep duration?

---

## 🎯 Objectives

The main objectives of the project are:

- Load and inspect the Sleep Health and Lifestyle Dataset.
- Understand the structure, data types, distributions, and summary statistics.
- Detect and handle missing values.
- Remove duplicate records.
- Clean inconsistent categorical values.
- Transform the Blood Pressure attribute into separate numerical features.
- Identify potential numerical outliers using the IQR method.
- Perform Pandas-based grouping, filtering, sorting, and aggregation.
- Explore relationships between sleep, stress, physical activity, occupation, and health variables.
- Create meaningful statistical visualizations.
- Apply Pearson and Spearman correlation analysis.
- Compare occupation groups using ANOVA and a Welch's t-test example.
- Build a linear regression model for Sleep Duration.
- Interpret the results and identify important patterns.
- Document conclusions, limitations, and possible future improvements.

---

## 🌐 Scope of the Project

The project focuses on exploratory and statistical analysis of sleep and lifestyle data.

### Included

- Demographic analysis
- Occupation-wise analysis
- Sleep duration analysis
- Sleep quality analysis
- Stress level analysis
- Physical activity analysis
- Heart rate analysis
- Daily steps analysis
- BMI category analysis
- Blood pressure feature engineering
- Sleep disorder prevalence analysis
- Correlation analysis
- ANOVA
- Welch's t-test example
- Linear regression
- Static and interactive visualizations

### Not Included

- Medical diagnosis
- Clinical decision-making
- Real-time health monitoring
- A production-grade medical prediction system
- Causal conclusions from observational relationships

---

## ⭐ Significance

The project demonstrates how data analysis can be used to move from raw health and lifestyle records to understandable insights.

Instead of relying only on manual observation, the project combines:

- Data cleaning
- Exploratory data analysis
- Statistical testing
- Data visualization
- Regression modelling

This makes it easier to study multiple variables together and identify patterns that may not be obvious from individual records.

---

# 📊 Dataset

## Dataset Name

**Sleep Health and Lifestyle Dataset**

## Source

The dataset was obtained from **Kaggle**.

**Dataset:** Sleep Health and Lifestyle Dataset by Laksika Tharmalingam

**Kaggle:**  
https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset

## Dataset Size

The dataset used by this project contains:

- **374 records**
- **13 original columns**
- **11 occupation categories**
- Age range: **27–59 years**

The notebook confirms that the loaded dataset has a shape of **(374, 13)**.

---

## Dataset Attributes

| Column | Description |
|---|---|
| `Person ID` | Unique identifier for each individual |
| `Gender` | Gender of the individual |
| `Age` | Age in years |
| `Occupation` | Occupation/profession |
| `Sleep Duration` | Sleep duration in hours |
| `Quality of Sleep` | Subjective sleep-quality rating |
| `Physical Activity Level` | Daily physical activity level in minutes |
| `Stress Level` | Subjective stress-level rating |
| `BMI Category` | BMI classification |
| `Blood Pressure` | Blood pressure in systolic/diastolic format |
| `Heart Rate` | Heart rate in beats per minute |
| `Daily Steps` | Number of daily steps |
| `Sleep Disorder` | Sleep disorder category |

### Main Target/Analysis Variables

- **Sleep Duration**
- **Quality of Sleep**
- **Sleep Disorder**

### Important Supporting Variables

- Age
- Gender
- Occupation
- Stress Level
- Physical Activity Level
- BMI Category
- Blood Pressure
- Heart Rate
- Daily Steps

---

# 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data loading, cleaning, manipulation, grouping and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Basic data visualization |
| Seaborn | Statistical visualizations and heatmaps |
| Plotly | Interactive visualizations |
| SciPy | Statistical tests and correlation analysis |
| Statsmodels | ANOVA and linear regression |
| Google Colab | Development and execution environment |
| Jupyter Notebook | Notebook-based analysis |

---

# 🧹 Data Loading and Inspection

The notebook loads the CSV using Pandas.

```python
df = pd.read_csv(filename)
```

The dataset is initially inspected using operations such as:

```python
df.shape
df.dtypes
df.head()
df.isna().sum()
df.describe(include="all")
```

The loaded dataset has:

```text
Rows:    374
Columns: 13
```

The analysis also examines numerical and categorical variables separately through summary statistics.

---

# 🧼 Data Preprocessing

## 1. Missing-Value Handling

The initial dataset contains missing values in the `Sleep Disorder` column.

```text
Sleep Disorder: 219 missing values
Total missing cells: 219
```

For this dataset, a missing `Sleep Disorder` value is interpreted as no diagnosed sleep disorder.

Therefore, missing values are replaced with:

```text
None
```

After cleaning:

```text
None           219
Sleep Apnea     78
Insomnia        77
```

No rows are dropped because of these missing values.

---

## 2. Blood Pressure Feature Engineering

The original `Blood Pressure` column contains values such as:

```text
126/83
125/80
140/90
```

The project splits this field into two numerical features:

- `Systolic_BP`
- `Diastolic_BP`

Example:

```text
Blood Pressure    Systolic_BP    Diastolic_BP
126/83            126            83
125/80            125            80
140/90            140            90
```

This transformation makes blood pressure suitable for numerical analysis.

---

## 3. Duplicate Removal

Exact duplicate rows are checked and removed using:

```python
df_clean = df_clean.drop_duplicates()
```

Result:

```text
Before: 374 rows
After:  374 rows
Removed: 0 duplicate rows
```

Therefore, no exact duplicate records were present in the analyzed dataset.

---

## 4. Outlier Detection

The project uses the **Interquartile Range (IQR)** method to identify potential outliers.

The analysis checks:

- Age
- Sleep Duration
- Quality of Sleep
- Physical Activity Level
- Stress Level
- Heart Rate
- Daily Steps
- Systolic BP
- Diastolic BP

The saved notebook output identifies:

```text
Heart Rate: 15 potential outliers
All other checked numerical variables: 0 potential outliers
```

The identified outliers are **flagged but not automatically removed**, because extreme values may still represent meaningful observations in a health-related dataset.

---

## 5. Categorical Data Cleaning

Categorical columns are converted to Pandas `category` dtype for cleaner handling and memory efficiency.

The notebook also standardizes:

```text
Normal Weight → Normal
```

in the `BMI Category` field.

---

# 📈 Pandas Operations and Data Manipulation

The project demonstrates multiple Pandas techniques, including:

### Data inspection

```python
df.head()
df.shape
df.dtypes
df.isna().sum()
df.describe()
```

### Filtering

Records can be filtered according to occupation, stress level, sleep duration, sleep disorder, and other conditions.

### Grouping

The project uses:

```python
df_clean.groupby('Occupation')
```

to calculate occupation-level statistics.

### Aggregation

Metrics such as:

- Mean
- Count
- Minimum
- Maximum

are used for comparisons.

### Sorting

Occupation-level metrics are sorted to compare groups.

### Crosstabulation

Sleep disorder prevalence is calculated using:

```python
pd.crosstab()
```

### Transformation

The Blood Pressure field is transformed into:

```text
Systolic_BP
Diastolic_BP
```

### Encoding

Occupation is one-hot encoded for the regression model.

---

# 🔎 Exploratory Data Analysis

The project contains several EDA sections.

## 1. Distribution Analysis

The project examines the distributions of:

- Sleep Duration
- Stress Level
- Physical Activity Level

This helps understand the overall range and distribution of important variables.

---

## 2. Sleep Duration and Quality by Occupation

Box plots are used to compare:

- Sleep Duration by Occupation
- Quality of Sleep by Occupation

This provides a visual comparison of sleep-related measures across occupational groups.

---

## 3. Correlation Heatmap

A Pearson correlation heatmap is created for:

- Sleep Duration
- Stress Level
- Physical Activity Level
- Quality of Sleep
- Heart Rate
- Daily Steps

The heatmap helps identify linear relationships between numerical variables.

---

## 4. Stress Level vs Sleep Duration

A scatter plot with a linear trend line is used to visualize the relationship between:

```text
Stress Level
       ↓
Sleep Duration
```

---

## 5. Physical Activity vs Quality of Sleep

A regression plot examines the relationship between:

```text
Physical Activity Level
       ↓
Quality of Sleep
```

---

## 6. Occupation-wise Averages

Sorted bar charts compare occupations using:

- Average Sleep Duration
- Average Stress Level
- Average Daily Steps

---

## 7. Sleep Disorder Prevalence

Stacked bar charts show sleep disorder prevalence:

### By Occupation

The analysis compares the percentage of each occupation group with:

- None
- Sleep Apnea
- Insomnia

### By Stress Level

The analysis also compares sleep disorder prevalence across stress-level groups.

---

## 8. Interactive Plotly Visualizations

The notebook includes interactive Plotly visualizations, including an interactive box plot for Sleep Duration by Occupation.

These charts allow users to inspect individual observations and occupation-level distributions interactively.

---

# 📊 Statistical Analysis

The project goes beyond descriptive analysis and performs statistical analysis.

## Pearson Correlation

Pearson correlation is used to measure linear relationships between numerical variables.

The saved notebook's Pearson correlation matrix reports, among others:

| Variables | Pearson r |
|---|---:|
| Sleep Duration – Stress Level | 0.038 |
| Sleep Duration – Physical Activity | -0.008 |
| Sleep Duration – Quality of Sleep | -0.031 |
| Sleep Duration – Heart Rate | -0.073 |
| Sleep Duration – Daily Steps | -0.019 |
| Physical Activity – Quality of Sleep | 0.054 |

These values in the saved notebook indicate very weak linear relationships for the listed pairs.

### Important

The direct Pearson/Spearman significance calculation for Stress Level vs Sleep Duration produced `NaN` values in the saved notebook output. Therefore, those significance values should be rerun and verified before using them as final statistical claims.

---

## Spearman Correlation

Spearman correlation is also calculated to examine monotonic relationships.

The saved notebook reports:

| Variables | Spearman rho |
|---|---:|
| Sleep Duration – Stress Level | 0.037 |
| Sleep Duration – Physical Activity | 0.004 |
| Sleep Duration – Quality of Sleep | -0.084 |
| Physical Activity – Quality of Sleep | 0.075 |
| Stress Level – Daily Steps | -0.124 |

---

# 🧪 ANOVA

One-way ANOVA is used to test whether average values differ across occupation groups.

### Sleep Duration ~ Occupation

```text
F = 1.411
p = 0.159112
```

### Stress Level ~ Occupation

```text
F = 1.095258
p = 0.36321
```

Based on conventional statistical significance thresholds, these saved results do **not** provide statistically significant evidence of occupation-level differences for Sleep Duration or Stress Level at p < 0.05.

---

# 🧪 Welch's t-test

A Welch's independent-samples t-test is included as a follow-up example comparing the occupations with the lowest and highest mean Sleep Duration in the saved run.

The notebook reports:

```text
Sales Representative:
Mean Sleep Duration = 5.65 hours

Engineer:
Mean Sleep Duration = 8.88 hours
```

The saved t-test output returned:

```text
t = NaN
p = NaN
```

Therefore, the difference in means is descriptive in the current saved execution and should not be presented as statistically significant without rerunning and validating the test.

---

# 📉 Linear Regression

An Ordinary Least Squares (OLS) regression model is used to predict **Sleep Duration**.

### Predictors

- Stress Level
- Physical Activity Level
- Occupation

Occupation is one-hot encoded.

### Model Result

The saved model reports:

```text
R² = 0.867
Adjusted R² = 0.862
F-statistic = 195.4
Prob(F-statistic) = 1.11e-149
```

The major coefficients include:

```text
Stress Level              = -0.3903
Physical Activity Level   = +0.0070
```

This indicates that, within this fitted model, higher Stress Level is associated with a lower predicted Sleep Duration, while higher Physical Activity Level is associated with a higher predicted Sleep Duration, after accounting for the included occupation variables.

The model also shows statistically significant coefficients for several occupation categories, while some occupation coefficients are not statistically significant.

---

# 📊 Visualizations Included

The project contains visual analysis using:

- Histograms
- Box plots
- Bar charts
- Stacked bar charts
- Scatter plots
- Regression plots
- Pearson correlation heatmap
- Interactive Plotly box plots

All visualizations are intended to include meaningful titles, axes, and legends.

---

# 🔑 Key Insights

The supplied Review-2 presentation describes the following overall project insights:

- Higher stress is associated with shorter sleep duration.
- Increased physical activity generally relates to better sleep quality.
- Sleep duration varies across occupational groups.
- Sleep disorder occurrence differs across occupation and stress-level groups.
- Stress, physical activity, and occupation can be used together in a regression model for Sleep Duration.

The notebook's saved statistical outputs should be treated as the quantitative source of truth. In particular, the saved correlation matrix shows near-zero Pearson/Spearman correlations for several headline relationships, while the regression model shows a strong negative Stress Level coefficient.

**Before final submission, rerun the notebook and reconcile the qualitative statements in the Review-2 PPT with the final numerical outputs.**

---

# ⚠️ Important Statistical Interpretation

This project is based on observational dataset analysis.

Therefore:

> **Correlation or regression association does not automatically imply causation.**

For example, an association between stress and sleep duration does not by itself prove that stress causes changes in sleep duration.

The project should be interpreted as an exploratory analysis of patterns within this dataset.

---

# 🧠 Conclusion

The project demonstrates a complete data-analysis workflow from raw data to statistical interpretation.

The analysis includes:

```text
Dataset Collection
       ↓
Data Loading
       ↓
Inspection
       ↓
Cleaning
       ↓
Feature Engineering
       ↓
EDA
       ↓
Statistical Analysis
       ↓
Visualization
       ↓
Interpretation
       ↓
Conclusion
```

The analysis shows that sleep health can be studied through a combination of lifestyle, occupational, and health-related variables. Regression analysis provides a quantitative model for Sleep Duration using Stress Level, Physical Activity Level, and Occupation.

The project also demonstrates how Pandas, visualization libraries, statistical testing, and regression can work together to turn structured data into interpretable findings.

---

# ⚠️ Limitations

1. The dataset contains only 374 analyzed records.
2. The dataset represents a limited set of demographic, lifestyle, occupational, and health variables.
3. The analysis is observational and cannot establish causation.
4. Sleep Disorder contains 219 missing values that are interpreted as `"None"` based on the dataset's intended meaning.
5. The dataset contains potential Heart Rate outliers that were flagged but retained.
6. Some statistical outputs in the saved notebook, including the direct Stress–Sleep Pearson/Spearman significance calculation and Welch's t-test, returned `NaN` and should be rerun before being used as final inferential claims.
7. The regression model reports a high R², but its diagnostic output indicates potential modelling concerns, including a relatively large condition number.
8. The project does not provide clinical diagnosis or medical recommendations.

---

# 🚀 Future Improvements

Possible future extensions include:

- Analyze Sleep Quality as an ordinal outcome.
- Study BMI Category and Gender as additional stratification variables.
- Build a classification model for Sleep Disorder.
- Compare multiple machine-learning algorithms.
- Perform cross-validation.
- Add model diagnostics.
- Investigate interactions between stress and physical activity.
- Develop an interactive dashboard.
- Use a larger and more diverse dataset.
- Validate findings on an independent dataset.

---

# 📂 Repository Structure

Recommended GitHub structure:

```text
Sleep-Health-and-Lifestyle-Analysis/
│
├── README.md
├── requirements.txt
│
├── data/
│   └── Sleep_health_and_lifestyle_dataset.csv
│
├── notebooks/
│   └── Sleep_Health_and_Lifestyle_Analysis.ipynb
│
├── presentations/
│   ├── Review-1-Presentation.pptx
│   └── Review-2-Presentation.pptx
│
└── results/
    └── findings.md
```

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/Sleep-Health-and-Lifestyle-Analysis.git
cd Sleep-Health-and-Lifestyle-Analysis
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux/macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# 📦 Requirements

The project uses:

```text
numpy
pandas
matplotlib
seaborn
plotly
scipy
statsmodels
jupyter
```

Google Colab already provides many of these libraries, and the notebook also installs Plotly, Seaborn, SciPy, and Statsmodels when required.

---

# ▶️ Running the Project

## Option 1 – Google Colab

1. Open the notebook.
2. Upload `Sleep_health_and_lifestyle_dataset.csv`.
3. Run the notebook cells in order.
4. Use **Runtime → Run all**.
5. Review the preprocessing, visualizations, statistical tests, regression output, and final insights.

## Option 2 – Jupyter Notebook

Place the dataset in the appropriate `data/` directory and open:

```text
notebooks/Sleep_Health_and_Lifestyle_Analysis.ipynb
```

Then run all cells sequentially.

---

# 📑 Project Deliverables

The GitHub repository should contain:

- [x] Project title
- [x] Problem statement
- [x] Objectives
- [x] Scope
- [x] Significance
- [x] Dataset description
- [x] Dataset source
- [x] Data loading
- [x] Data inspection
- [x] Missing-value handling
- [x] Duplicate removal
- [x] Data cleaning
- [x] Feature engineering
- [x] Pandas operations
- [x] Grouping and aggregation
- [x] Statistical analysis
- [x] Data visualization
- [x] Conclusions
- [x] Limitations
- [ ] Team number and team name
- [ ] Individual responsibilities
- [ ] `requirements.txt`
- [ ] Dataset CSV in repository
- [ ] Review-1 PPT
- [ ] Review-2 PPT

---

# 📊 Review Presentations

The project presentations should be stored in:

```text
presentations/
```

Recommended files:

```text
Review-1-Presentation.pptx
Review-2-Presentation.pptx
```

The supplied Review-2 presentation covers:

- Problem Understanding
- Introduction
- Current Approach & Limitations
- Proposed Approach
- Dataset Description
- Requirements
- Methodology
- Data Visualization
- Key Insights & Analysis
- Implementation Workflow
- Conclusion

---

# 👨‍💻 Team Contributions

Add the actual contribution of each member before final submission.

| Team Member | Roll Number | Contribution |
|---|---|---|
| M. Pruthviraj Srinivas | 25B11CS534 | _Add responsibility_ |
| E. Tejeshwanth | 25B11CS254 | _Add responsibility_ |
| S. Bhavitha | 25B11CS868 | _Add responsibility_ |
| K. Arun Kumar | 26B12CS104 | _Add responsibility_ |

All team members should understand the complete project because the repository will be used for project evaluation and viva.

---

# 🔗 Resources

- **Dataset:** https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset
- **Notebook:** `notebooks/Sleep_Health_and_Lifestyle_Analysis.ipynb`
- **Review Presentations:** `presentations/`

---
