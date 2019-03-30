
# Milestone 1: Proposal

### Research Question
This survey is designed to find out if the competitiveness of a student affects their preference on where they usually sit.
*Does self-perceived competitiveness of an individual influence where they prefer to sit in class?*

### Survey Questions
Q.1: Where do you prefer to sit?
- Yes
- No
- Prefer to not respond

> This question ....

Q.2: What gender do you identify with?
- Male
- Female
- Other
- Prefer to not respond

> This question ....

(Behavioural questions - needs editing by the responsible member)
Q.3: How curious do you consider yourself to be? (1 being little curiousity, 5 being very curious)
1 - 2 - 3 - 4 - 5

> This question ...

Q.4: How actively engaged are you usually in class? (1 being not very engaged, 5 being very engaged)
1 - 2 - 3 - 4 - 5
> This question ...


### Statistics Analysis

**Null Hypothesis**: The competitiveness of a student has no affect on their preference on where they usually sit.
**Alternative Hypothesis**: The competitiveness of a student has affects on their preference on where they usually sit.

We plan to analyze our survey results in the following steps:

**Step 1**:  Exploratory Data Analysis (EDA)
- Briefly summarize the main characteristics of variables.
- Adjust assumption or method if needed.

**Step 2**:  Develop Regression Test in R statistical software
- Use a two-tail hypothesis test on our response variable.
- Perform Linear Regression test based on the survey results.
- Decide whether to keep interaction terms by conducting Likelihood Ratio Test on different models.
- Interpret the effects of the significant predictor variables.

### Online Surveys Ethics

This survey will not be collecting identifiable information such as student numbers, IP address, etc. There will be indirect identifiers collected during this survey such as gender, preferred seating location and level of personal engagement. We expect a high level of k-anonymity among the majority of gender responses and understand outliers may need to be removed in risk of identifying an individual. The indirect identifier, seating location, should have high k-anonymity as we are breaking the locations into 3 major areas.  If the data was collected at a finer scale such as row number this has a higher probability of potentially identifying individuals when combined with other information. The engagement variable will also have high k-anonymity as there will be five rankings for the participant to rank themselves. If any of the ranks have only a few values they may need to be generalized to ensure privacy.

Even though no personal information is being collect the survey will be hosted within Canada and comply with relevant sections of British Columbia Freedom of Information and Protection of Privacy Act (FOIPPA). If the survey data needs to made publicly available it will be reviewed and any potential identifiable information will be removed prior to release. At the beginning of the survey a consent letter will be presented to the participant which must be accepted for the participant to continue the survey.
