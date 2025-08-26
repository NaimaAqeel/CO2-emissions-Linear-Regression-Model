
#  CO₂ Emissions Analysis & Train Regression Model to predict  CO₂ emissions

##  Objective

This project aims to analyze **CO₂ emissions from vehicles** and build predictive models to understand the factors influencing emissions.
We explore how vehicle characteristics (engine size, cylinders, fuel type, transmission, etc.) impact emissions and suggest practical recommendations to reduce CO₂.

---
## Project Overview

This project focuses on predicting CO₂ emissions (g/km) of vehicles using regression models. The dataset contains both categorical features (e.g., Make, Model, Vehicle Class, Transmission, Fuel Type) and numerical features (e.g., Engine Size, Cylinders, Fuel Consumption).

The goal is to:

#vCompare models using all features vs. only the most correlated features.

Handle issues of multicollinearity.

Apply regularization techniques (Ridge, Lasso) for model improvement.
##  Background

Carbon dioxide (CO₂) emissions are a major contributor to **climate change** and air pollution, affecting both the environment and human health.
By analyzing real-world vehicle data, we can:

* Identify the factors that increase emissions
* Suggest cleaner technologies & policies
* Build predictive models to estimate emissions

---

## Literature Review

Some key references that highlight the importance of reducing CO₂:

* *How to Avoid a Climate Disaster* – Bill Gates
* *The Sixth Extinction* – Elizabeth Kolbert
* *This Changes Everything* – Naomi Klein
* *Drawdown* – Paul Hawken

---

## 📊 Dataset

* Source: [Government of Canada Open Data](https://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64#wb-auto-6)
* Rows: **7,385**
* Columns: **12**
* Period: **7 years**

### Key Features

* **Engine Size (L)**
* **Cylinders**
* **Fuel Type** (Gasoline, Diesel, Ethanol, Natural Gas)
* **Transmission** (Manual, Automatic, CVT, etc.)
* **Vehicle Class**
* **Fuel Consumption (City, Hwy, Combined)**
* **CO₂ Emissions (g/km)**

---

##  Data Cleaning & Preprocessing

* ✅ Removed **1103 duplicate entries**
* ✅ No missing values
* ✅ Encoded categorical features (Make, Model, Transmission, etc.)
* ✅ Handled **outliers** using `np.log2` transformation
* ✅ Standardized numerical variables

---

##  Exploratory Data Analysis (EDA)

### 🔹 CO₂ Emissions by Vehicle Class

* **Two-Seater cars** have the highest emissions (\~500 g/km).
* Vans, SUVs, and Pickup trucks follow with \~400 g/km.

### 🔹 Engine Size vs. CO₂

* Larger engines burn more fuel → Higher CO₂ emissions.

### 🔹 Cylinders vs. CO₂

* More cylinders → More fuel burned → Higher emissions.

### 🔹 Transmission vs. CO₂

* **Automatic cars** → Highest emissions
* **Manual cars** → Lower emissions
* **CVT (Continuously Variable Transmission)** → Lowest emissions

### 🔹 Fuel Type vs. CO₂

* **Highest:** Premium Gasoline
* **Lowest:** Natural Gas

---

##  Statistical Analysis

### Descriptive Stats

* **Engine Size:** 0.9 – 8.4 L (mean = 3.16 L)
* **Cylinders:** 3 – 16 (mean = 5.62)
* **CO₂ Emissions:** 96 – 522 g/km (mean = 250.58 g/km)

### Correlations

* Engine Size → **0.85** with CO₂
* Cylinders → **0.83** with CO₂
* Fuel Consumption City → **0.92** with CO₂
* Fuel Consumption Hwy → **0.88** with CO₂
* Fuel Consumption (mpg) → **-0.91** with CO₂

---

##  Regression Models

### Model 1 – All Features

* Included all categorical + numerical features
* Categorical features encoded via One-Hot Encoding.
* Trained a Linear Regression model.
# Result:
* **RMSE:** Root Mean Squared Error: 0.0001218
* Predictions are very close to actual values.

### Model 2 – Most Correlated Features

* Features: Engine Size, Cylinders, Fuel Consumption
* Strong model fit, explains ~91% variance in test data.
# Result:
* **Training R²:** 0.911
* **Testing R²:** 0.908


### Hyperparameter Tuning – Regularization

* **Lasso Regression:** Poor performance (R² ≈ 0)
* **Ridge Regression:** Similar to Linear Regression (R² ≈ 0.91)
* Failed to capture variance → Not suitable for this dataset.

---
## Comparison

| Model                                   | Training R² | Testing R² | RMSE          | Notes                                 |
| --------------------------------------- | ----------- | ---------- | ------------- | ------------------------------------- |
| Linear Regression (All Features)        | –           | –          | **0.0001218** | Best accuracy with all data           |
| Linear Regression (Correlated Features) | 0.911       | 0.908      | –             | Slightly less accurate, simpler model |
| Ridge Regression                        | 0.911       | 0.908      | –             | Robust to multicollinearity           |
| Lasso Regression                        | 0.0         | -0.001     | –             | Not suitable                          |


##  Recommendations

*  Choose **smaller engines & fewer cylinders**
*  Use **alternative fuels** (ethanol, natural gas, electric)
*  Prefer **public transportation**
*  Support **stricter emission laws**
*  Drive responsibly (inflated tires, no idling, smooth driving)

---
## Key Takeaways

* All independent variables are strongly correlated with CO₂ emissions.

* Model 1 (all features) gives the lowest RMSE.

* Model 2 (correlated features) still performs well with fewer variables.

* Multicollinearity is present but doesn’t heavily degrade prediction performance.

* Ridge regression offers stability but doesn’t significantly improve results.

* Lasso regression is unsuitable for this dataset.
##  Conclusion

* **Engine size, cylinders, and fuel consumption** strongly influence CO₂ emissions.
* **Transmission type and fuel choice** also play significant roles.
* Predictive models (R² ≈ 0.91) perform well in estimating emissions.
* Collective actions—policy changes, technological innovation, and eco-friendly choices—can help mitigate climate change.

---
## Project Report
The complete analysis, insights, and visualizations are documented in CO2_Emissions_Analysis.pdf
.
You can refer to this file for a detailed explanation of the methodology, results, and key findings.
---
## 📂 Project Structure

```
├── data/                     # Dataset files
├── notebooks/                # Jupyter notebooks for analysis
├── src/                      # Source code (cleaning, modeling, visualization)
├── results/                  # Output graphs & model performance
├── README.md                 # Project documentation
├── requirements.txt          # Python dependencies
```

---

##  Tech Stack

* Python 
* Pandas, NumPy, Matplotlib, Seaborn
* Scikit-learn (Linear Regression, Ridge, Lasso)

---

##  Acknowledgements

Dataset compiled from **Government of Canada Open Data**:
🔗 [https://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64#wb-auto-6](https://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64#wb-auto-6)

---

 *By [Naima Aqeel](#) – Working towards sustainable AI solutions for climate challenges.*

---

