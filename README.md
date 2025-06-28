# CDSS_Labs: ASCVD Risk Interpreter

This project is a **Cardiovascular Disease (CVD) Risk Interpreter** based on the **ASCVD risk score and CVD lab results** of a patient. It is built using **Python, FastAPI, and PostgreSQL** to assist healthcare professionals in generating primary and biomarker-based care plans efficiently.

---

## 🚀 Features

- **Patient Management:** Store and manage patient demographic data securely.
- **ASCVD Risk Score Interpretation:** Accept ASCVD risk scores, calculate risk categories, and generate personalized care plans.
- **Lipid Biomarker Analysis:** Accept biomarker values, compute risk categories, and generate detailed care plans.
- **Automatic Unit Conversion:** Converts lipid biomarker units from mmol/L to mg/dL if needed.
- **Structured Care Plan Generation:**
  - **Actions:** Directive prescription actions.
  - **Medications:** Decision support with prioritization.
  - **Rationale:** Clinical reasoning for recommendations.
  - **Recommendations:** Lifestyle and treatment plans.
  - **Alternatives:** Alternative medications and lifestyle adjustments.
- **Robust Exception Handling:** Ensures stability with clear validation and error handling.

---

## 🩺 Data Fields Accepted

- **MRN** (Medical Record Number)
- **Patient Name**
- **Age**
- **Sex**
- **ASCVD Risk Score**
- **Biomarkers:**
  - HDL Cholesterol
  - LDL Cholesterol
  - Lipoprotein(a) [LP(a)]
  - Apolipoprotein B [ApoB]
  - Triglycerides
  - High-sensitivity C-reactive protein [hs-CRP]
  - Units: mg/dL (auto-converts from mmol/L if provided)

---

## 📡 API Endpoints

### 1️⃣ Create Patient
- **URL:** `/patient`
- **Method:** `POST`
- **Request Model:** `PatientModel`
- **Response Model:** `PatientModel`
- **Description:** Creates and stores a new patient record.

---

### 2️⃣ Submit ASCVD Risk Score
- **URL:** `/ascvd_risk`
- **Method:** `POST`
- **Request Model:** `RiskScoreModel`
- **Response Model:** `ResponseRiskScoreModel`
- **Description:** Accepts ASCVD risk score, calculates risk category, generates and stores care plan.

---

### 3️⃣ Submit Lipid Biomarkers
- **URL:** `/lipid_biomarkers`
- **Method:** `POST`
- **Request Model:** `LipidBiomarkersModel`
- **Response Model:** `ResponseLipidBiomarkersModel`
- **Description:** Accepts lipid biomarker data, calculates risk categories, generates and stores a care plan.

---

## 🐳 Deployment with Docker

### Prerequisites
- [Docker](https://www.docker.com/get-started) installed on your system.

---

### Build and Run Containers

1️⃣ Open your terminal and navigate to your project root (where `Dockerfile` and `docker-compose.yml` are located).

2️⃣ Build and start the application:

```bash
docker-compose build
docker-compose up
```
---

## 🗄️ Apply Database Migrations (Alembic)

Run the following commands to apply migrations for your PostgreSQL database:

```bash
docker-compose run app alembic revision --autogenerate -m "New Migration"
docker-compose run app alembic upgrade head
```
---

## 🗄️ Database Access

- **PostgreSQL:** Data storage for patient, ASCVD, and biomarker data.

- **PGAdmin:**
  - **URL:** [http://localhost:5050](http://localhost:5050)
  - **Username:** `admin@admin.com`
  - **Password:** `password`

---

## 🛠️ Tech Stack

- **Backend:** Python, FastAPI
- **Database:** PostgreSQL
- **Containerization:** Docker, Docker Compose
- **Migrations:** Alembic
- **Admin Interface:** PGAdmin

---

