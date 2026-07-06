# Laptop Price Prediction using Linear Regression & Regularization

## Project Overview

This project focuses on predicting laptop prices using various Linear Regression models while exploring the impact of regularization techniques.

Rather than simply fitting a regression model, the project follows a complete Machine Learning workflow including:

- Data Cleaning
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Feature Selection
- Feature Scaling
- Linear Regression
- Ridge Regression
- Lasso Regression
- Model Evaluation & Comparison

The objective was to understand **when and why regularization improves Linear Regression** on a real-world dataset containing laptop specifications.

---

# Dataset

### Shape

- **Rows:** 893
- **Columns:** 16

### Target Variable

- **Price**

### Data Quality

- No Missing Values
- No Duplicate Values

---

# Data Cleaning

The dataset required several preprocessing steps before modeling.

### Operating System

Grouped operating systems into common categories.

```
Windows
Mac
Android
Chrome
Ubuntu
DOS
Others
```

### RAM

Converted RAM values from strings to integers.

Example

```
8GB → 8
16GB → 16
```

### Storage

Converted storage capacities into numerical values.

| Original | Converted |
|----------|----------:|
| 32GB | 32 |
| 64GB | 64 |
| 128GB | 128 |
| 256GB | 256 |
| 512GB | 512 |
| 1TB | 1024 |
| 2TB | 2048 |

Standardized storage type

```
Hard-Disk → HDD
```

---

# Feature Engineering

Several new features were extracted from raw text columns.

## Processor

Extracted:

- Processor Brand
- Processor Family
- CPU Generation

Example

```
12th Gen Intel Core i5 1235U
```

↓

```
Generation = 12
Brand = Intel
Family = Core i5
```

---

## CPU Specifications

Extracted

- CPU Cores
- Threads
- Performance Cores
- Efficiency Cores

Example

```
12 Cores (4P + 8E), 16 Threads
```

↓

```
Cores = 12
Performance Cores = 4
Efficiency Cores = 8
Threads = 16
```

---

## GPU

Extracted

- GPU Brand
- GPU Series

GPU Series

```
RTX
GTX
Radeon
Integrated
Iris
Others
```

---

## Display

Created a new feature

### Pixels Per Inch (PPI)

```
PPI = √(Width² + Height²) / Display Size
```

PPI was added to better represent display quality than resolution alone.

---

## Gaming Laptop

Created a binary feature indicating whether a laptop contains a dedicated gaming GPU.

```
0 = Non Gaming
1 = Gaming
```

---

# Exploratory Data Analysis

Performed

- Univariate Analysis
- Correlation Analysis
- Outlier Detection
- Feature Importance Exploration

### Key Findings

- RAM, CPU Threads and CPU Cores showed the strongest correlation with laptop price.
- Gaming laptops have significantly higher average prices.
- SSD laptops are considerably more expensive than HDD laptops.
- Apple laptops have the highest average selling price.
- Premium processor families (Core i9, Ryzen 9) are associated with higher prices.
- Laptop prices exhibit a right-skewed distribution.

---

# Models Used

- Linear Regression
- Ridge Regression
- Lasso Regression
- LassoCV

---

# Model Performance

| Model | Train MSE | Test MSE | R² Score |
|-----------------------|----------:|----------:|---------:|
| Linear Regression | 0.0293 | 0.0362 | 0.8954 |
| Ridge Regression | **0.0295** | **0.0314** | **0.9092** |
| LassoCV | 0.0326 | 0.0320 | 0.9075 |

---

# Regularization Analysis

The project also investigates how different regularization techniques behave.

### Linear Regression

- Strong baseline performance.
- Sensitive to multicollinearity.

### Ridge Regression

- Shrinks coefficients.
- Handles correlated features effectively.
- Produced the best generalization performance.

### Lasso Regression

- Performs automatic feature selection.
- Removed **32 out of 91 engineered features** (~35%).
- Produced a simpler model while maintaining competitive performance.

---

# Key Learnings

This project demonstrates:

- Complete regression workflow on a real-world dataset.
- Importance of feature engineering.
- Effect of multicollinearity on Linear Regression.
- Difference between Ridge and Lasso regularization.
- Importance of hyperparameter tuning (`alpha`).
- Model comparison using Train/Test MSE and R² Score.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

- Feature importance analysis using SHAP
- Ensemble Regression Models
- Model deployment using Flask/Streamlit
