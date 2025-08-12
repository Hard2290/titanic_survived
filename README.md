# Titanic - Machine Learning from Disaster - Kaggle Competition
- Kaggle competition link - https://www.kaggle.com/competitions/titanic
- This is binary classification problem.
- The training dataset contains 11 features (Sex, Age, Fare, Name, etc) of 891 passengers, who boarded TItanic ship, along with the target feature "Survived" showing whether they survived (1) or not (0).

## Problem Statement :
- Our goal is to build a model to train on the training dataset and predict whether the passengers survived (1) or not (0) for the test dataset.
- Check the model's performance using "Accuracy" metric.

## Tools used :
- Python - Coding Language
- Pandas - For Data Processing
- Numpy - For Arrays and Computations
- Sklearn - For ML Models and Metrics
- Optuna - For Hyperparameter Tuning
- Matplotlib/Seaborn - For Data Visualization

## Creating Cross-validation Folds :
- Creating and using same cross-validation folds throughout to prevent any overfitting.
- Using Stratified KFold to preserve the class distribution of full dataset in each folds.
- Creating 5 folds and mentioning the validation folds in a separate column.
![Image](https://github.com/user-attachments/assets/d9e28151-110b-4b20-a859-a4714cf4700c)

## Handling Missing values:
- Mode Imputation has been done for Categorical features such as "Embarked".
- Median Imputation has been done for numerical features like "Fare" that have skewed distribution, i.e., has outliers.
- Predicted missing values for "Age" column using Kernel Ridge Regression model while using Label Encoding to deal with categorical data.

## Feature Engineering:
- Extracted a repeating pattern of data out of the unique ticket details of all the passengers onboard in "Ticket" column and created a new categorical feature named "ticket_type".
- Different "ticket_type" values showing different "Survival" probabilities for passengers.
![Image](https://github.com/user-attachments/assets/1ac5c2b8-a2fc-4bfb-9314-920f8e6f1540)

- Similarly, using "Cabin" feature containing alpha-numeric cabin name alloted to passsengers, a categorical feature has been created and named "cabin_type".
- Different "cabin_type" values showing different "Survival" probabilities for passengers.
![Image](https://github.com/user-attachments/assets/69534fd7-4756-4bac-9b37-20eae8cc6fef)

- Using unique "Name" column, two informations have been extracted, family to which the passengers belongs to and their title and these informations presented under two new categorical features, "family" and "title" respectively.
- Different "title" values showing different "Survival" probabilities for passengers.
![Image](https://github.com/user-attachments/assets/e8a3bade-1abd-4766-9b28-827b2d43c0bb)

- Created two new features; "family_size", using "SibSp" and "Parch" columns, and "family_count", containing count of all the families using "family" feature.
- Created two new features; "Age_NA", showing positions of missing values in "Age" column, and "Age_mean", containing Mean Imputation of "Age" column as data was nearly symmetrical.

## Handling Outliers:

