[Read Me.docx](https://github.com/user-attachments/files/15619128/Read.Me.docx)
README: Model Results for Biomarker-X
Overview
This document provides a detailed account of the processes and results obtained from various machine learning models applied to the Biomarker-X dataset. We focused on regression models and feature extraction using Convolutional Neural Networks (CNN) to predict the concentration levels of the biomarker. Below are the details of the models used, their configurations, and the performance metrics achieved.
Models and Methods
1. Baseline Regression Models -
We employed three types of regression models: Linear Regression, Lasso Regression, and Ridge Regression. The data preprocessing included subtracting background signals from raw signals to enhance the model accuracy.
Linear Regression:
Without background subtraction:
Adjusted R-squared: 7%
R-squared: 27.5%
After PCA (95% variance):
Adjusted R-squared: 6%
R-squared: 27.5%
With background subtraction:
Adjusted R-squared: 33.02%
R-squared: 54.94%
After PCA:
Adjusted R-squared: 0.59%
R-squared: 2.75%
Lasso Regression:
Without background subtraction:
R-squared: 32.78%
Adjusted R-squared: 0.09%
With background subtraction:
Results were not significantly better than Linear Regression.
Ridge Regression:
Without background subtraction:
R-squared: 6.39%
Adjusted R-squared: -39.13%
With background subtraction:
Results were not significantly better than Linear Regression.
2. Feature Extraction with CNN
A CNN architecture was used for feature extraction, and the extracted features were then applied to regression models.
CNN Architecture:

Layers: Convolutional layers followed by Batch Normalization and Max Pooling, with a final set of Fully Connected layers.
Total Parameters: 118,947,023
Training Configurations:
Epochs: 40 to 45
Criterion: CrossEntropyLoss
Optimizer: Adam, AdamW
Learning Rate: 0.00001 to 0.0001
Dropout: 0.1 to 0.5
Test Accuracy: 78% to 82%
CNN Training History
First CNN Training Configuration:
Parameters:
Epochs: 40
Criterion: CrossEntropyLoss
Optimizer: Adam
Learning Rate: 0.00001
Dropout: 0.5
Results:
Test Accuracy: 82%
Regression Features: fc3 (128 neurons)
Linear Regression Results:
Negative regression values for all models
Second CNN Training Configuration:
Parameters:
Epochs: 45
Criterion: CrossEntropyLoss
Optimizer: AdamW
Learning Rate: 0.00001
Dropout: 0.3
Results:
Test Accuracy: 78%
Regression Features: fc2 (512 neurons)
Linear Regression Results:
Ridge Regression:
R-squared: 74.9%
Adjusted R-squared: 38.5%
Linear and Lasso Regression:
Adjusted R-squared < 20%
Final CNN Training Configuration:
Parameters:
Epochs: 30
Criterion: CrossEntropyLoss
Optimizer: Adam
Learning Rate: 0.0001
Dropout: 0.1
Results: it is not correct because used seen test data
Test Accuracy: 79%
Regression Features: fc2 (512 neurons)
Regression Results: test_split = 0.05
Linear Regression:
R-squared: 85.26%
Adjusted R-squared: 63.87%
Lasso Regression (alpha = 25):
R-squared: 91.18%
Adjusted R-squared: 78.38%
Ridge Regression (alpha = 40):
R-squared: 91.85%
Adjusted R-squared: 80.03%

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
After test all models with unseen test data:
—Baseline linear regression with subtracted data is getting negative [adjusted r^2-> -1.08]

	It was 33% with entire dataset




—CNN classifier regression with 74% eval model [ adjust r^2 -> 1.04]

	
	Without test data model it gets 78% adjusted r^2 score




–CNN Regression 
Epoch - 30
Learning rate = 0.0001
Schedular [ReduceLROnPlateau-min] - factor = 0.01, patience = 5
Creterion  = MSEloss()
Loss is decreased from 29 to 9.6
When taking fc2 layer as feature extractor then linear regression model is  tested with unseen data it shows below output 


So CNN Regression can not do outstanding performance 


Feature selection in baseline linear regression
Recursive Feature Elimination (RFE)
LassoCV
RandomForest regression
Correlation matrix
ALL OF THEM are unuseful 



