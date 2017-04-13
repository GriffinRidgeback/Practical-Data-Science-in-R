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

## Lognormal distribution
The lognormal distribution is the distribution of a random variable _X_ whose natural log
**log(X)** is normally distributed. The distribution of highly skewed positive data, like
the value of profitable customers, incomes, sales, or stock prices, can often be modeled
as a lognormal distribution. A lognormal distribution is defined over all non-negative
real numbers; it’s asymmetric, with a long tail out toward positive infinity. 
The distribution of **log(X)** is a normal
distribution centered at **mean(log(X))**. For lognormal populations, the mean is generally
much higher than the median, and the bulk of the contribution toward the
mean value is due to a small population of highest-valued data points.

Intuitively, if variations in the data are expressed naturally as percentages or relative
differences, rather than as absolute differences, then the data is a candidate to be
modeled lognormally. For example, a typical sack of potatoes in your grocery store
might weigh about five pounds, plus or minus half a pound. The length that a specific
type of bullet will fly when fired from a specific type of handgun might be about 2,100
meters, plus or minus 100 meters. The variations in these observations are naturally
represented in absolute units, and the distributions can be modeled as normals. On
the other hand, differences in monetary quantities are often best expressed as percentages:
a population of workers might all get a 5% increase in salary (not an
increase of $5,000/year across the board); you might want to project next quarter’s
revenue to within 10% (not to within plus or minus $1,000). Hence, these quantities
are often best modeled as having lognormal distributions.

## Comparing variables using plotting

### Line Plots
First, let’s consider the relationship between two continuous variables. The most
obvious way (though not always the best) is the line plot.
Line plots work best when the relationship between two variables is relatively clean: each
x value has a unique (or nearly unique) y value

### Scatter Plots
When the data is not so cleanly related, line plots aren’t as useful; you’ll want to use
the scatter plot instead.

**SCATTER PLOTS AND SMOOTHING CURVES**
You’d expect there to be a relationship between age and health insurance, and also a
relationship between income and health insurance. But what is the relationship
between age and income? If they track each other perfectly, then you might not want
to use both variables in a model for health insurance. The appropriate summary statistic
is the correlation, which we compute on a safe subset of our data.

```
custdata2 <- subset(custdata,
(custdata$age > 0 & custdata$age < 100
& custdata$income > 0))
cor(custdata2$age, custdata2$income)
```
