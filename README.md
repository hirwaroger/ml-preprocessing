# Data Preprocessing for Housing Dataset

## RP Tumba College - Machine Learning Level 8
### Individual Assignment - Learning Outcome 1

**Author:** IZERE HIRWA Roger  

---

## Project Overview

This project performs a complete data preprocessing workflow on the `Housing.xls` dataset to prepare it for machine learning modeling. The preprocessing pipeline includes statistical analysis, missing value imputation, duplicate handling, inconsistency cleaning, outlier treatment, feature scaling, and categorical encoding.

---

## Repository Structure

```
mlassignment/
│
├── Housing.xls                    # Original dataset
├── house_preprocessing.ipynb      # Main Jupyter notebook with all preprocessing steps
├── README.md                      # Project documentation (this file)
│
├── Output Files (generated after running notebook):
│   ├── house_cleaned_final.csv    # Final preprocessed dataset (scaled + one-hot encoded)
│   ├── house_cleaned_unscaled.csv # Cleaned dataset without scaling
│   ├── house_label_encoded.csv    # Dataset with label encoding
│   ├── house_onehot_encoded.csv   # Dataset with one-hot encoding
│   ├── house_binary_encoded.csv   # Dataset with binary encoding
│   │
│   └── Visualizations:
│       ├── numerical_distributions.png
│       ├── missing_values.png
│       ├── missing_heatmap.png
│       ├── outlier_boxplots.png
│       ├── outlier_boxplots_after.png
│       └── scaling_comparison.png
```

---

## Dataset Description

The Housing dataset contains information about house properties and their prices with the following features:

| Column | Description | Type |
|--------|-------------|------|
| `price` | House price (Target variable) | Numerical |
| `area` | Area in square feet | Numerical |
| `bedrooms` | Number of bedrooms | Numerical |
| `bathrooms` | Number of bathrooms | Numerical |
| `stories` | Number of stories | Numerical |
| `mainroad` | Connected to main road (yes/no) | Categorical |
| `guestroom` | Has guest room (yes/no) | Categorical |
| `basement` | Has basement (yes/no) | Categorical |
| `hotwaterheating` | Has hot water heating (yes/no) | Categorical |
| `airconditioning` | Has air conditioning (yes/no) | Categorical |
| `parking` | Number of parking spaces | Numerical |
| `prefarea` | In preferred area (yes/no) | Categorical |
| `furnishingstatus` | Furnishing status (furnished/semi-furnished/unfurnished) | Categorical |

---

## Preprocessing Steps Performed

### 1. Statistical Summary of Numerical Variables
- Generated comprehensive statistics (mean, median, std, percentiles, skewness, kurtosis)
- Visualized distributions with histograms
- Interpreted data characteristics

### 2. Handling Missing Values
- Detected missing values across all columns
- Applied appropriate imputation techniques:
  - **Mean** for symmetric distributions
  - **Median** for skewed distributions
  - **Mode** for categorical variables

### 3. Detecting and Handling Duplicate Records
- Identified duplicate rows
- Removed exact duplicates to ensure data quality

### 4. Detecting and Handling Data Inconsistency
- Checked for incorrect data types
- Standardized categorical values (lowercase, trimmed whitespace)
- Identified unrealistic values in numerical columns

### 5. Detecting and Handling Outliers
- Applied **IQR Method** and **Z-Score Method** for detection
- Visualized outliers using box plots
- Applied **Winsorization** (capping at 1st and 99th percentiles)

### 6. Normalization and Scaling
- Applied three scaling techniques:
  - **Min-Max Scaling** (range [0,1])
  - **Standardization** (Z-score, mean=0, std=1)
  - **Robust Scaling** (based on median and IQR)
- Selected Standardization as the primary method

### 7. Encoding Categorical Variables
Implemented and documented five encoding techniques:

| Encoding Method | Description | Best For |
|-----------------|-------------|----------|
| **Label Encoding** | Assigns integers to categories | Tree-based models, ordinal data |
| **One-Hot Encoding** | Creates binary columns for each category | Linear models, low cardinality |
| **Binary Encoding** | Converts to binary representation | High cardinality features |
| **Ordinal Encoding** | Assigns ordered integers | Ordered categorical data |
| **Target Encoding** | Uses target variable statistics | Supervised learning |

---

## How to Run

### Prerequisites

Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn category_encoders
```

### Running the Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/hirwaroger/ml-preprocessing.git
   cd mlassignment
   ```

2. Open Jupyter Notebook:
   ```bash
   jupyter notebook house_preprocessing.ipynb
   ```

3. Run all cells sequentially (Cell -> Run All)

4. Output files will be generated in the same directory

---

## Results Summary

| Metric | Before Preprocessing | After Preprocessing |
|--------|---------------------|---------------------|
| Total Rows | 545 | ~543 (after deduplication) |
| Missing Values | Multiple | 0 |
| Duplicates | Present | 0 |
| Outliers | Present | Winsorized |
| Scaling | Not applied | Standardized |
| Encoding | Categorical strings | Numerical |

---

## Key Learnings

1. **Missing Value Imputation**: Choosing between mean/median depends on data distribution
2. **Outlier Handling**: Winsorization preserves data points while reducing extreme value impact
3. **Scaling Selection**: Standardization is versatile for most ML algorithms
4. **Encoding Choice**: Depends on the algorithm and cardinality of categorical features

---

## Files Generated

| File | Description |
|------|-------------|
| `house_cleaned_final.csv` | Production-ready dataset (scaled + encoded) |
| `house_cleaned_unscaled.csv` | Cleaned but original scale preserved |
| `house_label_encoded.csv` | With label encoding applied |
| `house_onehot_encoded.csv` | With one-hot encoding applied |
| `house_binary_encoded.csv` | With binary encoding applied |

---

## Technologies Used

- **Python 3.x**
- **Pandas** - Data manipulation
- **NumPy** - Numerical operations
- **Matplotlib & Seaborn** - Visualizations
- **Scikit-learn** - Preprocessing & scaling
- **Category Encoders** - Advanced encoding techniques
- **SciPy** - Statistical functions

---

## References

1. Scikit-learn Documentation: https://scikit-learn.org/stable/
2. Category Encoders Documentation: https://contrib.scikit-learn.org/category_encoders/
3. Pandas Documentation: https://pandas.pydata.org/docs/

---

## License

This project is submitted as part of academic coursework at RP Tumba College.

---
