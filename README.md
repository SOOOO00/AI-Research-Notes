# **TYUT AI Research Notes**

A curated repository documenting my continuous learning in **Machine Learning**, **Deep Learning**, and **Applied AI Research**.
This repo includes **fundamentals**, **applied projects**, and **paper replications**, aiming to build a solid foundation for undergraduate-level AI research.

Author: **Maria Mo**
Affiliation: *Taiyuan University of Technology — Computer Science Experimental Class*
Focus: *Machine Learning · Deep Learning · Research Practice*

---

## **Overview**

This repository collects my notes, experiments, and code implementations while learning AI.
It includes:

* Machine Learning basics and experiments
* Applied AI mini-projects
* Paper reproduction notebooks
* Model explainability (PDP, ICE, SHAP)
* Research-oriented coding practice

---

## **Repository Structure**

| Folder                           | Description                                                                      |
| -------------------------------- | -------------------------------------------------------------------------------- |
| **00_Environment_Setup/**        | Notes on Python, Conda/Colab, virtual environments, Git/GitHub configuration     |
| **01_ML_Basics/**                | Foundational ML modeling projects (regression, classification, feature analysis) |
| └─ **Housing_Price_Prediction/** | California Housing dataset regression + model interpretation                     |
| └─ explanation/                  | PDP、ICE、SHAP explainability plots & notes                                        |
| **02_AI_Applications/**          | Applied AI projects (sentiment analysis, recommendation systems, etc.)           |
| **03_Paper_Replication/**        | Replication and analysis of published AI papers                                  |
| **assets/**                      | Shared images, visualizations                                                    |

---

## **Current Progress**

### **Machine Learning Basics**

* **01_Housing_Price_Prediction.ipynb** — Linear Regression vs Random Forest
* **02_Model_Interpretation.ipynb** — SHAP / PDP / ICE interpretability
* `explanation.md` — Detailed model explanation notes

### **NLP Projects**

* Sentiment Analysis (classical + BERT-based, ongoing)

### **Paper Replication**

* Preparing to reproduce 1 ML/DL research paper in 2025

---

## **Model Interpretability (SHAP / PDP / ICE)**

Explainability results for the Housing Price project are located in:

```
01_ML_Basics/Housing_Price_Prediction/explanation/
```

They include:

* SHAP Summary Plot
* PDP plot for MedInc
* ICE plot showing sample-wise variation
* explanation.md（full interpretation text）

Summary:

* **MedInc（median income）是最重要特征，与房价强正相关**
* PDP 显示整体趋势稳定、线性
* ICE 显示不同样本对 MedInc 的影响方向一致
* SHAP 显示单个预测的贡献细节

---

## **Environment**

* Python 3.10+
* Google Colab / Local environment
* Required libraries:

  ```bash
  numpy pandas matplotlib seaborn scikit-learn shap
  ```

---

## **Future Work**

* Add more model explainability examples
* Begin text classification tasks (RNN / BERT)
* Replicate a 2025 machine learning research paper
* Add CI/CD for reproducible experiments

---

## **Contact**

If you’re interested in discussing ML/DL projects or undergraduate research collaboration, feel free to reach out!
