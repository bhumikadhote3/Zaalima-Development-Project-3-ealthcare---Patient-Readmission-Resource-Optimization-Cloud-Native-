# Zaalima-Development-Project-3-ealthcare---Patient-Readmission-Resource-Optimization-Cloud-Native-
MediFlow Cloud is a cloud-native healthcare analytics project using AWS S3, Glue, and Athena to analyze patient data. It tracks readmissions, Average Length of Stay (ALOS), and resource utilization. The solution enables cost-efficient, serverless data processing and provides insights through interactive dashboards.


# MediFlow Cloud – Healthcare Data Lake & Analytics Dashboard

# 📌 Project Overview

MediFlow Cloud is a Healthcare Data Analytics Project built using AWS and Power BI. The project focuses on designing a scalable data pipeline to process, clean, analyze, and visualize patient healthcare data.

It demonstrates real-world implementation of a data lake architecture using AWS services and business intelligence tools.

# 🎯 Objectives
Build a cloud-based data lake using Amazon S3
Perform schema detection using AWS Glue
Query large datasets using Amazon Athena
Clean and transform healthcare data
Create an interactive dashboard using Power BI
Generate insights on patient readmissions and hospital trends

# 🏗️ Architecture
S3 (Raw Data Storage)
        ↓
AWS Glue Crawler
        ↓
Glue Data Catalog
        ↓
Amazon Athena (SQL Queries)
        ↓
Power BI Dashboard

# 🛠️ Tools & Technologies
Amazon S3 – Data Lake Storage
AWS Glue – Data Catalog & Crawler
Amazon Athena – Serverless SQL Query Engine
Power BI – Data Visualization
SQL – Data Cleaning & Analysis

# 📂 Dataset Description

The dataset contains hospital patient records including:

Patient ID
Gender
Age Group
Admission Type
Hospital Stay Duration
Number of Medications
Diagnoses Count
Readmission Status

Missing values (?) were handled during data cleaning.

# 🔄 Project Workflow
🔹 1. Data Ingestion
Uploaded dataset to S3:
s3://mediflow-cloud-data-lake/raw/

🔹 2. Data Cataloging
Created AWS Glue crawler
Generated table:raw

🔹 3. Data Cleaning (Athena)
SELECT 
    encounter_id,
    patient_nbr,
    NULLIF(weight, '?') AS weight
FROM raw;

🔹 4. Create Clean Table
CREATE TABLE clean_data AS
SELECT 
    encounter_id,
    patient_nbr,
    race,
    gender,
    age,
    NULLIF(weight, '?') AS weight,
    admission_type_id,
    time_in_hospital,
    num_lab_procedures,
    num_medications,
    number_diagnoses,
    diabetesmed,
    readmitted
FROM raw;

🔹 5. Data Analysis
SELECT readmitted, COUNT(*) 
FROM clean_data 
GROUP BY readmitted;

# 📊 Dashboard Features
Total Patients KPI
Average Length of Stay
Readmission Distribution
Age Group Analysis
Hospital Stay Duration
Gender Filter

# 📸 Screenshots
S3 Bucket
Glue Crawler
Athena Queries
Power BI Dashboard

# 📈 Key Insights
Majority of patients are not readmitted
Average hospital stay is around 4–5 days
Certain age groups show higher admission rates
Data cleaning improved analysis accuracy

# ⚠️ Challenges Faced
Handling missing values (?)
AWS Glue & Lake Formation permission errors
Understanding Athena query execution

# ✅ Solutions
Used NULLIF() for data cleaning
Configured IAM roles properly
Used Athena for serverless querying

# 🚀 Future Improvements
Add Machine Learning predictions
Automate pipeline using AWS Glue Jobs
Real-time data streaming
Advanced dashboards
