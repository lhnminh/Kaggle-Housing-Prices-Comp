# 🏠 Kaggle Housing Price Prediction 

This project builds an end-to-end machine learning pipeline to predict house sale prices using the **Ames Housing dataset**.  
The workflow covers data loading, preprocessing, feature engineering, model training, and submission file generation for Kaggle.

The model is built **from scratch using scikit-learn pipelines and XGBoost**, with proper handling of missing values and categorical variables.

---

## 📁 Project Structure

```
.
├── housing-price-comp-from-scratch.ipynb
├── submission.csv
└── README.md
```

---

## 📊 Dataset

Data comes from Kaggle’s **Home Data for ML Course**:

- `train.csv` – training data with target variable `SalePrice`
- `test.csv` – test data without target

The data is loaded from the Kaggle input directory:

```
/kaggle/input/home-data-for-ml-course/
```

---

## ⚙️ Workflow Overview

### 1. Data Loading
- Load train and test datasets using `pandas`
- Drop rows with missing target values
- Separate predictors and target variable

---

### 2. Train/Validation Split
- 80/20 split using `train_test_split`
- Random seed fixed for reproducibility

---

### 3. Feature Selection
- **Categorical features**: object columns with < 10 unique values
- **Numerical features**: int and float columns
- Only selected features are used in modeling

---

### 4. Preprocessing Pipeline

#### Numerical Features
- Missing values filled with constant values

#### Categorical Features
- Missing values filled with most frequent value
- One-hot encoded
- Unknown categories handled safely

Implemented using `ColumnTransformer` and `Pipeline`.

---

### 5. Model

- **Model**: `XGBRegressor`
- **Parameters**:
  - `n_estimators = 1000`
  - `learning_rate = 0.05`
  - `random_state = 0`

The model is trained as part of a single pipeline:

```
Preprocessing → XGBoost Regression
```

---

### 6. Prediction & Submission

- Predictions generated on test set
- Output saved as `submission.csv` in Kaggle-compatible format

Example:
```csv
Id,SalePrice
1461,123456.78
1462,234567.89
```

---

## 🚀 How to Run

### Option 1: Kaggle Notebook (Recommended)

1. Upload the notebook to Kaggle
2. Attach the dataset
3. Run all cells
4. Download `submission.csv`

---

### Option 2: Local Run (Advanced)

Install dependencies:
```bash
pip install pandas numpy scikit-learn xgboost
```

Adjust file paths to point to your local dataset.

---

## 🧠 Key Concepts Demonstrated

- End-to-end ML pipeline design
- Feature selection by data type & cardinality
- Missing value imputation
- One-hot encoding with unknown categories
- XGBoost regression
- Reproducible training setup
- Kaggle submission workflow

---

## 📈 Next Improvements

- Hyperparameter tuning (GridSearchCV / Optuna)
- Cross-validation
- Feature importance analysis
- Log-transform of target variable
- Refactor into reusable modules
- Add unit tests
- Experiment with LightGBM / CatBoost

---

## ✍️ Author

**Morgan**  
Incoming Master’s in Data Science  
Interests: Data Engineering, MLOps, Machine Learning Systems
