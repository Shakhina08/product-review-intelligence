# Product Review Sentiment Intelligence System

## Project Information

- **Track:** Field-Based Scenario
- **Scenario:** RET-02 Product Review Sentiment Intelligence System
- **Task:** Binary text classification
- **Author:** YOUR FULL NAME

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
Shakhina Shokirova
