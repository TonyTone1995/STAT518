demo\_R
================
Antonio Ruiz
June 11, 2019

``` r
print('hello world')
```

    ## [1] "hello world"

Vectors
-------

``` r
A_vector <- c(1, 2, 3)
B_vector <- c(4, 5, 6)

# Take the sum of A_vector and B_vector
total_vector <- A_vector %*% B_vector
  
# Print out total_vector
total_vector
```

    ##      [,1]
    ## [1,]   32

some basic plotting and filters
-------------------------------

``` r
library(tidyverse)
```

    ## -- Attaching packages -------------------------------------------------------------------------------------------------------------------------- tidyverse 1.2.1 --

    ## v ggplot2 3.1.0     v purrr   0.2.5
    ## v tibble  1.4.2     v dplyr   0.7.8
    ## v tidyr   0.8.2     v stringr 1.3.1
    ## v readr   1.3.0     v forcats 0.3.0

    ## Warning: package 'ggplot2' was built under R version 3.5.2

    ## -- Conflicts ----------------------------------------------------------------------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](activity_1_2_files/figure-markdown_github/unnamed-chunk-3-1.png)

``` r
filter(mpg, cyl == 8)
```

    ## # A tibble: 70 x 11
    ##    manufacturer model displ  year   cyl trans drv     cty   hwy fl    class
    ##    <chr>        <chr> <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
    ##  1 audi         a6 q~   4.2  2008     8 auto~ 4        16    23 p     mids~
    ##  2 chevrolet    c150~   5.3  2008     8 auto~ r        14    20 r     suv  
    ##  3 chevrolet    c150~   5.3  2008     8 auto~ r        11    15 e     suv  
    ##  4 chevrolet    c150~   5.3  2008     8 auto~ r        14    20 r     suv  
    ##  5 chevrolet    c150~   5.7  1999     8 auto~ r        13    17 r     suv  
    ##  6 chevrolet    c150~   6    2008     8 auto~ r        12    17 r     suv  
    ##  7 chevrolet    corv~   5.7  1999     8 manu~ r        16    26 p     2sea~
    ##  8 chevrolet    corv~   5.7  1999     8 auto~ r        15    23 p     2sea~
    ##  9 chevrolet    corv~   6.2  2008     8 manu~ r        16    26 p     2sea~
    ## 10 chevrolet    corv~   6.2  2008     8 auto~ r        15    25 p     2sea~
    ## # ... with 60 more rows

``` r
filter(diamonds, carat > 3)
```

    ## # A tibble: 32 x 10
    ##    carat cut     color clarity depth table price     x     y     z
    ##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
    ##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
    ##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
    ##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
    ##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
    ##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
    ##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
    ##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
    ##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
    ## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
    ## # ... with 22 more rows

Loading DatasauRus
------------------

``` r
library(datasauRus)
```

    ## Warning: package 'datasauRus' was built under R version 3.5.3

``` r
datasaurus_dozen %>% count(dataset) %>% print(13)
```

    ## # A tibble: 13 x 2
    ##    dataset        n
    ##    <chr>      <int>
    ##  1 away         142
    ##  2 bullseye     142
    ##  3 circle       142
    ##  4 dino         142
    ##  5 dots         142
    ##  6 h_lines      142
    ##  7 high_lines   142
    ##  8 slant_down   142
    ##  9 slant_up     142
    ## 10 star         142
    ## 11 v_lines      142
    ## 12 wide_lines   142
    ## 13 x_shape      142

``` r
#?datasaurus_dozen
```

``` r
datasaurus_dozen
```

    ## # A tibble: 1,846 x 3
    ##    dataset     x     y
    ##    <chr>   <dbl> <dbl>
    ##  1 dino     55.4  97.2
    ##  2 dino     51.5  96.0
    ##  3 dino     46.2  94.5
    ##  4 dino     42.8  91.4
    ##  5 dino     40.8  88.3
    ##  6 dino     38.7  84.9
    ##  7 dino     35.6  79.9
    ##  8 dino     33.1  77.6
    ##  9 dino     29.0  74.5
    ## 10 dino     26.2  71.4
    ## # ... with 1,836 more rows

Exercise 1 Response:
--------------------

-   Description: A dataset demonstrating the utility of visualization. These 12 datasets are equal in standard measures: mean, standard deviation, and Pearson's correlation.
-   Columns: 3
-   Rows: 1846
-   Each row is a set of coordinates with a respective data.

Dino Data Frame
---------------

``` r
dino_data <- datasaurus_dozen %>% filter(dataset =="dino")
```

Some GGPlot
-----------

-   Answer to question:

Exercise 2
----------

-   Plotting x vs y,
-   Correlation: -0.06447185

``` r
ggplot(data=dino_data, mapping=aes(x=x,y=y)) + geom_point()
```

![](activity_1_2_files/figure-markdown_github/unnamed-chunk-7-1.png)

``` r
cor(dino_data$x, dino_data$y)
```

    ## [1] -0.06447185

``` r
dino_data %>% summarize(r = cor(x,y))
```

    ## # A tibble: 1 x 1
    ##         r
    ##     <dbl>
    ## 1 -0.0645
