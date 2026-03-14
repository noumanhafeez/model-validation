# Leave-One-Out Cross-Validation (LOOCV)

## 1. What is LOOCV?

**Leave-One-Out Cross-Validation (LOOCV)** is a special case of **K-Fold Cross-Validation**.

- In normal **K-Fold**, we split the dataset into **K parts**.
- In **LOOCV**, the number of folds **K = N**, where **N = total number of data points**.

This means:

- Each time **one data point is used for validation**
- All remaining **N−1 data points are used for training**

So if a dataset has **100 samples**, we will train **100 models**.

---

## 2. How LOOCV Works

Assume we have **5 data points**:

| Data Point |
|-------------|
| A |
| B |
| C |
| D |
| E |

### Model Runs

| Model | Training Data | Validation Data |
|------|---------------|----------------|
| Model 1 | B C D E | A |
| Model 2 | A C D E | B |
| Model 3 | A B D E | C |
| Model 4 | A B C E | D |
| Model 5 | A B C D | E |

Steps:

1. Train model using **N-1 samples**
2. Test on **1 remaining sample**
3. Repeat for **every data point**
4. Calculate the **average error of all models**

---

## 3. Why Use LOOCV?

LOOCV is useful when:

- Dataset is **very small**
- You want to **use maximum data for training**
- You want the **most reliable error estimate for a single new data point**

Example:

Suppose you only have **20 training samples**.

If you use **train-test split (80/20)**:
- Train = 16
- Test = 4

But with **LOOCV**:
- Train = 19
- Test = 1

So the model learns from **almost the entire dataset**.

---

## 4. Disadvantage of LOOCV

The main problem is **computation cost**.

If you have:

| Dataset Size | Number of Models |
|---------------|----------------|
| 100 samples | 100 models |
| 1,000 samples | 1,000 models |
| 10,000 samples | 10,000 models |

So training can become **very slow**.

That is why it is usually used **only with small datasets**.

---

## 5. Practical Tip

Before running LOOCV:

Try **K-Fold with large K (like 25 or 50)**.

If it runs quickly, then LOOCV might also be feasible.

---

## 6. Python Example

```python
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor()

# Number of samples
n = X.shape[0]

scores = cross_val_score(model, X, y, cv=n)

print(scores.mean())