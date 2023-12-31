# Module 12 Report Template
_Bootcamp: UPENN-VIRT-DATA-PT-06-2023-U-LOLC-MTTH Module 20 Challenge_

## Overview of the Analysis

This analysis uses a dataset of historical lending activity from a peer-to-peer lending services company to build a model that can identify the creditworthiness of borrowers.
The data contains points on 77,536 loans, with information about the size of the loan, interest rate, borrower income, debt-to-income ratio, number of accounts, derogatory remarks, and total debt.
It also includes whether the loan has been flagged as either "healthy" or "high-risk."
This is the value we are attempting to predict.

To do this, we split the data into training and test buckets using `sklearn`'s `train_test_split` module.
We then run a Logistic Regression Model, again using modules from `sklearn`.
The results of the model, fitted to the training data and tested on the test data, are outputted in a confusion matrix and classification report.

Of the 77,536 pieces of data, 75,036 (95%) are pre-categorized as healthy loans. because of this, a resampling was conducted using `imbalanced learning`'s `RandomOverSampler`.
This resampling allowed for a new regression model that, when fit with the resampled test data, provided greater recall for "high-risk" loans.

## Results

* Train_Test_Split model results:
  * Balanced Accuracy Score: 0.952
  * Precision (Weighted Avg): 0.99
  * Recall (Weighted Avg): 0.99
  * F1-Score (Weighted Avg): 0.99
  * Accuracy: 0.99


* RandomOverSampler model results:
  * Balanced Accuracy Score: 0.994
  * Precision (Weighted Avg): 0.99
  * Recall (Weighted Avg): 0.99
  * F1-Score (Weighted Avg): 0.99
  * Accuracy: 0.99

## Summary

While the original sampling provided excellent precision and recall for healthy loan (`0`) predictions, it was less accurate in predicting high-risk loans (`1`). 
Using `RandomOverSampler` keeps the accuracy for predicting healthy loans while increasing the recall of high-risk loan predictions at a slight cost to precision. 
The restulting f1-score is would imply that this is a good tradeoff.

It is recommended to use the `RandomOverSampler` if the risk of incorrectly categorizing a loan as healthy outweighs the risk of miscategorizing an unhealthy loan.
While the `RandomOverSampler` model is more performant in this regard, the original model also performs fairly well.

---

## Requirements
Files in this repo were made using the following package and program versions:
- Python 3.10
- Jupyter 1.0.0
- Pandas 1.5.3
- Scikit-Learn 1.2.2
- Imbalanced-Learn 0.11.0

## Installation
Clone this repo: `git clone https://github.com/4a6166/credit-risk-classification`

## Credits
Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.

## License
[MIT License](LICENSE)
