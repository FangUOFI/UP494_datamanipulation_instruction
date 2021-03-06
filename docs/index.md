---
title: "Chicago crimes in 2019 and 2020"
author: "Fang Fang"
knit: (function(input_file, encoding) {
  out_dir <- 'docs';
  rmarkdown::render(input_file,
 encoding=encoding,
 output_file=file.path(dirname(input_file), out_dir, 'index.html'))})
output: 
  html_document: 
    keep_md: yes

---

Objectives

- Examine data types in R;
- Clean and transform data into a proper format;  
- Explore how crime events change over time;
- Compare crime events before and after the pandemic;

## 1. Preparation

In this exercise you will be working as a group to get familiar with basic R data wrangling. The data sets we are working on are crime events in 2019 (pre-covid) and 2020(post-covid). Please note the data are originally downloaded from Chicago open data portal.Please check it out [here](https://data.cityofchicago.org/Public-Safety/Crimes-2020/qzdf-xmn8) and [here](https://data.cityofchicago.org/Public-Safety/Crimes-2019/w98m-zvie) for more information. 

We will first examine the data type for each variable in the dataset. Then, we will transform and summarize the data and be focusing on five specific factors:crime type, arrested or not, season, time of day, and day of the week. Crime type and arrested status are already given in the dataset, but we will need to wrangle the data and generate new columns to explore the pattern for other three factors.

## 2. Explore each factor and answer the questions

- Crime type: What are the most frequent crime type?
- Arrested status: Among the crime events, do we have more arrested or not arrested?
- Season: Do you find any seasonal difference affect crime events frequency (Spring: March-May; Summer: June-August; Fall: September-November; Winter: December-February)? 
- Time of day: Do you find any time period difference affect crime events frequency: mornings(4am-12pm), afternoons(12pm-8pm), nights (8pm-4am)?
- Day of the week: What is the crime type distribution during weekdays and weekends?

## 3. Examine the columns/variables

Load the dataset in R and examine the data type for each column carefully. Do we need to convert some numbers into chr? Or any chr into factors? Do we need to create any new columns or add new labels? Use `mutate` to generate new columns. Hint: to convert a numeric column into a  factor (e.g. convert Month into seasons) you can use the `cut` function. Alternatively you can use `if_else` function to assign values based on T/F conditions only. Use the R help page to learn more about these new functions. 


```r
library(tidyverse)
library(lubridate)

Crimes_2019 <- read_csv("data/Crimes_2019.csv")
```

## 4. Crime type and arrested status

You can use the table function to summarize the frequency of crime type and arrested status. 


```r
table()
```

## 5. Crime event distribution by season/time of the day/day of the week

You can use the `group_by` and `summarize` functions to summarize the frequency of crime. Do you see any seasonal/daily patterns of crime? Any differences of crime types between weekends vs weekdays? 


```r
Crimes_2019 %>% group_by() %>% summarise(N=n())
```

## 6. Compare the results between 2019 and 2020. Do you think we have different crime event patterns before/after the pandemic? 


