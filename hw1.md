hw1
================
Xinyuan Liu
2021/9/21

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
  vec_factor = c("high", "high", "high", "medium", "medium", "medium", "low", "low", "low", "low") ## factor vector of length 10 with 3 levels 
)
mean(pull(problem1_df, var = 1))
```

    ## [1] -0.2996863

``` r
mean(pull(problem1_df, var = 2))
```

    ## [1] 0.3

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
as.numeric(pull(problem1_df, var = 2))
as.numeric(pull(problem1_df, var = 3))
as.numeric(pull(problem1_df, var = 4))
```

In this case, the logical vector is able to become numeric

# Problem 2

``` r
data("penguins", package = "palmerpenguins")
penguins$flipper_length_mm[is.na(penguins$flipper_length_mm)] <- 0
penguins$bill_length_mm[is.na(penguins$bill_length_mm)] <- 0
```

The dataset “penguins” has different columns whose names are : species,
island, bill\_length\_mm, bill\_depth\_mm, flipper\_length\_mm,
body\_mass\_g, sex, year.

It has 344 rows and 8 columns.

The mean flipper length is 199.747093.

``` r
pg_df <- tibble(
  x = penguins$bill_length_mm,
  y = penguins$flipper_length_mm
)

ggplot(pg_df, aes(x = x, y = y, color = penguins$species)) + geom_point()
```

![](hw1_files/figure-gfm/penguins_scatterplot-1.png)<!-- -->

``` r
ggsave("scatter_plot.pdf")
```

    ## Saving 7 x 5 in image
