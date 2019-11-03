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

    ##  [1] -1.6425606 -0.6078876 -0.1564648 -0.8576463 -0.8713038  2.4184688
    ##  [7]  0.8377984  0.2079900 -0.6008281  1.7665388  0.2940387  0.4879988
    ## [13] -1.5224147  1.0681035 -0.1473632 -0.8914845 -0.8979417 -0.7705498
    ## [19]  0.7176757 -0.9409700  0.9555849 -0.3597910 -1.5034857 -0.3045122
    ## [25]  0.1281135  1.1513854  1.2627604  0.6495774  0.3599805 -0.2308108

``` r
(x_again - mean(x_again)) / sd(x_again)
```

    ##  [1]  0.55544725 -1.55439120  0.41755462 -0.24954766  2.51370752
    ##  [6]  0.42734550  0.57145339  0.04708557  0.08667934 -0.88124124
    ## [11]  0.97026135 -1.06174850  0.46610134 -0.15879607 -0.85226858
    ## [16] -1.01366271  1.03229481 -0.21990045  0.21094065  0.17012524
    ## [21] -0.63522134  1.55217920  0.80531839 -0.33432195  1.30745200
    ## [26] -1.23850705 -1.19828207 -2.14914552  0.53485605 -0.12176789

Now a function

``` r
z_score = function(x_arg) {
  (x_arg - mean(x_arg)) / sd(x_arg)
}
```

Try the function

``` r
z_score(x_arg = x_again)
```

    ##  [1]  0.55544725 -1.55439120  0.41755462 -0.24954766  2.51370752
    ##  [6]  0.42734550  0.57145339  0.04708557  0.08667934 -0.88124124
    ## [11]  0.97026135 -1.06174850  0.46610134 -0.15879607 -0.85226858
    ## [16] -1.01366271  1.03229481 -0.21990045  0.21094065  0.17012524
    ## [21] -0.63522134  1.55217920  0.80531839 -0.33432195  1.30745200
    ## [26] -1.23850705 -1.19828207 -2.14914552  0.53485605 -0.12176789

``` r
z_score(x_arg = 3)
```

    ## [1] NA

``` r
z_score(x_arg = "my name is jeff")
```

    ## Error in x_arg - mean(x_arg): non-numeric argument to binary operator

``` r
z_score(x_arg = c(TRUE, TRUE, FALSE, TRUE))
```

    ## [1]  0.5  0.5 -1.5  0.5

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

Try the function again

``` r
z_score(x_arg = x_again)
```

    ##  [1]  0.55544725 -1.55439120  0.41755462 -0.24954766  2.51370752
    ##  [6]  0.42734550  0.57145339  0.04708557  0.08667934 -0.88124124
    ## [11]  0.97026135 -1.06174850  0.46610134 -0.15879607 -0.85226858
    ## [16] -1.01366271  1.03229481 -0.21990045  0.21094065  0.17012524
    ## [21] -0.63522134  1.55217920  0.80531839 -0.33432195  1.30745200
    ## [26] -1.23850705 -1.19828207 -2.14914552  0.53485605 -0.12176789

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
