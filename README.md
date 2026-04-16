# Parametric Flood Risk Modeling for Climate-Resilient Insurance Triggers

## Overview
The frequency of extreme weather events is outpacing traditional insurance models’ ability to provide timely relief. Manual claim adjustments can take months, leaving vulnerable populations without capital. Our project aims to address this liquidity gap by utilizing a machine learning model that predicts flood probability based on environmental and infrastructure features. By creating a reliable trigger, we can enable parametric insurance products that provide near-instant financial support to affected regions.

## Problem Statement
The widening "protection gap" in disaster insurance is driven by a fundamental conflict between speed and accuracy. While parametric insurance offers the speed needed for immediate recovery, its adoption is hindered by basis risk—the discrepancy between an insurance payout and the actual loss experienced.

Current industry triggers are often univariate (e.g., rainfall only) and deterministic, failing to account for the physical "ground truth" of a disaster. For instance, a high-rainfall event may not cause a flood in resilient areas, while a moderate event could be catastrophic where infrastructure like dams or drainage systems are degraded. This project addresses this "protection vacuum" by developing a multidimensional, probabilistic framework to solve for basis risk issues, answering:

- Multidimensional Accuracy: Can a machine learning model incorporating 20+ features accurately predict flood probability (in contrast with traditional single-variable triggers)?

- Systemic Risk Drivers: How do infrastructural factors (e.g., Siltation, DamQuality) and socio-political drivers interact to influence regional disaster outcomes?

- Regulatory Defensibility: Can high-performance "black-box" models (XGBoost) be made transparent and audit-ready through interpretability frameworks (SHAP/SODT)?

## Project Objectives
* **Multidimensional Risk Modeling:** Evaluate 20+ distinct features including monsoon intensity, deforestation, urbanization, and infrastructure quality.
* **Model Benchmarking:** Compare a Multiple Linear Regression baseline against **XGBoost** and **Sparse Optimal Decision Trees (SODT)**.
* **Interpretability & Defensibility:** Leverage **SHAP (SHapley Additive exPlanations)** to provide an audit trail for stakeholders and regulators.
* **Robustness Testing:** Simulate **distribution shifts** caused by climate change and rapid urbanization to evaluate model performance under future "tail event" conditions.

## Repository Contents
```text
├── data/               # Processed environmental and socio-political datasets
├── 00_preprocessing_noise.ipynb
├── 01_modeling.ipynb
├── 02_distribution_shift.ipynb
├── 02_feature_importance.ipynb
├── 03_payout_trigger.ipynb
├── LICENSE
└── README.md
```
## Getting Started

### Prerequisites
- Python 3.9+
- XGBoost, Scikit-Learn, SHAP, Matplotlib

### Installation
```
git clone https://github.com/ammylin/IDS705_Final_Project.git
cd parametric-flood-modeling
pip install -r requirements.txt
```

## Contributors
- Lingyue Hao
- He Jiang
- Ammy Lin
- Myla Simmons
- Anvita Suresh

## Acknowledgments
This project was completed for IDS705: Machine Learning with Professor Kyle Bradbury at Duke University. 