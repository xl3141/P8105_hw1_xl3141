hw1
================
Xinyuan Liu
2021/9/22

# Problem 1

``` r
library(tidyverse)
problem1_df <- tibble(
  sample = rnorm(10), ## random sample of size 10 from a standard Normal distribution
  gr_than_0 = sample > 0, ## indicating whether elements of the sample are greater than 0
  vec_char = c("X", "i", "n", "y", "u", "a", "n", "L", "i", "u"), ##character vector with length = 10
  vec_factor = c("high", "high", "high", "middle", "middle", "middle", "low", "low", "low", "middle")  ## factor vector of length 10 with 3 levels 
)
mean(pull(problem1_df, var = 1))
```

    ## [1] -0.110806

``` r
mean(pull(problem1_df, var = 2))
```

    ## [1] 0.6

``` r
mean(pull(problem1_df, var = 3))
```

    ## Warning in mean.default(pull(problem1_df, var = 3)): ²ÎÊý²»ÊÇÊýÖµÒ²²»ÊÇÂß¼­
    ## Öµ£º»Ø¸²NA

    ## [1] NA

``` r
mean(pull(problem1_df, var = 4))
```

    ## Warning in mean.default(pull(problem1_df, var = 4)): ²ÎÊý²»ÊÇÊýÖµÒ²²»ÊÇÂß¼­
    ## Öµ£º»Ø¸²NA

    ## [1] NA

``` r
## These try to compute the mean of numbers in each column
```

We could only get the mean for the sample because it is the only numeric
variable.

``` r
as.numeric(pull(problem1_df, var = 2))
as.numeric(pull(problem1_df, var = 3))
as.numeric(pull(problem1_df, var = 4))
## These try to convert the non-numeric variables into numeric ones
```

In this case, the logical vector is able to become numeric but the
character vector and factor vector are not able to be transferred into
numerical variable

# Problem 2

``` r
data("penguins", package = "palmerpenguins")
```

The dataset “penguins” has different columns whose names are : species,
island, bill\_length\_mm, bill\_depth\_mm, flipper\_length\_mm,
body\_mass\_g, sex, year.

It has 344 rows and 8 columns.

The mean flipper length is 200.9152047 mm.

``` r
pg_df <- tibble(
  x = penguins$bill_length_mm, ## x is the bill length in mm
  y = penguins$flipper_length_mm ## y is the flipper length in mm
) ## This is the data frame of bill and flipper variable in the penguin dataset

ggplot(pg_df, aes(x = x, y = y, color = penguins$species)) + geom_point() + xlab("bill_length in mm") + ylab("flipper length in mm")
```

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](hw1_files/figure-gfm/penguins_scatterplot-1.png)<!-- -->

``` r
  ## This gives a scatterplot where x shows penguins' bill length and y shows penguins' flipper length, and colors differentiates different species of penguins 

ggsave("scatter_plot.pdf")
```

    ## Warning: Removed 2 rows containing missing values (geom_point).
