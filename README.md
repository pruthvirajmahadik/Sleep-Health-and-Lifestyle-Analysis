# Sleep Health and Lifestyle Analysis

> **Data Analysis Essentials – Cornerstone Project**

A Python-based exploratory and statistical analysis of the **Sleep Health and Lifestyle Dataset**, focusing on the relationships between sleep duration, sleep quality, stress, physical activity, occupation, health indicators, and sleep disorders.

---

## 👥 Team Information

**University:** Aditya University  
**Department:** Computer Science and Engineering  
**Course:** Data Analysis Essentials  
**Project Type:** Cornerstone Project  
**Team Number:** Team 9  
**Guide:** Mr. K. Ashok Teja, Assistant Professor, CSE Department

### Team Members

| Name | Roll Number |
|---|---|
| M. Pruthviraj Srinivas | 25B11CS534 |
| E. Tejeshwanth | 25B11CS254 |
| S. Bhavitha | 25B11CS868 |
| K. Arun Kumar | 26B12CS104 |



---

Overview

The project implements an end-to-end data-analysis workflow:

CSV Dataset
    ↓
Data Loading
    ↓
Data Inspection
    ↓
Data Filtering
    ↓
Data Extraction & Feature Engineering
    ↓
Data Validation & Cleaning
    ↓
Data Aggregation
    ↓
Statistical Analysis
    ↓
Data Visualization
    ↓
Results & Interpretation

The analysis is implemented in a Jupyter Notebook designed to run in Google Colab.

Features
Load a CSV dataset interactively in Google Colab
Inspect dataset dimensions, data types, missing values, and descriptive statistics
Select and validate the required dataset columns
Convert numeric fields to appropriate numeric types
Filter records using sleep-duration and stress-level conditions
Extract systolic and diastolic blood pressure from the Blood Pressure field
Create Age_Group and Sleep_Category features
Standardize inconsistent categorical values
Handle missing values according to the notebook's defined rules
Remove exact duplicate rows and duplicate Person ID records
Detect and remove values outside the defined valid ranges
Aggregate sleep, stress, and activity metrics by occupation
Compare groups using pivot tables and crosstabulations
Calculate Pearson correlations
Perform Pearson correlation significance tests
Perform one-way ANOVA across occupation groups
Perform a chi-square test between sleep disorder and BMI category
Fit a simple linear regression between stress level and sleep duration
Generate statistical visualizations using Matplotlib and Seaborn
Produce automatically generated textual interpretations from the calculated results
Technologies
Technology	Usage
Python	Main programming language
Pandas	Data loading, cleaning, transformation, grouping, and aggregation
NumPy	Numerical operations and data cleaning
Matplotlib	Data visualization
Seaborn	Statistical plots and visualizations
SciPy	Statistical tests, correlations, and linear regression
Google Colab	Primary execution environment
Jupyter Notebook	Notebook format and interactive development
Dataset

The supplied dataset is:

Sleep_Health_and_lifestyle_dataset_MESSY_v2.csv
Original Dataset Structure

The CSV contains 396 rows and 13 columns.

The columns are:

Column	Purpose
Person ID	Identifier for an individual record
Gender	Gender value
Age	Age
Occupation	Occupation category
Sleep Duration	Sleep duration
Quality of Sleep	Sleep-quality value
Physical Activity Level	Physical activity level
Stress Level	Stress-level value
BMI Category	BMI category
Blood Pressure	Blood pressure represented as text
Heart Rate	Heart rate
Daily Steps	Daily step count
Sleep Disorder	Sleep-disorder category

The supplied CSV intentionally contains inconsistent and missing values, making it suitable for the cleaning and validation workflow implemented in the notebook.

Prerequisites

The project requires:

Python 3.x
Pandas
NumPy
Matplotlib
Seaborn
SciPy
Google Colab or a Jupyter-compatible environment

The project does not include a requirements.txt file, so dependencies must be installed separately if they are not already available in the execution environment.

Dependencies
pandas
numpy
matplotlib
seaborn
scipy

Google Colab provides the notebook environment used by the project and includes the google.colab file-upload functionality used in the notebook.

Installation and Setup
Google Colab

The notebook is designed to run interactively in Google Colab.

Open:
Sleep_Health_and_Lifestyle_Analysis (2).ipynb
Run the first cells in order.
When the file-upload cell appears, select:
Sleep_Health_and_lifestyle_dataset_MESSY_v2.csv
Continue executing the notebook cells sequentially.

The notebook automatically obtains the uploaded filename:

from google.colab import files

uploaded = files.upload()
filename = list(uploaded.keys())[0]
df = pd.read_csv(filename)
Local Python/Jupyter Environment

The notebook also documents an alternative approach for a non-Colab environment:

df = pd.read_csv("your_file_name.csv")

The CSV should be accessible from the path supplied to pd.read_csv().

Usage

Run the notebook from top to bottom.

The notebook is organized into eight stages:

Stage	Description
1	Data Loading & Reading
2	Data Acquisition & Filtering
3	Data Extraction
4	Data Validation & Cleaning
5	Data Aggregation & Representation
6	Data Analysis
7	Data Visualization
8	Results & Interpretation

In Google Colab, the notebook can be executed sequentially using Runtime → Run all, or individual cells can be executed with Shift + Enter.

Data Processing
Column Selection

The notebook keeps the 13 expected source columns:

columns = [
    'Person ID',
    'Gender',
    'Age',
    'Occupation',
    'Sleep Duration',
    'Quality of Sleep',
    'Physical Activity Level',
    'Stress Level',
    'BMI Category',
    'Blood Pressure',
    'Heart Rate',
    'Daily Steps',
    'Sleep Disorder'
]

Completely empty rows are removed.

Numeric Conversion

The following fields are converted to numeric values, with invalid values converted to missing values:

Age
Sleep Duration
Quality of Sleep
Physical Activity Level
Stress Level
Heart Rate
Daily Steps
Blood Pressure Extraction

The text-based Blood Pressure field is split into two numerical features:

Systolic_BP
Diastolic_BP

For example:

Blood Pressure    Systolic_BP    Diastolic_BP
160/100           160            100
120/80            120            80
Derived Features

The notebook creates:

Age_Group
Sleep_Category

Age_Group uses these categories:

18-29
30-39
40-49
50-59
60+

Sleep_Category uses these categories:

Short (6h or less)
Normal (6-8h)
Long (over 8h)
Categorical Cleaning

The notebook standardizes:

Leading and trailing whitespace
Gender capitalization and abbreviations
Occupation capitalization
BMI category capitalization
Normal Weight → Normal
Sleep-disorder capitalization

Gender abbreviations are converted as follows:

M → Male
F → Female

Missing Sleep Disorder values are replaced with:

None

This is an assumption explicitly made by the notebook for this dataset.

Range Validation

The notebook validates numerical values against the following ranges:

Variable	Accepted Range
Age	18–100
Sleep Duration	2–14
Quality of Sleep	1–10
Physical Activity Level	0–300
Stress Level	1–10
Heart Rate	40–150
Daily Steps	0–40,000
Systolic_BP	70–250
Diastolic_BP	40–150

Values outside these ranges are converted to missing values.

If either blood-pressure component is invalid, both Systolic_BP and Diastolic_BP are cleared.

Duplicate Removal

Two duplicate-removal operations are performed:

df = df.drop_duplicates()
df = df.drop_duplicates(subset='Person ID')

For the supplied dataset:

Original rows:        396
Rows after cleaning:  370
Rows removed:          26

The notebook's saved execution reports 370 records used from the original 396 records.

Remaining missing values are not automatically filled after validation. Subsequent calculations therefore operate on the available values.

Data Aggregation

The notebook creates summaries including:

Occupation Summary

For each occupation, it calculates:

Average Sleep Duration
Average Stress Level
Average Daily Steps
Number of people
Occupation and Gender

A pivot table compares average sleep duration across:

Occupation × Gender
BMI and Sleep Disorder

A crosstabulation compares:

BMI Category × Sleep Disorder
Gender and BMI

Average sleep duration and stress level are also grouped by:

Gender × BMI Category
Statistical Analysis
Correlation Analysis

The notebook calculates a correlation matrix for:

Sleep Duration
Quality of Sleep
Stress Level
Physical Activity Level
Heart Rate
Daily Steps

The saved notebook execution reports:

Relationship	Pearson correlation
Sleep Duration – Stress Level	0.07
Sleep Duration – Quality of Sleep	-0.16
Sleep Duration – Physical Activity Level	-0.00
Sleep Duration – Heart Rate	-0.00
Sleep Duration – Daily Steps	-0.03
Physical Activity Level – Quality of Sleep	0.03
Pearson Tests

The notebook directly tests two relationships:

Stress Level ↔ Sleep Duration
Physical Activity Level ↔ Quality of Sleep

The saved execution reports:

Stress vs Sleep Duration
r = 0.07
p = 0.2237

Physical Activity vs Sleep Quality
r = 0.03
p = 0.6427

The notebook's generated interpretation therefore reports no statistically reliable relationship for either tested pair at the 0.05 significance level.

ANOVA

A one-way ANOVA tests whether sleep duration differs across occupation groups.

Only occupation groups containing at least 10 records are included.

The saved execution reports:

p = 0.2086
Chi-Square Test

A chi-square test examines the relationship between:

Sleep Disorder
BMI Category

The saved execution reports:

p = 0.5137
Simple Linear Regression

A simple linear regression estimates the relationship between:

Stress Level → Sleep Duration

The saved execution reports:

Slope:      0.05 hours per stress point
R-squared:  0.01

The model therefore explains approximately 1% of the observed variation in sleep duration in the saved execution.

Visualizations

The notebook generates the following visualizations:

Distributions

Histograms are generated for:

Sleep Duration
Stress Level
Physical Activity Level
Sleep Duration by Occupation

A Seaborn box plot compares sleep-duration distributions across occupations.

Correlation Heatmap

A heatmap displays correlations among the selected numerical variables.

Relationship Plots

Regression plots visualize:

Stress Level vs Sleep Duration
Physical Activity Level vs Quality of Sleep
Occupation Stress Levels

A horizontal bar chart displays average stress level by occupation.

Sleep Disorders by Occupation

A stacked percentage bar chart displays sleep-disorder categories by occupation.

Results

For the supplied dataset and the saved notebook execution:

370 of 396 records remain after the notebook's cleaning and duplicate-removal workflow.
Stress level and sleep duration have a Pearson correlation of approximately 0.07 with p = 0.2237.
Physical activity and sleep quality have a Pearson correlation of approximately 0.03 with p = 0.6427.
The occupation-based ANOVA for sleep duration reports p = 0.2086.
The chi-square test between sleep disorder and BMI category reports p = 0.5137.
The simple stress-to-sleep regression has a slope of approximately 0.05 hours per stress point and an R² of approximately 0.01.
In the saved occupation summary, the average sleep duration ranges from 5.65 hours for Sales Representatives to 7.12 hours for Engineers among the represented occupation groups.

These results describe the supplied dataset and should not be interpreted as causal or clinical conclusions.

Project Structure

The supplied project files currently consist of:

.
├── README.md
├── Sleep_Health_and_Lifestyle_Analysis (2).ipynb
└── Sleep_Health_and_lifestyle_dataset_MESSY_v2.csv

No separate application source modules, configuration files, shell scripts, dependency lockfiles, or test suite are included in the supplied project files.

Development Workflow

The notebook follows a sequential data-analysis workflow:

Load the CSV file.
Preserve a copy of the original dataset.
Inspect its structure and missing values.
Select the required columns.
Convert numeric fields.
Filter and inspect records.
Extract blood-pressure components.
Create age and sleep-duration groups.
Normalize categorical values.
Validate numerical ranges.
Remove duplicate records.
Recreate derived groups after cleaning.
Generate aggregated summaries.
Run statistical analyses.
Generate visualizations.
Produce automated result interpretations.

Because the notebook is sequential, cells should generally be executed from top to bottom.

Reproducibility

To reproduce the current analysis:

Use the supplied notebook.
Use the supplied CSV dataset.
Run the notebook cells sequentially.
Upload the CSV when prompted by the Colab file-upload cell.
Review the generated tables, statistical outputs, plots, and interpretation section.

The statistical outputs can change if the dataset is modified or if the cleaning rules are changed.

Testing and Validation

No automated test suite is included in the supplied project.

Validation is performed within the notebook through:

Dataset shape inspection
Data-type inspection
Missing-value counts
Descriptive statistics
Numeric conversion
Range validation
Duplicate detection
Aggregated summaries
Statistical tests
Generated visualizations
Automatically calculated result interpretations
Limitations
The analysis is based on a single supplied CSV dataset containing 396 original records.
Cleaning reduces the working dataset to 370 records.
Missing values remain in several fields after cleaning.
Missing Sleep Disorder values are interpreted as None, which is an explicit assumption in the notebook.
Values outside predefined ranges are converted to missing values rather than being investigated individually.
Occupation groups with fewer than 10 records are excluded from the ANOVA.
The data is observational, so statistical associations should not be interpreted as proof of causation.
The notebook itself notes that the dataset may be synthetic, so the results should not automatically be treated as real-world health evidence.
No clinical diagnosis or medical recommendation is produced by the project.
The simple regression between stress and sleep duration explains only approximately 1% of the observed variation in the saved execution.
Important Interpretation Note

The project is intended for data-analysis and educational purposes.

A statistical relationship, whether observed through correlation, regression, ANOVA, or another test, does not by itself establish a causal relationship between the variables.

The generated findings should therefore be interpreted within the scope and limitations of the supplied dataset and preprocessing workflow.

Future Development

The current notebook does not define a separate production application or deployment workflow. Possible extensions that are directly suggested by the notebook include:

Analyze sleep quality as an outcome.
Examine BMI and gender as additional group variables.
Build a classification model for sleep disorders.
Compare multiple machine-learning algorithms.
Apply cross-validation.
Add additional model diagnostics.
Investigate interactions between stress and physical activity.
Develop an interactive dashboard.
Evaluate the workflow on a larger dataset.
Validate findings against an independent dataset.



Files
File	Description
Sleep_Health_and_Lifestyle_Analysis (2).ipynb	Main analysis notebook containing the complete data-processing, statistical-analysis, visualization, and interpretation workflow
Sleep_Health_and_lifestyle_dataset_MESSY_v2.csv	Input dataset used by the notebook
README.md	Project documentation

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



| Team Member | Roll Number | Contribution |
|---|---|---|
| M. Pruthviraj Srinivas | 25B11CS534 | Team lead|

| E. Tejeshwanth | 25B11CS254 |Data & Tech Lead|

| S. Bhavitha | 25B11CS868 | Implementation Lead|

| K. Arun Kumar | 26B12CS104 |QA & Strartegy|

---

# 🔗 Resources

- **Dataset:** sleep-health-and-lifestyle-dataset
- **Notebook:** `notebooks/Sleep_Health_and_Lifestyle_Analysis.ipynb`
- **Review Presentations:** `presentations/`

---
