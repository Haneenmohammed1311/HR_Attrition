<div align="center">

# 📈 HR Analytics — Employee Attrition & Performance
### Predict. Understand. Retain.

*"Value your people, or watch them leave"*

<br/>

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat-square&logo=xgboost&logoColor=white)](https://xgboost.readthedocs.io)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://streamlit.io)
[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![Samsung SIC](https://img.shields.io/badge/Samsung%20Innovation%20Campus-1428A0?style=flat-square&logo=samsung&logoColor=white)](https://samsung.com)

<br/>

[![Kaggle Notebook](https://img.shields.io/badge/📓%20View%20Notebook-Kaggle-20BEFF?style=for-the-badge&logo=kaggle)](https://www.kaggle.com/code/haneenmohammed13/hr-employee-attrition)

</div>

---

## 📌 Overview

Employee attrition is one of the biggest hidden costs for any company. Replacing an employee is not only expensive — it also leads to loss of valuable skills, experience, and productivity.

**Is it mainly influenced by salary? Does tenure play a role? Or are there other hidden factors?**

This project is a full end-to-end **HR analytics pipeline** that answers these questions using machine learning. It identifies employees at risk of leaving, uncovers the key drivers behind attrition, and delivers a **deployed prediction tool** that HR teams can use in real time.

> Developed as part of **Samsung Innovation Campus (SIC)** — under supervision of **Eng. Farah Mostafa**.

---

## 🎯 Problem Statement

Organizations face significant challenges in retaining talent. Attrition leads to:
- High recruitment and onboarding costs
- Loss of institutional knowledge and productivity
- Team disruption and reduced morale

**Objective:** Build a machine learning system that predicts whether an employee is likely to leave, and surface the most actionable factors driving that decision — enabling data-driven retention strategies.

---

## 👥 Target Audience

| Audience | How They Benefit |
|---|---|
| 🏢 **HR Managers** | Identify at-risk employees and take preventive actions early |
| 📊 **Data Analysts** | Use insights for better workforce planning and retention strategies |

---

## 📊 Dataset

- **Name:** IBM HR Employee Attrition Dataset
- **Shape:** 1,470 rows × 35 columns
- **Target variable:** `Attrition` (Yes / No)
- **Class imbalance:** Dataset is unbalanced — addressed with SMOTEENN

**Key features used:**

| Feature | Why It Matters |
|---|---|
| `MonthlyIncome` | Salary influence on attrition |
| `JobLevel` | Seniority and growth opportunity |
| `TotalWorkingYears` | Experience and loyalty |
| `YearsAtCompany` | Tenure and stability |
| `Age` | Younger employees show higher attrition |
| `YearsWithCurrManager` | Management relationship quality |
| `OverTime` | Work-life balance impact |
| `JobSatisfaction` | Direct link to motivation |
| `WorkLifeBalance` | Satisfaction with personal time |
| `DistanceFromHome` | Commute burden |

---

## 🛠️ Technical Approach

### 1️⃣ Preprocessing Pipeline

```
Raw Data (1470 × 35)
    ↓
Create Categorical Bins     → Group numerical data into human-friendly categories
    ↓
Drop Unspecific Columns     → Remove columns with only one unique value
    ↓
Apply Encoding              → Convert categorical features to numerical format
    ↓
Standard Scaling            → Normalize all variables to the same scale
```

### 2️⃣ Modeling & Hyperparameter Tuning

Trained and compared **4 classification models**, each tuned with GridSearchCV and RandomizedSearchCV:

- Random Forest
- Support Vector Machine (SVM)
- Logistic Regression
- **XGBoost** ← Best performer

### 3️⃣ Class Imbalance Handling

The dataset is heavily imbalanced (most employees stay). We applied **SMOTEENN** — a combined over-and-under-sampling technique — which dramatically improved minority class recall.

### 4️⃣ Feature Selection

Used XGBoost feature importances to identify the **top 10 most influential features** for attrition prediction.

---

## 📈 Results

### Before SMOTEENN

| Metric | Value |
|---|---|
| Train Accuracy | 91.2% |
| Test Accuracy | 85.0% |
| Attrition Recall (class 1) | 0.09 ← very poor |
| Weighted F1 | 0.80 |

### After SMOTEENN ✅

| Metric | Value |
|---|---|
| Train Accuracy | **99.8%** |
| Test Accuracy | **91.8%** |
| Attrition Recall (class 1) | **0.89** ← major improvement |
| Macro F1 | **0.92** |
| Weighted F1 | **0.92** |

> SMOTEENN improved attrition class recall from 0.09 → 0.89, making the model far more useful for HR risk identification.

### 🏆 Top 10 Features by Importance

| Rank | Feature |
|---|---|
| 1 | MonthlyIncome |
| 2 | JobLevel |
| 3 | TotalWorkingYears |
| 4 | StockOptionLevel |
| 5 | Age |
| 6 | DailyRate |
| 7 | YearsAtCompany |
| 8 | MonthlyRate |
| 9 | JobInvolvement |
| 10 | YearsWithCurrentManager |

---

## 🔍 Key Insights

| Finding | Detail |
|---|---|
| 💰 Income | Attrition is highest among employees with very low monthly income (25%+) |
| 🏢 Department | Sales has the highest attrition (20.6%), R&D the lowest (13.8%) |
| 🎓 Education | Below-College and Bachelor's employees leave most frequently |
| 📅 Tenure | Young & new employees show 40% attrition — drops significantly with experience |
| ⚖️ Work-life balance | Poor balance → 31.2% attrition vs 14–18% for those with good balance |
| 📚 Training | No training → 25% attrition; trained employees show 10–15% |
| 😞 Job unhappiness | Very unhappy employees leave at 20% rate |
| ✈️ Frequent travel | 18% attrition among frequent travelers |

---

## 🚀 Deployment

The final XGBoost model was deployed as an interactive **Streamlit web application** where HR teams can input employee details and receive an instant attrition risk prediction with probability scores.

**App inputs:** Age · Monthly Income · Distance From Home · Job Level · Salary Hike % · Years With Manager · Number of Companies Worked · Total Working Years

**App output:** ✅ Low Risk / ⚠️ High Risk + probability score (Stay vs Leave)

[![Kaggle Notebook](https://img.shields.io/badge/📓%20Full%20Notebook-Kaggle-20BEFF?style=flat-square&logo=kaggle)](https://www.kaggle.com/code/haneenmohammed13/hr-employee-attrition)

---

## 🗂️ Repository Structure

```
HR-Attrition-Prediction/
│
├── app.py                    # Streamlit deployment app
├── IBM-Hr-Employee-Attrition.ipynb  # Full analysis notebook
├── Employee-Attrition.pbix   # Power BI dashboard
├── requirements.txt          # Python dependencies
├── README.md
│
├── models/                   # ← Trained model artifacts
│   ├── xgb_model.pkl         # Best XGBoost model
│   ├── scaler2.pkl           # StandardScaler
│   └── xgb_model_col.pkl     # Feature column order
│
└── assets/                   # Screenshots and visuals
    ├── dashboard.png
    └── app_demo.png
```

---

## ⚙️ Installation & Usage

```bash
# 1. Clone the repository
git clone https://github.com/Haneenmohammed1311/HR-Attrition-Prediction.git
cd HR-Attrition-Prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the Streamlit app
streamlit run app.py
```

**requirements.txt should include:**
```
streamlit
xgboost
scikit-learn
pandas
joblib
```

---

## ⚠️ Limitations

| Limitation | Impact |
|---|---|
| Small sample size (1,470 rows) | Reduced statistical significance |
| Missing education level details | Skews insight representation |
| No external factors (economy, market) | Incomplete contextual analysis |
| Limited job role diversity | Incomplete role representation |
| Subjective satisfaction variables | May introduce reporting inaccuracies |

---

## 👥 Team

| Name | LinkedIn |
|---|---|
| **Haneen Mohammed Mousa** | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/haneen-mohammed13) |
| **Faris Abouagour** | 
| **Ahmed Ayman** | 

**Supervisor:** Eng. Farah Mostafa — Samsung Innovation Campus

---

## 📜 License

This project is intended for **educational and research purposes** only.
