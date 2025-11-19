README.md for Brown University Student Academic Dataset Collection
1. Dataset Overview
This repository contains 6 interrelated datasets focused on Brown University student academic performance, learning behaviors, and course contexts. The data supports research on personalized education strategies, learning engagement analysis, and academic outcome prediction—while strictly adhering to privacy regulations and ethical guidelines.
All datasets are structured for compatibility with common data analysis tools (Python Pandas, R, SQL) and include clear column naming conventions for ease of integration.
2. Data Source & Compliance
All datasets are collected and processed in compliance with FERPA regulations, Brown University’s data governance policies, and ethical research standards. Below is the source and compliance details for each dataset:
2.1 raw_static.csv
Data Source: University’s official academic management system
Compliance & Consent Requirements: Collected with explicit, voluntary student consent; anonymized to remove PII (Personally Identifiable Information)
2.2 enrollment.csv
Data Source: University’s official academic management system
Compliance & Consent Requirements: Collected with explicit, voluntary student consent; adheres to FERPA; students may revoke consent at any time
2.3 weekly_activity.csv
Data Source: University’s learning analytics platform
Compliance & Consent Requirements: Collected with explicit, voluntary student consent; logs are aggregated to avoid individual identification
2.4 synthetic_features.csv
Data Source: Derived from aggregated, anonymized student behavior data (from the above 3 datasets)
Compliance & Consent Requirements: Generated via statistical modeling; contains no direct PII; aligns with university ethical research guidelines
2.5 courses.csv
Data Source: University’s public registrar system
Compliance & Consent Requirements: Contains only publicly available course information (no student data); used for contextual reference
2.6 behavior_text.csv
Data Source: Student-submitted educational interactions (discussion forums, reflective writing)
Compliance & Consent Requirements: Collected with explicit consent; PII stripped from text; reviewed and approved by Brown University’s IRB
3. Dataset Details
3.1 raw_static.csv – Student Performance Records
Purpose: Stores static data on student academic performance in exams and coursework.
Key Columns:
student_id: Anonymized unique identifier for students
course_code: Corresponding course (links to courses.csv)
exam_1_score, exam_2_score, final_score: Numeric scores for assessments
grade: Letter grade (A-F) for the course
Data Type: Structured numerical/categorical data
Update Frequency: Static (captures performance for a single academic term)
3.2 enrollment.csv – Student Enrollment Details
Purpose: Tracks student enrollment status in courses and academic programs.
Key Columns:
student_id: Anonymized unique identifier for students
course_code: Enrolled course (links to courses.csv)
enrollment_date: Date of course registration
program: Academic program (e.g., "Computer Science", "Psychology")
enrollment_status: Status (e.g., "Active", "Withdrawn")
Data Type: Structured numerical/categorical data
Update Frequency: Updated weekly during the enrollment period
3.3 weekly_activity.csv – Weekly Learning Activity Logs
Purpose: Records student engagement with learning platforms (e.g., LMS, discussion boards) on a weekly basis.
Key Columns:
student_id: Anonymized unique identifier for students
course_code: Course associated with the activity
week: Academic week (1–16)
login_count: Number of platform logins
assignment_submission_count: Number of on-time submissions
forum_post_count: Number of discussion contributions
Data Type: Structured numerical data
Update Frequency: Updated weekly
3.4 synthetic_features.csv – Derived Learning Pattern Features
Purpose: Provides precomputed, synthetic features to support predictive modeling (e.g., performance risk, engagement level).
Key Columns:
student_id: Anonymized unique identifier
course_code: Associated course
engagement_score: Normalized score (0–100) for learning engagement
performance_risk_flag: Binary flag (0=low risk, 1=high risk) for exam performance
study_consistency_index: Index (0–1) measuring regularity of weekly activity
Data Type: Structured numerical/categorical data
Generation Method: Derived via statistical modeling (e.g., moving averages, clustering) of raw_static.csv and weekly_activity.csv
3.5 courses.csv – Course Catalog Information
Purpose: Serves as a contextual reference for linking student data to course details.
Key Columns:
course_code: Unique course identifier (e.g., "CSCI 1010")
course_name: Full course name (e.g., "Introduction to Computer Science")
department: Academic department (e.g., "Computer Science")
credit_hours: Number of academic credits (e.g., 4)
instructor_id: Anonymized identifier for the course instructor
Data Type: Structured categorical/numerical data
Source: Publicly available from Brown University’s registrar system
3.6 behavior_text.csv – Anonymized Educational Text Data
Purpose: Contains text data reflecting student learning engagement (e.g., discussion contributions, reflective essays).
Key Columns:
text_id: Unique identifier for the text entry
student_id: Anonymized unique identifier
course_code: Course associated with the text
text_type: Type of text (e.g., "forum_post", "reflective_essay")
text_content: Anonymized text (PII like names/emails removed)
submission_date: Date of text submission
Data Type: Unstructured text + structured metadata
Preprocessing: Text is lowercased, with PII (e.g., names, email addresses) stripped via regex filtering
4. Data Usage Guidelines
4.1 Permitted Uses
Research on personalized education strategies (e.g., identifying at-risk students, optimizing learning interventions).
Analysis of learning engagement patterns (e.g., linking forum activity to exam performance).
Development of educational predictive models (with proper validation against raw_static.csv).
4.2 Prohibited Uses
Attempting to re-identify students (e.g., cross-referencing student_id with external datasets).
Using data for commercial purposes (e.g., selling derived features to third parties).
Modifying or republishing behavior_text.csv without IRB approval.
4.3 Citation Requirement
If using these datasets in research publications, please cite:
"Brown University Student Academic Dataset Collection. Brown University Learning Analytics Lab, 2025. Compliant with FERPA and IRB Guidelines."
5. Technical Notes
File Format: All datasets are saved as UTF-8 encoded CSV files for cross-platform compatibility.
Missing Values: Missing data is labeled as NA (numeric columns) or empty strings (text columns); see individual datasets for missing value rates.
Data Joining: Use student_id and course_code as primary keys to join datasets (e.g., enrollment.csv ↔ courses.csv via course_code).
Tools Compatibility: Tested with Python 3.8+ (Pandas 1.5+) and R 4.2+ (readr 2.1+).
6. Contact & Updates
For questions about data access, compliance, or updates, contact the Brown University Learning Analytics Lab at learning.analytics@brown.edu.
Last dataset update: 2023-02-15Next scheduled update: 2025-5-11
