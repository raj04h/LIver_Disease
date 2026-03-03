# DrCure: Liver Disease Prediction Module 🏥

This repository contains the machine learning core for the **DrCure** clinical diagnostic module. It is designed to assist healthcare professionals in the early detection of liver disorders by analyzing routine laboratory blood tests.

---
# Result Preview
<img width="326" height="87" alt="image" src="https://github.com/user-attachments/assets/b826d3d1-8986-4196-a5b4-16906ae7c492" />

## 📈 Performance Summary
The module prioritizes reliability in a clinical setting, achieving high scores across all key metrics:
* [cite_start]**Accuracy**: 88% [cite: 519]
* [cite_start]**ROC-AUC**: 0.93 (indicating excellent separability between healthy and diseased cases) [cite: 520]
* [cite_start]**F1-Score**: 0.86 (balancing precision and recall to minimize missed diagnoses) [cite: 521]

---

## 🛠️ Technical Methodology

### 1. Data Preprocessing & Balancing
* [cite_start]**Handling Imbalance**: Applied **SMOTE** (Synthetic Minority Over-sampling Technique) to address the 40:60 diseased-to-healthy class ratio in the dataset[cite: 361, 488].
* [cite_start]**Imputation**: Used **Median Imputation** for laboratory features to ensure robustness against extreme clinical outliers[cite: 490, 491].
* [cite_start]**Scaling**: Applied **StandardScaler** to continuous features to accelerate model convergence[cite: 492].

### 2. Model Selection: XGBoost vs. DNN
Two primary architectures were evaluated for this tabular data task:
* [cite_start]**XGBoost (Selected)**: Chosen for its superior handling of heterogeneous clinical data and built-in regularization to prevent overfitting[cite: 460, 462, 523].
* [cite_start]**Deep Neural Network (DNN)**: A feed-forward Keras network (128 → 64 ReLU units) with Dropout and Early Stopping was tested but showed higher sensitivity to hyperparameter tuning[cite: 466, 469].

---

## 🔍 Model Interpretability (Feature Importance)
The XGBoost model identifies the most critical clinical markers contributing to a diagnosis:
1. [cite_start]**Direct Bilirubin (42%)**: Primary indicator of liver excretory function[cite: 183].
2. [cite_start]**SGPT/ALT (28%)**: Key marker for hepatocellular injury[cite: 183].
3. [cite_start]**Albumin (10%)**: Reflects the liver's synthetic capacity[cite: 183].

[cite_start]These findings align with standard medical diagnostic knowledge, ensuring the AI's "logic" is transparent to clinicians[cite: 184].

---

## 🚀 Mobile Deployment Architecture
The model is integrated into a cross-platform mobile application:
* [cite_start]**Backend**: Served via a **Python Flask API**[cite: 198].
* [cite_start]**Optimization**: The model is serialized as a `.pkl` file and optimized for low-latency inference on mobile devices[cite: 198, 206].
* [cite_start]**Local Storage**: Uses an Android **Room Database** to log patient sessions and historical predictions for auditability[cite: 199].

---

## 📁 File Structure
* [cite_start]`liverfinalcapstone.ipynb`: Full training pipeline including Grid Search and SMOTE implementation[cite: 463].
* [cite_start]`models/`: Serialized XGBoost and DNN models ready for API integration[cite: 198].
* `requirements.txt`: Necessary libraries (XGBoost, Scikit-learn, Imbalanced-learn, etc.).
