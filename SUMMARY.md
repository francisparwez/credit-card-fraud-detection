# Credit Card Fraud Detection — Project Summary

## Project

Credit Card Fraud Detection: Tackling Class Imbalance with Resampling, Cost-Aware Metrics & Threshold Tuning

## Goal

Build a fraud detection workflow for a highly imbalanced credit card transaction dataset.

The project will focus on handling class imbalance correctly, comparing classification models, and selecting a decision threshold based on business costs.

## Dataset

- 284,807 transactions
- 31 columns
- 284,315 legitimate transactions
- 492 fraudulent transactions
- Fraud rate: approximately 0.17%

## Current Stage

### 01 — Data Audit & Class Imbalance Baseline

✅ Complete

The first stage covered:

- dataset inspection
- data quality checks
- class distribution
- fraud rate calculation
- naive baseline
- why accuracy is misleading
- precision
- recall
- F1-score
- ROC-AUC
- PR-AUC

### 02 — Leakage-Safe Preprocessing & Pipeline Setup

✅ Complete

The second stage covered:

- feature and target separation
- stratified train-test split
- verification of class proportions
- preprocessing pipeline setup
- imbalanced-learn pipeline setup
- leakage prevention
- keeping the test data untouched

### 03 — Imbalance Strategy Comparison

✅ Complete

The third stage compared:

- class weighting
- random undersampling
- SMOTE oversampling

All three approaches used Logistic Regression and were evaluated using stratified 5-fold cross-validation.

The evaluation metrics were:

- precision
- recall
- F1-score
- ROC-AUC
- PR-AUC

## Initial Finding

A model that predicts every transaction as legitimate achieves approximately 99.83% accuracy while detecting no fraudulent transactions.

This shows why accuracy alone is not suitable for evaluating fraud detection models.

## Part 02 Finding

The dataset was split into training and test sets using stratification so that the rare fraud class remained represented at approximately the same rate in both sets.

Preprocessing was placed inside a pipeline, and an imbalanced-learn pipeline was introduced so that future resampling methods can be applied only to training data during cross-validation.

## Part 03 Finding

The three imbalance strategies produced different precision, recall, F1-score, ROC-AUC and PR-AUC results.

The comparison showed the trade-off between detecting more fraudulent transactions and generating more false positive alerts.

PR-AUC was given particular attention because fraud represents only 0.17% of the dataset.

The strongest strategy at this stage was class weighting.

Class weighting achieved the highest precision, F1-score, ROC-AUC and PR-AUC across the three strategies, while SMOTE achieved the highest recall.

This shows that the strategies produce different trade-offs between catching more fraud and limiting false positive predictions.

## Current Files

- `notebooks/01_credit_card_fraud_detection.ipynb`
- `images/1_class_distribution.png`
- `images/2_class_distribution_percentage.png`
- `images/3_imbalance_strategy_comparison.png`
- `images/4_pr_auc_by_strategy.png`
- `README.md`
- `SUMMARY.md`
- `requirements.txt`
- `.gitignore`

## Planned Stages

1. Data Audit & Class Imbalance Baseline
2. Leakage-Safe Preprocessing & Pipeline Setup
3. Imbalance Strategy Comparison
4. Model Family Comparison
5. Cross-Validation & Model Tuning
6. Threshold Tuning & Business Cost Analysis
7. Final Model Evaluation & Stakeholder Reporting
