# Traditional Train/Test/Validation Split

## Why We Split Data
When training a machine learning model, we need to know how it performs on **unseen data**.  
- **Training set**: used to fit the model  
- **Validation set**: used to tune model parameters and check performance during training  
- **Test set**: used only for final evaluation  

## Common Dataset Ratios
A typical split is:  
- **Training:** 60%  
- **Validation:** 20%  
- **Testing:** 20%  

> Validation helps us choose the best model settings **without touching the test set**.

# Train, Validation, and Test Split Explained

## Why We Split Data
In machine learning, we want to know how our model performs on **unseen data**.  
To do this, we divide the data into **three sets**:

1. **Training set** – Data used to fit/train the model.  
2. **Validation set** – Data used to tune the model’s hyperparameters (like number of trees, learning rate, etc.) during training.  
3. **Test set** – Data used only once at the very end to check how good the model is on completely unseen data.

> The key idea: **Never touch the test set until everything else is finalized.**

---

## Common Dataset Ratios
- **Training:** 60%  
- **Validation:** 20%  
- **Testing:** 20%  

You can adjust depending on how much data you have.

---

## Step-by-Step Split with Example

Suppose we have a dataset of **10 samples**:
Data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


### Step 1: Split into Training + Test (80/20)
- Training + validation will get 80% → 8 samples  
- Test set will get 20% → 2 samples  

**Example Split:**
Training + Validation: [1, 2, 3, 4, 5, 6, 7, 8]
Test Set: [9, 10]


### Step 2: Split Training + Validation into Final Training + Validation (75/25)
- Training gets 75% of 8 samples → 6 samples  
- Validation gets 25% of 8 samples → 2 samples  

**Example Split:**

Training: [1, 2, 3, 4, 5, 6]
Validation: [7, 8]
Test: [9, 10] (kept aside)


✅ Now we have the **final split**:  
- 60% Training → 6/10 samples  
- 20% Validation → 2/10 samples  
- 20% Test → 2/10 samples  

---

## Dry Run in Python

```python
from sklearn.model_selection import train_test_split

# Example dataset
X = list(range(1, 11))  # Features
y = list(range(1, 11))  # Target (for simplicity, same as features)

# Step 1: Split into temp_train (80%) + test (20%)
X_temp_train, X_test, y_temp_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Step 2: Split temp_train into final_train (75%) + validation (25%)
X_train, X_val, y_train, y_val = train_test_split(
    X_temp_train, y_temp_train, test_size=0.25, random_state=42
)

print("Training Set:", X_train)
print("Validation Set:", X_val)
print("Test Set:", X_test)

```
Expected Output:
Training Set: [1, 2, 3, 4, 5, 6]
Validation Set: [7, 8]
Test Set: [9, 10]