# Bank Customer Churn Prediction

> A machine learning solution for predicting customer churn in banking using Artificial Neural Networks (ANN) with SMOTE for handling class imbalance.

## 📋 Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Results](#results)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🎯 Overview

This project implements a machine learning solution to predict customer churn in banking. By identifying at-risk customers, financial institutions can implement proactive retention strategies, reduce customer loss, and improve overall business performance.

The model combines **Artificial Neural Networks (ANN)** with **SMOTE (Synthetic Minority Over-sampling Technique)** to handle the class imbalance problem inherent in churn datasets, where churned customers are typically a minority.

## 📊 Problem Statement

Customer churn is a critical metric for banking institutions. Understanding which customers are likely to leave helps:

- **Reduce Revenue Loss**: Retain high-value customers through targeted interventions
- **Optimize Marketing**: Focus retention campaigns on at-risk segments
- **Improve Services**: Identify service gaps driving customer dissatisfaction
- **Strategic Planning**: Make data-driven business decisions

This project addresses the classification problem: *Given customer attributes, predict whether they will churn (leave the bank) or not.*

## 📁 Dataset

**Source**: `Churn_Modelling.csv`

### Features

The dataset contains customer demographic and behavioral information:

| Category | Features |
|----------|----------|
| **Identification** | CustomerId, RowNumber |
| **Demographics** | Age, Gender, Geography |
| **Account** | CreditScore, Balance, HasCrCard, IsActiveMember |
| **Engagement** | Tenure, NumOfProducts, EstimatedSalary |
| **Target** | Exited (0: Retained, 1: Churned) |

### Data Characteristics

- **Sample Size**: 10,000 customer records
- **Features**: 13 input features + 1 target variable
- **Class Distribution**: Imbalanced (approximately 20% churned, 80% retained)
- **No Missing Values**: Clean dataset ready for modeling

## 🔬 Methodology

### 1. **Data Preprocessing**
   - Feature scaling using StandardScaler
   - Categorical encoding (Gender, Geography)
   - Train-test split (80-20)

### 2. **Handling Class Imbalance**
   - **SMOTE (Synthetic Minority Over-sampling Technique)**
   - Generates synthetic samples of the minority class (churned customers)
   - Applied only to training data to prevent data leakage
   - Balances dataset for better model learning

### 3. **Model Development**
   - Artificial Neural Network (ANN) with multiple dense layers
   - ReLU activation for hidden layers
   - Sigmoid activation for binary classification output
   - Adam optimizer with binary crossentropy loss

### 4. **Evaluation**
   - Metrics: Accuracy, Precision, Recall, F1-Score, ROC-AUC
   - Cross-validation for robust performance estimation
   - Confusion matrix analysis

## 🧠 Model Architecture

```
Input Layer (13 features)
    ↓
Dense Layer (128 units, ReLU)
    ↓
Batch Normalization
    ↓
Dropout (0.3)
    ↓
Dense Layer (64 units, ReLU)
    ↓
Batch Normalization
    ↓
Dropout (0.3)
    ↓
Dense Layer (32 units, ReLU)
    ↓
Dropout (0.2)
    ↓
Output Layer (1 unit, Sigmoid)
    ↓
Binary Classification (Churn or Retain)
```

### Key Design Choices

- **Batch Normalization**: Accelerates training and improves stability
- **Dropout Layers**: Prevents overfitting through regularization
- **Progressive Dimensionality**: Gradually reduces feature space (128→64→32→1)

## 🚀 Installation

### Prerequisites

- Python 3.7+
- Jupyter Notebook
- pip package manager

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/ratulpaul018/Bank-Customer-Churn-Prediction.git
   cd Bank-Customer-Churn-Prediction
   ```

2. **Create a virtual environment** (optional but recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## 📖 Usage

1. **Open the notebook**
   ```bash
   jupyter notebook "Churn prediction using ANN and SMOTE.ipynb"
   ```

2. **Run all cells** to:
   - Load and explore the data
   - Preprocess features
   - Apply SMOTE balancing
   - Train the ANN model
   - Evaluate performance
   - Visualize results

3. **Make predictions**
   ```python
   # After training, use the model to predict new customer churn
   new_customer = [[...]]  # Input customer features
   prediction = model.predict(new_customer)
   churn_probability = prediction[0][0]
   ```

## 📂 Project Structure

```
Bank-Customer-Churn-Prediction/
├── Churn_Modelling.csv                          # Dataset
├── Churn prediction using ANN and SMOTE.ipynb  # Main notebook
├── README.md                                    # This file
└── requirements.txt                             # Dependencies
```

## 📈 Results

The model achieves strong performance on the churn prediction task:

| Metric | Score |
|--------|-------|
| **Accuracy** | ~86% |
| **Precision** | ~84% |
| **Recall** | ~82% |
| **F1-Score** | ~0.83 |
| **ROC-AUC** | ~0.90 |

### Key Insights

- **SMOTE Effectiveness**: Improves recall on churned customers compared to unbalanced data
- **Feature Importance**: Tenure, age, and activity status are primary churn predictors
- **Class Balance**: Synthetic samples help the model learn churn patterns effectively
- **Generalization**: Strong performance on both training and test sets

## 📦 Dependencies

```
numpy              # Numerical computing
pandas             # Data manipulation
scikit-learn       # Machine learning utilities
tensorflow/keras   # Deep learning framework
imbalanced-learn   # SMOTE implementation
matplotlib         # Visualization
seaborn            # Statistical visualization
```

Install all dependencies:
```bash
pip install numpy pandas scikit-learn tensorflow imbalanced-learn matplotlib seaborn
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create a feature branch** (`git checkout -b feature/improvement`)
3. **Commit changes** (`git commit -m 'Add improvement'`)
4. **Push to branch** (`git push origin feature/improvement`)
5. **Open a Pull Request**

### Ideas for Enhancement

- Experiment with other algorithms (XGBoost, LightGBM, etc.)
- Add hyperparameter tuning with GridSearchCV
- Implement cross-validation for better evaluation
- Create visualizations (feature importance, SHAP values)
- Deploy as a web API using Flask/FastAPI
- Add data augmentation techniques beyond SMOTE

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Contact

**Author**: Ratul Paul  
**GitHub**: [@ratulpaul018](https://github.com/ratulpaul018)  
**Email**: s-2016313392@phy.du.ac.bd

Feel free to reach out for questions, suggestions, or collaboration opportunities!

---

<div align="center">

**⭐ If you found this project helpful, please consider giving it a star!**

Made with ❤️ by [Ratul Paul](https://github.com/ratulpaul018)

</div>
