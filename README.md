# Education Data Modeling & LLM Pipeline

This project implements a complete, end-to-end Python pipeline for education data modeling. It includes:

- Three core modeling techniques
- Three integrated, (stubbed) LLM-based extensions for explainability and feature engineering

The pipeline is:

- Built with a modular, object-oriented design  
- Managed by a central `config.yaml` file  
- Orchestrated by `main.py`  

---

## Features

### Core Modeling Methods

#### Method 1.1: Static Early-Warning Model

- Trains a model (e.g., **LightGBM**, **XGBoost**, **RandomForest**) to predict student risk:
  - Classification: pass/fail
  - Regression: score
- Uses **static** and **aggregated behavioral features** as inputs.
- Outputs:
  - Feature importances
  - Validation metrics: **AUC**, **F1**, **Recall**

---

#### Method 2.2: Sequence-based Behavior Clustering

- Uses **K-Means** to cluster students into behavioral profiles.
- Input features: aggregated **weekly activity** (e.g., logins, study time, etc.).
- Outputs:
  - Cluster assignments for each student
  - Human-readable descriptions for each cluster  
    (e.g., `"High Engagement"`, `"Low Activity"`)

---

#### Method 3: Student-Course Graph Modeling

- Implements **Matrix Factorization** (via `scikit-surprise`) on student-course enrollment data.
- Learns:
  - Student embeddings
  - Course embeddings
- Outputs:
  - **Top-N course recommendations** for students

---

## LLM-based Extensions (Stubs)

### LLM Extension A: Explainable Report Generation

- Generates a human-readable `teaching_analytics_report.md` that summarizes:
  - Model performance
  - Key risk factors
  - Cluster profiles
- Behavior:
  - If `llm.enabled: true`: (stub) use LLM-based generation
  - If `llm.enabled: false`: fall back to a **simple template**-based report

---

### LLM Extension B: Text-based Feature Extraction

- Analyzes raw text logs (e.g., `behavior_text.csv`) to create new features:
  - Example features:
    - Sentiment scores
    - Confusion flags (e.g., keywords like “confused”, “stuck”)
    - Post count / message frequency
- Default implementation:
  - Provides a **runnable heuristic method** (keyword-based) that works without an LLM.
- Integration:
  - Generated features are **automatically merged** into the early-warning model’s feature set.

---

### LLM Extension C: Recommendation Explanation & Q&A

- Generates **natural-language explanations** for why a course was recommended to a student.
- Includes a stubbed Q&A assistant:
  - `answer_question(student_id, question)` style interface
  - Designed to answer questions about a student’s **progress** and **recommendations**

---

## How to Run

### 1. Setup

#### Dependencies

You will need **Python 3.8+** and the following packages:

```bash
pip install pandas numpy scikit-learn pyyaml matplotlib seaborn
pip install xgboost lightgbm
pip install scikit-surprise  # For Matrix Factorization
pip install torch torch_geometric # Optional: For GNN stub
