---
title: A Shortened MLB Season? The Good and the Bad.
author: ~
date: '2020-12-10'
slug: is-the-starting-pitcher-still-the-king-of-the-hill-in-mlb
categories: []
tags: []
---

```{r, message=FALSE}
library(tidyverse)
dat_mlb <- read_csv("mlb_elo_latest.csv")
```

## Data

The second dataset we'll be examining for this project is the Major League Baseball Elo dataset given in the mlb_elo_latest.csv file on the FiveThirtyEight website. The MLB Elo dataset has 951 observations of 26 variables: the variables team1 and team2 are abbreviations for the home and away team, the variables elo_prob1 and elo_prob2 define the home and away team's probability of winning according to Elo ratings, the variables pitcher1 and pitcher2 list the name of the home and away starting pitcher, the variables rating_prob1 and rating_prob2 indicate the home and away team's probability of winning according to team ratings AND starting pitcher adjustment, and the variables score1 and score2 provide the number of runs scored for either team in each game.

## Question 1:

Did games being played on a neutral site (mainly the postseason) lead to more runs being scored or was there not much of a difference? To explore this question, we visualize the total number of runs scored per game on a neutral site versus in series that were played in each team's respective home ballpark.

```{r}
home_ballparks <- dat_mlb %>% filter(neutral == FALSE) %>% mutate(total_runs = score1 + score2)
neutral_site <- dat_mlb %>% filter(neutral == TRUE) %>% mutate(total_runs = score1 + score2)
```


