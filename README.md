# Pre-Release Box Office Prediction and Risk Analysis

## 📌 Project Overview
In the film industry, the financial penalty of investing in a flop is exponentially higher than the opportunity cost of missing out on a hit. This project aims to predict whether a Bollywood movie will be a 'hit' or a 'flop' based solely on its pre-release features. 

The primary business objective is to build a risk-averse predictive model that **maximizes the recall of "flop" movies**. By accurately identifying potential flops before they happen, this model serves as a vital decision-support tool for investors, producers, and theater owners to mitigate devastating financial risks.

## 📊 The Dataset
The dataset utilized is `Movie_data_dmml_project.csv`, containing detailed records of **1,698 Hindi movies** released between 2005 and 2017. 

**Model Features include:**
- **Categorical:** Release Period, Remake Status, Franchise Status, Genre, New Actor/Director/Music Director, Lead Star.
- **Continuous:** Number of Screens, Budget (INR).

## ⚙️ Data Pipeline & Preprocessing
The preprocessing and model-building phases were unified into robust scikit-learn `Pipeline` objects to prevent data leakage and streamline production:
- **Null Value & Duplicate Checks:** The raw dataset was thoroughly cleaned.
- **Continuous Feature Scaling:** `StandardScaler` was applied to numeric features like 'Number of Screens'.
- **Categorical Feature Encoding:** `OneHotEncoder` was utilized, expertly handling binary drops and capping high-cardinality features (like Lead Stars or Directors) using `max_categories=15`.

## 🧠 Models & Hyperparameter Tuning
Two primary machine learning algorithms were built, extensively profiled (time/space complexity), and strictly evaluated heavily against **Recall for Class 1 (Flops)**. 

Hyperparameter tuning was conducted on both models utilizing `RandomizedSearchCV` (scoring for `f1` and `roc_auc`).

### 1. Decision Tree Classifier (The Winner)
* **Untuned:** Severely overfit the training data. Captured only 48% F1-score and 42% Recall on testing data.
* **Tuned:** Restricting tree depth, adjusting min-samples-split, and balancing class weights led to an incredible turnaround, completely eliminating overfitting.
  * **Recall (Flops): 88%**
  * **Precision (Hits): 66%**
  * **Test F1-Score:** 0.75

### 2. Bernoulli Naive Bayes Classifier
* **Tuned:** Remained highly generalized and robust, but captured slightly fewer flops than the Decision Tree. 
  * **Recall (Flops): 79%**
  * **Test F1-Score:** 0.77

## 🏆 Final Business Conclusion
Thanks to rigorous hyperparameter tuning, the **Decision Tree Classifier** emerged as the definitive choice. By correctly identifying **88% of all potential box office flops**, the model transcends statistical curiosity becoming a highly effective risk-management tool. It provides a highly reliable foundation for greenlighting projects and protecting stakeholder investments.

## 🚀 How to Run Locally

1. Clone the repository.
2. Ensure you have the required dependencies listed in `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the complete analysis workflow within `Movie_Outcome_analysis.ipynb`.
