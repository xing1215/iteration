Writing Functions
================

## Get start

we are going to write some functions

calculating z-scores

``` r
x = rnorm(n = 30, mean = 4, sd = 2.3)
x_again = rnorm(n = 30, mean = 6, sd = 0.3)

(x - mean(x)) / sd(x)
```

    ##  [1]  0.345308541 -1.303013054 -0.666074464  0.000193572  2.660653653
    ##  [6]  0.909609202  0.994548792 -0.719489639  1.946383878 -0.675973070
    ## [11] -0.045158854  0.234106777 -0.782149033 -0.227419052  0.090065369
    ## [16] -1.440052678 -0.442184095 -0.180856004  0.293236561  0.466372818
    ## [21] -0.980395642  0.666386727 -0.223276755 -1.010695530 -0.956944256
    ## [26]  2.272739633  0.240372203 -0.641232119 -0.848265255  0.023201777

``` r
(x_again - mean(x_again)) / sd(x_again)
```

    ##  [1]  1.580525712  0.008964741  0.409970152 -1.983430479 -2.064517379
    ##  [6]  0.095035535 -1.447642057  1.721987290  0.754885775  0.726859136
    ## [11]  0.727138349  0.143730055  0.354899137  1.027757842  0.276861117
    ## [16] -1.676213246  0.292121393 -0.914551544  0.653070331 -1.591602428
    ## [21] -0.067721193  0.655722246  0.786492040 -0.215247865  0.089073202
    ## [26]  0.063410632 -0.668773316 -0.903809772  0.126505350  1.038499244

Now a function

``` r
z_score = function(x_arg) {
  (x_arg - mean(x_arg)) / sd(x_arg)
}
```

Here, we receive a lot errors when using the functions. Thus, we want to
add some conditions to our fucntion.

``` r
z_score = function(x_arg) {
  
  if (!is.numeric(x_arg)) {
    stop("x should be numeric")
  } else if (length(x_arg) == 1) {
    stop("x should be larger than 3")
  }
  
  (x_arg - mean(x_arg)) / sd(x_arg)
  
}
```

Try the
    function

``` r
z_score(x_arg = x_again)
```

    ##  [1]  1.580525712  0.008964741  0.409970152 -1.983430479 -2.064517379
    ##  [6]  0.095035535 -1.447642057  1.721987290  0.754885775  0.726859136
    ## [11]  0.727138349  0.143730055  0.354899137  1.027757842  0.276861117
    ## [16] -1.676213246  0.292121393 -0.914551544  0.653070331 -1.591602428
    ## [21] -0.067721193  0.655722246  0.786492040 -0.215247865  0.089073202
    ## [26]  0.063410632 -0.668773316 -0.903809772  0.126505350  1.038499244

``` r
z_score(x_arg = 3)
```

    ## Error in z_score(x_arg = 3): x should be larger than 3

``` r
z_score(x_arg = "my name is jeff")
```

    ## Error in z_score(x_arg = "my name is jeff"): x should be numeric

``` r
z_score(x_arg = c(TRUE, TRUE, FALSE, TRUE))
```

    ## Error in z_score(x_arg = c(TRUE, TRUE, FALSE, TRUE)): x should be numeric
