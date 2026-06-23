# DDoS Attack Detection Using Machine Learning

A machine learning pipeline that detects DDoS attacks in network traffic using the CICIDS2017 dataset. It trains and compares four models and identifies the strongest performer for catching attacks with a near zero miss rate.

## What it does

The pipeline analyzes network connections and classifies each one as a DDoS attack or normal traffic. Every row in the dataset is one real network connection described by 79 measured features such as packet size, flow duration, and timing intervals.

## Dataset

The project uses CICIDS2017, the intrusion detection dataset from the Canadian Institute for Cybersecurity. The Friday DDoS capture used here contains 225,711 labeled connections (DDoS or BENIGN).

The dataset is not stored in this repository because it is large and freely available from the source. Download it and place the CSV in the same folder as the notebook:

- Official dataset: https://www.unb.ca/cic/datasets/ids-2017.html
- File used: Friday-WorkingHours-Afternoon-DDos.pcap_ISCX.csv (found inside MachineLearningCSV.zip)

## Models trained and compared

| Model | Accuracy | Attacks missed | False alarms |
| --- | --- | --- | --- |
| Random Forest | 99.99% | 4 | 0 |
| XGBoost | 100.00% | 0 | 1 |
| MLP Neural Network | 99.96% | 14 | 4 |
| Voting Ensemble | 99.99% | 3 | 0 |

XGBoost was the strongest, with 100% accuracy and zero missed attacks.

## Pipeline

1. Data loading and exploration
2. Preprocessing: remove infinite values and encode labels
3. Exploratory analysis: class distribution and feature variance
4. Feature engineering: reduce 78 features to 65 using variance filtering and Random Forest importance
5. Train and test split: 80% training, 20% testing, with feature scaling
6. Model training: Random Forest, XGBoost, MLP, and a Voting Ensemble
7. Evaluation: classification report and confusion matrix per model
8. Comparison: accuracy and F1 score across all four models

## Tech stack

Python with pandas and numpy for data handling, scikit-learn and XGBoost for modeling, and matplotlib and seaborn for visualization. Built in a Jupyter and Colab compatible notebook.

## Key result

XGBoost caught every DDoS attack in the test set, with only one false alarm out of 45,143 predictions. In security work, recall is the metric that matters most, because a missed attack means an intrusion goes undetected. This pipeline reaches a near zero miss rate on the test data.

## Running it

1. Download the dataset CSV (see Dataset above) and place it next to the notebook.
2. Open ddos_detection.ipynb in Jupyter or Google Colab.
3. Run the cells from top to bottom.

## Author

Nicolas Hoyos
