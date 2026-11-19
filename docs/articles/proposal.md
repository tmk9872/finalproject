# 260 Final Project Proposals

**To:** BST260 Teaching Team, Fall 2026

## Final Project Proposal 1: Firearm Legislation and Suicide Mortality

### Background and research question

Firearms are used in a substantial share of suicide deaths in the United
States, and attempts involving firearms are particularly likely to be
fatal. A [RAND review of firearm availability and
suicide](https://www.rand.org/research/gun-policy/analysis/essays/firearm-availability-suicide.html)
summarizes research finding that greater firearm availability is
consistently associated with higher firearm suicide rates.

In a recent lecture, Dr. Vikram Patel from Harvard Medical School also
discussed the relationship between firearm availability and suicide
mortality.

I am interested in whether a similar association can be observed when
examining state-level firearm legislation and suicide mortality.
Specifically, I plan to focus on firearm purchase waiting-period laws,
which may influence how readily firearms can be obtained.

**Research question:** Is the presence of a state firearm purchase
waiting-period law associated with lower firearm suicide mortality rates
across U.S. states?

### Proposed data and methodology

I plan to combine two publicly available sources:

1.  **RAND State Firearm Law Database:** The `gunleg` dataset provided
    in the course package contains historical records of firearm
    legislation, including implementation, modification, and repeal
    dates. I will use these records to construct a binary indicator of
    whether a general firearm purchase waiting-period law was in effect
    in each state and year. The exposure will be coded as 1 if a
    qualifying law was in effect and 0 otherwise. I will account for
    implementation and repeal dates and examine any missing or ambiguous
    legislative records before finalizing the indicator.

2.  **CDC mortality data:** I will obtain annual state-level suicide
    mortality data from [CDC WONDER’s Underlying Cause of Death
    database](https://wonder.cdc.gov/deaths-by-underlying-cause.html).
    The primary outcome will be the age-adjusted firearm suicide death
    rate per 100,000 people (ICD-10 codes X72–X74), treated as a
    continuous variable.

The unit of analysis will be the **state-year**, covering the 50 U.S.
states. For the primary analysis, I plan to focus on several selected
years to compare states with and without waiting-period legislation. I
will consider using the law status at the beginning of each year to
account for legislation implemented partway through a calendar year.

I will begin with descriptive statistics and visualizations to compare
mortality rates across the two groups. I will then fit **linear
regression models** to assess whether waiting-period legislation is
associated with differences in firearm suicide rates.

I expect interpretation to be limited by potential confounding,
differences in firearm ownership across states, other policies enacted
around the same time, and the ecological nature of state-level data.
Additionally, the RAND legislation and CDC mortality datasets do not
directly provide several potentially relevant state-level socioeconomic
and contextual variables. While these could potentially be obtained from
additional sources, the scope of the analysis may limit my ability to
fully account for these factors.

Missing or suppressed mortality observations will be identified and
excluded from analyses requiring those values, with the extent of
missingness summarized. I will also review the completeness of
legislative records before interpreting states without recorded
waiting-period laws as having no such requirement.

As a secondary analysis, I will examine states that implemented or
repealed waiting-period legislation during the study period. For states
with sufficient data before and after a legislative change, I will use
descriptive statistics and visualizations to explore how firearm suicide
rates evolved around the change.

### Goal and limitations

My goal is to examine whether these public datasets reveal an
association broadly consistent with patterns previously documented in
the literature. Because legislation is not a direct measure of firearm
availability, this analysis will explore a related relationship rather
than directly replicate earlier findings. I do not intend to establish
that firearm legislation causes changes in suicide mortality, as causal
inference would require addressing substantial confounding and other
methodological challenges.

As mentioned already, I expect interpretation to be limited by potential
confounding.

## Final Project Proposal 2: NHANES Variables Associated with Depressive Symptoms

### Background and research question

Mental health is shaped by a range of behavioral, socioeconomic, and
demographic factors. Sleep, physical activity, and financial
circumstances are all plausible correlates of depressive symptoms, but
their relationships may overlap. I am interested in whether these
factors remain associated with self-reported depressive symptoms when
considered together in a regression model.

For this project, I plan to use the National Health and Nutrition
Examination Survey (NHANES) data. The unit of analysis will be the
individual survey respondent, focusing on adults aged 20 years and older
from the 2009–2012 NHANES data available in the `NHANES` R package.

**Research question:** Among adults in the NHANES dataset, how are sleep
duration, recreational physical activity, and household income relative
to the poverty threshold associated with self-reported depressive
symptoms after accounting for demographic characteristics?

### Proposed data and methodology

The proposed variables are:

- **Primary outcome:** `Depressed`, which records the frequency of
  feeling down, depressed, or hopeless (`None`, `Several`, or `Most`).
  For the primary analysis, I will compare any reported symptoms
  (`Several` or `Most`) with `None`, creating a binary outcome (1 = any
  reported symptoms, 0 = none).
- **Main predictors:** `SleepHrsNight` (usual weekday/workday sleep
  duration, modeled as a continuous variable), `PhysActive` (binary
  Yes/No indicator of moderate- or vigorous-intensity recreational
  physical activity), and `Poverty` (continuous family income-to-poverty
  ratio).
- **Additional variables:** I plan to adjust for age, gender,
  race/ethnicity, and education level, based on their potential
  relationships with both the proposed predictors and depressive
  symptoms. Additional variables may be considered in exploratory
  analyses.
- **Missing data:** I will examine the extent and patterns of missing
  data across the outcome, predictors, and adjustment variables. If
  missingness substantially reduces the n-size, I will consider
  deprioritizing certain features or discuss the potential for selection
  bias.

I will begin with descriptive summaries, distributions, and
visualizations of depressive symptom frequency across the proposed
predictors. I will then fit a **multivariable logistic regression**
model to estimate the adjusted association between each predictor and
reporting any depressive symptoms.

As a secondary analysis, I may consider an **ordinal logistic
regression** using all four `Depressed` response categories, subject to
checking whether the modeling assumptions are reasonable.

### Goal and limitations

My goal is to use a familiar multivariable regression framework to
examine which behavioral and socioeconomic variables show associations
with depressive symptoms in the available data, and whether those
associations persist after adjustment for other measured
characteristics.

The main limitations are the cross-sectional nature of the data,
self-reported measures, potential unmeasured confounding, and possible
multicollinearity. Additionally, the `Depressed` variable captures a
self-reported depressive symptom rather than a clinical diagnosis of
depression. Findings may therefore not generalize to diagnosed
depression.

## AI Use

I’ve used AI to do exploratory investigation of publicly available
datasets for proposal 1 and clean up my proposal.

Model used: GPT-6

Prompts:

\-
`I want to investigate relationship between gun legislature and suicide mortalitiy. I already have gun legislature data from RAND. Suggest datasets I can use to understand suicide mortality by state`

\-
`Review my proposal for any grammar issue and any overreach in assumption`
