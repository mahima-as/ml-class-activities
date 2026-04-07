# Activity 3: Perceptron Learning Algorithm (Digit Data)

> **Notebook:** `Perceptron/Digits PLA.ipynb`
> **Suggested time:** 15 minutes
> **Dataset:** ZipDigits — see `data/README.md`

> **Note for instructors:** This is a shorter verification activity meant to
> follow Activity 2. Students apply the PLA implementation they built on
> synthetic data to real handwritten digit images. Use this activity when you
> want students to see how the algorithm behaves on real, higher-dimensional
> data. It can be run independently if students are given the PLA helper
> functions in advance.

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Extract two interpretable features (intensity and symmetry) from raw digit
   image data.
2. Apply a previously implemented PLA to a real binary classification problem
   (distinguishing two digit classes).
3. Interpret a scatter plot of real image data in feature space and evaluate
   whether the classes appear linearly separable.

---

## Prerequisites

- Completion of Activity 2 (Perceptron PLA on synthetic data), **or** access
  to working `sign`, `findMisclassified`, and `PLA` implementations
- Understanding of feature extraction (intensity and symmetry from Activity 1)
- ZipDigits dataset downloaded and accessible

---

## Materials

- Notebook: `Perceptron/Digits PLA.ipynb`
- Dataset: `Perceptron/Digits/ZipDigits.train`

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 2 min | Instructor frames the task: same algorithm, real data |
| Individual work | 8 min | Students run feature extraction and apply PLA |
| Share out | 5 min | Discuss results as a class |

---

## Instructor Notes

### Setup
- This notebook provides the `extract_features` and `plot_features` helper
  functions. Students should not need to rewrite them — the focus is on
  connecting the algorithm to real data.
- The notebook selects two digit classes to compare (e.g., digit 1 vs. digit 5).
  You can change `digit1` and `digit2` in the notebook to explore other pairs.
- If students did not complete Activity 2, provide a working `PLA` function
  snippet they can paste in.

### Facilitation Tips: Assign Different Digit Pairs to Different Groups
Deliberately assign different digit pairs to different groups (or halves of the
class). Suggested pairings:

| Group | Digit Pair | Expected Difficulty |
|-------|-----------|---------------------|
| A | 2 vs. 6 | Moderate — some overlap in symmetry |
| B | 7 vs. 9 | Harder — similar intensity and symmetry |
| C | 1 vs. 5 | Easier — well separated in feature space |
| D | 3 vs. 8 | Harder — similar shape characteristics |

Reserve the **last 5 minutes of share-out** specifically for groups to compare
their results across digit pairs:
- "Group A's PLA converged in X iterations. Group B's did not converge at all.
  Why might that be?"
- Display all scatter plots side-by-side if possible.
- Ask students to predict which pairs will be hardest before revealing results —
  then see if their intuition matched reality.

This structured comparison is one of the most effective parts of the activity:
students quickly internalize that the choice of what to classify matters as much
as the algorithm itself.

### Common Issues
- Students may get index errors if they forget that the first column of each row
  is the digit label, not a pixel. The `extract_features` function handles this,
  but if students modify it they may break it.
- Loading the ZipDigits file line-by-line with `float(x) for x in line.split()`
  can take a few seconds. Warn students not to re-run that cell repeatedly.

---

## Discussion Prompts

1. Does PLA converge on this digit pair? How do you know? What does that tell
   you about the data?
2. How does the scatter plot of real digit data compare to the synthetic dataset
   from Activity 2? What differences do you notice?
3. You used only 2 features (intensity and symmetry) from a 256-dimensional
   image. What information might you be losing?
4. Which digit pair do you think would be hardest to classify using just these
   two features? Why?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Successfully load the ZipDigits training data and filter to two digit classes
- [ ] Extract intensity and symmetry features for each example
- [ ] Run PLA (or Pocket, if not linearly separable) on the feature data
- [ ] Produce a scatter plot in feature space with the decision boundary overlaid
- [ ] Include a 1–2 sentence observation: does PLA converge? Does the boundary
      appear to separate the classes well?

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
