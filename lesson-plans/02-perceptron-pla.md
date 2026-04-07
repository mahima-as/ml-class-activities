# Activity 2: Perceptron Learning Algorithm (Synthetic Data)

> **Notebook:** `Perceptron/PLA.ipynb`, `Perceptron/PerceptronHelper.ipynb`
> **Suggested time:** 30–45 minutes
> **Dataset:** `synthetic_dataset.csv` — see `data/README.md` to regenerate

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Explain the update rule of the Perceptron Learning Algorithm (PLA) and why
   it converges on linearly separable data.
2. Implement PLA from scratch, including the sign function, misclassification
   check, and weight update loop.
3. Visualize the decision boundary produced by PLA on a 2D dataset.
4. Explain the Pocket Algorithm and describe when it is needed instead of PLA.
5. Compare the performance of PLA and Pocket on the same dataset.

---

## Prerequisites

- Linear algebra: dot products, vector notation for weights and inputs
- Understanding of binary classification (labels y ∈ {−1, +1})
- Python: loops, functions, NumPy, matplotlib scatter plots
- Conceptual understanding of what a linear decision boundary is

---

## Materials

- Notebook: `Perceptron/PLA.ipynb`
- Helper notebook: `Perceptron/PerceptronHelper.ipynb` (for dataset generation)
- Dataset: `Perceptron/synthetic_dataset.csv`
  - If not available, run `PerceptronHelper.ipynb` first or use the generation
    script in `data/README.md`

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor walks through the PLA update rule on the board |
| Individual coding | 10 min | Students implement `sign`, `findMisclassified`, and `PLA` |
| Group discussion | 10 min | Compare implementations; debug together |
| Share out | 10 min | Groups share their decision boundary plots; discuss differences |
| Pocket extension | 5–10 min | *(optional)* Students implement and compare Pocket Algorithm |

---

## Instructor Notes

### Setup
- The notebook provides function stubs with comments. Students are expected to
  fill in the body of `sign(x)`, `findMisclassified(x, y, w)`, and `PLA(df)`.
- The synthetic dataset has 50 points in 2D and is linearly separable, so PLA
  is guaranteed to converge.
- Remind students to prepend the bias column `x0 = 1` before running PLA (this
  cell is already in the notebook).

### Introducing the activity (5 min)
Write the PLA update rule on the board:

> If sign(**w** · **x**_i) ≠ y_i, update: **w** ← **w** + y_i · **x**_i

Ask students: "Why does adding y_i · **x**_i move the boundary in the right direction?"
Give them 60 seconds to think before accepting answers — this primes them for the
implementation.

### Common Issues
- Students often forget to include the bias term (`x0`) in the dot product.
  Point them to the `df['x0'] = 1` cell if they get stuck.
- The `findMisclassified` function should return **one** misclassified point,
  not all of them. This trips up students who loop through everything.
- If PLA runs for a very long time, the data may not be linearly separable in
  their subset — check that `df_sample` is being used correctly.

### Pocket Algorithm Extension (optional, 5–10 min)
If time allows, have students implement the Pocket Algorithm for a dataset that
is *not* linearly separable. The notebook includes a `findNumMisclassified`
helper and a `Pocket` function stub. This is a good opportunity to discuss the
difference between guaranteed convergence and best-effort approximation.

### Facilitation Tips
- During group discussion, ask groups to compare their weight vectors `w`. They
  will likely differ — use this to discuss that PLA can converge to different
  valid separators depending on the order points are visited.
- If a group finishes early, ask them to run PLA multiple times with different
  random seeds or sample sizes and observe how the boundary changes.

---

## Student Instructions

*Distribute or display these to students at the start of the activity:*

> Write your code and execute the Perceptron Learning Algorithm on the provided
> synthetic dataset. Plot the dataset along with the final hypothesis (decision
> boundary) selected by your algorithm when it terminates.
>
> **To submit:** Commit your completed notebook to your GitHub repository under
> a branch called `class-activities`. Submit the link to your Colab notebook.

---

## Discussion Prompts

1. How many iterations did your PLA take to converge? Did other groups get a
   different number? Why might that happen?
2. PLA is guaranteed to converge on linearly separable data. What would happen
   if the data were *not* linearly separable?
3. Look at your decision boundary. Is it the only valid separator? Is it the
   best one? What does "best" even mean here?
4. How does the Pocket Algorithm differ from PLA? When would you prefer one
   over the other?
5. How would you scale this algorithm to a dataset with 1,000 features instead
   of 2?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Correctly implement the `sign` function
- [ ] Correctly implement `findMisclassified` to identify one misclassified point
- [ ] Implement `PLA` that terminates when no misclassified points remain
- [ ] Produce a scatter plot of the dataset with the final decision boundary overlaid,
      colored by class label
- [ ] Include a brief comment (1–3 sentences) on the number of iterations and
      what the boundary looks like relative to the data

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
