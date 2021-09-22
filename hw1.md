hw1
================
Xinyuan Liu
2021/9/22

# Problem 1

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.4     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   2.0.1     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
problem1_df <- tibble(
  sample = rnorm(10), ## random sample of size 10 from a standard Normal distribution
  gr_than_0 = sample > 0, ## indicating whether elements of the sample are greater than 0
  vec_char = c("X", "i", "n", "y", "u", "a", "n", "L", "i", "u"), ##character vector with length = 10
  vec_factor = c("high", "high", "high", "middle", "middle", "middle", "low", "low", "low", "middle")  ## factor vector of length 10 with 3 levels 
)
mean(pull(problem1_df, var = 1))
```

    ## [1] -0.09803883

``` r
mean(pull(problem1_df, var = 2))
```

    ## [1] 0.2

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
)

ggplot(pg_df, aes(x = x, y = y, color = penguins$species)) + geom_point() ## This gives a scatterplot where x shows penguins' bill length and y shows penguins' flipper length, and colors differentiates different species of penguins 
```

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](hw1_files/figure-gfm/penguins_scatterplot-1.png)<!-- -->

``` r
ggsave("scatter_plot.pdf")
```

    ## Saving 7 x 5 in image

    ## Warning: Removed 2 rows containing missing values (geom_point).
