# Patient No-Show Prediction Project

## 📋 Project Overview
This project aims to predict patient no-shows for medical appointments using machine learning. By analyzing anonymized patient appointment data, we develop a model to identify patients likely to miss appointments, enabling healthcare providers to optimize follow-ups and reduce dropouts.

## 🗂️ Dataset
- **Source**: [Kaggle - No-show Appointments](https://www.kaggle.com/joniarroba/noshowappointments)
- **Size**: 110,527 appointments
- **Features**: 14 features including:
  - `PatientId`, `AppointmentID`
  - `ScheduledDay`, `AppointmentDay`
  - `Age`, `Gender`, `Neighbourhood`
  - `Scholarship`, `Hipertension`, `Diabetes`, `Alcoholism`, `Handcap`, `SMS_received`
  - **Target**: `No-show` (Yes = missed, No = attended)

## 🔍 Key Insights from EDA
### Binary Features Analysis
| Feature         | Higher No-show Rate | Insight |
|----------------|---------------------|---------|
| Scholarship     | ✅ Scholarship (1) | Slightly higher no-shows, possibly linked to socioeconomic issues |
| Hypertension    | ❌ No Hypertension (0) | Hypertensive patients are more consistent |
| Diabetes        | ❌ No Diabetes (0) | Diabetics show better adherence |
| Alcoholism      | ⚖️ Similar in both | No significant impact |
| Handicap        | ✅ Higher Handicap (3–4) | No-show rate increases with severity |
| SMS Received    | ✅ SMS Received (1) | Higher no-shows despite SMS — may indicate poor timing or alert fatigue |

### 🧠 Takeaway
Chronic conditions (e.g., hypertension, diabetes) correlate with better adherence. Higher no-show rates among scholarship recipients and highly handicapped patients highlight the need for targeted support. SMS reminders alone may not improve adherence.

## ⚠️ Data Issues
- **Imbalanced Data**: Target variable (`No-show`) is skewed.
- **Invalid Age Values**: `Age` contains a value of -1.
- **Negative Lead Times**: Some records had logically invalid negative lead times (e.g., scheduled after appointment), which were removed.

## 🛠️ Feature Engineering
- **LeadTime**: Created as the difference (in days) between `AppointmentDay` and `ScheduledDay`.
- **Data Cleaning**: Removed records with negative `LeadTime` and invalid `Age` values.

## 📊 Modeling
### Algorithms Used
- Logistic Regression
- Random Forest
- XGBoost (commented in code)

### Techniques
- Label Encoding for categorical variables
- SMOTE for handling class imbalance
- Train-test split for model evaluation
- Metrics: Accuracy, Precision, Recall, F1-score, ROC-AUC

## 🚀 How to Run
1. Install dependencies:
   ```bash
   pip install pandas scikit-learn imbalanced-learn matplotlib seaborn
   ```
2. Download the dataset from Kaggle and update the file path in the notebook.
3. Run the Jupyter notebook `patient-no-show-prediction-eda-feature-engg.ipynb` sequentially.

## 📈 Results
The models are evaluated using standard classification metrics. Key performance insights will be added after model training and evaluation.

## ✅ Conclusions
- Chronic conditions like hypertension and diabetes are associated with better appointment adherence.
- Factors like handicap severity and scholarship status may require targeted interventions.
- SMS reminders did not reduce no-shows as expected, suggesting a need for improved communication strategies.
- Feature engineering (e.g., `LeadTime`) and addressing data quality issues are crucial for model performance.

## 👩‍💻 Author
Developed as part of a case study on patient adherence prediction.
