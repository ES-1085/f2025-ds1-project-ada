Project proposal
================
ADA

``` r
#install packages 
install.packages(c("janitor", "skimr"))
install.packages(c("tidyverse", "broom"))
library(tidyverse)
library(broom)
library(skimr)
## Add any additional packages you are using here
```

## 1. Introduction

The introduction should introduce your general research question(s) and
your data (where it came from, how it was collected, what are the cases,
what are the variables, etc.).

Text goes here. Refer to the Markdown Quick Reference: Help -\> Markdown
Quick Reference.

## 2. Data

Text goes here. Place your data in the /data folder, and add dimensions
and codebook to the README in that folder. Then print out the output of
glimpse() or skim() of your data frame.

``` r
# Code goes here
# Read in your data file
setwd("/cloud/project/proposal")
library(readr)
social <- read_csv("../data/which_social_media_platforms_are_most_popular_data_2024-11-13.csv", skip = 2, n_max = 17)
```

    ## Rows: 17 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (13): Year, YouTube, Facebook, Instagram, Pinterest, TikTok, LinkedIn, W...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
demographic <- read_csv("../data/social_media_usage_among_demographic_groups - Sheet1 (1).csv", skip = 1)
```

    ## Rows: 6 Columns: 12
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (12): Group, Youtube, Facebook, Instagram, Pinterest, TikTok, LinkedIn, ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
# Print the output of glimpse() or skim()
demographic <- read_csv("../data/social_media_usage_among_demographic_groups - Sheet1 (1).csv", skip = 1)
```

    ## Rows: 6 Columns: 12
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (12): Group, Youtube, Facebook, Instagram, Pinterest, TikTok, LinkedIn, ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
glimpse(demographic)
```

    ## Rows: 6
    ## Columns: 12
    ## $ Group         <chr> "Men", "Women", "White", "Black", "Hispanic", "Asian"
    ## $ Youtube       <chr> "82%", "83%", "81%", "82%", "86%", "93%"
    ## $ Facebook      <chr> "59%", "76%", "69%", "64%", "66%", "67%"
    ## $ Instagram     <chr> "39%", "54%", "43%", "46%", "58%", "57%"
    ## $ Pinterest     <chr> "19%", "50%", "36%", "28%", "32%", "30%"
    ## $ TikTok        <chr> "25%", "40%", "28%", "39%", "49%", "29%"
    ## $ LinkedIn      <chr> "31%", "29%", "30%", "29%", "23%", "45%"
    ## $ WhatsApp      <chr> "27%", "31%", "20%", "31%", "54%", "51%"
    ## $ Snapchat      <chr> "21%", "32%", "25%", "25%", "35%", "25%"
    ## $ `Twitter (X)` <chr> "26%", "19%", "20%", "23%", "25%", "37%"
    ## $ Reddit        <chr> "27%", "17%", "21%", "14%", "23%", "36%"
    ## $ BeReal        <chr> "2%", "5%", "3%", "1%", "4%", "9%"

``` r
skim(demographic)
```

|                                                  |             |
|:-------------------------------------------------|:------------|
| Name                                             | demographic |
| Number of rows                                   | 6           |
| Number of columns                                | 12          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |             |
| Column type frequency:                           |             |
| character                                        | 12          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |             |
| Group variables                                  | None        |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| Group         |         0 |             1 |   3 |   8 |     0 |        6 |          0 |
| Youtube       |         0 |             1 |   3 |   3 |     0 |        5 |          0 |
| Facebook      |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| Instagram     |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| Pinterest     |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| TikTok        |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| LinkedIn      |         0 |             1 |   3 |   3 |     0 |        5 |          0 |
| WhatsApp      |         0 |             1 |   3 |   3 |     0 |        5 |          0 |
| Snapchat      |         0 |             1 |   3 |   3 |     0 |        4 |          0 |
| Twitter (X)   |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| Reddit        |         0 |             1 |   3 |   3 |     0 |        6 |          0 |
| BeReal        |         0 |             1 |   2 |   2 |     0 |        6 |          0 |

## 3. Data analysis plan

Text goes here. - What variables will you visualize to explore your
research questions? - Will there be any other data that you need to find
to help with your research question? - Very preliminary exploratory data
analysis, including some summary statistics and visualizations, along
with some explanation on how they help you learn more about your data.
(You can add to these later as you work on your project.) - The data
visualization(s) that you believe will be useful in exploring your
question(s). (You can update these later as you work on your project.)

``` r
# Code goes here
# Code to calculate summary statistics
# Code for a visualization
```
