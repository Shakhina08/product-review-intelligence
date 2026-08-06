# Project Status

## Project

**Title:** Product Review Sentiment Intelligence System  
**Track:** Field-Based Scenario  
**Scenario:** RET-02  
**Author:** Shakhina Shokirova

## Current Status

The capstone project is complete and ready for final repository verification and submission preparation.

## Completed Work

### Project Planning

- Project Brief completed
- Problem and intended user defined
- Dataset and evaluation strategy selected
- Risks, limitations and Responsible AI considerations documented

### Data Gate

- Amazon product-review dataset loaded
- Dataset structure inspected
- Missing and empty values checked
- Class balance checked
- Duplicate and conflicting reviews investigated
- Invalid and conflicting records removed
- Exact duplicate reviews removed
- Issue log created
- Stratified 70/15/15 train, validation and test split created
- Cross-split leakage checks completed
- Data Gate notebook uploaded to GitHub

### Model Gate

The following models were evaluated:

1. DummyClassifier baseline
2. TF-IDF unigrams with Logistic Regression
3. TF-IDF unigrams with Linear SVM
4. TF-IDF unigrams and bigrams with Logistic Regression

The final model was selected using validation macro F1.

### Selected Model

**TF-IDF unigrams and bigrams with Logistic Regression**

Validation results:

- Accuracy: 0.8514
- Macro F1: 0.8512

Protected test results:

- Accuracy: 0.8054
- Macro F1: 0.8053
- False positives: 14
- False negatives: 15

The protected test set was evaluated once, and no tuning was performed after viewing the result.

### Experiment Tracking

- MLflow runs completed
- Experiment comparison tables saved
- Model-selection rationale documented
- Error analysis completed

### Saved Artifacts

- `models/sentiment_pipeline.joblib`
- `models/model_metadata.json`
- `reports/error_analysis.csv`
- `reports/final_validation_comparison.csv`
- `reports/issue_log.csv`
- `reports/mlflow_runs.csv`
- `reports/test_comparison.csv`
- `mlflow/mlruns.zip`

### Demo

- `demo.ipynb` created
- Saved model loaded successfully
- Raw review input supported
- Positive and negative predictions tested
- Empty input handled safely
- Confidence score displayed
- Low-confidence warning added
- Mixed-sentiment example documented
- Clean-runtime test passed
- Demo uploaded to GitHub

### Documentation

- Main `README.md` completed
- Dataset documentation completed
- Repository structure organized

## Remaining Tasks

- Finalize `requirements.txt`
- Verify all repository files
- Prepare LMS submission document
- Prepare defense explanation and demonstration

## Final Model Limitation

The model may struggle with mixed sentiment, sarcasm, very short reviews, spelling errors, unfamiliar vocabulary and reviews requiring wider product context.

Low-confidence or ambiguous predictions should be checked by a human.
