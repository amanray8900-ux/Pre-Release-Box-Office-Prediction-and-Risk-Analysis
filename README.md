# Pre-Release Box Office Prediction and Risk Analysis

## Overview
This project aims to predict whether a Bollywood movie will be a 'hit' or a 'flop' based on its pre-release features. The primary objective is to build a risk-mitigating model that maximizes the recall of 'flop' movies. By prioritizing the accurate identification of potential flops, this model serves as a decision-support tool to help stakeholders (investors, producers, theater owners) avoid financial risk.

## Dataset
The dataset contains 1,698 Hindi movies released between 2005 and 2017. Features include release period, genre, whether it involves new actors or directors, movie screen count, and movie budget.

## Data Processing
The data preprocessing pipeline handles standard categorical encoding and checks for duplicates. 

## Models Evaluated
- **Naive Bayes Classifier**
- **Decision Tree Classifier**

## Usage
The `Movie_Outcome_analysis.ipynb` Jupyter Notebook outlines all exploratory data analysis and model training steps.

## Requirements
See `requirements.txt` for the full list of dependencies. Install them locally by running:
```bash
pip install -r requirements.txt
```
