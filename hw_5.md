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
    ##  1  0.28 Very Good E     VS1      62.2  59     428  4.19  4.23  2.62
    ##  2  1.53 Ideal     F     SI1      62    56   11229  7.43  7.38  4.59
    ##  3  0.31 Ideal     E     VS1      61.6  57     942  4.35  4.32  2.67
    ##  4  0.92 Premium   H     VS2      59.6  59    3916  6.32  6.29  3.76
    ##  5  0.61 Ideal     E     VVS2     62.4  53.9  2907  5.42  5.43  3.38
    ##  6  0.32 Ideal     D     VS2      61.7  54     758  4.38  4.43  2.72
    ##  7  0.3  Ideal     D     SI1      62.5  57     709  4.32  4.29  2.69
    ##  8  1.07 Premium   F     SI2      61.8  59    4560  6.53  6.57  4.05
    ##  9  0.54 Ideal     G     VS2      62.8  55    1441  5.23  5.17  3.27
    ## 10  1.09 Ideal     E     SI2      61.6  55    5035  6.6   6.64  4.08
    ## # … with 529 more rows

\#Part 3

``` r
clarity_size <- diamonds %>%
  group_by(clarity) %>%
  
 slice_max(order_by = carat, n=100, with_ties = FALSE)%>% #select the 100 largest diamonds in each clarity category
  summarise(average.clarify = mean(carat, na.rm = TRUE)) #calculate the average size
  (clarity_size)
```

    ## # A tibble: 8 × 2
    ##   clarity average.clarify
    ##   <ord>             <dbl>
    ## 1 I1                 2.51
    ## 2 SI2                2.62
    ## 3 SI1                2.30
    ## 4 VS2                2.23
    ## 5 VS1                2.10
    ## 6 VVS2               1.66
    ## 7 VVS1               1.51
    ## 8 IF                 1.40

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
