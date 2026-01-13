# 🧠 Depression Severity Classification using PHQ-9

## 📌 Project Overview
This project develops a machine learning system to **automatically classify depression severity** based on patient responses to the PHQ-9 (Patient Health Questionnaire). By automating the clinical scoring process, this model aims to assist healthcare professionals in triage and diagnosis, reducing administrative burden and manual calculation errors.

## 🎯 Key Objectives
* **Automate Scoring:** Convert qualitative survey responses (e.g., "More than half the days") into clinical severity categories.
* **Compare Algorithms:** Benchmark linear vs. non-linear models to determine the most effective approach for clinical scoring data.
* **Identify Risk Factors:** Analyze which symptoms are the strongest predictors of severe depression classification.

## 📊 Dataset
* **Source:** PHQ-9 Dataset (Mendeley).
* **Participants:** 682 individuals.
* **Features:** Responses to 9 standardized questions regarding sleep, energy, appetite, mood, etc.
* **Target:** Depression Severity Level (Minimal, Mild, Moderate, Moderately Severe, Severe).

## 🛠️ Methodology
### 1. Data Cleaning & Preprocessing
* **Text Normalization:** Stripped invisible characters and whitespace from survey text to ensure accurate mapping.
* **Ordinal Encoding:** Mapped survey responses to clinical scores (0–3):
    * *Not at all* → 0
    * *Several days* → 1
    * *More than half the days* → 2
    * *Nearly every day* → 3
* **Target Preparation:** Encoded severity labels (e.g., "Moderately Severe") into ordinal integers (0–4).

### 2. Model Selection
We tested three distinct machine learning algorithms to understand the data structure:
1.  **Logistic Regression** (Baseline Linear Model)
2.  **Random Forest Classifier** (Non-Linear Ensemble)
3.  **Support Vector Machine (SVM)** (Linear Kernel)

## 🏆 Results & Insights
The project revealed a critical insight: **Linear models significantly outperformed complex ensemble models.**

| Model | Accuracy | Insight |
|-------|----------|---------|
| **Linear SVM** | **98.54%** | **Best Performer.** Successfully captured the linear additive nature of PHQ-9 scoring. |
| Logistic Regression | 97.81% | Excellent baseline, proving the data is linearly separable. |
| Random Forest | 83.21% | Underperformed due to overfitting complex rules on simple additive data. |

### 🔍 Key Findings
* **The Victory of Linearity:** Since the PHQ-9 score is a mathematical sum of symptoms, linear models (SVM) drew near-perfect decision boundaries. Random Forest struggled by trying to create complex "if/else" rules for a simple summing problem.
* **Feature Analysis:** Symptoms like *"Little interest"* and *"Feeling tired"* were the most frequent drivers of severity classification, while *"Suicidal thoughts"* had lower statistical importance due to its rarity, despite its high clinical importance.

## 📸 Visualizations
*(You can upload your charts here, e.g., Confusion Matrix, Feature Importance)*

## 🚀 How to Run
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/depression-risk-classification.git](https://github.com/your-username/depression-risk-classification.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install pandas numpy scikit-learn seaborn matplotlib
    ```
3.  **Run the Jupyter Notebook:**
    Launch `Depression Risk Classification.ipynb` to reproduce the cleaning, training, and evaluation steps.

## 🔮 Future Work
* **Mobile Deployment:** Exporting the SVM model (`.pkl`) to a Flask API for a mobile screening app.
* **Feature Reduction:** Investigating if a subset of 3-4 questions can achieve similar accuracy for rapid screening.

---
*Created by Jacob Abenga*
