fair py-earth [![Build Status](https://travis-ci.org/scikit-learn-contrib/py-earth.png?branch=master)](https://travis-ci.org/scikit-learn-contrib/py-earth?branch=master)
========

## Installation

Make sure you have numpy and scikit-learn installed.  Then do the following:

```
git clone https://github.com/parianh/fairMARS.git
%cd py-earth
```

## Datasets
The two  Datasets included in this repository are: "student-mat" and "ELS"

ELS Dataset (Bozick, Lauff, and Wirt 2007):
This dataset consists of 970 instances with 40 predictor variables. A recommended sensitive attribute for fairness considerations is "pell_grant," a binary variable indicating the presence or absence of a Pell Grant. The response variable in this dataset is "GPA," representing the academic performance of the individuals.

Student Performance Dataset (Cortez 2014):
This dataset consists of 395 instances and 33 predictor variables, focusing on student performance. For fairness considerations, we consider the binary variable "gender" as the sensitive attribute, with a binary classification. The response variable in this dataset is the final grade.
