# Activity 1: Data Exploration with ZipDigits

> **Notebooks:** `Introduction/DigitsIntro.ipynb`, `Introduction/MyPlayground.ipynb`
> **Suggested time:** 10–15 minutes per sub-activity (modular; choose 1–4)
> **Dataset:** ZipDigits (see `data/README.md`)

---

## Learning Objectives

By the end of this activity, students will be able to:

1. Load a real-world image dataset into a pandas DataFrame and inspect its structure.
2. Describe the shape, data types, and basic statistics of the dataset.
3. Reconstruct and visualize a handwritten digit from its raw pixel representation.
4. Extract two interpretable features (intensity and symmetry) from image data and
   explain their geometric meaning.

---

## Prerequisites

- Basic Python and pandas (`read_csv`, `head`, `info`, `describe`)
- Familiarity with NumPy arrays and `matplotlib`
- Conceptual understanding of what a dataset row and column represent

---

## Materials

- Notebook: `Introduction/DigitsIntro.ipynb`
- Dataset: `ZipDigits.train` — see `data/README.md` for download instructions
- Students should have Google Colab or a local Jupyter environment ready

---

## Sub-Activities

This activity is divided into four short, modular sections. Each takes 10–15 minutes.
Instructors can assign any combination depending on available class time.

### Sub-Activity A: Loading the Data (10 min)

Students load the ZipDigits training set into a DataFrame and call `.head()` and
`.info()` to explore its structure.

**Key questions to pose before students start:**
- How many rows and columns do you expect?
- What does each row represent? What does each column represent?

**What students do:** Run the loading cells, observe the output, and answer the
questions above in a comment or markdown cell.

---

### Sub-Activity B: Exploring the Dataset (10–15 min)

Students use pandas to explore the dataset: value counts by digit class, null
checks, and basic statistics.

**Key questions to pose:**
- Is the dataset balanced? Which digit appears most/least frequently?
- Are there any missing values? How would you handle them if there were?

**What students do:** Write and run exploratory code, then note one observation
they find interesting.

---

### Sub-Activity C: Plotting a Digit (10 min)

Students reshape a single row (256 pixel values) into a 16×16 grid and visualize
it with `imshow`.

**Key questions to pose:**
- What does a pixel value of +1 mean? What about −1?
- Try plotting digits from different classes. What differences do you notice?

**What students do:** Plot at least two digits from different classes and describe
what they observe in a markdown cell.

---

### Sub-Activity D: Extracting Features (10–15 min)

Students implement or run the `extract_features` function that computes **intensity**
(average pixel brightness) and **symmetry** (horizontal symmetry of the image).

**Key questions to pose:**
- Why might intensity be a useful feature for classifying digits?
- What does symmetry capture that intensity does not?
- Can you think of a digit pair that would be easy to separate using these two
  features? A pair that would be hard?

**What students do:** Run feature extraction on a subset of digits and create a
scatter plot colored by class label.

---

## Instructor Notes

### Setup
- Ensure students have the ZipDigits dataset uploaded to Colab (or their local
  environment) before class. Share the download instructions from `data/README.md`
  at least one class session in advance.
- Update the file path in the notebook's first cell to match your setup before
  distributing.

### Common Issues
- Students may be confused that the file has no header row. Point out that the
  first column is the digit label (0–9) and the remaining 256 columns are pixels.
- The pixel values are in [−1, +1]. Normalizing to [0, 1] with `(pixel + 1) / 2`
  is needed before `imshow`.

### Facilitation Tips
- Sub-activity D often sparks good discussion. Encourage students to plot multiple
  digit classes on the same scatter plot to see separation visually before any
  algorithm is applied.
- If time is short, Sub-activities A and B can be combined into one 15-minute block.

---

## Discussion Prompts

1. What challenges do you anticipate when a machine learning algorithm tries to
   classify all 10 digits using only intensity and symmetry?
2. What other features could you extract from a 16×16 image? How would you
   decide which features to use?
3. How does the size of the training set affect your confidence in what you
   observed about the data?

---

## Pass/Fail Specifications

To **pass** this activity, a submission must:

- [ ] Successfully load the dataset and display output from `.head()` and `.info()`
- [ ] Include at least one observation about the dataset (class distribution,
      data types, etc.) in a markdown or comment cell
- [ ] *(Sub-activity C)* Display a correctly rendered digit image with axis labels
      or a title indicating the digit class
- [ ] *(Sub-activity D)* Produce a scatter plot of intensity vs. symmetry with
      points colored by digit class

Specifications for the specific sub-activities assigned will be released in class.
