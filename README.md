# Data Job Market Analysis

## Overview

This project analyzes data-related job postings to understand the current data job market, including:

- Most demanded data roles
- Required technical skills
- Salary patterns
- Factors associated with higher salaries
- Salary prediction using machine learning models

The goal is to explore what skills, locations, and job characteristics are commonly associated with data roles and compensation levels.

---

# Dataset

**Source:** Kaggle - Data Scientist Jobs Dataset
https://www.kaggle.com/datasets/andrewmvd/data-scientist-jobs

The dataset contains job postings with information such as:

- Job title
- Salary estimate
- Company information
- Location
- Industry
- Job description
- Company rating
- Job requirements

---

# Project Workflow

## 1. Data Understanding

Initial exploration of the dataset:

- Dataset dimensions
- Feature descriptions
- Data types
- Missing values
- Duplicate records

---

## 2. Data Cleaning

Data preprocessing steps included:

- Removing unnecessary columns
- Handling missing values
- Converting salary information into numerical features
- Extracting minimum, maximum, and average salary
- Cleaning inconsistent values
- Creating job categories and seniority levels

---

## 3. Exploratory Data Analysis (EDA)

The job market was explored through:

### Job Demand Analysis

Analyzed:

- Most common data-related job roles
- Companies with the highest number of data job postings
- Locations with the highest demand for data professionals
- Industries hiring the most data professionals


### Salary Analysis

Explored:

- Salary distribution
- Salary differences between job categories
- Salary differences by seniority level
- Relationship between company rating and salary


---

# 4. Skill Analysis Using NLP

Job descriptions were analyzed to extract frequently requested skills.

The process included:

- Text preprocessing
- N-gram analysis
- Extracting frequent technical terms
- Creating skill-based features


## Most Demanded Technical Skills

Top extracted skills:

| Skill | Number of Job Postings |
|---|---:|
| Python | 2057 |
| SQL | 2022 |
| Machine Learning | 1317 |
| Statistics | 1295 |
| Data Analysis | 913 |
| Big Data | 770 |
| Data Visualization | 550 |
| Data Analytics | 511 |
| Business Intelligence | 472 |
| Data Mining | 437 |


---

# 5. Salary Prediction

A regression task was created to predict average salary based on job characteristics.

## Feature Engineering

Created additional features:

- Company Age
- Job Category
- Seniority
- Technical skill indicators

Technical skills extracted from job descriptions were transformed into binary features:

- Skill present → 1
- Skill absent → 0


---

# Models

The following models were evaluated:

## Linear Regression

Used as a baseline model.

## Random Forest Regressor

Used to capture non-linear relationships between job characteristics and salary.

## Hyperparameter Tuning

RandomizedSearchCV was applied to optimize Random Forest parameters.

---

# Model Performance

Models were evaluated using:

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- R² Score


| Model | MAE (K) | RMSE (K) | R² |
|---|---:|---:|---:|
| Linear Regression | 27.32 | 35.01 | 0.15 |
| Random Forest | 24.62 | 31.70 | 0.30 |
| Tuned Random Forest | 25.63 | 31.89 | 0.29 |


The default Random Forest model achieved the best performance on the test set.

---

# Feature Importance Analysis

Feature importance from the Random Forest model showed that the strongest predictors were:

1. Job Category
2. Location
3. Company Age
4. Company Rating
5. Technical skills such as:
   - Data Analysis
   - Statistics
   - Python
   - SQL


The results suggest that salary differences are influenced by multiple factors, including job type and geographic market conditions, rather than technical skills alone.

---

# Key Findings

- Python and SQL are the most frequently requested technical skills in data-related roles.
- Machine Learning and Statistics are among the most common advanced requirements.
- Data Scientist roles generally show higher salary levels compared with some other data roles.
- Location is one of the strongest factors associated with salary differences.
- Technical skills contribute to salary prediction, but job category and location provide stronger signals in this dataset.

---

# Limitations

The dataset has some limitations:

- Missing information about exact years of experience
- Limited details about job level
- Salary estimates may not represent final compensation
- Skill extraction depends on predefined technical terms
- The model explains only part of salary variation (R² ≈ 0.30)

Therefore, model interpretations should be considered as patterns within this dataset rather than causal conclusions.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- NLP techniques (N-grams)

---

# Project Structure

Data-job-market-analysis/   
├── data/   
│ ├── raw/  
│ └── processed/    
│   
├── notebooks/  
│ ├── 01_data_understanding.ipynb   
│ ├── 02_data_cleaning.ipynb    
│ ├── 03_EDA.ipynb  
│ ├── 04_skill_analysis_NLP.ipynb   
│ └── 05_salary_prediction.ipynb    
│   
├── README.md   
└── requirements.txt    


---

# Future Improvements

Possible improvements:

- More advanced NLP techniques (TF-IDF, embeddings)
- Automatic skill extraction using NLP models
- Additional salary-related features
- More powerful models such as XGBoost
- Explainability analysis using SHAP values