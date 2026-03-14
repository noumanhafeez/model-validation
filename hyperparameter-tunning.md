# Hyperparameter Tuning (Simple Explanation)

## 1. Introduction
Hyperparameter tuning is the process of **finding the best settings for a machine learning model** to improve its performance.

When we train a model, we test different configurations and choose the one that gives the **best accuracy or performance**.

---

# 2. Model Parameters vs Hyperparameters

## Model Parameters
Model parameters are **learned automatically from the data during training**.

They are **not set by the programmer**.

### Example (Linear Regression)

A linear regression equation:

y = mx + b

Here:

- **m (slope)** → coefficient  
- **b (intercept)**

These values are **calculated by the model after training**.

In Python:

```python
from sklearn.linear_model import LinearRegression

lr = LinearRegression()
lr.fit(X_train, y_train)

print(lr.coef_)       # coefficients
print(lr.intercept_)  # intercept

Important point:

If .fit() is not called, these parameters do not exist yet, because the model has not learned anything.

Hyperparameters

Hyperparameters are settings chosen before training the model.

They control how the model learns.

They are manually set by the developer or tuned during experimentation.

3. Example: Random Forest Hyperparameters

Some important hyperparameters in Random Forest are:

| Hyperparameter      | Meaning                                      |
| ------------------- | -------------------------------------------- |
| `n_estimators`      | Number of trees in the forest                |
| `max_depth`         | Maximum depth of each tree                   |
| `max_features`      | Number of features considered when splitting |
| `min_samples_split` | Minimum samples required to split a node     |

from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(
    n_estimators=100,
    max_depth=10,
    min_samples_split=5
)
These values are chosen before training, so they are hyperparameters.

4. What is Hyperparameter Tuning?

Hyperparameter tuning means trying different hyperparameter values to find the best combination.

Process:

Choose hyperparameters to tune

Define possible values

Train the model with different combinations

Evaluate performance

Select the best configuration

5. Example of Hyperparameter Tuning

Suppose we try different values:

| n_estimators | max_depth | Accuracy |
| ------------ | --------- | -------- |
| 50           | 5         | 0.81     |
| 100          | 8         | 0.86     |
| 200          | 10        | 0.88     |
The third combination performs best, so we choose it.

6. Choosing Value Ranges

We define possible values for hyperparameters.

Example:
max_depth = [3, 5, 8, 10]
min_samples_split = [2, 4, 8]
max_features = [2, 4, 6]

During tuning, the model may randomly pick combinations like:

max_depth = 8

min_samples_split = 4

max_features = 2

You can see model settings using:
model.get_params()

7. Too Many Hyperparameters

Some models have many hyperparameters.

Example:

Random Forest may have 15+ hyperparameters.

But in practice:

We usually tune only a few important ones, such as:

n_estimators

max_depth

max_features

min_samples_split

Tuning too many parameters can:

Take a lot of time

Make results hard to analyze