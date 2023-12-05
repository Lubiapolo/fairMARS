fair py-earth [![Build Status](https://travis-ci.org/scikit-learn-contrib/py-earth.png?branch=master)](https://travis-ci.org/scikit-learn-contrib/py-earth?branch=master)
========

A Python implementation of Jerome Friedman's Multivariate Adaptive Regression Splines algorithm, 
in the style of scikit-learn. The py-earth package implements Multivariate Adaptive Regression Splines using Cython and provides an interface that is compatible with scikit-learn's Estimator, Predictor, Transformer, and Model interfaces.  For more information about 
Multivariate Adaptive Regression Splines, see the references below.


## Installation

Make sure you have numpy and scikit-learn installed.  Then do the following:

```
git clone git://github.com/scikit-learn-contrib/py-earth.git
cd py-earth
sudo python setup.py install
```

## Usage
```python
import numpy
from pyearth import Earth
from matplotlib import pyplot
    
#Create some fake data
numpy.random.seed(0)
m = 1000
n = 10
X = 80*numpy.random.uniform(size=(m,n)) - 40
y = numpy.abs(X[:,6] - 4.0) + 1*numpy.random.normal(size=m)
    
#Fit an Earth model
model = Earth()
model.fit(X,y)
    
#Print the model
print(model.trace())
print(model.summary())
    
#Plot the model
y_hat = model.predict(X)
pyplot.figure()
pyplot.plot(X[:,6],y,'r.')
pyplot.plot(X[:,6],y_hat,'b.')
pyplot.xlabel('x_6')
pyplot.ylabel('y')
pyplot.title('Simple Earth Example')
pyplot.show()
 ```
 
 
## References

1. Friedman, J. (1991). Multivariate adaptive regression splines. The annals of statistics, 
   19(1), 1–67. http://www.jstor.org/stable/10.2307/2241837
2. Stephen Milborrow. Derived from mda:mars by Trevor Hastie and Rob Tibshirani.
   (2012). earth: Multivariate Adaptive Regression Spline Models. R package
   version 3.2-3. http://CRAN.R-project.org/package=earth
3. Friedman, J. (1993). Fast MARS. Stanford University Department of Statistics, Technical Report No 110. 
   https://statistics.stanford.edu/sites/default/files/LCS%20110.pdf
4. Friedman, J. (1991). Estimating functions of mixed ordinal and categorical variables using adaptive splines.
   Stanford University Department of Statistics, Technical Report No 108. 
   http://media.salford-systems.com/library/MARS_V2_JHF_LCS-108.pdf
5. Stewart, G.W. Matrix Algorithms, Volume 1: Basic Decompositions. (1998). Society for Industrial and Applied 
   Mathematics.
6. Bjorck, A. Numerical Methods for Least Squares Problems. (1996). Society for Industrial and Applied 
   Mathematics.
7. Hastie, T., Tibshirani, R., & Friedman, J. The Elements of Statistical Learning (2nd Edition). (2009).  
   Springer Series in Statistics
8. Golub, G., & Van Loan, C. Matrix Computations (3rd Edition). (1996). Johns Hopkins University Press.
   
References 7, 2, 1, 3, and 4 contain discussions likely to be useful to users of py-earth.  References 1, 2, 6, 5, 
8, 3, and 4 were useful during the implementation process.



   
