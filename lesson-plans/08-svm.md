# Activity 8: Support Vector Machines

> **Notebook:** `SVM/SVM.ipynb`
> **Suggested time:** 20–30 minutes
> **Dataset:** `synthetic_dataset.csv` — see `data/README.md` to regenerate

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Fit a Support Vector Machine classifier using scikit-learn on a 2D dataset.
2. Visualize the SVM decision boundary and margin using a contour plot.
3. Identify support vectors and explain their role in defining the decision boundary.
4. Compare the SVM boundary to the PLA boundary from Activity 2 on the same dataset.

---

## Prerequisites

- Activity 2 (Perceptron Learning Algorithm on synthetic data) — students will
  compare SVM to PLA on the same dataset
- Understanding of what a linear decision boundary is
- Basic sklearn usage (`fit`, `predict`)

---

## Materials

- Notebook: `SVM/SVM.ipynb`
- Dataset: `Perceptron/synthetic_dataset.csv`
  - Same dataset used in Activity 2. Generate it using `PerceptronHelper.ipynb`
    or the script in `data/README.md`.

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor explains margin maximization conceptually |
| Individual work | 10 min | Students fit SVM and produce the decision boundary plot |
| Group discussion | 10 min | Compare SVM boundary to PLA boundary; discuss trade-offs |
| Share out | 5 min | Class reflection on when to use each algorithm |

---

## Instructor Notes

### Setup
- This notebook uses the same synthetic 2D dataset as Activity 2, making a
  direct comparison to PLA natural and concrete.
- The notebook uses `sklearn.svm.SVC` with a linear kernel. The `plot_contours`
  helper function visualizes the decision boundary and margin using `predict` on
  a mesh grid.
- Students do not need to implement SVM from scratch — the focus is on
  understanding what SVM produces and how it compares to PLA.

### Introducing the activity (5 min)
Draw two possible linear separators for a linearly separable dataset and ask:

> "PLA will find *a* separator. How would you choose the *best* one?"

Introduce margin as the distance from the boundary to the nearest points, and
explain that SVM finds the boundary that maximizes this margin. Keep this brief —
the notebook makes it concrete.

### Key Comparison: SVM vs. PLA
The most valuable part of this activity is the comparison. Ask students to:
1. Run SVM and plot the boundary
2. Recall or re-run their PLA boundary from Activity 2
3. Place both boundaries side-by-side (or overlay them)

Key questions to prompt:
- "Both algorithms correctly classify the data. What is different about the two
  boundaries?"
- "Which boundary do you think would generalize better to new data? Why?"

### Common Issues
- The `plot_contours` function requires building a mesh grid (`np.meshgrid`) over
  the feature space, which can be confusing. The function is provided — students
  should not need to modify it, just call it.
- Students may be surprised that the SVM boundary looks very different from PLA
  even though both achieve zero training error. Use this to reinforce that the
  training set error is not the only thing that matters.

### Facilitation Tips
- If students completed Activity 2, ask them to bring their PLA weight vector to
  this activity and compare it to the SVM coefficients. This can spark a useful
  discussion about the geometry.
- For advanced students: ask what happens when you change the kernel from
  `linear` to `rbf`. This previews the kernel trick without requiring a deep dive.

---

## Discussion Prompts

1. Both PLA and SVM find a line that separates the data. Why might SVM's line
   be considered "better" even if they both achieve 100% training accuracy?
2. What are "support vectors"? How many did your SVM use? What would happen to
   the boundary if you removed one of them?
3. PLA is sensitive to the order in which it sees misclassified points; SVM
   is not. What does that tell you about the stability of each algorithm?
4. SVM maximizes the margin to the nearest points. In what kind of problem might
   this strategy fail?
5. When would you choose SVM over logistic regression, or vice versa?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Successfully load the dataset and fit an SVM classifier
- [ ] Produce a scatter plot of the dataset with the SVM decision boundary and
      margin visualized
- [ ] Identify (by marking or describing) the support vectors in the plot
- [ ] Include a 2–3 sentence comparison to the PLA decision boundary from
      Activity 2: what is similar, what is different, and which do you prefer?

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
