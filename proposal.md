# Milestone 1: Proposal

### Main question of interest

Seating location in the classroom is commonly linked to grade performance, student engagement, and learning experience. Nevertheless, the question remains whether certain personality dispositions systematically influence where students prefer to sit in a classroom.

To address this gap in the literature, this study aims to explore the relationship between students' self-reported competitiveness and their seating preference. Specifically, this study will survey 69 Master of Data Science students at the University of British Columbia. The main objective of this survey is to explore the question: **Does self-reported competitiveness influence where an individual prefer to sit in class?**

The survey will measure _self-reported competitiveness_ with the following two questions:

**Q1**: Do you enjoy situations in which you compete with others?

**Q2**: Do you prefer competing with others when pursuing a goal over pursuing the goal alone?

Participants will answer these two questions using a 5-point Likert scale, with 1 being "very much not so", and 5 being "very much so". The average score of these two questions will be used as a measurement for competitiveness.

The survey will collect _seating preference_ with the following question:

**Q3**: Where do you prefer to sit in a classroom?

- [ ] Front of the class
- [ ] Middle of the class
- [ ] Back of the class
- [ ] Prefer not to respond

### Potential confounds

Gender has been directly linked to both student seating, and competitiveness. For this reason, the survey will also collect _gender_ using the following question: 

**Q4**: What gender do you identify with?

- [ ] Male
- [ ] Female
- [ ] Other
- [ ] Prefer not to respond

Students who sit in the back of the classroom are found to be less engaged, while competitive individuals are typically more engaged in a task. The survey will therefore measure _student engagement_ as a potential confound, using the following questions:

**Q5**: 

These questions will be answered using a 5-point Likert scale, with 1 being "very much not so", and 5 being "very much so". The average score of these two questions will be used as a measurement for student engagement.

### Plan of analysis

The current study hypothesizes that:

**Null hypothesis**: Self-reported competitiveness does not influence student seating preference.

**Alternative hypothesis**: Self-reported competitiveness does influence student seating preference.

Survey results will be analyzed in the following steps:

**Step 1**:  Exploratory Data Analysis (EDA)

We will examine the distribution of each variable, handle missing values, and perform transformations as necessary.
	
**Step 2**:  Statistical modelling in R

We will perform linear regression on the survey results, using _seating preference_ as the response, and using _self-reported competitiveness_ with other confounds variables as the co-variates. We will decide the appropriateness of including interaction terms by comparing different regression models. We will use t-test to determine whether the regression coefficient for _competitiveness_ is significantly different from zero, thereby evaluating its effects on _seating preference_.

**Step 3**: Limitations

The current study is observational and exploratory in nature, so we cannot make any _causal_ claims about the survey results. We will make apparent on additional limitations and generalizability of this study.

### Ethics and other considerations

All online survey data will be stored and accessed in Canada only and will be destroyed upon completition of this project. 
No private information (such as names, IP address, or any information that can identify someone) will be collected in the survey. 
A consent form/cover letter will be issued.

### References

