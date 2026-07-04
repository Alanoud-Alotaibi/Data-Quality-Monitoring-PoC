# Clinic Data Quality Audit & Monitoring System

A Python-based Data Quality Monitoring pipeline that automatically profiles, validates, and flags anomalies in messy healthcare datasets.

## Project Deliverables
- 📄 **[Detailed Project Report (PDF)](MessyClinicAppointments_Report.pdf)**
- 📊 **[Project Presentation Slides (PDF)](Messy_Clinic_Appointment_DataSet_Presentation%20(1).pdf)**

Hi! This is a Data Quality Monitoring project we built using Python and Pandas.

For this project, we acted as a Data Quality Analyst tasked with finding errors in a simulated healthcare database. We used the **[Messy Clinic Appointments Dataset](https://www.kaggle.com/datasets/nudratabbas/messy-clinic-appointments-dataset)** from Kaggle, which definitely lives up to its name, to build a prototype monitoring pipeline that catches bad data before it ruins a database.

## Tools Used
* Python
* Pandas for Data profiling and rule enforcement
* Matplotlib for Visualizing the failed records
* Google Colab

## What the Code Actually Does
We wrote a script that automatically scans incoming clinic data and flags rows that fail four major industry data quality rules:

1. **Completeness:** Are there missing patient names?
2. **Uniqueness:** Did the system generate duplicate Patient IDs?
3. **Validity:** Are the ages logically possible (0-120)? Did currency symbols (£, $) accidentally get typed into the billing amounts? Are genders formatted strictly as 'Male' and 'Female'?
4. **Consistency:** Do the appointment dates follow a strict format?

## The Biggest Finding
While running our consistency checks, our code flagged an incredible **92.4% failure rate** in the `appointment_date` column. 

After digging into the data, we realized the clinic's front-end system doesn't have any data validation. Receptionists were just typing dates into a free-text box in dozens of different formats (like "12-Jun-2024" or "May 18"). 

**Our Recommendation:** The permanent fix for this isn't just cleaning the data after the fact; it's changing the UI to use a strict Calendar Date-Picker so users are forced into a standardized format right at the source.

## Future Improvements
This project was built entirely in pure Pandas to serve as a fast Proof of Concept (PoC). If we were to scale this up for a real enterprise hospital, we would migrate these exact Python rules into a dedicated testing framework like Great Expectations and automate the daily runs using Airflow.

---
### Project Results:

### 1. Age Outliers Analysis
We generated an outlier boxplot for the `age` attribute:

![Age Outliers](age_outliers.png)

### 2. Quality Checks Implementation
We visualized the failed records count using two formats:

* **Detailed Quality Checks**
  ![IS346 Quality Checks](is346_quality_checks.png)

* **Data Quality System Summary**
  ![Data Quality System](data_quality_system.png)

### 3. Data Quality Metrics Dashboard
This overall metrics summary visualizes our completeness, uniqueness, validity, consistency, and general quality score:

![Overall Data Quality Dashboard](overall_data_quality_dashboard.png)

---
## Contributors

- **Alanoud Alotaibi**  
  GitHub: https://github.com/Alanoud-Alotaibi
- **Najd Altamimi**  
  GitHub: https://github.com/najdalt1
