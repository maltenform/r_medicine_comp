# R/Medicine 2024 Data Challenge

This is my entry into the R/Medicine 2024 Data Challenge attempting to analyze the harmonized multi-site data on drug treatment clinical files.

The questions I tackled were:

**1. What factors lead to successful randomization into a clinical trial?**

A patient can't be a successful participant in the trial without enrolling in the trial.  So I looked into what factors were relevant to a patient being enrolled. The major factor seemed to be age, where older patients were less likely to be enrolled.  Marital status and reported drug use were also predictors but in the sense that if the patient wasn't sharing info there, the patient was less likely to enroll.  Based on AUC and calibration curve, the prediction was pretty good.

**2. Once enrolled, what factors lead to better compliance?**

Using the example code for whether a patient shows up for a test in a given week, and what the test result was, I derived two metrics for participation:

*Attendance* was the ratio of weeks with tests done (positive or negative) to all the weeks possible for tests.  That is, the ratio of ('-' + '+') /  ('-' + '+' + 'o') based on the example code.

*Compliance* was the ratio of weeks with negative tests (no drugs) to all the weeks possible for tests.  That is, the ratio of ('-') /  ('-' + '+' + 'o') based on the example code.

Since both attendance and compliance were 0 to 1, beta regression was used to analyze them.  It turned out that age was yet again the major factor, however the effect was in the opposite direction -- older participants showed better attendance and compliance. While other factors showed statistical impact on outcomes, the results were less clear. 

