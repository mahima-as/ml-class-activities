# Activity 7: Decision Trees and Random Forests

> **Notebook:** `Decision Trees/Decision Trees.ipynb`
> **Suggested time:** 45–60 minutes
> **Dataset:** Credit Approval (UCI) — see `data/README.md`

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Handle missing values and categorical features through imputation and label
   encoding.
2. Fit a decision tree classifier using scikit-learn and tune basic hyperparameters
   (`max_depth`, `min_samples_split`, `criterion`).
3. Visualize a decision tree and trace a prediction path from root to leaf.
4. Compare decision tree and random forest performance and explain why ensembles
   tend to generalize better.
5. Distinguish between training accuracy and test accuracy and explain what a
   large gap indicates.

---

## Prerequisites

- Familiarity with pandas DataFrames and basic preprocessing
- Understanding of classification (labels, training/test split)
- Conceptual understanding of entropy or Gini impurity (helpful but not required)
- Basic sklearn usage (`fit`, `predict`, `score`)

---

## Materials

- Notebook: `Decision Trees/Decision Trees.ipynb`
- Dataset: `credit approval/crx.data` — see `data/README.md` for download
  instructions (UCI Machine Learning Repository)

---

## Suggested Timeline

| Phase | Time | Description |
|-------|------|-------------|
| Introduction | 5 min | Instructor introduces the credit approval problem and the preprocessing challenge |
| Preprocessing work | 10–15 min | Students clean missing values and encode categorical features |
| Model fitting | 10 min | Students fit decision tree and evaluate on train/test |
| Group discussion | 10–15 min | Compare hyperparameter choices; discuss train vs. test accuracy |
| Random Forest extension | 5–10 min | *(optional)* Fit random forest and compare |
| Share out | 5 min | Groups share key observations |

---

## Instructor Notes

### Setup
- The credit approval dataset has 690 instances and 15 attributes, with some
  missing values (marked as `?`) and a mix of continuous and categorical features.
  All attribute names are anonymized.
- Students load the data with `header=None` and `na_values='?'`.
- This is the most preprocessing-heavy activity in the set. Budget extra time
  if students are less familiar with pandas.

### Introducing the activity (5 min)
Frame the real-world context:

> "A bank wants to automatically decide whether to approve a credit card
> application. The features are anonymized, but the decision is real. What
> challenges do you expect before you can even train a model?"

Let students name challenges (missing data, categorical variables, scale) —
these are exactly what the preprocessing section addresses.

### Preprocessing Walkthrough
The notebook preprocesses the data in several steps. Point out each decision:
1. **Missing values for continuous features:** filled with column mean
2. **Missing values for categorical features:** filled with the mode
3. **Categorical encoding:** `LabelEncoder` converts strings to integers
4. **Feature scaling:** `MinMaxScaler` normalizes all features to [0, 1]

Ask after each step: "Why this choice? What would happen if you skipped it?"

### Decision Tree Fitting
The notebook uses:
```python
DecisionTreeClassifier(criterion="entropy", min_samples_split=4, max_depth=5)
```
Encourage students to experiment with `max_depth` (try 2, 5, 10, None) and
observe how training vs. test accuracy changes. This is a direct demonstration
of overfitting.

### Tree Visualization
The `tree.plot_tree` visualization is a highlight of this activity — students
can trace individual predictions from root to leaf. Ask them to:
- Find a leaf node and trace the path back to the root
- Identify which feature appears most frequently near the root (most informative)

### Random Forest Extension (optional, 5–10 min)
Students fit a `RandomForestClassifier(n_estimators=20, criterion='entropy')`.
The comparison between decision tree and random forest test accuracy is usually
striking and motivates the discussion on ensembles and variance reduction.

### Common Issues
- Students may apply `MinMaxScaler` before splitting train/test, which causes
  data leakage. Point out that the scaler should be fit on training data only.
- `LabelEncoder` must be applied column-by-column; students sometimes try to
  apply it to the whole DataFrame at once.

---

## Discussion Prompts

1. You have 690 data points and 15 features. Why might a very deep decision tree
   (max_depth=None) perform worse on the test set than on training?
2. Look at the decision tree visualization. Which feature appears closest to the
   root? Why might that be the most informative feature?
3. The features are anonymized (A1, A2, ...). Does that make the model more or
   less trustworthy for a real credit decision? Why?
4. How does the random forest improve on a single decision tree? What is it
   actually doing differently?
5. A model that approves a loan for someone who defaults is costly. So is
   rejecting a good applicant. How would you use the confusion matrix to think
   about these two types of errors?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Successfully load the dataset and handle all missing values (continuous
      and categorical) with a documented strategy
- [ ] Encode all categorical features and apply feature scaling
- [ ] Fit a decision tree classifier and report both training accuracy and test
      accuracy
- [ ] Include the tree visualization
- [ ] Include a 2–3 sentence reflection: what does the gap between training and
      test accuracy indicate, and how did changing `max_depth` affect it?

*(Optional for higher-level engagement)* Compare the decision tree to a random
forest and note the difference in test accuracy.

Specifications will be confirmed and released when the activity is discussed in class.
Students may revise and resubmit up to two times.
