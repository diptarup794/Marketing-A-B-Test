# 📊 A/B Testing Analysis

This project performs a full A/B testing workflow to determine whether a new landing page (variant B) leads to better conversion rates compared to the existing one (variant A). The analysis is statistical and data-driven, following the standard methodology of hypothesis testing with both parametric and simulation-based approaches.

---

## 📁 Files

- `A_B Test.ipynb`: Jupyter notebook that contains all the analysis, plots, and conclusions for the A/B test.

---

## 🎯 Objective

To evaluate whether changing the landing page increases the user conversion rate.

---

## 🧠 Hypotheses

### Null Hypothesis (H₀):
> The new landing page (variant B) has the **same or lower** conversion rate than the old page (variant A).

### Alternative Hypothesis (H₁):
> The new landing page (variant B) has a **higher** conversion rate than the old page (variant A).

---

## 🗃️ Dataset Description

The dataset includes information for each user in the A/B test:

| Column        | Description                             |
|---------------|------------------------------------------|
| `user_id`     | Unique identifier for each user          |
| `group`       | Either `control` (variant A) or `treatment` (variant B) |
| `landing_page`| Page version user landed on (`old_page` or `new_page`) |
| `converted`   | 1 if the user converted, 0 otherwise     |

---

## 🔍 Analysis Workflow

### 1. **Data Cleaning**
- Removed rows where the `group` and `landing_page` were mismatched (e.g., control with new_page).
- Ensured that each user was shown the correct landing page.

### 2. **Exploratory Data Analysis (EDA)**
- Checked the distribution of users in control and treatment groups.
- Calculated and compared conversion rates for both groups.

### 3. **Hypothesis Testing: Z-Test for Proportions**
- Used a one-tailed z-test to check if the treatment group had a higher conversion rate.
- Formula used:

  \[
  z = \frac{p_B - p_A}{\sqrt{p_{pooled}(1 - p_{pooled})(\frac{1}{n_A} + \frac{1}{n_B})}}
  \]

- Computed p-value from the z-score using:
  ```python
  from scipy.stats import norm
  p_value = 1 - norm.cdf(z_score)
