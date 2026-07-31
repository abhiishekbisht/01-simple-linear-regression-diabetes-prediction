# 🚀 Simple Linear Regression: Diabetes Progression Analysis

This repository contains a clean, professional implementation of **Simple Linear Regression** (SLR) using the standard Scikit-Learn Diabetes dataset. The goal is to predict disease progression one year after baseline using a single independent feature: **Body Mass Index (BMI)**.

---

## 📂 Project Structure

- 📓 **[SLR-1.ipynb](SLR-1.ipynb)**: The main Jupyter Notebook containing dataset exploration, feature selection, train-test splitting, model training, visualization, and performance evaluation.

---

## 📊 Dataset Overview

The project uses the **Diabetes dataset** from Scikit-Learn, which includes data from $n = 442$ diabetes patients.

### Features
| Attribute | Description | Type |
| :--- | :--- | :--- |
| `age` | Age in years | Numerical (scaled) |
| `sex` | Gender | Categorical (scaled) |
| `bmi` | **Body Mass Index (Selected Independent Feature)** | Numerical (scaled) |
| `bp` | Average blood pressure | Numerical (scaled) |
| `s1` - `s6` | Six blood serum measurements (tc, ldl, hdl, tch, ltg, glu) | Numerical (scaled) |
| `target` | **Progression measure one year after baseline (Dependent Variable)** | Continuous |

> [!NOTE]
> All feature variables are mean-centered and scaled by the standard deviation times the square root of `n_samples` (i.e. the sum of squares of each column totals 1).

---

## 🛠️ Step-by-Step Implementation Workflow

The regression modeling is implemented in the following sequence:

### 1. Data Preparation & Exploration
- Load the dataset via `sklearn.datasets.load_diabetes()`.
- Create a `pandas.DataFrame` representation for exploration.
- Inspect the relationship and formulate the problem: predicting disease progression from BMI.

### 2. Feature & Target Splitting
- **Independent Variable ($X$)**: Body Mass Index (`bmi`)
- **Dependent Variable ($y$)**: Progression target (`target`)

### 3. Training & Validation Split
- Split data into **80% Training** and **20% Testing** subsets.
- Set `random_state = 2` to guarantee reproducibility.

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=2)
```

### 4. Model Training
We fit a simple linear model $y = \beta_0 + \beta_1 X$ using Ordinary Least Squares (OLS) via `sklearn.linear_model.LinearRegression`.

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
```

#### Extracted Parameters:
- **Slope ($\beta_1$)**: $\approx 974.48$
- **Intercept ($\beta_0$)**: $\approx 152.45$

The resulting linear model equation is:
$$\text{Progression} = 974.48 \times \text{BMI} + 152.45$$

### 5. Evaluation
The model's performance on the unseen test set is measured using Mean Squared Error (MSE):
* **Mean Squared Error (MSE)**: $\approx 3898.26$

```python
from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y_test, y_pred)
```

---

## 💻 How to Run Locally

### 1. Install Dependencies
Ensure you have the required packages installed:
```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### 2. Execute the Jupyter Notebook
Run the following command to start Jupyter:
```bash
jupyter notebook
```
Then open **[SLR-1.ipynb](SLR-1.ipynb)** and run all cells to reproduce the results and visualizations.
