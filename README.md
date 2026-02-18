# FUTURE_ML_03

# Resume Screening and Candidate Ranking ML System

Author: Seana Mutinda
Organization: Future Interns - Task 3 ML Project
Date: February 2026



## Overview

Hiring teams receive hundreds of resumes for a single job role. Manually reading each one is slow, inconsistent, and error-prone.

This project builds a Machine Learning-based resume screening system that automatically screens, scores, and ranks candidates based on a given job description, mirroring how real HR-tech tools work in production environments.



## Objectives

- Read and preprocess resume text
- Extract skills and relevant keywords using NLP
- Compare resumes against a job description
- Score and rank candidates based on role fit
- Identify missing or required skills
- Generate detailed candidate reports



## ML Pipeline

The project follows a full 9-stage Machine Learning lifecycle:

Stage 1 - Problem Definition and Setup  
Stage 2 - Data Collection (Kaggle dataset)  
Stage 3 - Data Wrangling and Cleaning  
Stage 4 - Exploratory Data Analysis (EDA)  
Stage 5 - Feature Engineering  
Stage 6 - Model Development  
Stage 7 - Model Evaluation  
Stage 8 - Results and Insights  
Stage 9 - Deployment Preparation  



## Key Features Implemented

- Resume text cleaning and preprocessing using NLTK (tokenization, stopword removal, lemmatization)
- Skill extraction using spaCy noun chunk extraction combined with regex pattern matching
- Job description parsing from a real Kaggle dataset (22,000 job postings)
- Resume-to-role similarity scoring using TF-IDF vectorization and Cosine Similarity
- Candidate ranking based on weighted scoring: 40% text similarity + 60% skill match
- Skill gap identification with visualization
- 4-chart visual dashboard per screening run
- Detailed per-candidate screening reports with hire/no-hire recommendation
- Export functionality: JSON, CSV, and TXT formats



## Scoring Formula

    Overall Score = (Text Similarity x 0.4) + (Skill Match x 0.6)

Candidates are classified as:

- Strong Candidate (score >= 70%) - Recommend for immediate interview
- Good Candidate (score >= 50%) - Recommend for interview
- Moderate Fit (score >= 30%) - Consider for phone screening
- Weak Fit (score < 30%) - Not recommended



## Tools and Libraries

### NLP
- spaCy - Named entity recognition, noun phrase extraction
- NLTK - Tokenization, stopword removal, lemmatization

### Machine Learning and Data
- scikit-learn - TF-IDF vectorization, cosine similarity
- pandas - Data manipulation and analysis
- numpy - Numerical computing

### Visualization
- matplotlib
- seaborn

### Dataset Access
- kagglehub - Dataset download from Kaggle

### Dataset
- PromptCloudHQ/us-jobs-on-monstercom (22,000 real US job descriptions from Monster.com)



## Project Structure

    resume-screening-system/
    |-- Resume_Screening_ML_Complete.ipynb   # Main notebook
    |-- resume_screening_ml.py               # Converted Python script
    |-- screening_results.json               # Exported results (JSON)
    |-- screening_results.csv                # Exported results (CSV)
    |-- screening_report.txt                 # Full candidate reports (TXT)
    |-- README.md
    |-- LICENSE
    |-- requirements.txt



## How to Run

1. Clone the repository
2. Install dependencies:

        pip install -r requirements.txt
        python -m spacy download en_core_web_sm

3. Set up Kaggle API credentials (~/.kaggle/kaggle.json)
4. Open and run Resume_Screening_ML_Complete.ipynb in Jupyter or Google Colab



## How Candidates Are Scored

1. Resume text is cleaned and normalized using NLTK
2. Skills are extracted from the resume using regex matching and spaCy noun chunks
3. The cleaned resume is vectorized using TF-IDF and compared to the job description via cosine similarity
4. Skill overlap between the resume and required skills is calculated
5. Both scores are combined using the weighted formula above
6. All candidates are ranked from highest to lowest score
7. A shortlist is generated based on a configurable threshold



## Results Summary (Sample Run)

- Dataset: 22,000 Kaggle job descriptions
- Candidates screened: 10
- Shortlisted for interview: 7
- Average candidate score: 38.5%
- Top candidate: Frank Oduya (60.4%)



## Output Files

| File | Format | Contents |
|---|---|---|
| screening_results.json | JSON | Structured scoring data for all candidates |
| screening_results.csv | CSV | Tabular results for spreadsheet use |
| screening_report.txt | TXT | Full narrative report for each candidate |



## Disclaimer

This system is a decision-support tool. Final hiring decisions should always involve human judgment. Scores are based on keyword and text matching and do not account for all dimensions of candidate quality.
