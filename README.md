# BURNOUT--A-MotoGP-Datathon-by-IEEE-CS-MUJ-

# 🏍️ Burnout 2025: MotoGP Lap Time Prediction - Datathon Project

## 📌 Competition Overview

The Burnout 2025 MotoGP Datathon, hosted by IEEE MUJ on Kaggle, challenged participants to apply data science to predict MotoGP lap times based on a high-dimensional dataset containing rider statistics, race conditions, and technical performance metrics.

* **Platform**: Kaggle (Private Leaderboard)
* **Organizers**: IEEE Computer Society, Manipal University Jaipur
* **Duration**: 12-hour competition
* **Goal**: Predict `Lap_Time_Seconds` for unseen race events
* **Evaluation Metric**: Root Mean Squared Error (RMSE)

---

## 📂 Dataset Description

* `train.csv`: 1.9M+ rows, 45 features
* `val.csv`: 273K rows (validation holdout)
* `test.csv`: 547K rows (no target)
* `sample_submission.csv`: format template

Key data aspects:

* Rider metadata
* Bike and team specs
* Circuit profile (length, corners, temp)
* Weather and tire info
* Historical performance

---

## 🧪 Workflow Summary

### ✅ Phase 1: Data Exploration

* Checked nulls and data types
* Visualized distribution of `Lap_Time_Seconds`

### ✅ Phase 2: Target Transformation

* Applied `log1p()` to reduce skew
* Improved model stability for RMSE optimization

### ✅ Phase 3: Feature Engineering

Created new features based on domain understanding:

* `Speed_per_Km`, `Temp_Diff`
* `Experience_Score` (rider composite metric)
* `Tire_Strategy` (combined front & rear compound)
* `Total_Degradation` (tire wear impact)

### ✅ Phase 4: Categorical Encoding

* Applied `LabelEncoder` on high-cardinality categorical columns

### ✅ Phase 5: Modeling

* **Model**: XGBoost Regressor with `tree_method='hist'`
* Trained on log-transformed labels

### ✅ Phase 6: Hyperparameter Optimization

* **Tool**: Optuna (25 trials)
* Tuned: `max_depth`, `learning_rate`, `gamma`, `n_estimators`, etc.
* Used XGBoost `EarlyStopping` callback for efficient training

### ✅ Phase 7: Evaluation

* Inverted log predictions using `expm1()`
* Calculated RMSE on validation set

```text
✅ Final RMSE with XGBoost: ~0.034 - 0.045
```

### ✅ Phase 8: Submission

* Predicted `Lap_Time_Seconds` for test set
* Exported `solution.csv` matching submission format

---

## 📊 Feature Importance (Top Contributors)

* `Grid_Position`
* `Avg_Speed_kmh`
* `Experience_Score`
* `Track_Temperature_Celsius`
* `Total_Degradation`
* `Tire_Strategy`

---

## 🧠 Key Highlights

* Processed \~2M rows efficiently
* Applied advanced ML tuning with Optuna
* Balanced technical features with domain insights
* Generated submission-ready predictions under time constraints

---

## 📌 Potential Improvements

* Add LightGBM to form ensemble (XGB + LGBM)
* Use time-aware validation (e.g. by season)
* Incorporate SHAP for explainability

---

## 🚀 Tools & Tech

* Python 3.11
* Pandas, NumPy, Seaborn, Matplotlib
* XGBoost, Optuna, Scikit-learn
* Kaggle API for submission

---

## 🏁 Outcome

This project successfully demonstrates a high-performance pipeline for a real-world regression task in motorsport analytics. It showcases advanced data preparation, feature engineering, and hyperparameter tuning, making it a strong addition to any ML portfolio or resume.

---

**Created By**: Chaitanya Sai Kurapati
**Competition**: Burnout 2025 - IEEE CS MUJ
