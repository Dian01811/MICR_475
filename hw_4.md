Homework 4
================

Part 1

``` r
#########
# Print the sum of a and b
#########
a <- 3 # Assign the value 3 to a variable called a
b <- 2 # Assign the value 3 to a variable called a
(a+b) 
```

    ## [1] 5

Part 2

``` r
#########
# Calculate sum of 2 and 3 using the sum() function
#########
a <- 3
b <- 2
sum(a+b)
```

    ## [1] 5

Part 3

``` r
#########
# Load the nycflights13 package
#########
library(tidyverse)
library(nycflights13) 
```

Part 4

``` r
#########
# Make a scatter plot about the departure delay vs. arrival delay
#########
AA_flights <- filter(flights, carrier == "AA")
#view(AA_flights)
ggplot(data = AA_flights) + 
  geom_point(mapping = aes(x = dep_delay, y = arr_delay)) #make a scatter plot by mapping the departure delay vs. arrival delay
```

![](hw_4_files/figure-gfm/our_first_plot-1.png)<!-- -->
