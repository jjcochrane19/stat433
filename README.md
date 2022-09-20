---
title: "hw1"
output: html_document
---

```{r}
install.packages("nycflights13")
library(nycflights13)
library(tidyverse)
library(dplyr)
library(ggplot2)
```
# Question 1.
```{r}
summary(flights)
```

8,255 flights are missing `dep_time`. Similarly, 8,255 flights are missing `dep_delay`, 8,713 are missing `arr_time`, 9,430 are missing `arr_delay`, and 9,430 are missing `air_time`. There could be many explanations for this, including flights that never took off, never landed, or were rerouted. Alternatively, it is very possible that mistakes were made in record keeping, resulting in imperfect data.

# Question 2.
```{r}
flights%>%
  mutate(dep_time = ((dep_time - dep_time%%100)*.6) + dep_time%%100, sched_dep_time = ((sched_dep_time - sched_dep_time%%100)*.6) + sched_dep_time%%100)
```