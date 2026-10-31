# 🫀 HeartDrive — Public Health Demographic Risk Planner & Policy Decision System

<div align="center">

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B.svg)](https://streamlit.io/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E.svg)](https://scikit-learn.org/)
[![GovTech](https://img.shields.io/badge/Domain-Public%20Health%20%26%20GovTech-134E4A.svg)]()
[![Status](https://img.shields.io/badge/Status-Active-00E599.svg)]()

**A dual-portal public health decision-support platform that analyzes population cardiovascular risk across Indian demographic cohorts, identifies geographic disease clusters, and triggers automated civic intervention guidelines.**

</div>

---

## 🏛️ Project Motivation & Public-Interest Impact

Non-communicable diseases (NCDs), particularly cardiovascular conditions, represent one of India's most urgent public health challenges. Municipal health departments and state health missions frequently face resource constraints when deciding where to deploy mobile screening clinics, diagnostic equipment, and vernacular preventive awareness drives.

**HeartDrive** bridges clinical risk prediction with civic health administration:
1. **For Public Health Administrators:** Provides a centralized government analytics terminal to upload regional patient cohorts, evaluate risk factor influence rankings (blood pressure, cholesterol, glucose, lifestyle), segment populations by age and location, and receive automated alert thresholds.
2. **For Citizens:** Provides a self-service intake portal to record baseline biometrics and receive immediate, understandable risk assessments.

---

## 🌟 Key Capabilities & System Architecture

```
                          ┌───────────────────────────┐
                          │   HeartDrive Entry Point   │
                          │        (Streamlit)        │
                          └─────────────┬─────────────┘
                                        │
                 ┌──────────────────────┴──────────────────────┐
                 ▼                                             ▼
     ┌────────────────────────┐                   ┌────────────────────────┐
     │  🏛 Government Portal   │                   │    👥 Citizen Portal    │
     │  (Gov UID & Password)  │                   │   (Aadhar & Password)  │
     └───────────┬────────────┘                   └───────────┬────────────┘
                 │                                             │
      ┌──────────┴──────────┐                       ┌──────────┴──────────┐
      ▼                     ▼                       ▼                     ▼
┌──────────────┐     ┌──────────────┐         ┌──────────────┐     ┌──────────────┐
│ Cohort CSV   │     │ ML Predictive│         │ Biometric    │     │ Historical   │
│ Ingestion    │     │ Engine (LR)  │         │ Intake Form  │     │ Records Log  │
└──────┬───────┘     └──────┬───────┘         └──────────────┘     └──────────────┘
       │                    │
       ▼                    ▼
┌───────────────────────────────────┐
│     Civic Policy Decision Logic   │
│  - Location Risk Ranking (Cities) │
│  - Demographic Slices (Age/Gender)│
│  - Automated Alert Thresholds:    │
│    • Urgent (>=75% risk)          │
│    • Warning (50-74% risk)        │
│    • Caution (25-49% risk)        │
└───────────────────────────────────┘
```

### 1. 🏛️ Government Health Administration Panel
* **Population Cohort Processing:** Ingests large-scale demographic and clinical CSV datasets (`cardio_train.csv`, 70,000+ records) and maps variables across systolic/diastolic blood pressure (`ap_hi`, `ap_lo`), cholesterol, glucose, smoking, and physical activity.
* **Feature Influence Ranking:** Computes regression coefficient influence curves to show administrators which physical variables are driving cardiovascular risk in specific populations.
* **Geographic Prevalence Analysis:** Compares disease probability distributions across major municipal clusters (Bengaluru, Mumbai, Delhi, Chennai, Pune).
* **Multivariate Demographic Filtering:** Slices population risk dynamically across age bands (30–40, 40–50, 50–60, 60–70) and gender to pinpoint high-vulnerability cohorts.
* **Automated Intervention Thresholds:**
  - 🚨 **Urgent ($\ge 75\%$ High Risk):** Triggers recommendation for immediate mobile screening camps and specialized clinical deployment.
  - ⚠️ **Warning ($50\%\text{--}74\%$ Risk):** Recommends preventive community monitoring and dietary intervention drives.
  - 🔍 **Caution ($25\%\text{--}49\%$ Risk):** Suggests localized vernacular awareness campaigns.
  - ✅ **Low Risk ($<25\%$ Risk):** Baseline public health maintenance.

### 2. 👥 Citizen Self-Service Portal
* **Biometric Intake:** Simple, accessible form capturing age, gender, height, weight (BMI calculation), blood pressure readings, and lifestyle factors.
* **Aadhar-Keyed Authentication:** Enables recurring health checkups and longitudinal risk tracking across visits.
* **Local Audit Logging:** Maintains client-side and authenticated server logs (`user_log.csv`, `user_data.csv`) for continuity of care.

---

## 📁 Repository Structure

```
Heartdrive/
├── cardio_train.csv       # Training dataset (70,000+ cardiovascular demographic records)
├── cardiotest.csv         # Validation and test cohort dataset
├── heart.py               # Complete dual-portal Streamlit application & ML engine
└── README.md              # Project documentation & public health architecture
```

---

## ⚡ Quick Start for Developers & Health Teams

### Prerequisites
- Python 3.10 or higher
- `pip` package manager

### 1. Clone & Set Up Environment
```bash
git clone https://github.com/ChAakshay/Heartdrive.git
cd Heartdrive

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install required packages
pip install streamlit pandas numpy scikit-learn matplotlib seaborn
```

### 2. Launch the Application
```bash
streamlit run heart.py
```
The terminal will open an interactive web browser session at `http://localhost:8501`.

### 3. Usage Walkthrough
1. **Government Portal:** Click **🏛 Government Portal**, register a test administrator UID, and upload `cardiotest.csv` to explore population-wide prevalence graphs and automated intervention recommendations.
2. **Citizen Portal:** Click **👥 User Portal**, register with an ID/Aadhar, input sample health indicators, and review the personal risk prediction.

---

## 🛡️ Data Privacy & Ethical Considerations
- Clinical demographic records are processed locally in-memory during active sessions.
- Biometric inputs avoid unencrypted network transmission, adhering to public health data minimization guidelines.

---

<div align="center">
  <sub>Authored by <b><a href="https://github.com/ChAakshay">CH Aakshay</a></b> • Built for public interest and preventive civic health engineering.</sub>
</div>
