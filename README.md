# Cardiovascular-Decision-Support-System
This is a CVD risk interpreter based on the ASCVD risk score and CVD lab results of a Patient. The application is built using Python, FastAPI and Postgresql database. The end points accept patient's data and has following fields:
MRN: Medical Record Number
Name of the Patient
Age of the patient
Sex of the patient
It accepts the ASCVD Risk score of the patient and a primary careplan is generated based on the risk score,
Ascvd risk
The primary care plan includes, Actions: Directive Actions to be taken for writing prescriptions Medications: Decision support for Medicines, In order to which to target and modifications to be done Rationale: rationale for the recommendations Recommendations: lifestyle and treatment changes Alternatives: Alternative medications/Lifestyle modifications to be considered

It accepts the Biomarkers of the patient and a Biomarker careplan is generated based on the biomarker risk category, -List of Biomarkers accepted:
hdl cholesterol
ldl cholesterol
lipoprotein-a (lp(a))
apolipoprotein-b(apob)
triglycerides
high-sensitivity c-reactive protein
units: mg/dl
The application includes a method to check and convert the units from mmol/L to mg/dl if needed.

The biomarker care plan includes, Actions: Directive Actions to be taken for writing prescriptions Medications: Decision support for Medicines, In order to which to target and modifications to be done Rationale: rationale for the recommendations Recommendations: lifestyle and treatment changes Alternatives: Alternative medications/Lifestyle modifications to be considered

This FastAPI application contains the following endpoints:

POST /patient
URL: /patient HTTP Method: POST Request Model: PatientModel Response Model: PatientModel Description: This endpoint is used to create a new patient record. It expects a JSON request with patient details including MRN (Medical Record Number), name, age, and sex. It then stores the patient data in the database and returns the created patient's details as a response. POST /ascvd_risk

URL: /ascvd_risk HTTP Method: POST Request Model: RiskScoreModel Response Model: ResponseRiskScoreModel Description: This endpoint calculates and stores the ASCVD (Atherosclerotic Cardiovascular Disease) risk score for a patient. It takes the ASCVD score as input, calculates the risk category, and generates a care plan. The risk score and care plan are then stored in the database, and the response includes the calculated risk score and category. POST /lipid_biomarkers

URL: /lipid_biomarkers HTTP Method: POST Request Model: LipidBiomarkersModel Response Model: ResponseLipidBiomarkersModel Description: This endpoint receives lipid biomarker data, including HDL-C, LDL-C, LP(a), triglycerides, Apo B, Apo A1, hs-CRP, and units. It calculates risk categories for each biomarker, generates a care plan, and stores both the biomarker data and care plan in the database. The response includes the calculated risk categories. These endpoints handle different aspects of patient data, cardiovascular risk calculation, and lipid biomarker analysis, allowing users to interact with the application by submitting data and receiving calculated results and care plans. The application also includes exception handling for request validation errors, HTTP exceptions, and unhandled exceptions, ensuring robust error handling.

Prerequisites
Ensure you have Docker installed on your system.

Building the Docker Image
Open a terminal or command prompt.
Navigate to the root directory of your project, where the Dockerfile and docker-compose.yml files are located.
Run the following command to build the Docker image: -docker-compose build -docker-compose up
for postgresql database: -docker-compose run app alembic revision --autogenerate -m "New Migration" -docker-compose run app alembic upgrade head
