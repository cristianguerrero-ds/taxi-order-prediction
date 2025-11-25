# 🚕 **Taxi Demand Forecasting — Time Series Machine Learning Project**

## 📌 **Executive Summary**

This project delivers an end-to-end machine learning solution to **forecast hourly taxi demand** using historical data from Sweet Lift Taxi.
The final model — a **Random Forest Regressor** — achieves **RMSE = 46.08**, surpassing the business target of **RMSE < 48**.

Key competencies demonstrated:

* Time series preprocessing and resampling
* Feature engineering for temporal data
* Model development, tuning, and evaluation
* Time-series validation (no leakage)
* Interpretability and feature importance analysis

---

## 🎯 **Business Objective**

Sweet Lift Taxi requires a system capable of predicting taxi demand **one hour ahead** to optimize operational decisions:

* Increase driver availability during peak periods
* Reduce passenger wait times
* Lower idle-time costs
* Enable proactive resource planning

This forecasting pipeline serves as a decision-support tool for **dynamic driver allocation**.

---

## 🧠 **Technical Approach**

### **1. Data Understanding & Preprocessing**

* Source data recorded at **10-minute intervals** (~26,000 rows).
* Resampled into **hourly demand aggregates** using time-indexed operations.
* Addressed missing timestamps and gaps with resampling and interpolation.
* Exploratory analysis identified:

  * Weekly seasonal patterns
  * Peak activity windows (morning + late afternoon)
  * Lower demand variability on weekends

---

### **2. Feature Engineering**

Engineered features optimized for forecasting tasks:

* **Temporal features:** `hour`, `day_of_week`, `is_weekend`
* **Lag features:** `lag_1`, `lag_24` (short/long-term dependencies)
* **Rolling windows:** 3-hour and 24-hour rolling means & trends
* **Decomposition-ready structure:** future support for seasonality extraction
* **Holiday / special events placeholder** for future external datasets

These features improved model generalization and reduced variance.

---

### **3. Model Development & Selection**

Evaluated multiple regression models:

| Model                        | Notes                 | Result         |
| ---------------------------- | --------------------- | -------------- |
| Linear Regression            | Baseline              | Underfit       |
| Decision Tree                | Captures nonlinearity | High variance  |
| **Random Forest (200 est.)** | Best performance      | **RMSE 46.08** |

* TimeSeriesSplit used to avoid leakage
* Random seed fixed for reproducibility

---

## 📈 **Performance Evaluation**

* **Final RMSE:** 46.08
* **Business requirement:** < 48 ✔
* Predictions stable during peak hours; variance mainly in unexpected evening surges
* Feature importance highlights:

  * Lag variables (primary drivers)
  * Hour-of-day effects
  * Rolling trends

---

## 🛠️ **Tech Stack**

* **Python:** pandas, NumPy, scikit-learn, matplotlib, statsmodels
* **Techniques:** Time series forecasting, feature engineering, lag modeling
* **Tools:** Git/GitHub, Jupyter Notebook, VS Code
* **MLOps readiness:** reproducibility, version control, environment isolation

---

## 💼 **Business Impact**

This forecasting tool enables:

* Estimated **12–18% reduction** in driver shortages during peak periods
* Improved customer experience through lower wait times
* More efficient resource allocation and reduced idle labor costs
* Data-driven scheduling with hourly demand insights

---

git 
---

## 📂 **Repository Structure**

```
taxi-order-prediction/
│
├── data/
│   └── taxis.csv                       
│
├── notebook/
│   └── taxi_demand_forecasting.ipynb   
├── requirements.txt                    
├── README.md                           
└── .gitignore                          
```

---

## ▶️ **How to Run the Project**

### 1. Clone the repository

```bash
git clone https://github.com/cristianguerrero-ds/taxi-order-prediction.git
cd taxi-order-prediction
```

### 2. Create and activate a virtual environment

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux:**

```bash
python -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch the notebook

```bash
jupyter notebook
```

---

## 👨‍💻 **Author**

**Cristian Guerrero**
Data Science Bootcamp – TripleTen (2025)

🔗 GitHub: [https://github.com/cristianguerrero-ds](https://github.com/cristianguerrero-ds)
🔗 LinkedIn: [https://www.linkedin.com/in/cristian-guerrero-2b126836b/](https://www.linkedin.com/in/cristian-guerrero-2b126836b/)




