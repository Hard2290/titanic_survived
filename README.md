# Titanic - Machine Learning from Disaster - Kaggle Competition
- Kaggle competition link - https://www.kaggle.com/competitions/titanic
- This is binary classification problem.
- The training dataset contains 11 features (Sex, Age, Fare, Name, etc) of 891 passengers, who boarded TItanic ship, along with the target feature "Survived" showing whether they survived (1) or not (0).

## Rank on Kaggle Public Leaderboard - 407 out of 13256

![Image](https://github.com/user-attachments/assets/2d120bb8-5ffe-4653-8cf2-22f08d4e3c86)

## Best Score Achieved on Kaggle Public Leaderboard - 0.80382

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
- According to the heatmap showing correlation among features, "Age_mean" has high correlation with "Age" and "Age_NA" has no correlation with "Age", so we need to drop "Age_mean" and "Age_NA" columns. Similarly, "SibSp" and "Parch" have high correlation with "family_size" and "family_count", so drop "SibSp" and "Parch" columns to prevent redundancy in linear models.

![Image](https://github.com/user-attachments/assets/03df9dea-e15d-4ce2-b5ff-5b88b94f2bfb)

## Handling Outliers:
- Using boxplot, outliers detected in "Age", "Age_mean" and "Fare" features.
![Image](https://github.com/user-attachments/assets/2de31ad2-62b5-4ed8-963f-f90229aab96e)


![Image](https://github.com/user-attachments/assets/7fc4a3ed-0cb1-4697-92c1-c24e0da6517d)


![Image](https://github.com/user-attachments/assets/680c170a-83f0-4b38-8729-0d59816dd625)


- Data distribution of "Age" and "Age_mean" is nearly symmetrical, so to deal with outliers, their values have been bounded within 3σ wrt mean.

![Image](https://github.com/user-attachments/assets/38a660a0-15ff-485e-8ec6-9ee658936b04)

![Image](https://github.com/user-attachments/assets/066da803-b1b7-49c1-8220-5968aa0489b9)

- Since "Fare" has skewed data distribution, so its values have been bounded within 3IQR (Interquartile Range) from 75th and 25th percentile value.

![Image](https://github.com/user-attachments/assets/c7a68ddc-a20a-47a9-93b2-05e35a20eafe)

## Feature Encoding and Modeling:
- 4 types of Feature Encodings, "One-Hot Encoding", "Label Encoding", "Mean Encoding" and "Frequency Encoding" used.
- 5 types of classifiers, "Random Forest Classifier", "Gradient Boosting Classifier", "KNeighbors Classifier", "Support Vector Classifier" and "XGBoost Classifier" used.
- Using "Optuna" for "XGBoost" and manual "Grid Search" for rest of the classifiers, Hyperparameter tuning done  over 5 cross-validation folds for all the 20 Classifier-Encoding combinations to obtain the best performing model in terms of accuracy.
- Final Hyperparameters of the best performing models obtained after further careful tuning of parameters to remove overfitting or underfitting as indicated by the differences in accuracy scores of the validation and test dataset according to scores on Kaggle's Public Leaderboard.

![Image](https://github.com/user-attachments/assets/57068e2c-f97c-4c33-a304-37906fcfaa69)

![Image](https://github.com/user-attachments/assets/50ff5fac-b457-4e7c-ab62-8696be4b0f28)

![Image](https://github.com/user-attachments/assets/37467fcf-e705-4407-b8b5-7acb89c201b7)

![Image](https://github.com/user-attachments/assets/7310a9aa-8480-4b13-897d-86448fd48d2c)

![Image](https://github.com/user-attachments/assets/8a3f0a16-1622-449d-a2f2-54b1778316df)

## Final Submission:
- Below are the Top 5 best performing models out of 20 models.

![Image](https://github.com/user-attachments/assets/c24f6284-8e34-44e7-8bfa-eb4e318502d4)

- Final prediction obtained by taking mean of the top 3 best performing models and converting them to binary (0 & 1) by choosing 0.5 as threshold.
- An accuracy of 0.80382 has been achieved by the model on Kaggle's Public Leaderboard.
