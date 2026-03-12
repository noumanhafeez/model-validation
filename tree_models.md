# Regression Models and Random Forest (Simple Explanation)

## Two Types of Machine Learning Models
In machine learning, there are mainly two types of predictive models.

- **Regression Models** → Used when the output is a **continuous number**.
- **Classification Models** → Used when the output is a **category or class**.

### Example
Regression Example:
- Predict **house price**
- Predict **salary**
- Predict **temperature**

Classification Example:
- Email is **Spam or Not Spam**
- Tumor is **Cancer or Not Cancer**
- Image is **Cat or Dog**

## Focus of This Lesson
This lesson focuses on **Regression Models**, specifically **Random Forest Regression** using **scikit-learn**.

---

# Random Forest in Scikit-learn

## What is Random Forest?
Random Forest is a machine learning model that combines **many decision trees** to make better predictions.

Instead of relying on **one decision tree**, it creates **many trees** and averages their predictions.

This usually gives **more accurate and stable results**.

---

# Decision Trees (Basic Idea)

## What is a Decision Tree?
A **decision tree** splits data step by step based on conditions until it reaches a final prediction.

The final point is called a **leaf node**.

### Example
Suppose we want to predict **how much debt a person has**.

The tree might ask questions like:

- Are you **left-handed?**
- What is your **age?**
- Do you **like onions?**

Based on the answers, the observation moves through the tree.

Example path:

Bob's information:
- Left-handed → Yes
- Age → 18
- Likes onions → Yes

After following the tree, the model predicts:

**Debt = $4,000**

This value is usually the **average value of similar people in the training data**.

---

# Random Forest Idea

## Why Use Many Trees?
One decision tree can sometimes make **poor predictions**.

Random Forest solves this by building **many decision trees**.

Each tree gives its own prediction.

Then the model calculates the **average prediction**.

### Example
Suppose 5 trees predict Bob's debt:

Tree 1 → $4000  
Tree 2 → $4200  
Tree 3 → $4300  
Tree 4 → $4100  
Tree 5 → $4400  

Final Random Forest Prediction:

Average = **$4200**

This makes the model **more accurate and stable**.

---

# Important Random Forest Parameters

## n_estimators
This tells the model **how many trees to create**.

Example:
- n_estimators = 10 → 10 trees
- n_estimators = 100 → 100 trees

More trees usually give **better predictions** but require **more computation**.

---

## max_depth
This controls **how deep each decision tree can grow**.

Depth means how many splits the tree can make.

Example:
- max_depth = 3 → small/simple tree
- max_depth = 10 → larger/more complex tree

Too deep trees may cause **overfitting**.

---

## random_state
This ensures the model gives **the same results every time you run it**.

Example:

```python
RandomForestRegressor(random_state=1111)