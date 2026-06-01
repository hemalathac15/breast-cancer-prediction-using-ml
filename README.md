#Breast Cancer Prediction Using K-Nearest Neighbors (KNN)
This project implements a machine learning workflow to classify breast cancer tumors as either Malignant or Benign based on cellular characteristics. The model utilizes the K-Nearest Neighbors (KNN) Classifier built with scikit-learn.  
IPYNB
+ 1

Table of Contents
Dataset Overview

Project Workflow

Dependencies

Model Performance

Usage

Dataset Overview
The model trains on a dataset containing clinical characteristics of breast cancer tumor nuclei.  
IPYNB

Total Instances: 569 patient records  
IPYNB

Total Features: 30 continuous numerical features (e.g., radius mean, texture mean, perimeter mean, smoothness, concavity)  
IPYNB

Target Variable (diagnosis):

1 = Malignant (Cancer Detected)  
IPYNB

0 = Benign (No Cancer)  
IPYNB

Project Workflow
Data Exploration & Cleaning:

Load the dataset (breast cancer.csv) and examine its dimensions, structural info, and numerical distributions.  
IPYNB

Unnecessary tracking columns like id are removed to prevent overfitting.  
IPYNB

Standardize the string target text values, strip trailing white spaces, and encode categorical values (M/B) into numeric binary representations (1/0).  
IPYNB

Dataset Partitioning:

Separate features (X) from the target (y).  
IPYNB

Split the dataset into 80% Training and 20% Testing subsets using stratified sampling to maintain proper class distributions.  
IPYNB

Feature Scaling:

Apply StandardScaler to calculate mean and standard deviation variations solely from the training data, scaling both subsets effectively to safeguard against data leakage.  
IPYNB

Model Training & Inference:

Initialize a KNeighborsClassifier configured with k=5 neighbors.  
IPYNB

Fit the model onto the scaled training features and make test class predictions.  
IPYNB

Predictive System:

Build an inference pipeline capable of reshaping, scaling, and classifying isolated patient samples.  
IPYNB

Dependencies
To run this notebook successfully, ensure you have the following Python libraries installed:

Bash
pip install pandas numpy matplotlib scikit-learn
Model Performance
Classification Algorithm: K-Nearest Neighbors (k=5)  
IPYNB

Evaluation Metric: Accuracy Score  
IPYNB

Achieved Test Accuracy: ~95.61%

  
IPYNB

Usage
Running the Notebook
Make sure your dataset file is named exactly breast cancer.csv and placed in the same directory as the notebook.  
IPYNB

Execute the notebook cells sequentially to clean the data, train the classifier, and view performance results.  
IPYNB

Predicting New Sample Data
You can test isolated patient data profiles using the predictive step at the end of the script. For example:  
IPYNB

Python
# Extract and format an individual patient profile from your dataset
sample = X.iloc[0].values.reshape(1, -1)
sample_scaled = scaler.transform(sample)

# Generate inference decision
prediction = knn.predict(sample_scaled)
if prediction[0] == 1:
    print("Prediction: Malignant (Cancer Detected)")
else:
    print("Prediction: Benign (No Cancer)")
