# Classification Metrics (Simple Explanation)

## 1. What is a Classification Model?

A **classification model** predicts **categories or classes**, not numbers.

### Examples

* Email → **Spam or Not Spam**
* Medical test → **Disease or No Disease**
* Basketball game → **Win or Loss**

Because the output is a **category**, we use different accuracy metrics than regression.

---

# 2. Common Classification Metrics

There are many metrics used to evaluate classification models:

* Accuracy
* Precision
* Recall
* Specificity
* F1-score

But the most common and easy to understand are:

* **Accuracy**
* **Precision**
* **Recall**

---

# 3. Confusion Matrix

A **confusion matrix** is a table used to evaluate classification models.

For **binary classification**, it is a **2 × 2 table**.

| Actual / Predicted | Predicted 0         | Predicted 1         |
| ------------------ | ------------------- | ------------------- |
| Actual 0           | True Negative (TN)  | False Positive (FP) |
| Actual 1           | False Negative (FN) | True Positive (TP)  |

### Meaning of each term

**True Positive (TP)**
Model predicted **1 and it is actually 1**

Example:
Model predicts **a patient has cancer** and the patient **really has cancer**

---

**True Negative (TN)**
Model predicted **0 and it is actually 0**

Example:
Model predicts **no cancer** and the patient **really does not have cancer**

---

**False Positive (FP)**
Model predicted **1 but actually it is 0**

Example:
Model predicts **cancer**, but patient **does not have cancer**

---

**False Negative (FN)**
Model predicted **0 but actually it is 1**

Example:
Model predicts **no cancer**, but patient **actually has cancer**

---

# 4. Accuracy

## What is Accuracy?

Accuracy measures **how many predictions were correct overall**.

### Formula

Accuracy = (TP + TN) / Total Predictions

### Example

| Value          | Count |
| -------------- | ----- |
| True Positive  | 62    |
| True Negative  | 23    |
| False Positive | 7     |
| False Negative | 8     |

Total = 100

Accuracy = (62 + 23) / 100 = **85%**

Meaning:
The model predicted **85% of cases correctly**.

---

# 5. Precision

## What is Precision?

Precision measures **how accurate the positive predictions are**.

### Formula

Precision = TP / (TP + FP)

### Example

TP = 62
FP = 7

Precision = 62 / (62 + 7)

Precision = **62 / 69 ≈ 0.90**

Meaning:

When the model predicts **positive**, it is correct **about 90% of the time**.

---

### When Precision is Important

Use precision when **false positives are costly**.

Example:

* Hiring candidates
* Fraud detection
* Expensive marketing campaigns

Example scenario:
If flying candidates for interviews costs **$2000**, you want to be sure predicted candidates **are really good**.

---

# 6. Recall

## What is Recall?

Recall measures **how many real positive cases the model found**.

### Formula

Recall = TP / (TP + FN)

### Example

TP = 62
FN = 8

Recall = 62 / (62 + 8)

Recall = **62 / 70 ≈ 0.89**

Meaning:

The model detected **89% of all real positive cases**.

---

### When Recall is Important

Use recall when **missing positive cases is dangerous**.

Example:

* Cancer detection
* Fraud detection
* Security threats

Example scenario:
Missing a cancer patient could be **life-threatening**, so doctors prefer **high recall**.

---

# 7. Using Scikit-Learn

These metrics can be calculated easily in Python.

```python
from sklearn.metrics import accuracy_score, precision_score, recall_score

accuracy_score(y_test, predictions)
precision_score(y_test, predictions)
recall_score(y_test, predictions)
```

Each function returns **a single value representing the metric**.

---

# 8. Quick Comparison

| Metric    | What it Measures              | When to Use                    |
| --------- | ----------------------------- | ------------------------------ |
| Accuracy  | Overall correct predictions   | Balanced datasets              |
| Precision | Correct positive predictions  | False positives are costly     |
| Recall    | Ability to find all positives | Missing positives is dangerous |

---

# Key Idea

* **Accuracy** → Overall performance
* **Precision** → How reliable positive predictions are
* **Recall** → How many real positives were detected
