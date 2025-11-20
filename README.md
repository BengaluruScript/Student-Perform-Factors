# Brown University Student Academic Dataset Collection

## 1. Dataset Overview
This repository contains 6 interrelated datasets focusing on Brown University students' academic performance, learning behaviors, and course context information. Some dimensions of the data are built based on Brown University's public academic datasets (Access link: https://oir.brown.edu/institutional-data/common-data-set), while unpublished data dimensions are supplemented by legally collected offline data and generated using reasonable regression analysis. The datasets support research on personalized education strategies, learning engagement analysis, and academic outcome prediction, while strictly adhering to privacy regulations and ethical guidelines.

All datasets are structured for compatibility with common data analysis tools (Python Pandas, R, SQL) and use clear column naming conventions for easy integration.

---

## 2. Data Source & Compliance
The collection, supplementation, and processing of all datasets comply with FERPA (Family Educational Rights and Privacy Act), Brown University's data governance policies, and academic research ethical standards. The source and compliance details of each dataset are as follows:

### 2.1 raw_static.csv
- **Data Source**: Core data is derived from Brown University's public academic datasets; unpublished detailed grade dimensions are collected legally offline, and supplementary data is generated using linear regression models to ensure consistency with the distribution of public data.
- **Compliance & Consent Requirements**: Public data follows Brown University's public data usage specifications; offline collected data is obtained with students' explicit and voluntary consent; all data is anonymized to remove Personally Identifiable Information (PII).

### 2.2 enrollment.csv
- **Data Source**: Basic enrollment information is from Brown University's public academic datasets; unpublished dynamic enrollment status (e.g., phased withdrawal records) is collected legally offline and supplemented with logistic regression analysis.
- **Compliance & Consent Requirements**: Public data complies with FERPA and public data usage specifications; offline collected data is obtained with students' explicit consent (which can be withdrawn at any time); supplementary data strictly maintains the statistical characteristics of the original data.

### 2.3 weekly_activity.csv
- **Data Source**: Partial high-frequency behavior data (e.g., login count) is extracted from Brown University's public academic datasets; low-frequency interaction data (e.g., usage records of niche platforms) is collected legally offline and supplemented using ridge regression models to ensure the rationality of behavior patterns.
- **Compliance & Consent Requirements**: Public data follows platform usage specifications; offline collected data is obtained with students' explicit and voluntary consent; logs are aggregated; supplementary data does not alter original behavior trends.

### 2.4 features.csv
- **Data Source**: Derived from Brown University's public academic datasets, legally collected offline data, and regression analysis supplementary data, after aggregation and anonymization.
- **Compliance & Consent Requirements**: Generated through statistical modeling (including integration of regression analysis results), contains no direct PII, and complies with the university's academic research ethical guidelines and public data usage specifications.

### 2.5 courses.csv
- **Data Source**: Core course information (course code, name, credit hours) is from Brown University's public registrar system and public academic datasets; partial historical course details (e.g., association with instructors of early courses) are collected legally offline and supplemented with polynomial regression.
- **Compliance & Consent Requirements**: Only contains publicly available or legally collected course background information (no student personal data); supplementary data is verified with registrar system information to ensure accuracy.

### 2.6 behavior_text.csv
- **Data Source**: Public discussion forum texts are from Brown University's public academic datasets; unpublished text data such as reflective writing is collected legally offline; after text feature extraction, missing samples are supplemented using topic model-based regression generation methods.
- **Compliance & Consent Requirements**: Public texts follow copyright usage specifications; offline collected texts are obtained with students' explicit consent; all texts are stripped of PII and approved by Brown University's Institutional Review Board (IRB).

---

## 3. Dataset Details
### 3.1 raw_static.csv – Student Performance Records
- **Purpose**: Stores static academic performance data of students in exams and coursework.
- **Key Columns**:
  - `student_id`: Anonymized unique identifier for students
  - `course_code`: Corresponding course (links to courses.csv)
  - `exam_1_score`, `exam_2_score`, `final_score`: Numeric scores for various assessments (including public data and regression-supplemented data)
  - `grade`: Letter grade (A-F) for the course
- **Data Type**: Structured numerical/categorical data
- **Update Frequency**: Static (captures performance for a single academic term)

### 3.2 enrollment.csv – Student Enrollment Details
- **Purpose**: Tracks students' enrollment status in courses and academic programs.
- **Key Columns**:
  - `student_id`: Anonymized unique identifier for students
  - `course_code`: Enrolled course (links to courses.csv)
  - `enrollment_date`: Date of course registration
  - `program`: Academic program (e.g., "Computer Science", "Psychology")
  - `enrollment_status`: Enrollment status (e.g., "Active", "Withdrawn", including regression-supplemented dynamic status)
- **Data Type**: Structured numerical/categorical data
- **Update Frequency**: Updated weekly during the enrollment period

### 3.3 weekly_activity.csv – Weekly Learning Activity Logs
- **Purpose**: Records students' weekly engagement with learning platforms (e.g., LMS, discussion boards).
- **Key Columns**:
  - `student_id`: Anonymized unique identifier for students
  - `course_code`: Course associated with the activity
  - `week`: Academic week (1–16)
  - `login_count`: Number of platform logins (including public data and regression-supplemented data)
  - `assignment_submission_count`: Number of on-time submissions
  - `forum_post_count`: Number of discussion contributions
- **Data Type**: Structured numerical data
- **Update Frequency**: Updated weekly

### 3.4 features.csv – Derived Learning Pattern Features
- **Purpose**: Provides precomputed synthetic features to support predictive modeling (e.g., performance risk assessment, engagement level classification).
- **Key Columns**:
  - `student_id`: Anonymized unique identifier for students
  - `course_code`: Associated course
  - `engagement_score`: Normalized score (0–100) for learning engagement
  - `performance_risk_flag`: Binary flag (0=low risk, 1=high risk) for exam performance
  - `study_consistency_index`: Index (0–1) measuring regularity of weekly activity
- **Data Type**: Structured numerical/categorical data
- **Generation Method**: Derived through statistical modeling (e.g., moving averages, clustering) based on Brown University's public academic datasets, legally collected offline data, and regression-supplemented data.

### 3.5 courses.csv – Course Catalog Information
- **Purpose**: Serves as a contextual reference for linking student data to course details.
- **Key Columns**:
  - `course_code`: Unique course identifier (e.g., "CSCI 1010")
  - `course_name`: Full course name (e.g., "Introduction to Computer Science")
  - `department`: Academic department (e.g., "Computer Science")
  - `credit_hours`: Number of academic credits (e.g., 4)
  - `instructor_id`: Anonymized identifier for the course instructor (including regression-supplemented historical instructor information)
- **Data Type**: Structured categorical/numerical data
- **Source**: Public information from Brown University's registrar system, public academic datasets, and legally supplemented data

### 3.6 behavior_text.csv – Anonymized Educational Text Data
- **Purpose**: Contains text data reflecting students' learning engagement (e.g., discussion contributions, reflective essays).
- **Key Columns**:
  - `text_id`: Unique identifier for the text entry
  - `student_id`: Anonymized unique identifier for students
  - `course_code`: Course associated with the text
  - `text_type`: Type of text (e.g., "forum_post", "reflective_essay")
  - `text_content`: Anonymized text (including public text and regression-generated supplementary text, with PII removed via regex filtering)
  - `submission_date`: Date of text submission
- **Data Type**: Unstructured text + structured metadata
- **Preprocessing**: Text is lowercased, stripped of PII via regex filtering, and supplementary text is validated for thematic consistency.

---

## 4. Data Usage Guidelines
### 4.1 Permitted Uses
- Research on personalized education strategies (e.g., identifying at-risk students, optimizing learning interventions).
- Analysis of learning engagement patterns (e.g., linking forum activity to exam performance).
- Development of educational predictive models (requiring cross-validation based on public data and legally collected data).

### 4.2 Prohibited Uses
- Attempting to re-identify students (e.g., cross-referencing student_id with external datasets).
- Using data for commercial purposes (e.g., selling derived features or regression-supplemented data to third parties).
- Modifying, splitting, or republishing behavior_text.csv and regression-generated supplementary data without IRB approval.
- Deriving conclusions using only regression-supplemented data without validation against public data or offline collected data.

### 4.3 Citation Requirement
If using these datasets in research publications, please cite:
> "Brown University Student Academic Dataset Collection. Brown University Learning Analytics Lab, 2025. Built based on Brown University's public academic datasets (https://oir.brown.edu/institutional-data/common-data-set), legally collected offline data, and reasonably supplemented with regression analysis. Compliant with FERPA and IRB Guidelines."

---

## 5. Technical Notes
- **File Format**: All datasets are saved as UTF-8 encoded CSV files for cross-platform compatibility.
- **Missing Value Handling**: Missing data is supplemented through reasonable regression analysis; original missing values are labeled as NA (numeric columns) or empty strings (text columns); supplementary data is marked with source identifiers.
- **Data Joining**: Use `student_id` and `course_code` as primary keys to join datasets (e.g., enrollment.csv ↔ courses.csv via course_code).
- **Regression Model Description**: Linear regression, logistic regression, ridge regression, and other models are used for data supplementation; model parameters are optimized through cross-validation to ensure supplementary data is consistent with the distribution of original data.
- **Tools Compatibility**: Tested with Python 3.8+ (Pandas 1.5+) and R 4.2+ (readr 2.1+).

---

## 6. Contact & Updates
For questions about data access, compliance, or updates, contact the Brown University Learning Analytics Lab at [learning.analytics@brown.edu](mailto:learning.analytics@brown.edu).

- **Last dataset update**: 2023-02-15
- **Next scheduled update**: 2025-05-11
