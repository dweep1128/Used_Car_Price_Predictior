# 🚗 Used Car Price Prediction: Breaking the Linear Barrier 

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Model](https://img.shields.io/badge/Model-Random%20Forest-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Project Overview
Buying a used car is often a gamble. Prices fluctuate wildly based on brand prestige, engine condition, and mileage. 

This project aims to build a machine learning model that accurately predicts the **Resale Value** of a car. 
We started with a simple Linear Regression baseline (which failed to capture non-linear depreciation) and iteratively improved performance using Feature Engineering and Ensemble Learning (Random Forest).

**🎯 Goal:** Predict the selling price with >90% accuracy (R² Score).

---

## 🛠️ The Challenge: Why Linear Regression Failed
My initial approach using **Linear Regression** yielded an R² score of only **0.67**. 
Upon analyzing the residuals, I realized the problem: **Car depreciation is non-linear.**
* A 10-year-old **BMW** holds value differently than a 10-year-old **Maruti**.
* A car with a **Turbo Engine** depreciates differently than a standard engine.

Linear models could not capture these complex "Interactions" between features.

---

## ⚙️ The Solution: Feature Engineering & Ensemble Learning

### 1. Advanced Feature Engineering
Instead of blindly feeding raw data, I created domain-specific features:
* **`is_luxury`**: A boolean flag identifying premium brands (BMW, Audi, Jaguar, Volvo). This helped the model differentiate between "Prestige Value" and "Utility Value."
* **`tech_score`**: A composite metric combining `max_power` and `engine_displacement`. This helps distinguish high-performance trims from base models.
* **`petrol_wear`**: An interaction term (`km_driven * fuel_Petrol`). Petrol engines generally wear out faster than Diesel engines; this feature penalizes high-mileage petrol cars more heavily.

### 2. Model Selection (The Upgrade)
I tested three different approaches:
| Model | R² Score | Verdict |
| :--- | :--- | :--- |
| **Linear Regression** | 0.67 | ❌ Too simple. High Bias. |
| **KNN (K=2)** | 0.88 | ⚠️ Good, but sensitive to outliers. |
| **Random Forest Regressor** | **0.908** | ✅ **Winner.** Handles non-linearities & interactions perfectly. |

---

## 📊 Key Results
* **Final Accuracy:** 91% (R² Score = 0.908)
* **Generalization:** The difference between Train Score (0.98) and Test Score (0.91) is <8%, indicating **No Major Overfitting**.

### 📉 Actual vs. Predicted Prices
*(Insert your scatter plot image here)*
> The points tightly cluster around the diagonal line, proving the model's high precision across budget and luxury segments.

---

## 💻 Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, Seaborn, Matplotlib
* **Techniques:** Feature Engineering, Grid Search, Bagging (Random Forest), Data Scaling (StandardScaler)
