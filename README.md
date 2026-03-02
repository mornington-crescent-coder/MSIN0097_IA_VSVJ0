# MSIN0097 – Predictive Analytics: Individual Assignment

**Title:** Predicting Online Purchase Intent: A Session-Level Classification Approach  
**Candidate Number:** VSVJ0  
**Module:** MSIN0097 Predictive Analytics, UCL School of Management  

---

## Project Overview

This project builds an end-to-end machine learning pipeline to predict whether an online shopping session will result in a purchase (revenue = `True`), using the [Online Shoppers Purchasing Intention dataset](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset) from the UCI Machine Learning Repository.

**Problem type:** Binary classification  
**Target variable:** `Revenue` (True = purchase made, False = no purchase)  
**Primary metric:** PR-AUC (Precision-Recall AUC), chosen due to class imbalance (~15% positive rate)  
**Business context:** Real-time coupon targeting — identifying high-intent sessions for intervention

### Models compared
| Model | Type |
|-------|------|
| Logistic Regression | Baseline (linear) |
| Random Forest | Ensemble (tree-based) |
| MLP (scikit-learn) | Neural network |
| **XGBoost + Optuna** | Final model (gradient boosting + HPO) |

---

## Submission Context

The final report was submitted via Moodle. This repository is provided to support reproducibility (code + environment + data access instructions).

---

## Repository Structure

```
├── README.md                          ← This file
├── requirements.txt                   ← Python dependencies
├── MSIN0097_IA_VSVJ0.ipynb            ← Main analysis notebook (run this)
└── data/
    ├── README_data.md                 ← Data source and citation
    └── online_shoppers_intention.csv  ← Dataset
```

---

## How to Run

### Step 1 – Clone the repository
```bash
git clone https://github.com/mornington-crescent-coder/MSIN0097_IA_VSVJ0.git
cd MSIN0097_IA_VSVJ0
```

### Step 2 – Install dependencies

**Option A – Standard pip (recommended for most users):**
```bash
python -m venv venv

# Activate (Mac/Linux):
source venv/bin/activate

# Activate (Windows):
venv\Scripts\activate

pip install -r requirements.txt
```

**Option B – Anaconda:**
```bash
pip install -r requirements.txt
```

### Step 3 – Launch the notebook
```bash
jupyter notebook MSIN0097_IA_VSVJ0.ipynb
```

### Step 4 – Run all cells in order
In Jupyter: **Kernel → Restart & Run All**

> ⚠️ Run cells top-to-bottom. The notebook uses a fixed random seed (`SEED = 42`) throughout to ensure full reproducibility.

---

## Environment

| Item | Version |
|------|---------|
| Python | 3.11 |
| Key libraries | pandas, numpy, scikit-learn, xgboost, imbalanced-learn, optuna, shap |
| Full dependency list | `requirements.txt` |

---

## Reproducibility

- **Random seed:** `SEED = 42` is set globally (NumPy, Python `random`, and all model-level seeds).
- **Train/val/test split:** Fixed stratified split (70% / 15% / 15%) applied once before any preprocessing — no leakage.
- **Hyperparameter optimisation:** Optuna study with fixed sampler seed; results are deterministic given the same seed.
- All metrics, thresholds, and feature importance values are computed within the notebook and do not rely on pre-saved artefacts.

---

## Dataset

**Source:** UCI Machine Learning Repository  
**DOI:** https://doi.org/10.24432/C5F88Q  
**Citation:** Sakar, C. and Yomi Kastro. 2018. "Online Shoppers Purchasing Intention Dataset." UCI Machine Learning Repository. https://doi.org/10.24432/C5F88Q.

---

## Agent Tooling

Generative AI tools (OpenAI Codex) were used to accelerate development tasks including code scaffolding, debugging, and documentation drafting, following a **plan → delegate → verify → revise** workflow. All agent outputs were reviewed, tested, and edited by the candidate before inclusion; no agent output was adopted without explicit verification. AI-assisted code contributions are attributed in the report Appendix. Full interaction logs and a decision register (accepted / modified / rejected) are provided there.

---

## Academic Integrity

This work is submitted in partial fulfilment of the requirements for MSIN0097 at UCL. All code was written or verified by the candidate; AI-assisted contributions are documented and attributed in the report Appendix. The dataset is publicly available under UCI's standard terms of use.
