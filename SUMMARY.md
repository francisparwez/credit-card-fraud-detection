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

The first stage covers:

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

## Initial Finding

A model that predicts every transaction as legitimate achieves approximately 99.83% accuracy while detecting no fraudulent transactions.

This shows why accuracy alone is not suitable for evaluating fraud detection models.

## Current Files

- `notebooks/01_credit_card_fraud_detection.ipynb`
- `images/1_class_distribution.png`
- `images/2_class_distribution_percentage.png`
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
