# 🚕 Taxi Data Cleaning & Visualization

Clean, analyse, and visualize NYC taxi trip data using **Pandas**, **Matplotlib**, and **Seaborn** to uncover patterns in fares, distances, tips, and customer behaviour.

> **Python DA Assignment 2: Data Visualization | Data Analytics (DA), Module 5**

---

## 📌 Problem Statement

Taxi services generate large amounts of trip data daily, which can be used to understand patterns and improve operations. Raw data often contains missing values and is difficult to interpret without proper analysis.

In this project, you act as a data analyst to:

- Load and inspect the dataset
- Handle missing values
- Explore trends in fare, distance, and customer behaviour
- Build clear visualizations that communicate insights

---

## 📂 Dataset

The project uses the built-in **`taxis`** dataset from Seaborn.

```python
import seaborn as sns

df = sns.load_dataset("taxis")
```

**Key columns used:** `pickup`, `dropoff`, `passengers`, `distance`, `fare`, `tip`, `tolls`, `total`, `color`, `payment`, `pickup_zone`, `dropoff_zone`, `pickup_borough`, `dropoff_borough`

---

## 🗂️ Project Structure

```text
taxi-data-visualization/
│
├── taxi_visualization.ipynb   # Notebook with all tasks (or .py script)
└── README.md                  # Project documentation
```

---

## 🧰 Requirements

- Python 3.x
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook (optional)

```bash
pip install pandas matplotlib seaborn
```
---

## 🧹 Step 1: Handling Missing Values

| Task | Approach |
|------|----------|
| Detect missing data | Check null counts per column with `df.isnull().sum()` |
| Numerical columns | Impute using **mean or median** |
| Categorical columns | Impute using the **mode** |
| Critical columns that cannot be reasonably imputed | **Drop rows** with missing values to maintain data integrity |

---

## 📊 Step 2: Visualizations with Matplotlib / Pandas Plot

| Chart | Description |
|-------|-------------|
| **Line Chart** | Fare over time, with `pickup` (converted to datetime) on the x-axis and `fare` on the y-axis |
| **Bar Chart** | Total fare per `pickup_borough` (group by borough and sum fare) |
| **Pie Chart** | Distribution of trips by `payment` method, with each slice showing trip count |
| **Histogram** | Distribution of `distance`, with a customised number of bins for better granularity |
| **Box Plot** | Distribution of `tip` amounts for each `pickup_borough` |

---

## 🎨 Step 3: Visualizations with Seaborn

| Chart | Description |
|-------|-------------|
| **Count Plot** | Number of trips in each `pickup_borough` |
| **Scatter Plot** | `distance` vs `fare`, with points colored by `pickup_borough` |
| **Heatmap** | Correlation matrix of `distance`, `fare`, `tip`, `tolls`, and `total` |
| **Pair Plot** | Pairwise relationships between `distance`, `fare`, `tip`, and `total`, colored by `pickup_zone` |
| **Violin Plot** | Distribution of `fare` for each `payment` method |

---

## 📈 Sample Code Snippets

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset("taxis")

# Convert pickup to datetime
df['pickup'] = pd.to_datetime(df['pickup'])

# Bar chart: total fare by borough
df.groupby('pickup_borough')['fare'].sum().plot(kind='bar')
plt.title('Total Fare by Pickup Borough')
plt.show()

# Seaborn count plot
sns.countplot(data=df, x='pickup_borough')
plt.show()

# Correlation heatmap
sns.heatmap(df[['distance', 'fare', 'tip', 'tolls', 'total']].corr(),
            annot=True, cmap='coolwarm')
plt.show()
```

---

## 🔍 Key Insights to Look For

- Which boroughs generate the most trips and the highest total fare
- How strongly `distance` and `fare` are correlated
- Which payment methods are most common, and how fares differ across them
- Whether tips vary across boroughs
- Outliers in fare, distance, and tip amounts

*(Add your own observations here after running the analysis.)*

---

## 💡 Concepts Demonstrated

- Missing value detection and imputation
- Datetime conversion with `pd.to_datetime()`
- Grouping and aggregation with `groupby()`
- Visualization with Matplotlib/Pandas plotting: line, bar, pie, histogram, box
- Statistical visualization with Seaborn: count, scatter, heatmap, pair, violin

---

## 👤 Author

**Revathi**

---

## 📄 License

This project is created for educational purposes as part of a Data Analytics course assignment.
