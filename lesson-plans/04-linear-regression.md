# Activity 4: Linear Regression from Scratch

> **Notebook:** `Linear Models/LinearRegressionComplete.ipynb`
> **Suggested time:** 30–45 minutes
> **Dataset:** Synthetically generated (in-notebook)

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Derive and implement the closed-form solution to linear regression using the
   pseudoinverse: **w** = (X^T X)^{−1} X^T **y**
2. Explain what the pseudoinverse minimizes and why it is the optimal solution
   under squared error.
3. Evaluate and compare in-sample and out-of-sample (test) error for a linear
   model.
4. Demonstrate that the regression solution produces lower in-sample error than
   any other weight vector.

---

## Prerequisites

- Matrix multiplication and transpose (NumPy: `np.matmul`, `np.transpose`)
- Matrix inversion (`np.linalg.inv`)
- Understanding of squared error loss
- Familiarity with training vs. test set distinction

---

## Materials

- Notebook: `Linear Models/LinearRegressionComplete.ipynb`
- Dataset: Generated inside the notebook using `generate_lr(N, w0, w1)`; no
  external file needed

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor writes the pseudoinverse formula on the board |
| Individual coding | 10–15 min | Students implement the regression steps |
| Group discussion | 10 min | Compare weight vectors; discuss in-sample vs. test error |
| Share out | 10 min | Groups share and instructor connects to the math |

---

## Instructor Notes

### Setup
- The notebook generates a synthetic dataset from a known target function (e.g.,
  y = x + noise). Students compute the regression weights and compare the learned
  hypothesis to the true function visually.
- No external dataset is required — the `generate_lr` function is defined in
  the notebook.

### Introducing the activity (5 min)
Write on the board:

> **w*** = (X^T X)^{−1} X^T **y**

Ask students: "Where does this formula come from?" Briefly connect it to
minimizing sum of squared errors. The goal is not to re-derive it but to make
sure students understand what each matrix operation is doing before they implement it.

### Step-by-step guidance
The notebook walks through the pseudoinverse in four steps:
1. Construct X^T X
2. Invert it
3. Compute X^T (the pseudoinverse)
4. Multiply by **y** to get **w**

Students should run each step separately and check the shape of the output —
this helps catch dimension errors early.

### Common Issues
- Students sometimes forget to prepend the bias column (a column of 1s) to X.
  The notebook includes this but students may delete it accidentally.
- `np.linalg.inv` will raise a `LinAlgError` if X^T X is singular. This
  shouldn't happen with the generated data, but if students modify the generator
  they may hit this.
- Students may not understand why the test error is higher than the in-sample
  error. Use this as a teaching moment about in-sample optimization vs.
  generalization.

### Key Demonstration
The notebook includes a cell comparing the regression weights **w*** to an
arbitrary weight vector **w_other = [3, 2]**. The squared error for **w_other**
is always larger. Have students run this and ask: "Can you find a **w_other**
that beats **w***? Why or why not?"

---

## Discussion Prompts

1. The pseudoinverse gives us the global minimum of the squared error. Does that
   mean it gives us the best possible model? What are its limitations?
2. Your in-sample error is lower than your test error. What does this gap tell
   you about the model?
3. What would happen to the learned weights if you added more training data?
   What if you added more features?
4. Linear regression minimizes squared error. Can you think of a problem where
   squared error is not the right loss function to use?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Correctly compute X^T X and its inverse
- [ ] Correctly compute the pseudoinverse and the weight vector **w**
- [ ] Plot the dataset, the true target function, and the learned hypothesis
      on the same axes (colored differently)
- [ ] Report both in-sample squared error and test squared error
- [ ] Include a 1–2 sentence observation comparing the two errors

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
