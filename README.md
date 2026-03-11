# 💳 Credit Card Fraud Detection

A machine learning project to detect fraudulent credit card transactions using Random Forest Classifier.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Latest-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Latest-green.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Model Performance](#model-performance)
- [Project Structure](#project-structure)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

---

## 🔍 Overview

This project implements a **Random Forest Classifier** to identify fraudulent credit card transactions. The dataset contains transactions made by European cardholders in September 2013, with features transformed using PCA (Principal Component Analysis) for confidentiality.

### Key Highlights:
- ⚡ Handles highly imbalanced dataset (fraud cases: ~0.17%)
- 🎯 Achieves high accuracy with ensemble learning
- 📊 Comprehensive data visualization and analysis
- 🔒 No confidential data exposed (PCA-transformed features)

---

## 📊 Dataset

| Property | Value |
|----------|-------|
| **Source** | [Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) |
| **Total Transactions** | 284,807 |
| **Features** | 30 (V1-V28, Time, Amount) |
| **Target Variable** | Class (0 = Valid, 1 = Fraud) |
| **Fraud Cases** | 492 (~0.172%) |
| **Valid Cases** | 284,315 (~99.828%) |

### Feature Description:
- **V1-V28**: PCA-transformed numerical features (confidential)
- **Time**: Seconds elapsed between transaction and first transaction
- **Amount**: Transaction amount
- **Class**: Target variable (1 = Fraud, 0 = Valid)

---

## ✨ Features

- ✅ **Data Preprocessing**: Load and explore credit card transaction data
- ✅ **Exploratory Data Analysis**: Statistical analysis and correlation visualization
- ✅ **Imbalanced Data Handling**: Strategies for dealing with rare fraud cases
- ✅ **Random Forest Classification**: Ensemble learning for robust predictions
- ✅ **Comprehensive Metrics**: Accuracy, Precision, Recall, F1-Score, MCC
- ✅ **Confusion Matrix**: Visual evaluation of model performance
- ✅ **Visualization**: Heatmaps and statistical charts using Seaborn & Matplotlib

---

## 🛠️ Installation

### Prerequisites

```bash
Python 3.8 or higher
pip package manager
Step 1: Clone the Repository
bash
Copy
git clone https://github.com/yourusername/credit-card-fraud-detection.git
cd credit-card-fraud-detection
Step 2: Create Virtual Environment (Recommended)
bash
Copy
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
Step 3: Install Dependencies
bash
Copy
pip install numpy pandas matplotlib seaborn scikit-learn
Or install from requirements file:
bash
Copy
pip install -r requirements.txt
Requirements File (requirements.txt)
plain
Copy
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
🚀 Usage
1. Prepare the Dataset
Download the creditcard.csv dataset from Kaggle and place it in your project directory.
2. Run the Analysis
Python
Copy
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt 
import seaborn as sns 
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, matthews_corrcoef, confusion_matrix
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

# Load dataset
data = pd.read_csv("creditcard.csv")

# Quick overview
print(data.shape)  # (284807, 31)
print(data.describe())

# Check fraud vs valid distribution
fraud = data[data['Class'] == 1] 
valid = data[data['Class'] == 0] 
print(f'Fraud Cases: {len(fraud)}')
print(f'Valid Transactions: {len(valid)}')
3. Train the Model
Python
Copy
# Prepare features and target
X = data.drop(['Class'], axis=1) 
Y = data["Class"]

# Split data (80% train, 20% test)
xTrain, xTest, yTrain, yTest = train_test_split(
    X.values, Y.values, test_size=0.2, random_state=42
)

# Create and train Random Forest Classifier
rfc = RandomForestClassifier()
rfc.fit(xTrain, yTrain)

# Make predictions
yPred = rfc.predict(xTest)
4. Evaluate Performance
Python
Copy
# Calculate metrics
acc = accuracy_score(yTest, yPred)
prec = precision_score(yTest, yPred)
rec = recall_score(yTest, yPred)
f1 = f1_score(yTest, yPred)
mcc = matthews_corrcoef(yTest, yPred)

print(f"Accuracy: {acc}")
print(f"Precision: {prec}")
print(f"Recall: {rec}")
print(f"F1-Score: {f1}")
print(f"Matthews Correlation Coefficient: {mcc}")

# Confusion Matrix
cm = confusion_matrix(yTest, yPred)
print(cm)
📈 Model Performance
Table
Metric	Description
Accuracy	Overall correctness of predictions
Precision	Ratio of true frauds to predicted frauds
Recall	Ratio of detected frauds to actual frauds
F1-Score	Harmonic mean of Precision and Recall
MCC	Matthews Correlation Coefficient (balanced measure)
Why Random Forest?
🌲 Ensemble Learning: Combines multiple decision trees for better accuracy
🎯 Feature Importance: Automatically ranks feature significance
🛡️ Robust to Outliers: Handles extreme values well
⚖️ Handles Imbalance: Effective with skewed datasets
🚀 Parallel Processing: Fast training and prediction
📁 Project Structure
plain
Copy
credit-card-fraud-detection/
├── creditcard.csv              # Dataset (not included in repo)
├── fraud_detection.py          # Main analysis script
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
└── results/                    # Output directory
    ├── correlation_heatmap.png
    └── confusion_matrix.png
📊 Results & Visualizations
Correlation Matrix
Visualize relationships between PCA features using Seaborn heatmap:
Python
Copy
corrmat = data.corr() 
fig = plt.figure(figsize=(12, 9)) 
sns.heatmap(corrmat, vmax=.8, square=True) 
plt.show()
Key Findings
Table
Finding	Insight
Class Imbalance	Fraud cases represent only 0.172% of data
Amount Distribution	Fraudulent transactions show different amount patterns
PCA Features	V1-V28 are uncorrelated (by design)
Time Feature	Seconds from first transaction, useful for temporal analysis
🤝 Contributing
Contributions are welcome! Please follow these steps:
Fork the repository
Create a feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request
Ideas for Contribution:
[ ] Implement additional ML models (XGBoost, Neural Networks)
[ ] Add SMOTE for better imbalance handling
[ ] Create interactive dashboard with Streamlit
[ ] Implement real-time prediction API
[ ] Add feature engineering techniques
📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgments
Dataset provided by ULB Machine Learning Group
Kaggle for hosting the dataset
Scikit-learn team for the excellent ML library
📧 Contact
For questions or suggestions, please open an issue or contact the repository owner.
Developed by: Hasnain Haider
