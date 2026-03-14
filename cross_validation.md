# Cross-Validation

## 1. What is Cross-Validation?
- Cross-validation is a **better way to validate models** than a single training/testing split.
- Instead of using just one train/test split, we **create multiple training/validation splits**.
- This ensures our model is tested on **all data points**, giving a more reliable estimate of its performance.

---

## 2. Why Use Cross-Validation?
- Single splits can give **misleading results**.
- Different splits may produce different accuracy or error metrics.
- Cross-validation reduces the risk of **overfitting or underestimating errors**.

---

## 3. How It Works (K-Fold Example)
- Suppose we have **5-fold cross-validation**:
  - Split the dataset into 5 parts (folds).
  - Each fold is used **once as the validation set**, while the remaining 4 folds are used for training.
  - Repeat this 5 times so every data point is validated exactly once.
- Example:
  - X = numbers 0–39  
  - y = first 20 zeros, next 20 ones  
  - KFold with 5 splits → generates **indices** for training and validation sets.
- Training/validation datasets are created by **indexing X and y using these indices**.

---

## 4. Steps to Use Cross-Validation
1. Create K folds of your data using `KFold(n_splits=K)` from scikit-learn.
2. Loop through each fold:
   - Train the model on the training indices.
   - Validate the model on the validation indices.
   - Record the performance metric (e.g., accuracy, MAE).
3. Compute the **average metric** across all folds → gives a more **robust estimate of model performance**.

---

## 5. Key Takeaways
- Cross-validation is the **gold standard** for model validation.
- It ensures **all data is used for training and validation**.
- Reduces the effect of **random train/test splits** on your evaluation.
- Helps in **choosing better models and hyperparameters** reliably.
