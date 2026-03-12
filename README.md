💳 Credit Card Fraud Detection
A machine learning project that uses a Random Forest Classifier to detect fraudulent credit card transactions from a highly imbalanced dataset.

📋 Table of Contents

Overview
Dataset
Project Structure
Dependencies
How It Works
Model & Evaluation
Results
Usage
Known Issues
Author


🔍 Overview
Credit card fraud is a major financial problem worldwide. This project builds a binary classification model to distinguish between fraudulent (Class = 1) and legitimate (Class = 0) transactions using the popular Kaggle Credit Card Fraud dataset.

📊 Dataset

File: creditcard.csv
Total Records: 284,807 transactions
Features: 30 input features (Time, V1–V28, Amount) + 1 target (Class)
Fraud Cases: 492 (~0.17% of all transactions)
Valid Transactions: 284,315


⚠️ The dataset is highly imbalanced — fraudulent transactions represent only 0.17% of all records.

Feature Description
FeatureDescriptionTimeSeconds elapsed since the first transactionV1 - V28PCA-transformed anonymized featuresAmountTransaction amountClassTarget variable: 1 = Fraud, 0 = Legitimate

📁 Project Structure
credit-card-fraud-detection/
│
├── creditcard.csv          # Dataset (not included, download from Kaggle)
├── fraud_detection.ipynb   # Main Jupyter Notebook
└── README.md               # Project documentation

📦 Dependencies
Install the required libraries using pip:
bashpip install numpy pandas matplotlib seaborn scikit-learn
LibraryPurposenumpyNumerical computationspandasData loading and manipulationmatplotlibData visualizationseabornCorrelation heatmapscikit-learnModel training and evaluation

⚙️ How It Works

Load Data — Read creditcard.csv using Pandas
Explore Data — Check shape, class distribution, and transaction amount statistics
Visualize — Generate a correlation heatmap using Seaborn
Preprocess — Separate features (X) from labels (Y), convert to NumPy arrays
Split — 80% training / 20% testing using train_test_split (random_state=42)
Train — Fit a RandomForestClassifier on the training set
Predict — Generate predictions on the test set
Evaluate — Measure performance using multiple metrics


🤖 Model & Evaluation
Model Used: RandomForestClassifier (scikit-learn default parameters)
Evaluation Metrics:
MetricDescriptionAccuracyOverall correct predictionsPrecisionOf predicted frauds, how many were actually fraudRecallOf actual frauds, how many were correctly identifiedF1-ScoreHarmonic mean of Precision and RecallMCCMatthews Correlation Coefficient — robust for imbalanced dataConfusion MatrixVisual breakdown of TP, TN, FP, FN

📈 Results

Results are generated upon running the notebook. Example expected output:

The model used is Random Forest classifier
The accuracy is 0.9996
The precision is 0.9583
The recall is 0.7755
The F1-Score is 0.8571
The Matthews correlation coefficient is 0.8609

🚀 Usage

Download the dataset from Kaggle - Credit Card Fraud Detection
Place creditcard.csv in the project directory
Open fraud_detection.ipynb in Jupyter Notebook or Google Colab
Run all cells sequentially


💡 Tip: If using Google Colab, mount your Google Drive and update the file path accordingly:
pythonfrom google.colab import drive
drive.mount('/content/drive')
data = pd.read_csv("/content/drive/MyDrive/creditcard.csv")


⚠️ Known Issues

NameError: name 'data' is not defined — This occurs if cells are not run in order. Always restart the kernel and run all cells from the beginning.
The dataset is highly imbalanced. Consider techniques like SMOTE, undersampling, or class weighting to improve recall on fraud cases.


👤 Author
Hasnain Haider

This project is intended for educational purposes in machine learning and fraud analytics.
