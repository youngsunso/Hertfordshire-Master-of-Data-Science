This repository contains a machine learning pipeline designed to predict the outcomes  
(Fail / Moderate / Success) of international development projects.  
The model integrates ex-ante project information with institutional and macro-financial  
indicators, providing both **predictive accuracy** and **interpretability**—crucial for  
development banks that must make lending decisions under uncertainty.



##  Key Features

###  Multiclass Outcome Prediction  
- Fail (0) / Moderate (1) / Success (2)  
- MLP (Multilayer Perceptron) optimized via Optuna  
- Probability calibration (Isotonic)

###  Comprehensive Feature Set  
Includes both project-level & country-level variables:
- **WGI governance indicators (6)**  
- **OECD Country Risk**  
- **GDP per capita, GDP growth, inflation**  
- **Project size (ordinal + log midpoint)**  
- **Sector (One-hot encoded)**  
- **Approval Year**

###  Full Explainability (SHAP)  
- Global feature importance  
- Class-level SHAP analysis  
- Interaction plots centered on Rule of Law  
- Interpretation for Fail and Success classes

###  Risk Warning Module  
A SHAP-based interpretation tool that generates:
- Failure probability  
- Top risk-increasing and risk-reducing factors  
- Human-readable risk notes

##  Model Overview

### **Algorithms Compared**
- Decision Tree  
- Random Forest  
- XGBoost  
- **MLP (Best Performance)**  
  - hidden_layer_sizes = (40, 200)  
  - calibrated with CalibratedClassifierCV (isotonic)

### **Evaluation Metrics**
- Accuracy  
- Macro-F1  
- Weighted F1  
- Confusion Matrix (per class)

The **MLP model** achieved the highest macro-F1.


##  SHAP Explainability Highlights

### **Top Global Drivers**
1. Project Size (log)  
2. Voice & Accountability  
3. Approval Year  
4. Rule of Law  
5. Country Risk  
6. GDP per Capita  

### **Key Insights from Interaction Analysis**
- High ROL can increase failure probability depending on context  
- Low ROL + strong macro fundamentals → success-leaning  
- High ROL + high income/low risk → can still be failure-leaning  
- Confirmed strong nonlinear interactions among features  


## Risk Warning Module

A lightweight SHAP-based tool that gives:
- Failure probability for an individual project  
- Top positive/negative SHAP factors  
- A narrative summary for decision-makers  

This is particularly useful for **development banks**, which often must finance  
high-risk projects; the module highlights factors that require ongoing monitoring  
throughout implementation.
Useful for ex-ante screening and mid-implementation monitoring.

