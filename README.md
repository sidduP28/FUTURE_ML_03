# FUTURE_ML_03
# Resume Screening System — ML-Powered Candidate Ranker

> Automatically rank job applicants against a target role using TF-IDF similarity scoring and domain-specific skill extraction — mimicking how ATS (Applicant Tracking Systems) work under the hood.

---

## 📌 Project Overview

This project builds a **Resume/Candidate Screening System** that:
1. Reads a pool of resumes for a target role (e.g., IT, Finance, Healthcare)
2. Extracts domain-relevant skills from each resume
3. Compares resumes to a job description using **TF-IDF + Cosine Similarity**
4. Produces a **ranked candidate list** with matched and missing skills highlighted

The system uses a **hybrid scoring formula** that combines semantic similarity (TF-IDF) with rule-based skill matching for interpretability.

---

## 🗂️ Dataset

| File | Description |
|------|-------------|
| `Resume.csv` | Resumes with `Category`, `Resume_str`, `Resume_html` fields |

> Source: [Kaggle — Resume Dataset](https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset)
> 24 job categories · 962 resumes

---

## ⚙️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.10-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange)
![NLTK](https://img.shields.io/badge/NLTK-3.8-yellow)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)

- **Text Cleaning** — Regex, lowercasing, stopword removal (NLTK)
- **Skill Extraction** — Custom domain-specific skill dictionaries (24 categories)
- **Vectorization** — `TfidfVectorizer`
- **Similarity** — `cosine_similarity` from scikit-learn
- **Scoring** — Weighted hybrid: 30% TF-IDF score + 70% skill match %
- **Output** — Ranked candidate list with skill gap analysis

---

## 🏗️ Project Structure

```
ResumeScreening/
│
├── JOB_SCREENING_ML_03.ipynb      # Main notebook
├── data/
│   └── Resume.csv                 # Dataset(use link)
└── README.md
```

---


To screen for a different role, update these two variables in the notebook:

```python
TARGET_ROLE = "FINANCE"   # Any key from SKILLS_BY_CATEGORY
JOB_DESCRIPTION = """Your custom job description here..."""
```

---

## 📊 How Scoring Works

```
Final Score = 0.30 × TF-IDF Cosine Similarity
            + 0.70 × (Matched Skills / Total Required Skills)
```

| Component | Weight | What it captures |
|-----------|--------|-----------------|
| TF-IDF Similarity | 30% | Overall semantic relevance of resume to JD |
| Skill Match % | 70% | Presence of explicitly required skills |

---

## 🏆 Sample Output

```
============================================================
  TOP 5 CANDIDATES FOR: INFORMATION-TECHNOLOGY
============================================================

🏆 Rank #1
   Final Score    : 0.7823
   TF-IDF Score   : 0.4512
   Skill Match    : 85.7%
   Matched Skills : ['python', 'sql', 'linux', 'aws', 'git']
   Missing Skills : ['scala']
```

---

## 🔍 Key Learnings

- TF-IDF alone over-rewards verbose resumes; combining it with explicit skill matching makes scoring more fair and interpretable
- Stopword removal before skill extraction prevents false negatives on common words
- Cosine similarity is robust to document length differences, making it ideal for resume comparison

---

## 👤 Author

**PITCHUKA ANJANI SIDDARTHA**
[LinkedIn](linkedin.com/in/pitchuka-anjani-siddartha-7a88593bb/?skipRedirect=true) · [Kaggle](https://www.kaggle.com/siddartha4)
