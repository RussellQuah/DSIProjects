# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Testing, Statistical Summaries and Inference

## Problem Statement

How can the SAT College Board increase participation rates in potential states of opportunity?

## Executive summary
The new format for the SAT was released in March 2016 in an attempt to catch up to increasing ACT participation rates across the United. States. This project aims to uncover actionable insights and trend using SAT and ACT test scores for 2017 and 2018 data at the state level, in hopes of increasing future SAT participation rates.

### Findings:
- High levels of negative correlation were found among ACT and SAT participation rates and their respective test results.
- Additionally, negative correlation was found between the ACT and SAT participation rates.
- Median SAT participation rate is increasing from 2017 to 2018
- The distribution of variables (scores and participation rates) were found to not follow a normal distribution. Possible selection bias at play.

## Conclusion and Recommendation
The simplest way to drive SAT participation rates is to convince the state's education board that the SAT is better suited as an exam for college and work context than the ACTs. However this is easier said than done.

One of the reasons why Colorado switched from ACT to SAT across the state was because Khan Academy provided free SAT prep material for students to help them with the test. Additionally, the fee was waived for SAT test. The College Board should use this as a point on why the SATs are more accessible than the ACTs, using the example of Colorado as a framework to push for mandatory testing in other states.

The process of actually convincing the education board to switch to the SAT test is outside the scope of this project. Further exploration can be done using graduates who took the SAT vs graduates who took the SAT and those who took both.

However, what this data set can tell the College Board is that, ACT and SAT scores are inversely correlated with their participation rates. Most likely attributed to selection bias, the test of low participation rates are measuring the best while tests on large participation rates are measuring the cohort.

Once the SAT is made mandatory, the large increase in participation is going to drive down the average SAT scores and the smaller participation of ACT is going to drive up the average composite score.

Additional data on the effectiveness of the SAT fee waivers and SAT school day would help drive decision making. We would be able to measure the effective of these policies and how they influence participation rates.


## Data Dictionary
|Feature|Type|Range|Dataset|Description|
|---|---|---|---|---|
|state|object|All states|final|US states of the data|
|participation_sat18|float64|0-1|final|State participation rate for the SAT in 2018|
|reading_writing_sat18|int64|200-800|final|State average SAT Evidence-Based Reading and Writing score in 2018|
|math_sat18|int64|200-800|final|State average SAT Math score in 2018|
|total_sat18|int64|400-1600|final|State average SAT Total score in 2018|
|participation_act18|float64|0-1|final|State participation rate for the ACT in 2018|
|composite_act18|float64|1-36|final|State average ACT Composite score for 2018|
|english_act18|float64|1-36|final|State average ACT English score for 2018|
|math_act18|float64|1-36|final|State average ACT Math score for 2018|
|reading_act18|float64|1-36|final|State average ACT Reading score for 2018|
|science_act18|float64|1-36|final|State average ACT Science score for 2018|
|participation_sat17|float64|0-1|final|State participation rate for the SAT in 2017|
|reading_writing_sat17|int64|200-800|final|State average SAT score for Evidence-Based Reading and Writing in 2017|
|math_sat17|int64|200-800|final|State average SAT Math score in 2017|
|total_sat17|int64|400-1600|final|State average SAT Total score in 2017|
|participation_act17|float64|0-1|final|State participation rate for the ACT in 2017|
|english_act17|float64|1-36|final|State average ACT English score for 2017|
|math_act17|float64|1-36|final|State average ACT Math score for 2018|
|reading_act17|float64|1-36|final|State average ACT Reading score for 2018|
|science_act17|float64|1-36|final|State average ACT Science score for 2018|
|composite_act17|float64|1-36|final|State average ACT Composite score for 2017|
