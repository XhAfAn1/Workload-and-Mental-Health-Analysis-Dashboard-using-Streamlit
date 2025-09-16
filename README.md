# Student Well-Being & Stress Analysis  

## Overview  
This project explores the factors influencing student stress, anxiety, and well-being using survey data. Our goal was to understand how academic workload, extracurricular involvement, jobs, and sleep patterns contribute to mental health.  

We conducted **data cleaning, feature engineering, exploratory data analysis (EDA), hypothesis testing, and regression modeling**, and finally developed an **interactive dashboard** to present the findings.  

The project shows not only the challenges of analyzing complex human data but also our growth as data analysts.  

---

## Dataset  
The dataset was collected through a survey of **115 students** and includes:  
- **Academic performance**: CGPA, study hours, courses enrolled  
- **Demographics**: age, gender, year of study  
- **Time commitments**: extracurricular activities, job status, hours spent  
- **Wellbeing metrics**: stress (1–5), anxiety (1–5), sleep hours, sleep quality (1–10)  

---

##  Data Preparation & Feature Engineering  
1. **Cleaning & Handling Missing Data**  
   - Filled missing CGPA values with the mean  
   - Set extracurricular/job hours to 0 if the student answered "No"  
   - Removed unrealistic course load values (max capped at 5)  

2. **Feature Engineering**  
   - Converted **categorical to numerical**:  
     - Year of Study → ordinal values (1–4)  
     - Extracurricular & Job → binary (0 = No, 1 = Yes)  
   - Created **consistent numeric features** linking participation with hours  

---

## Exploratory Data Analysis (EDA)  
- **Summary statistics** for all variables  
- **Distribution plots** of CGPA, study hours, sleep, stress, anxiety  
- **Correlation heatmap** of numerical variables  
- **Scatterplots & boxplots** showing relationships, e.g.  
  - Study hours vs. CGPA  
  - Sleep hours vs. stress  
  - Anxiety levels across year of study  
  - Stress levels by job status  

---

## Hypothesis Testing  
We applied statistical tests (α = 0.05):  

- **t-test**: Stress by extracurricular participation → *no significant difference*  
- **ANOVA**: Anxiety across years of study → *no significant difference*  
- **Correlation test**:  
  - Study hours vs stress → weak, not significant  
  - Sleep hours vs anxiety → weak, not significant  
- **Proportion test**: High stress prevalence by job status → *no significant difference*  

 **Key insight**: None of the simple bivariate relationships were significant. Stress and anxiety are influenced by more complex, multivariate factors.  

---

## Regression Modeling  

### Simple Regressions  
- **Stress ~ Study Hours** → weak positive effect (R² = 0.031, p = 0.060)  
- **Stress ~ Year of Study** → not significant (R² = 0.023, p = 0.107)  
- **Anxiety ~ Sleep Quality** → significant negative effect (R² = 0.063, p = 0.007)  

### Multiple Regressions  
- **Stress ~ Study Hours + Courses + Extracurricular + Job + Sleep Quality**  
  - Not significant overall (R² = 0.069, p = 0.162)  
  - Study hours showed the strongest (but weak) effect  

- **Sleep Quality ~ Sleep Hours + Stress + Anxiety**  
  - Significant overall (R² = 0.216, p < 0.001)  
  - Sleep hours positively predicted sleep quality  
  - Stress/anxiety were weak predictors  

 **Interpretation**:  
- Models explain only a small part of the variation (low R²).  
- Student stress is driven by unmeasured factors (financial issues, personal life, course difficulty, etc.).  
- Still, sleep quality and study hours emerged as meaningful predictors.  

---

## Interactive Dashboard  

### Student Stress Analysis Dashboard  
A **Streamlit-based web dashboard** for exploring the dataset interactively.  

**Features:**  
- Interactive filters (year, gender, job, extracurriculars)  
- Distribution & correlation analysis  
- Hypothesis testing results  
- Regression model summaries  
- Raw data table  

**Technologies:**  
- Python, Pandas, NumPy  
- Streamlit  
- Matplotlib, Seaborn, Plotly  
- SciPy, Statsmodels  

**Run locally:**  
```bash
git clone <repo-url>
cd <repo-folder>
pip install -r requirements.txt
streamlit run app.py
