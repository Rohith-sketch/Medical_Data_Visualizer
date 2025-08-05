# Medical_Data_Visualizer
This project analyzes a dataset of medical examination records (`medical_examination.csv`) using Python, Pandas, and Seaborn. It produces two key visualizations to help explore relationships between patient attributes and cardiovascular disease (`cardio` column).
## What the Code Does

### 1. Load and Preprocess Data
- **Import the dataset** into a Pandas DataFrame.
- **Add a new column** `overweight` based on BMI:
  - BMI = weight (kg) / height² (m²)
  - BMI > 25 → `overweight = 1` (Yes), otherwise `0` (No)
- **Normalize** `cholesterol` and `gluc`:
  - Values of `1` → good → converted to `0`
  - Values `>1` → bad → converted to `1`

---

### 2. Categorical Plot
- The following binary categorical features are selected:
  - `cholesterol`, `gluc`, `smoke`, `alco`, `active`, `overweight`
- Data is reshaped using `pd.melt()` to a long format suitable for seaborn's `catplot()`.
- A grouped bar chart is created:
  - Shows the count of `0` (good) and `1` (bad) values for each feature
  - Splits the view into two panels: one for patients with heart disease (`cardio=1`) and one without (`cardio=0`)
- The figure is saved as `catplot.png`.

---

### 3. Heatmap of Correlations
- **Data cleaning** is performed:
  - Removes rows with invalid blood pressure readings (`ap_lo` > `ap_hi`)
  - Removes outliers in `height` and `weight` (outside 2.5th–97.5th percentile)
- A **correlation matrix** is calculated on the cleaned data.
- A **heatmap** is drawn using `seaborn.heatmap()` to show relationships between all numerical variables.
- Only the **lower triangle** of the matrix is displayed using a mask.
- The figure is saved as `heatmap.png`.

---

## Files

- `medical_examination.csv`: Input dataset
- `catplot.png`: Bar chart of categorical health features by cardiovascular condition
- `heatmap.png`: Correlation heatmap of cleaned medical data

---

##  Libraries Used

- `pandas` for data manipulation
- `numpy` for numeric operations
- `seaborn` and `matplotlib` for visualizations
