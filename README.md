# ML Class Activities — CMPE 257

Jupyter notebooks for in-class activities covering core machine learning concepts.
Designed for use with Google Colab, but can be adapted to run locally.

## Topics

| Folder | Topics Covered |
|--------|---------------|
| `Introduction/` | Intro to data exploration with handwritten digits |
| `Perceptron/` | Perceptron Learning Algorithm (PLA), helper utilities |
| `Linear Models/` | Linear regression, logistic regression, digit classification |
| `Nonlinear Transformation/` | Nonlinear feature transforms with linear regression |
| `Decision Trees/` | Decision trees with credit approval and tennis datasets |
| `SVM/` | Support Vector Machines |
| `ML/` | Neural Networks |

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/ml-class-activities.git
cd ml-class-activities
```

### 2. Set up datasets

Data files are not included. See [`data/README.md`](data/README.md) for download
and preprocessing instructions for each dataset.

### 3. Run notebooks

**Google Colab (recommended):**
1. Upload the notebook to Colab (or open directly from GitHub via the Colab URL)
2. Mount your Google Drive or upload the required data files
3. Update the file paths at the top of each notebook to match your setup

**Local (Jupyter):**
```bash
pip install jupyter numpy pandas matplotlib scikit-learn
jupyter notebook
```

## Prerequisites

- Python 3.8+
- `numpy`, `pandas`, `matplotlib`, `scikit-learn`
- `cvxopt` (required for SVM notebook)

## Citation

The lesson plans and course design in this repository are based on the following work:

> M. Agumbe Suresh, "WIP: Incorporating Active Learning and Group Work into
> Specifications Grading for Graduate Level Data Science Courses," *2025 IEEE
> Frontiers in Education Conference (FIE)*, 2025.
> DOI: [10.1109/FIE63693.2025.11328544](https://doi.org/10.1109/FIE63693.2025.11328544)

## Notes

- Notebooks contain cleared outputs — run cells top-to-bottom to reproduce results
- File paths in notebooks are set to Google Drive locations; update them for local use
