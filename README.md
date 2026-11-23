# Breast cancer classification

CodeAlpha ML task 4. Prepared for Mariam Ibrahim's review.

**Status:** Working review package, not yet submitted. Prepared with AI assistance. Mariam should run the project, review the choices and explain the results before it is represented as her completed internship work. No claim of independent authorship, internship completion or certification is made.

## What the project does

Use the 569-row Wisconsin Diagnostic Breast Cancer dataset bundled with scikit-learn. The 30 numeric features describe cell nuclei in digitized fine-needle-aspirate images, not ordinary symptom checklists. The target is explicitly recoded as malignant=1 and benign=0 so recall refers to malignant cases.

An 80/20 stratified split leaves 114 held-out records. Five-fold training-only ROC-AUC selects between standardized logistic regression and a random forest. Standardization and imputation are fitted inside each training fold. A majority baseline is included. Even high test performance on this small, familiar dataset is not clinical validation. It can miss malignant cases. It is a classroom classification project, not a diagnosis, screening tool, medical device or advice for patients.

## Run it

Python 3.10.12 was used for the recorded run. Install Python first, then run from this folder:

```bash
python -m venv .venv
# Linux/macOS:
source .venv/bin/activate
# Windows PowerShell, instead:
# .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python main.py
python -m unittest test_project.py
```

The first run of credit/sales needs internet to download the source data. Subsequent runs use the local cache. Iris and breast-cancer data are bundled with scikit-learn. Results are written under `results/`. No credentials are required. Nothing is sent or published by the scripts. The notebook needs Jupyter (`pip install notebook`) only if you want to open it interactively.

## Recorded held-out results

Seed: 42. Training rows: 455. Test rows: 114.

| Model | accuracy | precision | recall | f1 | roc_auc | average_precision |
|---|---:|---:|---:|---:|---:|---:|
| baseline | 0.6316 | 0.0000 | 0.0000 | 0.0000 | 0.5000 | 0.3684 |
| logistic | 0.9649 | 0.9750 | 0.9286 | 0.9512 | 0.9960 | 0.9943 |


Binary classification precision, recall and F1 use class 1 (default or malignant). Iris metrics use macro averaging. Classification row indexes in `test_predictions.csv` refer to the cleaned analysis table, not the original file. Sales row indexes are original CSV row indexes. Exact train-only cross-validation means and standard deviations are in `results/metrics.json`. Data-quality counts are in `results/data_quality.json` for classification.

## Files

- `main.py`: complete source, including data loading and model evaluation.
- `walkthrough.ipynb`: executed notebook with explanation, code, recorded output and plots.
- `results/`: actual run metrics, test predictions and charts, not invented examples.
- `test_project.py`: automated output checks and a full rerun.
- `requirements.txt`: versions used in the verified run.

## Data and attribution

Source: https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html

Original dataset: https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic. The scikit-learn loader documents the source and target labels.

## Review before publishing

Explain the target, the split, why the baseline matters, what leakage means, and one limitation. Re-run the code and check the outputs. A LinkedIn video/post and the official form are still required by CodeAlpha; neither is included as a completed step here.
