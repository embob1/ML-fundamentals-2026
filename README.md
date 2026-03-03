# Machine Learning Foundations – Assignment 1  
## Data Preparation and Pipeline Design  
UCI Bank Marketing Dataset (bank-additional.csv)

---

## Objective

The goal of this assignment is to design a clean and leakage-free data preparation pipeline to predict whether a client subscribes to a term deposit.

The emphasis is not on maximizing performance, but on:
- Correct task ordering
- Avoiding data leakage
- Justifying preprocessing decisions
- Demonstrating proper ML pipeline discipline

---

## Dataset

- Dataset: **bank-additional.csv**
- Observations: 4,119
- Features: 21
- Target variable: `y` (yes / no)

The dataset contains demographic, financial, campaign-related, and macroeconomic variables.

---

## Pipeline Steps

### 1. Target Identification
- `y` selected as prediction target.
- Justified based on marketing campaign objective.

### 2. Exploratory Data Analysis
- Identified categorical and numerical variables.
- Checked class imbalance (~89% no / ~11% yes).
- Detected implicit missing values (`"unknown"`).
- No explicit NaN values found.

### 3. Stratified Data Splitting
- 60% Training
- 20% Validation
- 20% Test
- Stratified split performed before preprocessing to prevent leakage.

### 4. Data Leakage Prevention
- Removed `duration` variable because it is not available at prediction time.

### 5. Encoding
- Applied One-Hot Encoding to categorical variables.
- Encoder fitted only on the training set.

### 6. Feature Scaling
- Applied StandardScaler to numerical variables.
- Scaler fitted only on the training set.

### 7. Class Imbalance Handling
- Used Logistic Regression with `class_weight="balanced"`.

### 8. Logistic Regression (Sanity Check)
- Model trained on processed training data.
- Evaluated on validation set.

---

## Validation Results

| Model | Accuracy | Recall (Yes) |
|-------|----------|--------------|
| Zero Rule | ~89% | 0% |
| Logistic Regression | ~83.6% | 60% |

Although the Zero Rule baseline achieves higher accuracy, it fails to detect subscribers.  
The Logistic Regression model improves minority class detection significantly.

---

## Key Principle

All transformations that learn parameters (encoding and scaling) were fitted only on the training set to prevent data leakage.

---

## Reproducibility

Run the notebook using:

Runtime → Restart runtime → Run all

The dataset is downloaded programmatically, so no manual upload is required.
