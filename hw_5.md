Homework 5
================

\#Part 1

``` r
library(tidyverse)
number_cut <- diamonds %>%
  group_by(cut) %>% #group the data
  summarise(count = n()) #count of diamonds in each “cut” 
(number_cut) #print the data frame
```

    ## # A tibble: 5 × 2
    ##   cut       count
    ##   <ord>     <int>
    ## 1 Fair       1610
    ## 2 Good       4906
    ## 3 Very Good 12082
    ## 4 Premium   13791
    ## 5 Ideal     21551

\#Part 2

``` r
dplyr::sample_frac(diamonds, 0.01, replace = TRUE) #create a data set that contains 1% of the rows
```

    ## # A tibble: 539 × 10
    ##    carat cut       color clarity depth table price     x     y     z
    ##    <dbl> <ord>     <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  0.38 Ideal     E     VVS1     62.4    56  1327  4.67  4.64  2.9 
    ##  2  0.9  Very Good H     VS2      61.8    56  4155  6.18  6.25  3.84
    ##  3  0.42 Ideal     D     VS1      61.4    55  1006  4.8   4.9   2.98
    ##  4  0.4  Ideal     G     VS2      62.3    54   792  4.73  4.77  2.96
    ##  5  0.74 Good      G     SI1      63.6    58  1865  5.73  5.71  3.64
    ##  6  0.43 Ideal     E     SI1      62.6    56   975  4.82  4.79  3.01
    ##  7  1.06 Very Good F     VS2      62.7    55  6627  6.54  6.5   4.09
    ##  8  0.34 Very Good G     VVS2     62.3    59   740  4.45  4.48  2.78
    ##  9  0.3  Very Good E     VS2      62.8    56   658  4.28  4.32  2.7 
    ## 10  0.4  Premium   I     VVS1     61.5    58  1080  4.76  4.7   2.91
    ## # … with 529 more rows

\#Part 3

``` r
clarity_size <- diamonds %>%
  group_by(clarity) %>%
  arrange(carat, .by_group = TRUE) %>%
  top_n(100,carat) %>% #select the 100 largest diamonds in each clarity category
  summarise(average.clarify = mean(carat, na.rm = TRUE)) #calculate the average size
  (clarity_size)
```

    ## # A tibble: 8 × 2
    ##   clarity average.clarify
    ##   <ord>             <dbl>
    ## 1 I1                 2.46
    ## 2 SI2                2.62
    ## 3 SI1                2.29
    ## 4 VS2                2.22
    ## 5 VS1                2.10
    ## 6 VVS2               1.64
    ## 7 VVS1               1.50
    ## 8 IF                 1.39

\#Part 4

``` r
ggplot(data = diamonds) + 
  geom_point(mapping = aes(x = x, y = y))
```

![](hw_5_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
ggplot(data = diamonds) + 
  geom_point(mapping = aes(x = x, y = z))
```

![](hw_5_files/figure-gfm/unnamed-chunk-4-2.png)<!-- -->

\#Part 5

``` r
correct_size <- diamonds %>%
  filter (x > 3, y < 20, z > 2 & z < 10) #remove bad points
ggplot(data = correct_size) + 
  geom_point(mapping = aes(x = x, y = y))
```

![](hw_5_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
ggplot(data = correct_size) + 
  geom_point(mapping = aes(x = x, y = z))
```

![](hw_5_files/figure-gfm/unnamed-chunk-5-2.png)<!-- -->
