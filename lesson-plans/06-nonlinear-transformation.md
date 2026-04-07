# Activity 6: Nonlinear Transformation with Linear Regression

> **Notebook:** `Nonlinear Transformation/LinearRegressionNonLinear.ipynb`
> **Suggested time:** 30–45 minutes
> **Dataset:** Synthetically generated (in-notebook)

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Explain how a nonlinear feature transformation allows a linear model to fit
   nonlinear data.
2. Apply polynomial feature expansion (up to degree 4) to a 1D regression problem.
3. Observe and describe the trade-off between in-sample and out-of-sample error
   as model complexity increases.
4. Connect the concept of overfitting to what happens when the model memorizes
   training data at the expense of generalization.

---

## Prerequisites

- Activity 4 (Linear Regression from Scratch) — students should understand the
  pseudoinverse and be able to interpret in-sample vs. test error
- Understanding of polynomial functions
- NumPy array operations

---

## Materials

- Notebook: `Nonlinear Transformation/LinearRegressionNonLinear.ipynb`
- Dataset: Generated inside the notebook using `generate_lr`; no external file needed

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor demonstrates fitting a line to nonlinear data |
| Individual work | 15 min | Students run linear fit, then expand to polynomial features |
| Group discussion | 10 min | Compare train vs. test error for different polynomial degrees |
| Share out | 10 min | Groups report findings; instructor connects to bias-variance trade-off |

---

## Instructor Notes

### Setup
- The notebook generates data from a target function and adds noise. The key
  experiment is to compare regression with:
  - Linear features: X = [1, x]
  - Polynomial features: X = [1, x, x², x³, x⁴]
- The `generate_lr` function and `lr` (linear regression) helper are defined in
  the notebook. The pseudoinverse is already implemented — students focus on the
  feature construction.

### Introducing the activity (5 min)
Plot a clearly nonlinear dataset (or draw one on the board) and ask:

> "Can a straight line fit this data? What if we could transform the data first?"

Briefly show on the board that mapping x → [1, x, x²] and then fitting a linear
model in the new space is equivalent to fitting a parabola in the original space.

### Core Experiment
Students should run the notebook for at least two configurations:
1. `X = [[1, x] for x in data]` — linear fit
2. `X = [[1, x, x**2, x**3, x**4] for x in data]` — degree-4 polynomial

For each, they should record in-sample squared error and test squared error.

### Key Teaching Moment
The polynomial model will have lower in-sample error but potentially higher
test error (especially with small N). Use this to introduce the concept of
overfitting without naming it — let students describe what they see first, then
name the phenomenon.

> "What does it mean when your model is very accurate on the training data but
> much worse on new data?"

### Common Issues
- Students sometimes construct X with the wrong shape. Remind them that each row
  should be a feature vector for one data point.
- With very few training points (N=10), the degree-4 polynomial may interpolate
  the data perfectly (in-sample error ≈ 0). This is a great observation — prompt
  students to increase N and see what changes.
- The `plot4poly` function visualizes the fitted polynomial — students should use
  this rather than writing their own.

---

## Discussion Prompts

1. You added more features and your in-sample error went down. Is that always a
   good thing? What happened to your test error?
2. What does the degree-4 polynomial "know" that the linear model does not?
   What might it "believe" that isn't true?
3. How would you choose the right polynomial degree if you didn't know the true
   target function?
4. This activity used synthetic data where you know the true function. In
   practice, you never know it. How does that change your strategy?
5. What does a very low in-sample error with a very high test error tell you
   about a model?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Fit a linear regression model (degree 1) and report in-sample and test squared error
- [ ] Fit a degree-4 polynomial regression model and report in-sample and test squared error
- [ ] Plot both the training data and both fitted curves (linear and polynomial)
      on the same axes
- [ ] Include a 2–3 sentence observation comparing the two models: which has
      lower in-sample error? Which generalizes better? What does this suggest?

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
