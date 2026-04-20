# 🎬 Pre-Release Box Office Prediction and Risk Analysis
*A Machine Learning Pipeline to Predict Bollywood Movie Outcomes*

## 📊 Executive Summary
Investing in a movie production carries immense financial risk. From a business perspective, the financial loss of investing in a 'flop' is exponentially more damaging than the opportunity cost of missing out on a 'hit'. 

This project develops a **risk-averse predictive model** designed to identify potential Bollywood flops based entirely on pre-release features (e.g., Lead Star, Director, Screen Count). The primary business objective is to **maximize the Recall of the 'Flop' class (Outcome = 1)**, serving as an automated decision-support tool to help investors and producers mitigate financial exposure before theatrical release.

## 🛠️ Data Architecture & Preprocessing
To build a robust, production-ready system, data preprocessing was heavily automated using Scikit-Learn's `Pipeline` and `ColumnTransformer`. This ensures no data leakage and makes the model easily deployable for new, unseen data.

### Feature Engineering (`ColumnTransformer`)
Given the mix of numerical, binary, and high-cardinality categorical data, a custom `ColumnTransformer` was engineered:
* **Numerical Scaling:** Applied `StandardScaler` to `Number of Screens` to normalize the variance.
* **Binary Categoricals:** Applied `OneHotEncoder(drop='if_binary')` to features like `Release Period`, `Whether Remake`, `New Actor`, and `New Director`.
* **High-Cardinality Categoricals:** Applied `OneHotEncoder(max_categories=15, handle_unknown="ignore")` to `Lead Star`, `Director`, and `Music Director`. This prevents the dimensionality from exploding while retaining the most frequent and influential personnel in the industry.

## 🤖 Modeling Strategy
In this project, I intentionally restricted the modeling phase to just **two classifiers** to deeply explore their behavior, tune them effectively, and compare a probabilistic approach against a tree-based approach.

Both models were integrated seamlessly into Scikit-Learn `Pipeline` objects along with the `ColumnTransformer`.

1. **Bernoulli Naive Bayes (`BernoulliNB`)**
   * *Why:* Excellent baseline for datasets heavily populated by binary/boolean features (post-OneHotEncoding).
   * *Tuning:* Evaluated with `fit_prior=False` to handle class probabilities natively.

2. **Decision Tree Classifier (`DecisionTreeClassifier`)**
   * *Why:* Highly interpretable. It allows stakeholders to see exactly *which* pre-release features (e.g., a specific director combined with a low screen count) lead to a flop prediction.
   * *Evaluation:* Analyzed through its confusion matrix to monitor the False Negative rate (Flops predicted as Hits).

## 📈 Results & Business Implementation

<img width="1120" height="368" alt="image" src="https://github.com/user-attachments/assets/1e728263-006a-40d1-a262-fb000d81c73b" />

**Business Impact:** By utilizing the model with the highest **Recall for Flops**, production houses can flag risky investments early. If a script/personnel combination is flagged as a high-probability flop, stakeholders can opt to renegotiate budgets, change the release window, or alter the screen count strategy to hedge their bets.

## 📁 Repository Structure
```text
├── Movie_Outcome_analysis.ipynb   # Main notebook with EDA, Pipelines, and Modeling
├── Movie_data_dmml_project.csv    # Raw dataset (1,698 Hindi movies)
└── README.md
