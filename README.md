# Parametric Flood Risk Modeling for Climate-Resilient Insurance Triggers

## Overview
Traditional indemnity insurance models often fail to provide the immediate liquidity required for disaster recovery. This project proposes a probabilistic, multidimensional framework for parametric insurance. By utilizing machine learning to predict flood probability across 20 environmental, infrastructural, and socio-political features, we enable a reliable trigger mechanism for near-instant financial support.

A core finding of this research is that governance and institutional quality—specifically political factors, disaster preparedness, and planning quality—are stronger individual predictors of flood probability than purely geophysical measurements. This provides stakeholders with a transparent, evidence-based foundation for automated payout decisions.

---

## Key Features and Findings

### 1. Multidimensional Risk Modeling
This framework moves beyond univariate triggers (e.g., rainfall only) to evaluate a 20-feature matrix across four categories:

- **Physical/Environmental:** Monsoon intensity, topography drainage, siltation  
- **Infrastructure:** River management, dam quality, deteriorating infrastructure, drainage systems  
- **Human/Land Use:** Deforestation, urbanization, agricultural practices  
- **Socio-Political:** Political factors, disaster preparedness, planning quality, climate change impact  

---

### 2. Model Performance and Robustness
We benchmarked three architectures to balance predictive power with auditability:

- **XGBoost:** Achieved the highest predictive performance under normal conditions (R² ~0.67) but demonstrated significant sensitivity to systematic reporting bias in governance data.  
- **Multiple Linear Regression:** Served as the baseline and proved the most robust model under "Distribution Shift" scenarios (simultaneous extreme climate stress and rapid urbanization).  
- **Sparse Optimal Decision Trees (SODT):** Provided a fully interpretable, rule-based benchmark but lacked the depth to capture high-dimensional additive risk.  

---

### 3. Automated Payout Mechanism
To minimize "basis risk"—the discrepancy between insurance payouts and actual losses—we implemented a Four-Tier Payout Structure:

| Predicted Probability | Payout Percentage | Operational Phase        |
|----------------------|------------------|--------------------------|
| < 0.50               | 0%               | Monitoring / Baseline    |
| 0.50 – 0.70          | 25%              | Early Mobilization       |
| 0.70 – 0.85          | 60%              | Major Flood Response     |
| > 0.85               | 100%             | Catastrophic Event       |

---

## Methodology

### Distribution Shift Analysis
To simulate non-stationary climate conditions, models were tested on a "shifted" subset where Climate Change and Urbanization simultaneously exceeded their 75th percentile thresholds. While XGBoost remained the most accurate for these high-risk subsets, the analysis revealed a tendency for models to slightly under-predict probability as conditions intensified, suggesting a need for model recalibration in extreme environments.

---

### Interpretability (SHAP)
We utilized SHapley Additive exPlanations (SHAP) to decompose model outputs. This provides a mathematically grounded audit trail for every payout decision, ensuring that the model logic is consistent with established hydrological and institutional risk principles.

---

### Noise Sensitivity
Experiments demonstrated that systematic reporting bias in socio-political features is 5–10x more destructive to model accuracy than random sensor noise. This confirms that the reliability of parametric triggers depends more on the integrity of governance data than on the precision of physical sensors.

---

### Stakeholder Optimization
We identified optimal trigger thresholds based on stakeholder priorities:

- **Reinsurance Underwriters:** Optimal threshold of 0.556 to minimize unnecessary payouts (false positives).  
- **Disaster Management Agencies:** Optimal threshold of 0.495 to prioritize disaster detection (minimizing false negatives).  

---

## Repository Structure

```plaintext
├── data/                                # Processed datasets (Synthetic proof-of-concept)
│   ├── flood_test_scaled.csv
│   ├── flood_train_scaled.csv
│   ├── flood.csv
│   ├── noise_experiment_results.csv
│   └── test_predictions_for_trigger.csv
├── 00_preprocessing_noise.ipynb         # Data cleaning, VIF analysis, and noise injection
├── 01_modeling.ipynb                   # Regression, XGBoost, and SODT implementation
├── 02_distribution_shift.ipynb         # Evaluation under extreme climate scenarios
├── 02_feature_importance.ipynb         # SHAP analysis and feature ranking
├── 03_payout_trigger.ipynb             # Threshold optimization and payout simulation
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
- Lingyue Hao: Climate Robustness and Ethics Lead
- He Jiang: Lead Model Architect
- Ammy Lin: Project Manager and Risk Strategist
- Myla Simmons: Feature IMportance Lead
- Anvita Suresh: Lead Data Engineer

## Acknowledgments
This project was completed for IDS705: Machine Learning with Professor Kyle Bradbury at Duke University. 

## Ethical Considerations
This model is a proof-of-concept utilizing synthetic data. Real-world deployment requires migrating to institutionally validated meteorological data (e.g., NOAA) and infrastructure records. This is critical to prevent algorithmic bias against infrastructure-poor or underserved regions and to ensure the financial sustainability of the insurance pool.