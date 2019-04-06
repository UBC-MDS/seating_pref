Investigate: Competitiveness and seating preference
================

The current analysis seeks to explore the relationship between
`self-reported competitiveness` and `seating preference` in a classroom.
We also want to determine whether this relationship is confounded by an
individual’s `gender` or `enagement` level. Toward this goal, we
constructed a
[survey](https://ubc.ca1.qualtrics.com/jfe/form/SV_d1ex7dheBUxPGPb), and
collected responses from individuals affiliated with the Master of Data
Science program at the University of British Columbia.

## Data ingestion

We compiled the seating preference, self-reported competitiveness,
gender, as well as engagement information from 64 survey entries. A full
description of the dataset and ingestion procedures can be found
[here](https://github.ubc.ca/sedv8808/seat_pref_survey).

``` r
# load libraries
suppressPackageStartupMessages(library(tidyverse))
suppressPackageStartupMessages(library(gridExtra))
library(apaTables)
```

``` r
# load data
df <- read_csv("../seat_tidy.csv")

# convert categorical variables to factors
df <- df %>% 
  mutate_at(c("seat_pref", "gender"), factor)

# preview data
df %>% head()
```

    ## # A tibble: 6 x 4
    ##   seat_pref  comp gender engage
    ##   <fct>     <dbl> <fct>   <dbl>
    ## 1 1           2   1        2   
    ## 2 2           3.5 2        2.33
    ## 3 2           3   2        3.33
    ## 4 2           4   1        3.67
    ## 5 2           4.5 1        3   
    ## 6 4           1   2        3

Note that the column `seat-pref` corresponds to seating preference,
`comp` corresponds to self-reported competitiveness, `gender`
corresponds to gender, and `engage` corresponds to an individual’s
engagement level.

## Data overview

#### Missing data

We offered the option for participants not to respond to certain survey
questions. We will simply consider these omitted responses as missing
values.

``` r
# re-encode "prefer not to response" (level 4) as missing data
df$seat_pref <- df$seat_pref %>% 
  fct_recode("Front" = "1", 
             "Middle" = "2", 
             "Back" = "3",  
             NULL = "4")

df$gender <- df$gender %>% 
  fct_recode("Man" = "1",
             "Woman" = "2",
             NULL = "4")

# evaluate missing data
df %>% summary()
```

    ##   seat_pref       comp         gender       engage     
    ##  Front :20   Min.   :1.000   Man  :34   Min.   :1.667  
    ##  Middle:28   1st Qu.:2.000   Woman:25   1st Qu.:3.000  
    ##  Back  :12   Median :3.000   NA's : 5   Median :3.667  
    ##  NA's  : 4   Mean   :3.047              Mean   :3.661  
    ##              3rd Qu.:4.000              3rd Qu.:4.333  
    ##              Max.   :5.000              Max.   :5.000  
    ##                                         NA's   :1

We are missing 4 entries for `seating preference`, 5 entries for
`gender`, as well as 1 entry for `engagement`. As we do not have enough
information to meaningfully impute these missing values, we will simply
drop these missing records from the dataset.

Note also that there were no participants that identified with genders
other than man or woman.

``` r
# drop missing data
df <- df %>% drop_na()
df %>% dim()
```

    ## [1] 56  4

We have 56 remaining records after removing the missing information.

#### Variable scaling

Both continuous variables, `comp` and `engage`, were measured using a
5-point Likert scale, as such, there should be no scaling issues for
these two variables.

#### Multicollinearity

We want to make sure that the two continuous variables, namely the
competitiveness variable (`comp`) and the engagement variable
(`engage`), are not measuring the same psychological construct. For this
reason, we will examine the Pearson correlation coefficient between
these two variables.

``` r
# evaluate correlation between comp and engage
# note that for EDA, we are not calculating the p-value for this coefficient
cor(x = df$comp, y = df$engage, method = "pearson")
```

    ## [1] 0.2106774

It appears that self-reported competitiveness is rather weakly and
positively associated with engagement level. This association is weak
enough that we needn’t worry too much about multicollinearity issues for
this dataset. They seem to be indeed measuring different contructs.

## Univariate analysis

Let’s take a closer look at each variable individually. Specifically,
let’s visualize the distribution of each variable.

``` r
# visualize seating preference
g31 <- df %>%   
  ggplot(aes(x = seat_pref)) +
  geom_bar() +
  theme_minimal() +
  xlab("Seating preference") +
  ylab("Number of people")

# visualize competitiveness
g32 <- df %>% 
  ggplot(aes(x = comp)) +
  geom_histogram(bins = 5, binwidth = 1) +
  theme_minimal() +
  xlab("Self-reported competitiveness") +
  ylab("Number of people")

# visualize gender
g33 <- df %>%   
  ggplot(aes(x = gender)) +
  geom_bar() +
  theme_minimal() +
  xlab("Gender") +
  ylab("Number of people")

# visualize engagement
g34 <- df %>% 
  ggplot(aes(x = engage)) +
  geom_histogram(binwidth = 1) +
  theme_minimal() +
  xlab("Engagement") +
  ylab("Number of people")

# display distribution of each variable
grid.arrange(g31, g32, g33, g34)
```

![](eda_files/figure-gfm/visualize%20univariate%20distribution-1.png)<!-- -->

We can also examine each variable numerically.

``` r
# obtain descriptive statistics of each variable
df %>% summary()
```

    ##   seat_pref       comp         gender       engage     
    ##  Front :18   Min.   :1.000   Man  :33   Min.   :1.667  
    ##  Middle:26   1st Qu.:2.000   Woman:23   1st Qu.:3.250  
    ##  Back  :12   Median :3.000              Median :3.667  
    ##              Mean   :3.161              Mean   :3.702  
    ##              3rd Qu.:4.000              3rd Qu.:4.333  
    ##              Max.   :5.000              Max.   :5.000

Both visual and numeric examinations of each variable has led to the
following observations:

Many participants prefer to sit in the middle of the classroom (n = 26),
and fewer participants prefer sitting in the front (n = 18), or in the
back (n = 12). Note that the number of participants in each response
level is somewhat unbalanced.

The distribution of self-reported competitiveness is largely normal with
a mean of 3. There are very few (less than five) participants with a
score of 1 or with a score of 5.

There are slightly more self-identified men (n = 33) than
self-identified women (n = 23) being included in the current analysis.
The number of each gender is very roughly balanced (not terribly
unbalanced).

The distribution of engagement level is slightly left-skewed with a mean
of about 3.7. There are no participants associated with a score below 1.
We believe the skewness of this distribution does not warrant major data
transformations.

## Bivariate analysis
