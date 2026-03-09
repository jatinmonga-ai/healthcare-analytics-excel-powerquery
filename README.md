# 📊 Patient Readmission Analytics Dashboard
Excel + Power Query | Healthcare Analytics Portfolio Project
Tool: Microsoft Excel | Features: Power Query, Pivot Tables, Interactive Dashboard, Slicers

# 📌 Overview
This project demonstrates a complete data analytics workflow built entirely inside Microsoft Excel —
from raw data ingestion and cleaning using Power Query, to pivot table analysis, to a fully
interactive dashboard with slicers.
The dataset covers 99,492 diabetic patient encounters across 130 US hospitals from 1999 to 2008.
The central question: what factors are associated with a patient being readmitted within 30 days?
This was built as part of a 3-project healthcare analytics portfolio series, with the same dataset
also analysed using an AI pipeline (Julius AI + Mostly AI + Python) and PostgreSQL.

# 🖼️ Dashboard Preview
<img width="986" height="572" alt="Patient Dasboard" src="https://github.com/user-attachments/assets/a33af8c3-28cc-4c3f-8f34-ff4699134e57" />


# 🔧 Tools & Features Used
FeaturePurposePower QueryFull data cleaning — replaced nulls, dropped columns, added calculated columnsPivot Tables6 pivot tables each answering a different analytical questionPivot Charts6 charts built directly from pivot tablesSlicers6 interactive slicers connected to all pivot tables simultaneouslyCustom ColumnsAge Band, Insulin Status, Readmission Status, Readmitted Binary

# 🧹 Power Query Cleaning Steps
Starting from the raw 101,766-row CSV file, the following cleaning was applied entirely inside Power Query — no manual editing, no formulas, no external tools:

Replaced all ? placeholder values with proper nulls across the entire dataset
Removed 2 ID columns (encounter_id, patient_nbr) — no analytical value
Removed 5 high-missing columns — weight (96.9% missing), payer_code (39.6%), medical_specialty kept but nulls handled, max_glu_serum (94.7%), A1Cresult (83.3%)
Removed 9 near-zero variance medication columns (99%+ values were "No")
Removed 3 diagnosis code columns (diag_1, diag_2, diag_3) — 700+ unique codes each, too high-cardinality
Filtered out rows with null race and invalid gender values
Renamed 10 columns for readability (e.g. time_in_hospital → Days in Hospital)
Added 4 custom calculated columns:

Readmitted Binary — 1 if readmitted within 30 days, 0 otherwise
Readmission Status — readable label (Not Readmitted / Readmitted < 30 Days)
Age Band — grouped age ranges (Young ≤35 / Middle Aged 36-60 / Senior 61-80 / Elderly 81+)
Insulin Status — readable label (No Insulin / Steady / Increased / Reduced)



Result: 101,766 rows → 99,492 clean rows | 50 columns → 36 columns

# 📊 Pivot Tables & Charts
### PT 1 — Patient Count by Race & Gender

Rows: Race | Columns: Gender | Values: Total Patients + Total Readmitted
Chart: Clustered Horizontal Bar
Finding: Caucasian patients make up 76,099 of 99,492 records. AfricanAmerican patients are the second largest group at 19,210.

### PT 2 — Hospital Stats by Readmission Status

Rows: Readmission Status | Values: Max Lab Procedures, Max Medications
Chart: Clustered Bar by Admission Type ID
Finding: Readmitted patients consistently show higher lab procedure and medication counts across all admission types.

### PT 3 — Prior Visits by Race

Rows: Race | Values: Max Inpatient Visits, Max Emergency Visits, Max Outpatient Visits
Chart: Clustered Horizontal Bar
Finding: Caucasian patients show the highest absolute prior visit counts due to volume, but per-patient prior inpatient visits are highest among readmitted patients at 1.23 vs 0.57 for non-readmitted.

### PT 4 — Insulin Status for Different Age Groups

Rows: Age Band | Columns: Insulin Status | Values: Patient Count
Chart: Clustered Column (grouped by Age Band)
Finding: Senior (61-80) patients dominate all insulin categories. No Insulin is the most common across all age groups. Reduced insulin patients had the highest readmission rate at 14%.

### PT 5 — Top 10 Medical Specialties by Patient Count

Rows: Medical Specialty (blank filtered out) | Values: Total Patients + Total Readmitted
Chart: Horizontal Bar
Finding: Internal Medicine leads with 14,197 patients, followed by Emergency/Trauma (7,540) and Family/General Practice (7,271).

### PT 6 — Diabetes Medication × Readmission

Rows: On Diabetes Med | Columns: Readmission Status | Values: Patient Count
Chart: Clustered Column
Finding: 76,491 patients (76.9%) were on diabetes medication. Patients on diabetes medication had a slightly higher readmission rate than those not on it.


# 📈 Key Findings
FindingDetailOverall Readmission Rate11.2% of 99,492 patients were readmitted within 30 daysHighest Risk Insulin GroupPatients with reduced insulin had the highest readmission rate at 14%Prior Visits SignalReadmitted patients averaged 1.23 prior inpatient visits vs 0.57 for non-readmitted — over 2x moreDominant Age GroupSenior (61-80) patients made up the largest group at 47,456 recordsTop SpecialtyInternal Medicine treated the most patients — 14,197 encountersOn Diabetes Medication76.9% of all patients were on diabetes medication


#  How to Open & Explore

Download excel/patient_data.xlsx
Open in Microsoft Excel (2016 or later recommended)
Go to the Dashboard sheet
Use the slicers on the right to filter by Race, Age Band, Gender, Admission Type, Diabetes Med, Insulin Status, and Readmission Status
All 6 charts update simultaneously with every slicer click

To view the Power Query steps:

Go to Data tab → Queries & Connections → double click PatientData
The Applied Steps panel on the right shows every cleaning step in order


# 🎓 Dataset
Name: Diabetes 130-US Hospitals (1999–2008)
Source: UCI Machine Learning Repository
Link: https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008
Records: 101,766 raw → 99,492 after cleaning
Features: 50 raw → 36 after cleaning

# 🏆 Skills Demonstrated

Excel Power Query for end-to-end data cleaning without any code
Multi-step data transformation including null handling, column removal, and custom calculated columns
Pivot table design for multi-dimensional analysis
Interactive dashboard design with connected slicers
Healthcare domain knowledge and analytical storytelling


## Part 2 of 3 — Healthcare Analytics Portfolio Series
Project 1: AI Pipeline (Julius AI + Mostly AI + Python) | Project 3: PostgreSQL
