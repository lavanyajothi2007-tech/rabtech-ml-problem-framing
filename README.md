# ML Problem Framing & Responsible Data Card

## 📌 Project Overview

This project was completed as part of an **Artificial Intelligence & Machine Learning Internship with RabTech Academy**.

The project focuses on responsible ML problem framing before model training, using a small **Customer Churn** dataset.

The objective is to determine whether machine learning is appropriate for supporting a customer-retention decision and to document the dataset, potential risks, evaluation criteria, and a transparent non-ML baseline.

---

## 🎯 Problem Statement

Customer churn prediction can help a retention team identify customers who may be at risk of leaving.

In this project, the ML system is designed to **prioritize customers for possible retention outreach**.

The model should **not** automatically cancel services, deny benefits, change prices, or make other high-impact decisions about customers.

---

## 📊 Dataset

The project uses the provided **Customer Churn Training Dataset**.

### Dataset details

* **Number of records:** 12
* **Target variable:** `churned`
* **Churned customers:** 5
* **Non-churned customers:** 7
* **Churn rate:** 41.7%

### Features

| Feature             | Description                                |
| ------------------- | ------------------------------------------ |
| `customer_id`       | Customer identifier                        |
| `tenure_months`     | Customer tenure in months                  |
| `support_tickets`   | Number of support tickets                  |
| `monthly_spend_inr` | Monthly customer spending                  |
| `last_login_days`   | Days since the customer's last login       |
| `plan_type`         | Customer subscription plan                 |
| `churned`           | Target label: 1 = churned, 0 = not churned |

`customer_id` is treated as an identifier and should not be used as a predictive feature.

---

## 🧠 ML Problem Framing

### Decision

Identify customers who may be at risk of churn so that a retention team can prioritize appropriate outreach.

### Prediction Target

`churned`

* `1` → Customer churned
* `0` → Customer did not churn

### Unit of Observation

One customer record/snapshot.

### Action Window

A proposed **30-day action window** after the prediction snapshot.

> This is a framing assumption because the supplied dataset does not specify an operational action window.

---

## 📏 Non-ML Baseline

A **majority-class baseline** was selected before ML model training.

The dataset contains:

* 7 non-churned customers
* 5 churned customers

Therefore, the baseline predicts **not churned (0)** for every customer.

### Baseline Result

**Accuracy: 58.3%**

The baseline provides a simple reference point that any future ML model should improve upon.

---

## 📈 Evaluation Metrics

### Model Metrics

* Recall for churn
* Precision for churn
* PR-AUC
* Calibration
* Error analysis

### Business Metrics

* Retention intervention conversion rate
* Incremental retention
* Cost per retained customer
* Customer complaints or opt-outs

### Error Costs

**False Positive:**
A customer is predicted to churn but would not have churned. This can result in unnecessary outreach costs and customer annoyance.

**False Negative:**
A customer is predicted not to churn but actually churns. This can result in a missed retention opportunity.

Exact monetary costs were not supplied and should be estimated before production deployment.

---

## 🔐 Responsible Data Card

The responsible data card documents:

* Dataset provenance
* Permission and consent status
* Population representation
* Features and target
* Missingness
* Data quality
* Leakage risks
* Sensitive attributes and possible proxies
* Bias and privacy risks
* False-positive and false-negative risks
* Intended evaluation

---

## ⚠️ Risk Register

| Risk                       | Impact | Mitigation                                         |
| -------------------------- | ------ | -------------------------------------------------- |
| Very small dataset         | High   | Do not deploy; collect more historical data        |
| Unknown provenance/consent | High   | Verify permission before operational use           |
| Data leakage               | High   | Use point-in-time features and temporal validation |
| False positives            | Medium | Monitor precision and outreach impact              |
| False negatives            | High   | Monitor churn recall                               |
| Sampling bias              | High   | Use representative historical data                 |
| Proxy discrimination       | High   | Perform subgroup/error analysis                    |
| Model misuse               | High   | Use predictions only as prioritization signals     |

---

## 📓 Baseline Notebook

The `baseline_notebook.ipynb` contains:

1. Dataset loading
2. Dataset inspection
3. Missing-value check
4. Duplicate check
5. Target distribution
6. Majority-class baseline
7. Baseline accuracy
8. Responsible ML interpretation

---

## 📁 Project Structure

```text
rabtech-ml-problem-framing/
│
├── ML_problem_framing_memo.md
├── responsible_data_card.md
├── risk_register.md
├── baseline_notebook.ipynb
├── customer-churn-training.csv
└── README.md
```

---

## 🚨 Limitations

This dataset contains only **12 records**, which is insufficient for reliable production ML.

Therefore, this project focuses on **responsible problem framing and baseline establishment**, rather than claiming production-level model performance.

Before deployment, a larger historical dataset, clear feature timestamps, a defined intervention strategy, temporal validation, business error costs, and fairness/error analysis would be required.

---

## 🏁 Conclusion

This project demonstrates that responsible machine learning begins **before model training**.

The decision, target, baseline, data provenance, potential harms, leakage risks, evaluation metrics, and fallback approach were documented before building an ML model.

**Project completed as part of the Artificial Intelligence & Machine Learning Internship at RabTech Academy.**

---

## 🛠️ Technologies

* Python
* Pandas
* Jupyter Notebook
* Machine Learning
* Responsible AI
* Data Analysis
* GitHub

---

### 👩‍💻 Author

**Lavanya**

Artificial Intelligence & Data Science Student

**GitHub:** `lavanyajothi2007-tech`
