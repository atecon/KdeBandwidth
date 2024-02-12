# Introduction

Calculate the bandwidth for kernel density estimation (KDE) for univariate data only (at the moment). Currently Silverman's rule-of-thumb and Scott's method are supported.

In practice, we do not know whether `X` is normally distributed. If it is, then
rule-of-thumb methods will return the optimal optimal bandwidth. If not, then method will compute a bandwidth not too far from the optimum if the distribution of `X` is not too different from the normal distribution (the 'reference distribution'). The rule-of-thumb approach will give reasonable results for all distributions that are unimodal, fairly symmetric and do not have tails that are too fat. Both, Silverman's and Scott's methods, are easy to compute, but may yield widely inaccurate estimates when the density is not close to being normal.

You may uses the rule-of-thumb methods for both the Gaussian or Epanechnikov
kernel when calling Gretl's built-in `kdensity()` function.

Please report bugs or comments on the gretl mailing list, write to
atecon@posteo.de or report an issue on github
(https://github.com/atecon/KdeBandwidth).


# References

- https://en.wikipedia.org/wiki/Kernel_density_estimation#A_rule-of-thumb_bandwidth_estimator
- http://sfb649.wiwi.hu-berlin.de/fedc_homepage/xplore/ebooks/html/spm/spmhtmlnode15.html
- D.W. Scott, “Multivariate Density Estimation: Theory, Practice, and Visualization”, John Wiley & Sons, New York, Chicester, 1992.
- B.W. Silverman, “Density Estimation for Statistics and Data Analysis”, Vol. 26, Monographs on Statistics and Applied Probability, Chapman and Hall, London, 1986.

# Public function

```
function scalar (matrix input, string method, const int df_correction[0::1], const int skip_na[0:1:1], const int verbose[0:1:0])
```

Calculate the bandwidth for kernel density estimation (KDE) using either Scott's or Silverman's method for uni-variate data only (at the moment).


## Parameters

- `input`: `matrix`, Input data as a column vector
- `method`: `string`, Method for bandwidth selection. Supported values: `scott` and `silverman`.
- `df_correction`: `bool`, Indicator for degrees of freedom correction when computing the standard deviation. `FALSE` not to correct, `TRUE` to correct (default: `TRUE`).
- `skip_na`: `bool`, Indicator for skipping missing values. `FALSE` to include missing values, `TRUE` to remove them (default: `TRUE`).
- `verbose`: `bool`, Indicator for printing bandwidth selection results. `FALSE` to disable, `TRUE` to enable (default: `FALSE`).

## Returns

`scalar`: The calculated bandwidth for KDE.


# Changelog

* **v0.1 (February 2024)**
    * Initial version
