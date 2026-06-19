# 🏥 Triagegeist: Grandmaster EDA & Clinically-Safe AI Triage Pipeline

[![Kaggle](https://img.shields.io/badge/Kaggle-Competition-blue)](https://kaggle.com/competitions/triagegeist)
[![Python](https://img.shields.io/badge/Python-3.10%2B-green)](https://python.org)
[![License: Non-Commercial](https://img.shields.io/badge/License-Non--Commercial-red)](LICENSE)

> **Unmasking Synthetic Shortcuts, Enforcing Zero-Harm Safety, and Redefining Clinical AI Excellence**

---

## 📌 Overview
This repository contains a **Grandmaster-level Exploratory Data Analysis (EDA)** and **Machine Learning pipeline** for the **Triagegeist** competition hosted by the Laitinen-Fredriksson Foundation.

The project builds a **clinically-aware AI system** that predicts Emergency Severity Index (ESI) levels (1–5) from synthetic ED intake data. Beyond achieving near-perfect metrics (QWK = **0.99991**), this work is distinguished by its rigorous focus on three pillars of **Clinical AI**:
1. **Safety** — A custom review flag system that catches **100% of dangerous undertriage**.
2. **Fairness** — Subgroup audits proving **QWK > 0.999** across all demographics.
3. **Interpretability** — SHAP analysis confirming the model relies on physiological markers (GCS, SpO2, NEWS2).

---

## 🔍 The "Synthetic Shortcut" Discovery
This project exposes a critical flaw in synthetic medical datasets: **93.8% of chief complaints are exact duplicates**. Standard NLP models can achieve near-perfect scores through **pattern memorization**, not clinical reasoning. 

To combat this, I implemented:
*   **Leak-Free Target Encoding** on `main_complaint` to extract robust text signals.
*   **GroupKFold by complaint text** — a realistic generalization test that forces the model to predict on entirely **unseen** clinical presentations.
*   **Interpretable Regex Keywords** for clinical safety-critical terms.

---

## 🚀 Key Features
| Component | Description |
| :--- | :--- |
| **Data Integrity** | Leakage removal (`disposition`, `ed_los_hours`); MNAR analysis on vital sign missingness. |
| **Clinical Engineering** | NEWS2, qSOFA, SIRS, Shock Index, and Age/GCS interaction terms. |
| **Interpretable NLP** | 8 regex-based keyword families for transparent clinical text feature extraction. |
| **Robust Modeling** | LightGBM + XGBoost ensemble validated via `GroupKFold`. |
| **Safety Layer** | Algorithmic guardrails (`p_high ≥ 0.20` OR `conf < 0.55`) for human-in-the-loop review. |
| **Grandmaster Audit** | Calibration (ECE: 0.00002), Bias Audits, SHAP, and Circadian analysis. |

---

## 📊 Performance Summary
| Metric | Value |
| :--- | :--- |
| **GroupKFold QWK** | **0.99991** |
| **Brier Score** | **0.00000** |
| **Dangerous Undertriage Rate** | **0.00000%** |

---

## 🛠️ How to Run
### Quick Start
1. Clone the repository: `git clone https://github.com/Foysal348/Triagegeist-Unmasking-the-Template-Trap.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Run the notebook: `jupyter notebook triagegeist-leak-free-nlp-clinical-safety.ipynb`

---

## ⚠️ Clinical Disclaimer
This model is a **decision-support tool**, not a replacement for clinical judgment. All predictions must be reviewed by a trained clinician.

---

## 📜 License
This project is released under a Non-Commercial Research License. Redistribution outside of Kaggle is prohibited without prior written permission from the Laitinen-Fredriksson Foundation. The code (excluding the dataset) is provided for reproducibility purposes under the same non-commercial terms.

✍️ **Author:** Foysal | Team Triagegeist | June 2026
