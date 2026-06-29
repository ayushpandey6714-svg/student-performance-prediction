# 🎓 Student Performance Prediction

A machine-learning project that predicts whether a student will **Pass or Fail** based on personal, academic, and lifestyle features.

---

## 📁 Project Structure

```
student_performance_prediction/
│
├── data/
│   └── student_data.csv          # Generated dataset (1 000 rows)
│
├── models/
│   └── best_model.pkl            # Saved best ML model + scaler
│
├── results/
│   ├── eda_charts.png            # Exploratory Data Analysis
│   ├── confusion_matrix.png      # Best model confusion matrix
│   ├── model_comparison.png      # All model accuracy comparison
│   ├── feature_importance.png    # Random Forest feature importance
│   └── correlation_heatmap.png   # Feature correlation heatmap
│
├── generate_dataset.py           # Creates synthetic student dataset
├── train_model.py                # EDA + model training + evaluation
├── predict.py                    # Predict outcome for a new student
├── requirements.txt              # Python dependencies
└── README.md                     # You are here
```

---

## ✨ Features Used

| Feature | Description |
|---|---|
| `gender` | Male / Female |
| `parent_education` | None / HighSchool / Bachelor / Master |
| `internet_access` | Whether student has internet at home (0/1) |
| `study_hours_per_day` | Average daily study hours (1–10) |
| `attendance_percentage` | Class attendance % (0–100) |
| `previous_score` | Score from the last exam (0–100) |
| `sleep_hours` | Average sleep per night (4–10) |
| `tutoring_sessions` | Attending private tutoring (0/1) |
| `extra_curricular` | Involved in extra-curricular activities (0/1) |

**Target → `result`**: `Pass` (score ≥ 50) or `Fail` (score < 50)

---

## 🤖 Models Trained

| Model | Description |
|---|---|
| Logistic Regression | Baseline linear classifier |
| Decision Tree | Interpretable tree-based model |
| **Random Forest** | Ensemble of trees — usually best 🏆 |
| K-Nearest Neighbors | Distance-based classifier |

All models are evaluated using **test accuracy** and **5-fold cross-validation**.

---

## 🚀 How to Run

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Generate the dataset
```bash
python generate_dataset.py
```

### 3. Train and evaluate models
```bash
python train_model.py
```

This will:
- Print model accuracy comparisons
- Save 5 charts to `results/`
- Save the best model to `models/best_model.pkl`

### 4. Predict for a new student
```bash
python predict.py
```

Or import the function in your own script:

```python
from predict import predict_student

result, confidence = predict_student(
    gender='Female',
    parent_education='Bachelor',
    internet_access=1,
    study_hours_per_day=7.5,
    attendance_percentage=90,
    previous_score=78,
    sleep_hours=7,
    tutoring_sessions=1,
    extra_curricular=1
)
print(f"Prediction: {result}  ({confidence:.1%} confidence)")
```

---

## 📊 Sample Results

```
── Model Comparison ──────────────────────────────────────
  Logistic Regression       Test Acc: 0.9500  CV Acc: 0.9475
  Decision Tree             Test Acc: 0.9600  CV Acc: 0.9450
  Random Forest             Test Acc: 0.9700  CV Acc: 0.9637  ← Best
  K-Nearest Neighbors       Test Acc: 0.9400  CV Acc: 0.9250

Best model → Random Forest  (Accuracy: 0.97)
```

---

## 📈 Output Charts

| Chart | Description |
|---|---|
| `eda_charts.png` | Score distribution, scatter plots, group averages |
| `confusion_matrix.png` | Pass/Fail prediction matrix |
| `model_comparison.png` | Bar chart of all model accuracies |
| `feature_importance.png` | Which features matter most |
| `correlation_heatmap.png` | How numerical features relate to each other |

---

## 🛠 Tech Stack

- **Python 3.8+**
- **pandas** — data loading & manipulation
- **numpy** — numerical operations
- **scikit-learn** — ML models, preprocessing, evaluation
- **matplotlib** — charts
- **seaborn** — heatmaps

---

## 💡 Key Insights

1. **Study hours** and **previous score** are the strongest predictors of success.
2. **Attendance** and **tutoring** also have significant positive impact.
3. **Random Forest** consistently outperforms simpler models.
4. Students with higher parental education tend to score better on average.

---

## 📝 License

MIT — free to use and modify for educational purposes.
