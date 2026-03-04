# Machine Learning Foundations – Assignment 1  
## Data Preparation Pipeline (UCI Bank Marketing)

---

## Overview

This project implements a leakage-free data preparation pipeline to predict whether a client subscribes to a term deposit using the **bank-additional.csv** dataset (4,119 observations, 21 features).

The focus is on correct task ordering, preprocessing justification, and avoiding data leakage — not maximizing model performance.

---

## Pipeline Summary

- Identified `y` as target variable.
- Performed exploratory data analysis and detected class imbalance (~89% no / ~11% yes).
- Split data into 60% train, 20% validation, 20% test (stratified).
- Removed `duration` to prevent data leakage.
- Applied One-Hot Encoding (fitted on training set only).
- Scaled numerical features using StandardScaler (training set only).
- Trained Logistic Regression with `class_weight="balanced"` as a sanity check.

---

## Validation Results

| Model | Accuracy | Recall (Yes) |
|-------|----------|--------------|
| Zero Rule | ~89% | 0% |
| Logistic Regression | ~83.6% | 60% |

Although accuracy decreases slightly, the model substantially improves detection of the minority class.

---

## Key Principle

All preprocessing steps that learn parameters were fitted exclusively on the training set to ensure unbiased evaluation.

---

## Reproducibility

Run the notebook from top to bottom:

Runtime → Restart runtime → Run all

The dataset is downloaded programmatically.
