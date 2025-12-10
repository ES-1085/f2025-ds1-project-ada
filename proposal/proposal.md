Project proposal
================
ADA

``` r
library(tidyverse)
library(broom)
library(skimr)
```

## 1. Introduction

Our project explores trends in the popularity of various social media
platforms among U.S. adults over time. The research question guiding
this analysis is: *How has social media usage evolved from 2012-2024,
and what patterns can be seen across different platforms?* By examining
changes in user engagement across platforms like YouTube, Facebook,
Instagram, TikTok, Reddit, and others, this project aims to understand
how digital behaviors and communication preferences have shifted over
the past decade.

The data set used for this project was obtained from Pew Research
Center. The data was collected through **nationally representative
surveys** of U.S. adults, asking what social media platforms they use.
Each row represents survey results for a specific *year*, while the
columns correspond to the **percentage of U.S. adult who reported using
each platform.** This dataset provides us with a clear basis for a
quantitative analysis of social media trends, allowing for comparisons
across years and platforms to identify long-term evolution in digitial
media engagement.

## 2. Data

``` r
setwd("/cloud/project/proposal")
library(readr)
social <- read_csv("../data/which_social_media_platforms_are_most_popular_data_2024-11-13.csv", skip = 2, n_max = 17)
```

    ## Rows: 17 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (13): Year, YouTube, Facebook, Instagram, Pinterest, TikTok, LinkedIn, W...
    ## 

``` r
demographic <- read_csv("../data/social_media_usage_among_demographic_groups - Sheet1 (1).csv", skip = 1)
```

    ## Rows: 6 Columns: 12
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (12): Group, Youtube, Facebook, Instagram, Pinterest, TikTok, LinkedIn, ...
    ## 

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

The variables that we will visualize to explore our research questions
are: - `gender`, will be created through defining the specific gender -
`race`, will be created by defining the specific race - `year`
(2012-2024) - `platform` (%), will be created through defining the
specific social media platform - `group`

Other data needed: - Engagement data (i.e. average time spent, purpose
of use) - Regional data to assess geographic patterns This would give us
more context about why certain groups prefer specific platforms.

The types of visualizations we want to use: - Bar Chart – to compare
platform usage across `group` - Stacked Bar Chart – to show the overall
distribution of platform use by `gender` or `race` - Heatmap – to
visualize the correlation between `group` and `platform` popularity -
Trend Line Chart - to show how `platform` popularity changes over time

## Clean the demographic data to take out percentages

``` r
demographic_clean <- demographic %>%
  mutate(across(where(is.character), ~ as.numeric(gsub("%", "", .))))
```

## Example of summary statistics

``` r
## summary_stats <- demographic_clean %>%
##   group_by(Group) %>%
##  summarise(
##    Facebook_mean = mean(Facebook, na.rm = TRUE),
##    Instagram_mean = mean(Instagram, na.rm = TRUE),
##    TikTok_mean = mean(TikTok, na.rm = TRUE)
##  ) %>%

##print(summary_stats)
```

This is a sample of summary statistics that can be used to which
platforms are most popular across U.S. adults.

# Draft bar chart for specific platform usage by demographic use

``` r
# Code for a visualization

## data_long <- demographic %>%
##  pivot_longer(cols = c(Instagram, TikTok),
##               values_to = "Percent_Using")

##data_long <- data_long %>%
##  mutate(Percent_Using = as.numeric(gsub("%", "", Percent_Using)))

##ggplot(data_long, aes(x = Percent_Using, y = Group, fill = Platform)) +
##  geom_col(position = "dodge") +
##  scale_x_continuous(labels = function(x) paste0(x, "%"),
##                     limits = c(0, 100),
##                     breaks = seq(0, 100, by = 10)) + 
##  labs(title = "Social Media Usage by Age Group",
##       x = "Percentage Using Platform",
##       y = "Demographic Group") +
##  theme_minimal()
```

This chart helps answer key exploratory questions like: - Which
demographic groups prefer which social media platforms? - Are there
clear differences in usage patterns by race or gender?

Graph for Figure 2

``` r
#ggplot(df_long, aes(x = Platform, y = Usage, group = Group)) + geom_col(aes(fill = Group), position = position_dodge(width = 0.8), width = 0.55, alpha = 0.85) + geom_line(aes(color = Group), linewidth = 1.4, position = position_dodge(width = 0.8), lineend = "round") + geom_point(aes(color = Group), size = 4, position = position_dodge(width = 0.8)) + scale_fill_manual(values = c("Men" = cb_blue, "Women" = cb_pink)) + scale_color_manual(values = c("Men" = cb_blue, "Women" = cb_pink)) + labs( title = "Social Media Usage by Gender", x = "", y = "%") + theme_minimal(base_size = 16) + theme( plot.title = element_text(face = "bold", hjust = 0.5), axis.text.x = element_text(angle = 40, hjust = 1), legend.position = "top")
###
```
