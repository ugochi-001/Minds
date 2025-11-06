# Minds
This is our solution to the 2025 WiGE Hackathon


# Carbon Capture, Utilization, and Storage (CCUS) — Contact Angle Prediction

## 🧠 Project Overview
This project was developed as part of the **WiGE Hackathon 2025**, focusing on **Contact Angle Prediction** for **Carbon Capture, Utilization, and Storage (CCUS)** systems.  
It explores how geological and chemical parameters affect **wettability** in subsurface formations — a critical factor in predicting CO₂ storage efficiency.

The goal: **Predict the contact angle** (a measure of wettability) using physical and chemical properties such as pressure, temperature, salinity, and mineral composition.

---

## 📂 Project Structure

├── Train.ipynb # Exploratory Data Analysis (EDA) ├── minds.ipynb # Feature Engineering and Model Development ├── train.csv # Training dataset ├── test.csv # Test dataset ├── sample_submission.csv # Template for submission └── submission.csv # Model predictions (output)

---

## ⚙️ Key Libraries Used

- **Data Handling:** pandas, numpy  
- **Visualization:** matplotlib, seaborn  
- **Machine Learning:** scikit-learn, XGBoost, LightGBM  
- **Evaluation:** R² score, Mean Squared Error (MSE)

---

## 🔍 Data Overview

**Dataset size:**  
- Training set: 5,000 samples, 7 features  
- Test set: 630 samples, 6 features

**Features:**
| Feature | Type | Description |
|----------|------|-------------|
| `pressure` | Numeric | CO₂ system pressure |
| `temperature` | Numeric | System temperature |
| `salinity` | Numeric | Brine salinity |
| `mineral` | Categorical | Mineral type (e.g., quartz, calcite) |
| `contact_type` | Categorical | Contact condition (advancing/static) |
| `theta0` | Numeric | Initial angle or setup parameter |
| `contact_angle` | Target | Wettability indicator (°) |


## 📊 Exploratory Data Analysis (EDA)

Performed in **`Train.ipynb`**:
- **Distribution Analysis:**  
  Contact angle follows an approximately normal distribution with slight right skew — most values between 20°–80°.
- **Correlation Heatmap:**  
  - Temperature → **strong positive** correlation (+0.74)  
  - Pressure → **moderate positive** correlation (+0.52)  
  - Salinity → **weak positive** correlation (+0.18)  
- **Feature Insights:**  
  - High temperature increases contact angle (CO₂-wet behavior).  
  - Pressure has a moderate effect.  
  - Mineral and contact type show distinct median differences in contact angle.  
- **Visualization Techniques:**  
  - Histograms, scatter plots, box plots, and pairplots for pattern discovery.


## 🧩 Feature Engineering

Implemented in **`minds.ipynb`**:
- **Label Encoding:** Converted categorical features (`mineral`, `contact_type`) into numeric form.
- **Interaction Features:**  
  - `pressure_temp` = `pressure` × `temperature`  
  - `salinity_temp` = `salinity` × `temperature`
- **Scaling:** Standardized numerical features for consistency across models.


## 🤖 Model Development

Three models were trained and compared:

| Model | Avg. R² | Notes |
|--------|----------|-------|
| Random Forest | 0.854 | Strong baseline, good generalization |
| XGBoost | 0.844 | Slightly lower performance, stable |
| LightGBM | **0.859** | Best performing model overall |

**Cross-validation:** 5-Fold  
**Scoring Metric:** R² (Coefficient of Determination)

Final ensemble model combined all three model predictions by averaging results.


## 📈 Results

- **Best Model:** LightGBM (Average R² ≈ 0.86)  
- **Final Prediction:** Ensemble average across RandomForest, XGBoost, and LightGBM.  
- **Output File:** `submission.csv` containing predicted `contact_angle` values for test samples.



## 🚀 How to Run

1. Clone the repository or upload the notebooks to **Google Colab**.
2. Upload the required CSV datasets (`train.csv`, `test.csv`, `sample_submission.csv`).
3. Run `Train.ipynb` for EDA.
4. Run `minds.ipynb` for model training and prediction generation.
5. The final predictions are saved automatically as `submission.csv`.



## 💡 Key Insights

- **Temperature** and **pressure** are dominant predictors of wettability behavior.  
- **Mineral composition** and **contact type** significantly influence contact angle distributions.  
- **Ensemble learning** improves robustness and prediction accuracy across models.



## 🏁 Conclusion

This solution provides a reliable ML pipeline for predicting **contact angles** in CCUS research — combining strong exploratory analysis, engineered features, and ensemble model optimization.  
The workflow can be adapted for other **geological modeling** and **energy transition** challenges involving multiphase fluid interactions.

 
**WiGE Hackathon 2025 Submission**  
