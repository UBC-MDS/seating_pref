EDA\_Gender
================
Seating Preference Team
2019-04-05

## Research Question of Interest

`Seating location` in the classroom is commonly linked to grade
performance, student engagement, and learning experience (Gowan et al.,
2017; Shernoff, et al., 2017). Nevertheless, the question remains
whether certain personality dispositions systematically influence where
students prefer to sit in a classroom. We are asking a group of MSD
students in order to learn more about the relationship between `seating
location` and competitiveness.

## Gender as a Cofound

In our survey, we are also wanting to take into consideration confound
variables and we think `Gender` is one, since `Gender` has been directly
linked to both student seating (Shernoff, et al., 2017)

### Some Tables

``` r
data <- read_csv("data/seat_tidy.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   seat_pref = col_double(),
    ##   comp = col_double(),
    ##   gender = col_double(),
    ##   engage = col_double()
    ## )

``` r
data %>%
  group_by(gender) %>%
  na.omit() %>%
  summarize(count = n(), competitiveness = mean(comp), engagement = mean(engage))
```

    ## # A tibble: 3 x 4
    ##   gender count competitiveness engagement
    ##    <dbl> <int>           <dbl>      <dbl>
    ## 1      1    34            3.18       3.66
    ## 2      2    24            3.04       3.75
    ## 3      4     5            2.6        3.27

**Interpretation:** We can see that individuals that identified
themselves as `Women` have the highest `Competitiveness` average while
individuals that prefer to not disclose their gender had the lowest.

The previous table was merely used considering `Gender` without taking
into consideration where each individual likes seating. Let’s explore
that now:

``` r
data %>%
  group_by(gender, seat_pref) %>%
  summarize(count = n(), competitiveness = mean(comp), engagement = mean(engage))
```

    ## # A tibble: 11 x 5
    ## # Groups:   gender [3]
    ##    gender seat_pref count competitiveness engagement
    ##     <dbl>     <dbl> <int>           <dbl>      <dbl>
    ##  1      1         1    11            3.27       3.73
    ##  2      1         2    13            3.08       3.54
    ##  3      1         3     9            3.22       3.70
    ##  4      1         4     1            3          4   
    ##  5      2         1     7            2.86       3.90
    ##  6      2         2    14            2.89      NA   
    ##  7      2         3     3            4.17       4   
    ##  8      2         4     1            1          3   
    ##  9      4         1     2            3          2.83
    ## 10      4         2     1            1          4.67
    ## 11      4         4     2            3          3

**Interpretation:** Individuals gender seems to be somewhat linked to
where they prefer to seat AND to their competitiveness.

Women seem to be the most “average” competitors in terms that, no matter
where they seat, they share a high level of competitiveness, all above 3
points. Even women who did not disclose where they would sit, had a high
score of 3. (Men who did not want to disclose their preferred seat had a
score of 1.)

For Men, Individuals seating at the front had the lowest competitiveness
average, same as individuals in the middle. However, self reported men
seating at the back end had the highest competitiveness levels of the
whole sample. Surprisingly, men who did not disclose where they
preferred seating had the lowest competitiveness average, same as people
who did not disclose gender but preferred seating in the middle.

Individuals who did not disclose their gender but preferred seating in
the front had a high competitiveness level; very different from those
who preferred seating in the middle (lowest competitiveness level).

I believe `Gender` is definitely linked to competitiveness and seating
preference.

Engagement is another variable that we studied, and we can see that most
`Men` identified inidividuals had a really high engagement rate. Even
groups who had a low `Competitiveness` average, showcased a very high
`Engagement` score. Women’s ranged from 3.5 to 4; Men’s from 3 to 4, Not
identified, from 2.8 to 4.6; the highest engagement value\!\! However,
we have to be very careful when block-ing too much the values since we
can see that for some groups of people, our count is just of 1
individual, not enough data.

## Including Plots

The most basic plot we can do from here, is to do a count of the
`Gender` of our respondents:

``` r
data %>%
  ggplot(aes(factor(gender))) +
  geom_bar() +
  theme_bw() +
  labs(title = "Gender Count", 
       x = "Self-identified Gender",
       y = "Count")
```

![](EDA_Gender_files/figure-gfm/gender%20count-1.png)<!-- -->

**Interpretation:** We can see that we have about 35 `Women` respondents
while just 25 `Men` respondents. Individuals who preferred to not
disclosed their `Gender` are 5.

It would be interesting to see how this count reflects in their seat
preference:

``` r
data %>%
  ggplot(aes(factor(gender))) +
  geom_bar() +
  facet_wrap(~seat_pref) +
  theme_bw() +
  labs(title = "Gender Count as per Seat Preference", 
       x = "Self-identified Gender",
       y = "Count")
```

![](EDA_Gender_files/figure-gfm/gender%20count%20by%20seat%20preference-1.png)<!-- -->
**Interpretation:** Women seem more likely to seat either at the fron or
middle. Men seem to prefer the middle. People who would not disclose
their gender, would also prefer to not disclose their preferred seat.

We would like now to explore what role does the `Gender` play in an
individuals `Engagement`

``` r
data %>%
  filter(!is.na(engage)) %>%
  ggplot(aes(gender, engage)) +
  geom_boxplot() +
  theme_bw() +
  labs(title = "Gender vs Engagement",
       x = "Gender",
       y = "Engagement")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](EDA_Gender_files/figure-gfm/engagement%20and%20gender-1.png)<!-- -->
**Interpretation:** Men’s `Engagement` seems to have a smaller standard
deviation, with most of them having an `Engagement` score between 3.3
and 4.1; Women rated their engagement anywhere from 3 to almost 4.4
while Unidentified individuals ranged from 2.4 to 3.6. Although `men`
seem to have similar patterns of engagement, some females scored higher
in this aspect.

Same as before, it is normal to wonder where are these people seating:

``` r
data %>%
  ggplot(aes(gender, comp)) +
  geom_boxplot() +
  geom_jitter(alpha = 0.2) +
  theme_bw() +
  labs(title = "Gender vs Competitiveness",
       x = "Gender",
       y = "Competitiveness")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](EDA_Gender_files/figure-gfm/competitiveness%20and%20gender-1.png)<!-- -->

**Interpretation:** It is interesting to see that the competitiveness
average is pretty similar same for the three categories of `Gender` we
have. However, women show a larger span in terms of How competitive they
perceive themselves to be, while men had a shorter span. Men’s mean
percentile is also closer to their 75 percentile. For individuals who
did not report their gender, we do not really have a plot that throws
much information; we need more individuals.
