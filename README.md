# Practical-Data-Science-in-R

## Most common modeling tasks

1. Classification:  deciding
2. Scoring:  predicting/estimating; produce numeric output such as a price or probability
3. Ranking: order by preference
4. Clustering:  grouping
5. Finding relations:  correlations
6. Characterization:  plotting and report generation

## Most commmon algorithms for Classification
1. logistic regression
2. Naive Bayes
3. decision trees (rpart)

## Notes
* Reasoning behind the classification
* confidence in the model

## Confusion matrix

good summary of classifier accuracy; tabulates actual classifications against predicted ones.

* Recall:  how many of the bad loans the model can actually find
* Precision:  how many loans indetified as bad are bad
* False positive rate:  how many good loans are mistakenly identified as bad
* Null model:  obvious guess that your model must do better than; lower bound on model performance.  Its error rate is called the base error rate.
* Hypothesis testing/significance testing:  tests whether your model is equivalent to a null model

## Working with data

* In order to decrypt troublesome data, you need what’s called the schema documentation or a data dictionary.

## Lists

__Lists are R’s map structures.__ They can map strings to arbitrary objects. The important list operations [] and %in% are vectorized. This means that, when applied to a vector of values, they return a vector of results by performing one lookup per entry.
