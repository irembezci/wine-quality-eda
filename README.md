# Wine Quality - Exploratory Data Analysis

## Overview

This project presents an exploratory data analysis of the Wine Quality dataset using Python.

The analysis focuses on understanding the dataset structure, assessing data quality, exploring variable distributions, identifying potential outliers and investigating relationships between physicochemical properties and wine quality.

## Dataset

The dataset used in this project is the Wine Quality dataset obtained from Kaggle.

It contains 1,143 observations and 13 variables, including physicochemical properties such as acidity, residual sugar, chlorides, sulfur dioxide, density, pH, sulphates and alcohol together with a wine quality score.

### Dataset Source

[Wine Quality Dataset - Kaggle](https://www.kaggle.com/datasets/yasserh/wine-quality-dataset)

## Tools & Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Google Colab

## Analysis

### 1. Dataset Inspection

The dataset was first inspected to understand its structure, dimensions, data types, and descriptive statistics.

**Methods used:**

```python
df.shape
df.info()
df.describe()
````

The dataset contains 1,143 observations and 13 variables.

### 2. Data Quality Check

Missing values and duplicate rows were checked before performing further analysis.

**Methods used:**

```python
df.isnull().sum()
df.duplicated().sum()
```

No missing values or duplicate rows were found.

### 3. Wine Quality Distribution

The distribution of the target variable was examined using a count plot.

**Method used:**

```python
sns.countplot(data=df, x="quality")
```

The quality scores are mainly concentrated around 5 and 6, while very low and very high quality scores are less frequent.

### 4. Numerical Variable Distributions

Histograms were used to examine the distributions and ranges of the numerical features.

**Method used:**

```python
numerical_features = df.drop(columns=["quality", "Id"])

numerical_features.hist(figsize=(15, 12), bins=20)
```

Several variables show right-skewed distributions, particularly residual sugar, sulphates and sulfur dioxide.

### 5. Correlation Analysis

A correlation matrix was used to examine linear relationships between numerical variables.

**Methods used:**

```python
correlation_matrix = df.drop(columns=["Id"]).corr()

sns.heatmap(
    correlation_matrix,
    annot=True,
    cmap="coolwarm",
    fmt=".2f"
)
```

Alcohol has the strongest positive linear correlation with wine quality (r = 0.48), while volatile acidity has the strongest negative linear correlation (r = -0.41).

### 6. Outlier Analysis

Boxplots were used to identify potential outliers and examine the spread of the numerical variables.

**Method used:**

```python
sns.boxplot(data=df.drop(columns=["quality", "Id"]))
```

Potential extreme observations were observed across several variables, particularly the sulfur dioxide measurements.

### 7. Quality and Physicochemical Features

Boxplots were used to compare selected physicochemical features across wine quality levels.

The following relationships were examined:

* Alcohol vs. wine quality
* Volatile acidity vs. wine quality
* Sulphates vs. wine quality
* Citric acid vs. wine quality
* Density vs. wine quality

**Example:**

```python
sns.boxplot(data=df, x="quality", y="alcohol")
```

These comparisons provide a visual perspective on the relationships identified through the correlation analysis.

## Key Findings

* Wine quality scores are mainly concentrated around 5 and 6.
* Alcohol has the strongest positive linear correlation with wine quality (r = 0.48).
* Volatile acidity has the strongest negative linear correlation with wine quality (r = -0.41).
* Sulphates and citric acid show weaker positive correlations with quality.
* Density has a weak negative correlation with quality.
* Several numerical variables show right-skewed distributions and potential outliers.
* No missing values or duplicate rows were identified.

## Project Structure

```text
wine-quality-eda/
│
├── Wine_Quality_EDA.ipynb
└── README.md
```

## Disclaimer

Correlation does not imply causation. The findings from this exploratory analysis describe patterns in the dataset and do not establish causal relationships.
