# Multi-Stage Patient Risk Stratification and Intervention Planner

## 📌 Project Overview
This repository contains the implementation for an **Applied AI Assignment** designed to assist in mental health clinical decision-making. 

The system acts as a two-stage **Clinical Decision Support System (CDSS)**:
1.  **Risk Prediction (ML):** Uses **XGBoost** to analyze health indicators (sleep, BMI, activity) and predict the likelihood of moderate-to-severe depression (based on PHQ-9 standards).
2.  **Intervention Planning (Search):** Uses an **A* (A-Star) Search Algorithm** to generate an optimal, cost-aware, 3-step intervention pathway customized to the patient's specific constraints (e.g., budget, time, technology access).

## 🚀 Key Features
* **Hybrid AI Approach:** Combines Statistical Learning (Gradient Boosting) with Symbolic AI (Heuristic Search).
* **Synthetic NHANES Data:** Includes a robust data generator that mimics the statistical properties of the CDC's National Health and Nutrition Examination Survey (NHANES).
* **Cost-Aware Planning:** The planner minimizes a weighted cost function combining financial cost, time burden, and dropout risk.
* **Constraint Handling:** Automatically prunes interventions that are invalid for specific patients (e.g., excluding app-based therapy for patients without smartphones).

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Machine Learning:** `xgboost`, `scikit-learn`
* **Data Processing:** `pandas`, `numpy`
* **Search Algorithm:** Custom implementation of **A*** (using `heapq` for priority queues).

## 📂 Project Structure
* `applied_ai_assignment.ipynb`: The main Jupyter Notebook containing the full end-to-end pipeline.
* `data_generator.py`: (Internal function in notebook) Generates synthetic patient records with realistic correlations between lifestyle factors and PHQ-9 scores.

## 📊 How It Works
### Stage 1: The Predictor
The system takes tabular patient data (Age, BMI, Sleep Duration, Smoking Status, Physical Activity) and classifies the patient as **Low Risk** or **High Risk** (Target: PHQ-9 ≥ 10).

### Stage 2: The Planner
If a patient is flagged as **High Risk**, the A* algorithm searches the state space of possible interventions to find a sequence that:
1.  Reduces the estimated risk score below the threshold.
2.  Minimizes total cost (Money + Time).
3.  Respects patient constraints.

## ⚡ Quick Start
1.  Clone the repository:
    ```bash
    git clone [https://github.com/Parindyaa/Applied_AI_Depression-risk-decision-support.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy xgboost scikit-learn
    ```
3.  Open `applied_ai_assignment.ipynb` in Jupyter Lab or VS Code and run all cells.

## 📝 License
This project is created for educational purposes as part of a Final Year Computer Science Applied AI module.
