# Regression Model Accuracy Metrics (Simple Summary)

## 1. What is a Regression Model?
- Regression models are used to **predict continuous values** (numbers).
- Examples:
  - Predicting how many points a player will score.
  - Predicting the number of puppies a dog will have.
  - Predicting monthly gas expenses.

---

# 2. Mean Absolute Error (MAE)

### What it is
MAE measures the **average absolute difference** between the **actual value** and the **predicted value**.

### Formula
MAE = (|Actual - Predicted| + ... ) / Total observations

### Example
Actual puppies = 6  
Predicted puppies = 4  

Error = |6 - 4| = **2**

### Key Points
- Takes the **absolute difference**.
- **All errors are treated equally**.
- **Not sensitive to outliers**.

### When to Use
Use MAE when **large errors should not affect the model too much**.

Example:
- Predicting **monthly gas bills** where a rare road trip may create an unusual value.

---

# 3. Mean Squared Error (MSE)

### What it is
MSE measures the **average squared difference** between the **actual value** and the **predicted value**.

### Formula
MSE = ((Actual - Predicted)² + ... ) / Total observations

### Example
Actual puppies = 6  
Predicted puppies = 4  

Error = (6 - 4)² = **4**

### Key Points
- Errors are **squared**.
- **Large errors become much bigger**.
- **Sensitive to outliers**.

### When to Use
Use MSE when **large errors should be penalized more**.

Example:
- Detecting **rare but important events** (like unusual behavior in data).

---

# 4. MAE vs MSE

| Metric | How It Treats Errors | Sensitivity to Outliers |
|------|---------------------|-------------------------|
| MAE | All errors treated equally | Low |
| MSE | Large errors punished more | High |

⚠️ Their values are in **different units**, so they **should not be directly compared**.

---

# 5. Example from Candy Dataset
A model predicted the **win percentage of candies**.

Results:
- **MAE ≈ 10**
- This means predictions are **about 10 percentage points off on average**.

- **MSE ≈ 141**
- Large errors had **more influence on the result**.

---

# 6. Evaluating Model on Specific Data

Sometimes we want to test accuracy on **specific groups of data**.

Example:
- Chocolate candies
- Non-chocolate candies

Results:
- Chocolate candies error < 9
- Non-chocolate candies error ≈ 11

✔ This means the model **performed better on chocolate candies**.

---

# Final Idea

When validating regression models:

- Use **MAE** if you want **simple average error**.
- Use **MSE** if **large errors are very important**.
- You can also **evaluate performance on specific subsets of data**.