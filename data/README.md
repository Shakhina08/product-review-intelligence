# Dataset

## Dataset name

Sentiment Labelled Sentences — Amazon subset

## Source

UCI Machine Learning Repository

## File

amazon_cells_labelled.txt

## Structure

- `review`: English product-review sentence
- `label`: 0 for negative and 1 for positive

## Task

Binary sentiment classification.

## Data-quality checks

The project checks missing values, empty text, invalid labels, duplicate
reviews, class balance and review length before splitting.

## Limitations

The dataset is small, contains English reviews only, has no neutral class,
and may not represent every marketplace or product category.

## Download process

Download the Sentiment Labelled Sentences dataset from UCI, extract the ZIP
file and use `amazon_cells_labelled.txt`.