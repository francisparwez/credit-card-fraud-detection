# Credit Card Fraud Detection — Stakeholder Report

## Executive Summary

The goal of this project was to build a fraud detection model for a highly imbalanced credit card transaction dataset.

The dataset contains 284,807 transactions, but only 492 are fraudulent, meaning fraud represents approximately 0.17% of all transactions.

A tuned XGBoost model was selected after comparing Logistic Regression and XGBoost using stratified cross-validation.

The final operating threshold was selected using illustrative business costs that treated a missed fraud as 100 cost units and an incorrectly blocked legitimate transaction as 5 cost units.

## Final Model

The selected model is a tuned XGBoost classifier using:

- `n_estimators = 200`
- `max_depth = 4`
- `learning_rate = 0.1`
- `subsample = 1.0`
- `colsample_bytree = 0.8`

The selected classification threshold is:

**0.5200**

The threshold was selected using out-of-fold predictions from the training data. The test set was not used during threshold selection.

## Final Test Results

| Metric              | Result |
| ------------------- | -----: |
| Precision           | 0.6058 |
| Recall              | 0.8469 |
| F1-score            | 0.7064 |
| ROC-AUC             | 0.9812 |
| PR-AUC              | 0.8549 |
| False Positives     |     54 |
| False Negatives     |     15 |
| Total Business Cost |   1770 |

## Business Interpretation

The model identified a large proportion of fraudulent transactions, with a recall of 0.8469.

There were 15 missed fraudulent transactions on the test set. Under the selected cost assumptions, each missed fraud carries a much higher cost than an incorrectly blocked legitimate transaction.

The model also produced 54 false positives. These represent legitimate transactions that would have been incorrectly flagged.

The total business cost was 1770 cost units under the illustrative cost assumptions.

The selected threshold therefore represents a trade-off between catching fraud and reducing the number of legitimate customers incorrectly flagged.

## Why Accuracy Was Not Used as the Main Metric

A model that predicts every transaction as legitimate would achieve approximately 99.83% accuracy because fraud is extremely rare.

However, that model would detect no fraud.

For this reason, precision, recall, F1-score and especially PR-AUC were used to evaluate the fraud detection models.

## Key Findings

Class weighting performed best among the three imbalance strategies tested.

XGBoost performed better overall than Logistic Regression.

Hyperparameter tuning improved XGBoost PR-AUC from 0.8033 to 0.8345 in cross-validation.

Threshold tuning showed that the operating point should be selected based on the relative cost of missed fraud and false positive alerts rather than automatically using a threshold of 0.50.

## Limitations

The business costs used in this project are illustrative and should not be treated as actual financial estimates.

The dataset contains anonymized features, so the model cannot provide direct business explanations for why an individual transaction was identified as suspicious.

The transaction patterns in the historical dataset may change over time.

A production fraud detection system would require ongoing monitoring, threshold review and model retraining.

## Recommendation

The tuned XGBoost model is the strongest candidate from this analysis.

The selected threshold of 0.5200 provides a practical starting point under the assumed business costs.

Before production use, the cost assumptions should be replaced with real financial and operational estimates, and the model should be monitored for changes in fraud patterns and false positive rates.
