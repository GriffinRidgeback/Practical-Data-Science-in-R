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

## Examining the data
```
print(d[1:3,'Purpose'])
summary(d$Purpose)
table(d$Purpose,d$Good.Loan)
```
## How narrow is “too narrow” a data range?
Of course, the term narrow is relative. If we were predicting the ability to read for chil- dren between the ages of 5 and 10, then age probably is a useful variable as-is. For data including adult ages, you may want to transform or bin ages in some way, as you don’t expect a significant change in reading ability between ages 40 and 50. You should rely on information about the problem domain to judge if the data range is nar- row, but a rough rule of thumb is the ratio of the standard deviation to the mean. If that ratio is very small, then the data isn’t varying much.

## Logarithmic scale used for plotting
If the data is non-negative, then one way to bring out more detail is to plot the distribution on a logarithmic scale.  This is equivalent to plotting the density plot of log10(plot_variable); For example, the base 10 logarithm of 1000 is 3, as 10 to the power 3 is 1000.

## When should you use a logarithmic scale?
You should use a logarithmic scale when percent change, or change in orders of magnitude, is more important than changes in absolute units. You should also use a log scale to better visualize data that is heavily skewed.  For example, in income data, a difference in income of five thousand dollars means something very different in a population where the incomes tend to fall in the tens of thousands of dollars than it does in populations where income falls in the hundreds of thousands or millions of dollars. In other words, what constitutes a “significant difference” depends on the order of magnitude of the incomes you’re looking at. Similarly, in a population like that in figure 3.5, a few people with very high income will cause the majority of the data to be compressed into a relatively small area of the graph. For both those reasons, plotting the income distribution on a logarithmic scale is a good idea.

## How is dnorm calculated?

You know the probability density function for a standard normal distribution is [described here](https://stats.stackexchange.com/questions/157662/rnorm-vs-dnorm-in-r/157667)

The dnorm() function is just used to calculate the value of this function.

You can test using the following R code

```
density_standard_norm <- function(x)
{
1/sqrt(2*pi)*exp(-0.5*x^2)
}
```

```
dnorm(1, mean = 0, sd = 1)
[1] 0.2419707
density_standard_norm(1)
[1] 0.2419707

dnorm(2, mean = 0, sd = 1)

[1] 0.05399097

density_standard_norm(2) 
[1] 0.05399097
```

They are equal. For non-standard normal it's same.
