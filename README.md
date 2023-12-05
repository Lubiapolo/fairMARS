fair py-earth [![Build Status](https://travis-ci.org/scikit-learn-contrib/py-earth.png?branch=master)](https://travis-ci.org/scikit-learn-contrib/py-earth?branch=master)
========

## Installation

Make sure you have numpy and scikit-learn installed.  Then do the following:

```
git clone https://github.com/Lubiapolo/fairMARS.git
%cd py-earth
```

## Datasets
The two  Datasets included in this repository are: "student-mat" and "ELS"

ELS Dataset (Bozick, Lauff, and Wirt 2007):
This dataset consists of 970 instances with 40 predictor variables. A recommended sensitive attribute for fairness considerations is "pell_grant," a binary variable indicating the presence or absence of a Pell Grant. The response variable in this dataset is "GPA," representing the academic performance of the individuals.

Student Performance Dataset (Cortez 2014):
This dataset consists of 395 instances and 33 predictor variables, focusing on student performance. For fairness considerations, we consider the binary variable "gender" as the sensitive attribute, with a binary classification. The response variable in this dataset is the final grade.

## fairMARS
The fairMARS model introduces three additional arguments in the `model.fit` function to facilitate fairness adjustments within the algorithm:
  ```python
    model.fit(X_train, y_train, disparity_indices=[31], petha=0.2, fair_coef=True)

*   **disparity_indices (fairknot component):**

  This argument expects a list of column numbers corresponding to sensitive attributes in your dataset.
  *   Ensure proper one-hot encoding of sensitive attributes during preprocessing.
  *   In the ELS dataset, with binary values representing the protected attribute 'pell_grant', obtain the column number using:
    ```python
    x.columns.get_loc('pell_grant')
    ```

  <!-- In the ELS dataset, with binary values representing five protected attributes and column names 'Asian', 'Black', 'Hispanic', 'MR', 'White' obtain column numbers using:
    ```python
    x.columns.get_loc('Asian') -->

*  **petha (fairknot regularization parameter):**

  - This regularization parameter varies across datasets, influencing the model’s performance attributes.

  - For the original MARS algorithm developed by Friedman, `petha` value is set to 0.
  - In fairMARS, the `petha` value given to the argument should be greater than 0.
  - It must be tuned for each dataset to achieve fairness in the fairMARS model.

*  **fair_coef (faircoef component)::**

  A binary switch (True/False).
  When set to True, activates the fair coefficient component.


Additional MARS Parameter:

* **xlabels_` : list**
  - List of column names for training predictors.
  - Defaults to `['x0','x1',....]` if column names are not provided.
  - Including `xlabels` in your `model.fit` argument allows you to see feature names in the model summary.
```python
model.fit(X_train, y_train, disparity_indices=[31], petha=0.2, fair_coef=True, xlabels=x.columns.tolist())
```

* **Other parameters: ** For a comprehensive list of other MARS parameters, you can refer to the scikit-learn documentation at https://contrib.scikit-learn.org/py-earth/_modules/pyearth/earth.html




