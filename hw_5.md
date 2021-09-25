Homework 5
================

# Part 1

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

# Part 2

``` r
sample_frac(diamonds, 0.01, replace = TRUE) #create a data set that contains 1% of the rows
```

    ## # A tibble: 539 × 10
    ##    carat cut       color clarity depth table price     x     y     z
    ##    <dbl> <ord>     <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  0.5  Ideal     G     VVS2     62.7    55  1836  5.07  5.1   3.19
    ##  2  0.85 Ideal     F     VS2      62.4    57  3641  6.13  6.01  3.79
    ##  3  0.42 Premium   E     SI1      61.6    59   773  4.83  4.85  2.98
    ##  4  1.09 Ideal     D     SI1      61.9    57  6133  6.57  6.61  4.08
    ##  5  1.03 Ideal     F     VVS1     61.3    54  9881  6.56  6.62  4.04
    ##  6  1.5  Premium   G     SI1      62.7    58 10087  7.28  7.23  4.55
    ##  7  0.31 Ideal     D     VS2      62.1    54   942  4.37  4.33  2.7 
    ##  8  0.31 Ideal     D     VS2      62.2    55   942  4.34  4.31  2.69
    ##  9  0.3  Very Good I     SI1      61.2    58   405  4.28  4.31  2.63
    ## 10  0.31 Very Good J     SI1      58.1    62   353  4.44  4.47  2.59
    ## # … with 529 more rows

# Part 3

``` r
clarity_size <- diamonds %>%
  group_by(clarity) %>%
 slice_max(order_by = carat, n=100, with_ties = FALSE) %>% #select the 100 largest diamonds in each clarity category
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

# Part 4

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

# Part 5

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
