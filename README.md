# Product Review Sentiment Intelligence System

## Project Information

- **Track:** Field-Based Scenario
- **Scenario:** RET-02 Product Review Sentiment Intelligence System
- **Task:** Binary text classification
- **Author:** Shakhina Shokirova

## Project Overview

This project classifies English product reviews as either:

- **Positive**
- **Negative**

The system is designed to support retail and customer-experience teams by helping them review large amounts of customer feedback more efficiently.

The final system accepts raw review text and returns:

- the predicted sentiment;
- a confidence score;
- a warning when the prediction confidence is low.

## Dataset

The project uses the Amazon product-review subset from the **UCI Sentiment Labelled Sentences Dataset**.

Each record contains:

- `review`: raw English product-review text;
- `label`: sentiment class.

Label meanings:

- `0` = Negative
- `1` = Positive

The original dataset is not stored directly in this repository. Dataset source information and preparation instructions are available in:

```text
data/README.md
```

## Data Preparation

The Data Gate included:

- checking dataset shape and column types;
- checking missing and empty values;
- checking class balance;
- identifying duplicate reviews;
- removing conflicting duplicate labels;
- removing exact duplicates;
- validating labels;
- creating stratified train, validation and test sets;
- checking that no review appeared in more than one split.

The split proportions were:

- 70% training;
- 15% validation;
- 15% protected test.

The random seed was fixed at `42`.

## Models Evaluated

Four controlled experiments were compared:

1. DummyClassifier baseline
2. TF-IDF unigrams with Logistic Regression
3. TF-IDF unigrams with Linear Support Vector Machine
4. TF-IDF unigrams and bigrams with Logistic Regression

Macro F1 was used as the primary model-selection metric.

## Experiment Results

| Model | Validation Accuracy | Validation Macro F1 |
|---|---:|---:|
| DummyClassifier | 0.5000 | 0.3333 |
| TF-IDF + Logistic Regression | 0.8311 | 0.8309 |
| TF-IDF + Linear SVM | 0.8108 | 0.8108 |
| TF-IDF unigrams+bigrams + Logistic Regression | 0.8514 | 0.8512 |

## Final Model

The selected model is:

```text
TF-IDF unigrams and bigrams + Logistic Regression
```

It was selected because it achieved the highest validation macro F1 score.

The complete preprocessing and classifier are stored together inside a Scikit-learn Pipeline.

Saved model:

```text
models/sentiment_pipeline.joblib
```

Model metadata:

```text
models/model_metadata.json
```

## Protected Test Results

The final model was evaluated once on the protected test set.

- **Test accuracy:** 0.8054
- **Test macro F1:** 0.8053
- **False positives:** 14
- **False negatives:** 15

No model tuning was performed after viewing the protected test result.

## Demo

The main demonstration notebook is:

```text
demo.ipynb
```

The demo:

- loads the saved trained Pipeline;
- accepts a raw English review;
- validates empty input;
- predicts positive or negative sentiment;
- displays the prediction confidence;
- displays a warning for low-confidence results.

### Example Input

```text
The product is excellent and works perfectly.
```

### Example Output

```text
Predicted sentiment: Positive
Confidence: 0.82
```

A mixed-sentiment review may receive a lower-confidence prediction:

```text
The screen is beautiful but the battery is terrible.
```

This type of review should be checked by a human.

## Running the Demo in Google Colab

1. Open `demo.ipynb` in Google Colab.
2. Download `models/sentiment_pipeline.joblib` from this repository.
3. Upload the model file to the Colab Files panel.
4. Run the notebook from top to bottom.
5. Enter an English product review when prompted.

The demo was tested successfully in a clean Colab runtime.

## Running the Training Notebooks

The project notebooks are:

```text
notebooks/01_data_gate.ipynb
notebooks/02_model_gate.ipynb
```

`01_data_gate.ipynb` contains:

- data inspection;
- cleaning;
- issue logging;
- stratified data splitting;
- leakage checks.

`02_model_gate.ipynb` contains:

- baseline training;
- controlled model experiments;
- validation comparison;
- MLflow tracking;
- final model selection;
- protected test evaluation;
- error analysis;
- model saving and reload verification.

## Installation

Install the required Python packages with:

```bash
pip install -r requirements.txt
```

## Repository Structure

```text
product-review-intelligence/
├── data/
│   └── README.md
├── docs/
│   └── RET02_Product_Review_Project_Brief_Completed.docx
├── mlflow/
│   └── mlruns.zip
├── models/
│   ├── model_metadata.json
│   └── sentiment_pipeline.joblib
├── notebooks/
│   ├── 01_data_gate.ipynb
│   └── 02_model_gate.ipynb
├── reports/
│   ├── error_analysis.csv
│   ├── final_validation_comparison.csv
│   ├── issue_log.csv
│   ├── mlflow_runs.csv
│   └── test_comparison.csv
├── demo.ipynb
├── PROJECT_STATUS.md
├── README.md
└── requirements.txt
```

## Limitations

The model may struggle with:

- mixed positive and negative opinions;
- sarcasm;
- very short reviews;
- spelling mistakes;
- unfamiliar vocabulary;
- reviews requiring wider product context.

The dataset is relatively small and mainly contains short English product reviews. Results may not generalize equally well to other languages, longer reviews or different business domains.

## Responsible AI

This model should be used as a support tool, not as the only basis for business decisions.

Low-confidence, ambiguous and mixed-sentiment reviews should be reviewed by a human.

The model may reflect limitations or biases in its training dataset. Predictions should therefore be interpreted carefully and should not be used to unfairly evaluate individual customers or employees.

## Conclusion

The project produced a complete and reproducible sentiment-classification workflow, including data validation, baseline comparison, controlled experiments, experiment tracking, protected test evaluation, saved artifacts and a clean interactive demo.
