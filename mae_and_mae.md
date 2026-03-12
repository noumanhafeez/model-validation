# Train, Validation, and Test Split Explained

## Why We Split Data
In machine learning, we want to know how our model performs on **unseen data**.  
To do this, we divide the data into **three sets**:

1. **Training set** – Data used to fit/train the model.  
2. **Validation set** – Data used to tune the model’s hyperparameters (like number of trees, learning rate, etc.) during training.  
3. **Test set** – Data used only once at the very end to check how good the model is on completely unseen data.

> The key idea: **Never touch the test set until everything else is finalized.**

---

## When Do We Need a Validation Set?
A **validation set** is needed when:  
- We want to **tune hyperparameters** of the model (e.g., number of layers, learning rate, number of trees).  
- We want to **compare multiple models** and select the best one.  
- We want to **prevent overfitting** by monitoring performance on data not seen during training.  

> If the dataset is very small, sometimes **cross-validation** can replace a separate validation set.

---

## Common Dataset Ratios
- **Training:** 60%  
- **Validation:** 20%  
- **Testing:** 20%  

You can adjust depending on how much data you have.

---

## Step-by-Step Split with Example

Suppose we have a dataset of **10 samples**:
