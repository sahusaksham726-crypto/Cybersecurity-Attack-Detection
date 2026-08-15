Cyber Security Attack Detection

A machine learning project for detecting benign vs. attack network traffic using a cybersecurity dataset containing network, protocol, traffic-volume, user-agent, URL, and attack-related information.

Project Objective

The objective is to build and compare three supervised machine-learning models for cybersecurity attack detection and to study the effect of missing URL information.

Dataset

File: cyber security data.csv

Total records: 10,000

Total columns: 13

Target: label

0 = Benign

1 = Attack

URL available: 6,768

URL missing: 3,232

The missing URLs were not artificially filled because the URL values are mostly unique and there was no reliable relationship for reconstructing the original URLs.

Project Workflow

Data loading and inspection

Data cleaning and missing-value analysis

Exploratory Data Analysis (EDA)

Visualization

Feature engineering

Model A training and testing

Model B training and testing

Model C training and testing

Model comparison

Final model selection

Exploratory Data Analysis

The EDA includes:

Benign vs Attack traffic

Attack type distribution

Protocol distribution

Internal vs External traffic

Attack distribution by protocol

Bytes sent distribution

Bytes received distribution

Bytes sent vs Bytes received

Correlation heatmap

Graphs are stored in the graphs/ folder.

Model A — Complete Dataset

Model A uses all 10,000 records and does not use the URL as a feature, allowing prediction even when a URL is unavailable.

Metric

Score

Accuracy

71.75%

Precision

9.52%

Recall

71.25%

F1 Score

16.79%

ROC-AUC

81.18%

Model B — URL Available

Model B uses the 6,768 records where URL information is available.

URL-derived features include URL length, dots, slashes, hyphens, underscores, special characters, digits, letters, HTTP/HTTPS indicators, query, fragment, and IP-address indicators.

Metric

Score

Accuracy

74.37%

Precision

9.19%

Recall

61.11%

F1 Score

15.98%

ROC-AUC

77.38%

Model C — URL Missing

Model C uses the 3,232 records where the URL is missing. No URL-derived features are used.

It relies on network and traffic features such as source/destination ports, protocol, bytes sent/received, user agent, internal traffic, and time-based features.

Metric

Score

Accuracy

75.12%

Precision

10.06%

Recall

65.38%

F1 Score

17.44%

ROC-AUC

79.50%

Final Model Comparison

Model

Rows

Accuracy

Precision

Recall

F1 Score

ROC-AUC

Model A

10,000

71.75%

9.52%

71.25%

16.79%

81.18%

Model B

6,768

74.37%

9.19%

61.11%

15.98%

77.38%

Model C

3,232

75.12%

10.06%

65.38%

17.44%

79.50%

Conclusion

Model C has the highest accuracy, precision, and F1 score, while Model A has the highest recall and ROC-AUC.

For a cybersecurity system where detecting as many attacks as possible is the main priority, Model A's higher recall is important. Model C performs strongly on records where the URL is unavailable. Model B provides a URL-aware approach when URL information exists.

Project Structure

Cyber Security Project/
│
├── cyber security data.csv
├── Cybersecurity_EDA.ipynb
├── Cybersecurity_Model_A.ipynb
├── Cybersecurity_Model_B.ipynb
├── Cybersecurity_Model_C.ipynb
├── Cybersecurity_Final_Model_Comparison.ipynb
│
├── model_A.pkl
├── model_B.pkl
├── model_C.pkl
├── model_comparison_results.csv
├── model_ranking_results.csv
│
└── graphs/
    ├── 01_benign_vs_attack.png
    ├── 02_benign_vs_attack_pie.png
    ├── 03_attack_type_distribution.png
    ├── 04_protocol_distribution.png
    ├── 05_internal_vs_external.png
    ├── 06_attack_by_protocol.png
    ├── 07_bytes_sent_distribution.png
    ├── 08_bytes_received_distribution.png
    ├── 09_bytes_sent_vs_received.png
    ├── 10_correlation_heatmap.png
    ├── final_accuracy_comparison.png
    ├── final_precision_comparison.png
    ├── final_recall_comparison.png
    ├── final_f1_comparison.png
    ├── final_roc_auc_comparison.png
    └── final_overall_model_comparison.png

Technologies Used

Python

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn

Joblib

Jupyter Notebook

Key Learning Outcomes

Cybersecurity dataset analysis

Data cleaning and missing-value investigation

Exploratory Data Analysis

Data visualization

Feature engineering

Classification modelling

Imbalanced classification evaluation

Train/test splitting

Model comparison

Saving trained ML models with .pkl

Future Improvements

Hyperparameter tuning

Cross-validation

Better class-imbalance handling

Feature-importance analysis

Threshold optimization

Advanced classifiers such as XGBoost

Real-time network traffic prediction

Deployment with Flask, FastAPI, or Streamlit

Author

Saksham Sahu

B.Tech CSE | Data Science Enthusiast