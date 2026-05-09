# DDoS Attack Detection Using Machine Learning

A machine learning pipeline that detects DDoS attacks in real network traffic using the CICIDS2017 dataset. Built as part of a cybersecurity and AI course at Montclair State University.

## What It Does

Analyzes network connections and classifies them as either a DDoS attack or normal traffic. Every row in the dataset represents one real network connection with 79 measured features like packet size, flow duration, and timing intervals.

## Dataset

**CICIDS2017** — Canadian Institute for Cybersecurity Intrusion Detection System Dataset  
225,745 real network connections labeled as DDoS or BENIGN.

## Models Trained and Compared

| Model | Accuracy | Attacks Missed | False Alarms |
|---|---|---|---|
| Random Forest | 99.99% | 4 | 0 |
| XGBoost | 100.00% | 0 | 1 |
| MLP Neural Network | 99.96% | 14 | 4 |
| Voting Ensemble | 99.99% | 3 | 0 |

**Winner: XGBoost** with 100% accuracy and zero missed attacks.

## Pipeline

1. Data loading and exploration
2. Preprocessing — removed infinite values, encoded labels
3. Exploratory Data Analysis — class distribution, feature variance
4. Feature Engineering — reduced 78 features to 65 using variance filtering and Random Forest importance scoring
5. Train-Test Split — 80% training, 20% testing with StandardScaler
6. Model Training — Random Forest, XGBoost, MLP, Voting Ensemble
7. Evaluation — classification report, confusion matrix per model
8. Comparison — accuracy and F1-score across all four models

## Tech Stack

- Python
- pandas, numpy
- scikit-learn
- XGBoost
- matplotlib, seaborn
- Google Colab

## Key Result

XGBoost caught every single DDoS attack in the test set with only one false alarm out of 45,143 predictions. In cybersecurity, recall is the critical metric — a missed attack means a hacker gets through undetected. This system would have a near-zero miss rate on real network traffic.

## Author

Nicolas Hoyos — CSIT 365, Montclair State University, April 2026
