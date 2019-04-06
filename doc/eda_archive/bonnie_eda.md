EDA\_Seat
================

``` r
data = read_csv('data/seat_tidy.csv')
```

    ## Parsed with column specification:
    ## cols(
    ##   seat_pref = col_double(),
    ##   comp = col_double(),
    ##   gender = col_double(),
    ##   engage = col_double()
    ## )

``` r
data$gender <- as.factor(data$gender)
data$seat_pref <- as.factor(data$seat_pref)
data$gender = fct_recode(data$gender, Woman = "1", Man = "2", Not_answer = "4")
data$seat_pref = fct_recode(data$seat_pref, Front = "1", Middle = "2", Back = "3", Not_answer = "4")
```

##### Bar graph of the count of different seat preferences

``` r
data %>%
  ggplot(aes(factor(seat_pref), fill = seat_pref)) +
  geom_bar() +
  theme() +
  xlab("Seating Preference")
```

![](EDA_Seat_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

**Interpretation**: We can see there are about 20 respondents choose to
sit in the front, 28 respondents choose to sit in the middle and 12
respondents choose to sit in the back. Individuals who preferred to not
disclosed their `Seat Preference` are 4.

#### Bar graph of the count of different seat preferences by gender

``` r
data %>%
  ggplot(aes(factor(seat_pref),fill = gender)) +
  geom_bar() +
  theme() +
  xlab("Seating Preference")
```

![](EDA_Seat_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

**Interpretation:** The count of woman who prefer to sit in the front is
similar that who prefer to sit in the middle. Man have stronger
preference to sit in the middle comparing to the front and back seats.
Majority of man choose to sit in the middle.

#### box plot of engagement by different seat preference

``` r
data %>%
  filter(!is.na(engage)) %>%
  ggplot(aes(seat_pref,engage, fill = seat_pref)) +
  geom_boxplot() +
  theme() +
  xlab("Seating Preference")
```

![](EDA_Seat_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

**Interpretation:** Individuals who prefer to sit in the front has the
highest average engagement level around 3.8, while individuals who
prefer to sit in the middle and back has similar average engagement
level around 3.7. The engagement average is pretty similar same for the
three seat preferences.We also notice that the average engagement level
of individuals who choose to sit in the front is more spread out
comparing to the other two seat preferences. For individuals who choose
not to answer, we do not really have a plot that throws much
information.

#### box plot of competitiveness by different seat preference

``` r
data %>%
  ggplot(aes(seat_pref,comp, fill = seat_pref)) +
  geom_boxplot() +
  theme() +
  xlab("Seating Preference")
```

![](EDA_Seat_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

**Interpretation:** Individuals who prefer to sit in the back has the
highest average competitivenes level around 3.8, while individuals who
prefer to sit in the front and middle has similar average competitivenes
level around 3.0. For individuals who choose not to answer, we do not
really have a plot that throws much information.
