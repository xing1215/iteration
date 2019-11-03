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

    ##  [1] -0.61509671 -0.62623683  0.51438019 -0.33063517  1.84799710
    ##  [6]  0.38683599 -0.76816167  0.80265522 -0.21736976 -0.62134924
    ## [11]  0.14345243  1.08121742 -0.55709019  0.75755055  1.17031880
    ## [16]  0.61011034  0.17227206  0.22334576  1.16725840 -1.67588569
    ## [21] -1.18684553 -2.36864289  0.80209397 -0.11368289  0.02747018
    ## [26] -1.58927677  1.72448417  0.57888979 -0.39792921 -0.94212981

``` r
(x_again - mean(x_again)) / sd(x_again)
```

    ##  [1] -0.69212862 -0.12812881 -1.29920809  2.02630842 -0.04244377
    ##  [6]  0.13696023  0.02723602  0.59385949 -0.58748065 -0.83547322
    ## [11]  2.46847675 -2.00986104 -0.19081206  1.25076503  0.26444447
    ## [16]  1.00408318 -1.18086984 -0.54980756 -1.61600208  0.72046533
    ## [21] -0.25144669 -0.48322555 -0.49583264 -0.68634339  0.26858821
    ## [26]  1.17339547  0.40456541  0.65518423  0.57387315 -0.51914138

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

    ##  [1] -0.69212862 -0.12812881 -1.29920809  2.02630842 -0.04244377
    ##  [6]  0.13696023  0.02723602  0.59385949 -0.58748065 -0.83547322
    ## [11]  2.46847675 -2.00986104 -0.19081206  1.25076503  0.26444447
    ## [16]  1.00408318 -1.18086984 -0.54980756 -1.61600208  0.72046533
    ## [21] -0.25144669 -0.48322555 -0.49583264 -0.68634339  0.26858821
    ## [26]  1.17339547  0.40456541  0.65518423  0.57387315 -0.51914138

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

    ##  [1] -0.69212862 -0.12812881 -1.29920809  2.02630842 -0.04244377
    ##  [6]  0.13696023  0.02723602  0.59385949 -0.58748065 -0.83547322
    ## [11]  2.46847675 -2.00986104 -0.19081206  1.25076503  0.26444447
    ## [16]  1.00408318 -1.18086984 -0.54980756 -1.61600208  0.72046533
    ## [21] -0.25144669 -0.48322555 -0.49583264 -0.68634339  0.26858821
    ## [26]  1.17339547  0.40456541  0.65518423  0.57387315 -0.51914138

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

## Multiple outputs

``` r
mean_and_sd = function(input_x) {
  
  if (!is.numeric(input_x)) {
    stop("x should be numeric")
  } else if (length(input_x) == 1) {
    stop("x should be larger than 3")
  }
  
  list(
    mean_input = mean(input_x),
    sd_input = sd(input_x),
    z_score = (input_x - mean(input_x)) / sd(input_x)
  )
  
}
```

test the function

``` r
mean_and_sd(input_x = x)
```

    ## $mean_input
    ## [1] 3.528253
    ## 
    ## $sd_input
    ## [1] 1.866055
    ## 
    ## $z_score
    ##  [1] -0.61509671 -0.62623683  0.51438019 -0.33063517  1.84799710
    ##  [6]  0.38683599 -0.76816167  0.80265522 -0.21736976 -0.62134924
    ## [11]  0.14345243  1.08121742 -0.55709019  0.75755055  1.17031880
    ## [16]  0.61011034  0.17227206  0.22334576  1.16725840 -1.67588569
    ## [21] -1.18684553 -2.36864289  0.80209397 -0.11368289  0.02747018
    ## [26] -1.58927677  1.72448417  0.57888979 -0.39792921 -0.94212981

## Multiple inputs
