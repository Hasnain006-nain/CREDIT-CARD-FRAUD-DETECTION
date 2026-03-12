<div align="center">

# 💳 Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.24+-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-2ea44f?style=for-the-badge)

<br/>

> **Detecting fraudulent credit card transactions using Machine Learning**  
> with a Random Forest Classifier on a real-world imbalanced dataset.

<br/>

[🚀 Getting Started](#-getting-started) • [📊 Dataset](#-dataset) • [🤖 Model](#-model--evaluation) • [📈 Results](#-results) • [👤 Author](#-author)

---

</div>

<br/>

## 📌 Table of Contents

- [🔍 Overview](#-overview)
- [📊 Dataset](#-dataset)
- [📁 Project Structure](#-project-structure)
- [⚙️ Tech Stack](#️-tech-stack)
- [🚀 Getting Started](#-getting-started)
- [🔬 How It Works](#-how-it-works)
- [🤖 Model & Evaluation](#-model--evaluation)
- [📈 Results](#-results)
- [⚠️ Known Issues & Fixes](#️-known-issues--fixes)
- [🔮 Future Improvements](#-future-improvements)
- [👤 Author](#-author)

<br/>

---

## 🔍 Overview

<table>
<tr>
<td>

Credit card fraud is one of the most significant financial threats in the digital age, costing billions of dollars globally each year. This project builds a robust **binary classification model** capable of identifying fraudulent transactions from legitimate ones — even in a severely imbalanced dataset where fraud represents less than **0.2%** of all records.

Using the **Random Forest algorithm**, this model analyzes anonymized transaction features to flag suspicious activity with high accuracy and reliability.

</td>
</tr>
</table>

### ✨ Key Highlights

| 🏆 Feature | 📋 Detail |
|---|---|
| 🧠 Algorithm | Random Forest Classifier |
| 📦 Dataset Size | 284,807 transactions |
| 🎯 Task | Binary Classification (Fraud vs. Legitimate) |
| ⚖️ Class Imbalance | ~0.17% fraud rate |
| 📐 Evaluation | Accuracy, Precision, Recall, F1, MCC, Confusion Matrix |

<br/>

---

## 📊 Dataset

<div align="center">

```
📂 creditcard.csv
├── 284,807 total transactions
├── 492 fraudulent cases    (0.17%)
└── 284,315 valid cases     (99.83%)
```

</div>

> 📥 Download from [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

### 🧾 Feature Description

| Feature | Type | Description |
|---------|------|-------------|
| `Time` | Numerical | Seconds elapsed since the first transaction in the dataset |
| `V1 – V28` | Numerical | PCA-transformed anonymized features to protect user privacy |
| `Amount` | Numerical | The monetary value of the transaction |
| `Class` | Binary | **Target** — `1` = Fraudulent, `0` = Legitimate |

### 📉 Class Distribution

```
Legitimate  ████████████████████████████████████████████████  99.83%
Fraudulent  ░                                                   0.17%
```

> ⚠️ **Note:** The dataset is highly imbalanced. Standard accuracy alone is misleading — precision, recall, F1, and MCC provide a more complete picture.

<br/>

---

## 📁 Project Structure

```
📦 credit-card-fraud-detection/
│
├── 📄 creditcard.csv              ← Dataset (download separately from Kaggle)
├── 📓 fraud_detection.ipynb       ← Main Jupyter Notebook
└── 📝 README.md                   ← Project documentation
```

<br/>

---

## ⚙️ Tech Stack

<div align="center">

| Library | Version | Purpose |
|---------|---------|---------|
| ![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white) | 3.8+ | Core language |
| ![NumPy](https://img.shields.io/badge/-NumPy-013243?logo=numpy&logoColor=white) | 1.24+ | Numerical operations |
| ![Pandas](https://img.shields.io/badge/-Pandas-150458?logo=pandas&logoColor=white) | 2.0+ | Data loading & manipulation |
| ![Matplotlib](https://img.shields.io/badge/-Matplotlib-11557C?logo=python&logoColor=white) | 3.7+ | Data visualization |
| ![Seaborn](https://img.shields.io/badge/-Seaborn-4C72B0?logo=python&logoColor=white) | 0.12+ | Correlation heatmap |
| ![scikit-learn](https://img.shields.io/badge/-scikit--learn-F7931E?logo=scikit-learn&logoColor=white) | 1.0+ | ML model & metrics |

</div>

### 📦 Installation

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

<br/>

---

## 🚀 Getting Started

### Option 1 — Local Environment

```bash
# 1. Clone the repository
git clone https://github.com/your-username/credit-card-fraud-detection.git
cd credit-card-fraud-detection

# 2. Install dependencies
pip install numpy pandas matplotlib seaborn scikit-learn

# 3. Add dataset
# Place creditcard.csv in the project root directory

# 4. Launch Jupyter Notebook
jupyter notebook fraud_detection.ipynb
```

### Option 2 — Google Colab ☁️

```python
# Mount your Google Drive
from google.colab import drive
drive.mount('/content/drive')

# Load the dataset
data = pd.read_csv("/content/drive/MyDrive/creditcard.csv")
```

<br/>

---

## 🔬 How It Works

```
┌─────────────────────────────────────────────────────────────┐
│                     PIPELINE OVERVIEW                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. 📥 Load Data        →  Read creditcard.csv with Pandas  │
│                                                             │
│  2. 🔎 Explore Data     →  Shape, stats, class balance      │
│                                                             │
│  3. 📊 Visualize        →  Correlation heatmap (Seaborn)    │
│                                                             │
│  4. 🔧 Preprocess       →  Split X (features) / Y (labels)  │
│                                                             │
│  5. ✂️  Split Data       →  80% Train | 20% Test            │
│                                                             │
│  6. 🌲 Train Model      →  RandomForestClassifier.fit()     │
│                                                             │
│  7. 🔮 Predict          →  rfc.predict(xTest)               │
│                                                             │
│  8. 📈 Evaluate         →  Accuracy, F1, MCC, CM            │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

<br/>

---

## 🤖 Model & Evaluation

### 🌲 Random Forest Classifier

Random Forest is an **ensemble learning** method that builds multiple decision trees and merges their outputs for a more accurate and stable prediction. It is particularly well-suited for:

- ✅ High-dimensional data
- ✅ Imbalanced datasets
- ✅ Capturing non-linear feature relationships
- ✅ Resistance to overfitting

### 📐 Evaluation Metrics Explained

| Metric | Formula | Why It Matters |
|--------|---------|----------------|
| **Accuracy** | (TP+TN) / Total | General correctness — misleading on imbalanced data |
| **Precision** | TP / (TP+FP) | How many flagged frauds are real frauds |
| **Recall** | TP / (TP+FN) | How many actual frauds were caught |
| **F1-Score** | 2 × (P×R)/(P+R) | Balance between Precision and Recall |
| **MCC** | Balanced metric | Best single metric for imbalanced classification |
| **Confusion Matrix** | TP/TN/FP/FN grid | Visual breakdown of all prediction outcomes |

<br/>

---

## 📈 Results

<div align="center">

```
╔══════════════════════════════════════════════════════╗
║           MODEL PERFORMANCE SUMMARY                 ║
╠══════════════════════════════════════════════════════╣
║  Model        │  Random Forest Classifier            ║
║  Accuracy     │  99.96%  ████████████████████ ✅     ║
║  Precision    │  95.83%  ███████████████████  ✅     ║
║  Recall       │  77.55%  ███████████████      ⚠️     ║
║  F1-Score     │  85.71%  █████████████████    ✅     ║
║  MCC          │  86.09%  █████████████████    ✅     ║
╚══════════════════════════════════════════════════════╝
```

</div>

> 🔎 **Interpretation:** The model achieves near-perfect accuracy but recall can be further improved — meaning some fraudulent transactions may still slip through. Techniques like SMOTE or threshold tuning can help boost recall.

<br/>

---

## ⚠️ Known Issues & Fixes

### ❌ `NameError: name 'data' is not defined`

**Cause:** Notebook cells were not executed in order — `data` was never loaded into memory.

**Fix:**
```
Kernel → Restart & Run All
```
Always run all cells **from the top** in sequence to ensure variables remain in scope.

---

### ⚖️ Class Imbalance Warning

With only 0.17% fraud cases, standard training may bias toward predicting "legitimate." Consider:

```python
# Option 1: Class weighting
rfc = RandomForestClassifier(class_weight='balanced')

# Option 2: SMOTE oversampling
from imblearn.over_sampling import SMOTE
sm = SMOTE(random_state=42)
xTrain, yTrain = sm.fit_resample(xTrain, yTrain)
```

<br/>

---

## 🔮 Future Improvements

- [ ] 🔄 Apply **SMOTE** or undersampling to handle class imbalance
- [ ] 🔧 Hyperparameter tuning with `GridSearchCV`
- [ ] 🧪 Compare with **XGBoost**, **LightGBM**, and **Isolation Forest**
- [ ] 📉 ROC-AUC curve and Precision-Recall curve visualization
- [ ] 🚀 Deploy as a real-time fraud detection **REST API** using Flask/FastAPI
- [ ] 💾 Save the trained model using `joblib` for production use

<br/>

---

## 👤 Author

<div align="center">

<br/>

```
╔════════════════════════════════════╗
║                                    ║
║         Hasnain Haider             ║
║                                    ║
║   Machine Learning Enthusiast      ║
║   Data Science | AI | Python       ║
║                                    ║
╚════════════════════════════════════╝
```

[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/your-username)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/your-profile)

<br/>

---

*© 2024 Hasnain Haider — Built for educational purposes in Machine Learning & Financial Analytics*

⭐ **If you found this project helpful, please give it a star!** ⭐

</div>
