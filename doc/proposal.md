# Milestone 1: Proposal

### Main question of interest

Seating location in the classroom is commonly linked to grade performance, student engagement, and learning experience (Gowan et al., 2017; Shernoff, et al., 2017). Nevertheless, the question remains whether certain personality dispositions systematically influence where students prefer to sit in a classroom.

To address this gap in the literature, this study aims to explore the relationship between students' self-reported competitiveness and their seating preference. Specifically, this study will survey 69 Master of Data Science students at the University of British Columbia. The main objective of this survey is to explore the question: **Does self-reported competitiveness influence where an individual prefers to sit in class?**

The survey will measure _self-reported competitiveness_ with the following two questions (adapted from Bönte, Lombardo, & Urbig, 2017):

**Q1**: Do you enjoy situations in which you compete with others?

**Q2**: Do you prefer competing with others when pursuing a goal over pursuing the goal alone?

Participants will answer these two questions using a 5-point Likert scale, with 1 being "very much not so", and 5 being "very much so". The average score of these two questions will be used as a measurement for _competitiveness_.

The survey will collect _seating preference_ with the following question:

**Q3**: Where do you prefer to sit in a classroom?

- [ ] Front of the class
- [ ] Middle of the class
- [ ] Back of the class
- [ ] Prefer not to respond

### Potential confounds

Gender has been directly linked to both student seating (Shernoff, et al., 2017), and competitiveness (Buser, Niederle, & Oosterbeek, 2012). For this reason, the survey will also collect _gender_ using the following question: 

**Q4**: What gender do you identify with?

- [ ] Male
- [ ] Female
- [ ] Other
- [ ] Prefer not to respond

Students who sit in the back of the classroom are found to be less engaged (Shernoff, et al., 2017), while competitive individuals are typically more engaged in a task (Karatepe & Olugbade, 2009). The survey will therefore measure _student engagement_ as a potential confound, using the following questions (adapted from Shernoff, et al., 2017):

**Q5**: Did you enjoy what you were doing in the MDS program? (enjoyment)

**Q6**: Do you often find your mind wander off in class? (reverse coded) (concentration)

**Q7**: Do you find the course content in MDS to be interesting? (interest)

These questions will be answered using a 5-point Likert scale, with 1 being "very much not so", and 5 being "very much so". The average score of these questions will be used as a measurement for _engagement_.

### Plan of analysis

The current study hypothesizes that:

**Null hypothesis**: Self-reported competitiveness does not influence student seating preference.

**Alternative hypothesis**: Self-reported competitiveness does influence student seating preference.

Survey results will be analyzed in the following steps:

**Step 1**:  Exploratory Data Analysis

We will examine the distribution of each variable, handle missing values, and perform transformations as necessary.
	
**Step 2**:  Statistical modelling in R

We will attempt to fit a generalized linear model to the survey results, using _seating preference_ as the response, and using _self-reported competitiveness_ with other confounds variables as the co-variates. We will decide the appropriateness of including interaction terms by comparing different regression models. We will use t-test to determine whether the regression coefficient for _competitiveness_ is significantly different from zero, thereby evaluating its effects on _seating preference_.

**Step 3**: Limitations

The current study is observational and exploratory in nature, as such, we cannot make any _causal_ claims about the survey results. We will make apparent on additional limitations and generalizability of this study.

### Ethics and other considerations

This study will not be collecting identifiable information such as student numbers, IP address, etc. There will be indirect identifiers collected during the survey such as gender, preferred seating location and level of personal engagement. We expect a high level of k-anonymity among the majority of gender responses and understand outliers may need to be removed in risk of identifying an individual. The indirect identifier, seating location, should have high k-anonymity as we are breaking the locations into thhree major areas. If the data was collected at a finer scale such as row number this has a higher probability of potentially identifying individuals when combined with other information. The engagement variable will also have high k-anonymity as there will be five rankings for the participant to rank themselves. If any of the ranks have only a few values they may need to be generalized to ensure privacy.

Even though no personal information is being collected, the survey will be hosted within Canada and comply with relevant sections of British Columbia Freedom of Information and Protection of Privacy Act (FOIPPA). If the survey data needs to be made publicly available, it will be reviewed and any potential identifiable information will be removed prior to release. At the beginning of the survey a consent form will be presented to the participant which must be accepted for the participant to continue the survey.

### References

Buser, T., Niederle, M., & Oosterbeek, H. (2012). Gender, Competitiveness and Career Choices. National Bureau of Economic Research Working Paper Series, 18576. doi:10.3386/w18576

Bönte, W., Lombardo, S., & Urbig, D. (2017). Economics meets psychology: Experimental and self-reported measures of individual competitiveness. Personality and Individual Differences, 116, 179-185. doi:10.1016/j.paid.2017.04.036

Gowan, A. M., Hanna, P., Greer, D., Busch, J., & Anderson, N. (2017). Learning to program - does it matter where you sit in the lecture theatre? 2017 40th International Convention on Information and Communication Technology, Electronics and Microelectronics (MIPRO). doi:10.23919/mipro.2017.7973500

Karatepe, O. M., & Olugbade, O. A. (2009). The effects of job and personal resources on hotel employees’ work engagement. International Journal of Hospitality Management, 28(4), 504-512. doi:10.1016/j.ijhm.2009.02.003

Shernoff, D. J., Sannella, A. J., Schorr, R. Y., Sanchez-Wall, L., Ruzek, E. A., Sinha, S., & Bressler, D. M. (2017). Separate worlds: The influence of seating location on student engagement, classroom experience, and performance in the large university lecture hall. Journal of Environmental Psychology, 49, 55-64. doi:10.1016/j.jenvp.2016.12.002
