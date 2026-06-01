# Breast Cancer Prediction Using K-Nearest Neighbors (KNN)

This project implements a machine learning workflow to classify breast cancer tumors as either **Malignant** or **Benign** based on cellular characteristics. The model utilizes the **K-Nearest Neighbors (KNN) Classifier** built with `scikit-learn`.

---

## Table of Contents
* [Dataset Overview](#dataset-overview)
* [Project Workflow](#project-workflow)
* [Dependencies](#dependencies)
* [Model Performance](#model-performance)
* [Usage](#usage)

---

## Dataset Overview
The model trains on a dataset containing clinical characteristics of breast cancer tumor nuclei.

* **Total Instances:** 569 patient records
* **Total Features:** 30 continuous numerical features (e.g., radius mean, texture mean, perimeter mean, smoothness, concavity)
* **Target Variable (`diagnosis`):** * `1` = Malignant (Cancer Detected)
  * `0` = Benign (No Cancer)

---

## Project Workflow

### 1. Data Exploration & Cleaning
* Load the dataset (`breast cancer.csv`) and examine its dimensions, structural info, and numerical distributions.
* Unnecessary tracking columns like `id` are removed to prevent overfitting.
* Standardize the string target text values, strip trailing white spaces, and encode categorical values (`M`/`B`) into numeric binary representations (`1`/`0`).

### 2. Dataset Partitioning
* Separate features ($X$) from the target ($y$).
* Split the dataset into **80% Training** and **20% Testing** subsets using stratified sampling to maintain proper class distributions.

### 3. Feature Scaling
* Apply `StandardScaler` to calculate mean and standard deviation variations solely from the training data, scaling both subsets effectively to safeguard against data leakage.

### 4. Model Training & Inference
* Initialize a `KNeighborsClassifier` configured with $k=5$ neighbors.
* Fit the model onto the scaled training features and make test class predictions.

### 5. Predictive System
* Build an inference pipeline capable of reshaping, scaling, and classifying isolated patient samples.

---

## Dependencies

To run this notebook successfully, ensure you have the following Python libraries installed:

## Model Performance

* **Classification Algorithm:** K-Nearest Neighbors ($k=5$)
* **Evaluation Metric:** Accuracy Score
* **Achieved Test Accuracy:** `~95.61%`

---

## Usage

### Running the Notebook
1. Make sure your dataset file is named exactly `breast cancer.csv` and placed in the same directory as the notebook.
2. Execute the notebook cells sequentially to clean the data, train the classifier, and view performance results.

### Predicting New Sample Data
You can test isolated patient data profiles using the predictive step at the end of the script:

```python
# Extract and format an individual patient profile from your dataset
sample = X.iloc[0].values.reshape(1, -1)
sample_scaled = scaler.transform(sample)

# Generate inference decision
prediction = knn.predict(sample_scaled)
if prediction[0] == 1:
    print("Prediction: Malignant (Cancer Detected)")
else:
    print("Prediction: Benign (No Cancer)")

```bash
pip install pandas numpy matplotlib scikit-learn
