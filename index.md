---
layout: default
title: Predicting presidential approval ratings with Reddit comments
---

## Motivation & Background
Many politicos and pundits complain about the accuracy of polls during presidential, state, and federal election cycles. While issues with public perception of polling accuracy are nothing new, some of the unconventional and non-traditional ways to predict outcomes nowadays are: Polymarket–an online betting platform–outperformed most traditional pollsters in predicting Donlad Trump as the winner of the presidential election. 

For this project, we wanted to employ a similar non-traditional prediction method, and see if a model trained on the sentiment of reddit comments about sitting presidents could yield similar approval rating results to actual polls. Findings could potentially produce a way to gauge approval rating without the need for extensive polling more broadly, or at the very least, augment pollsters’ findings. 

## Data
Our data came from 2 main sources: 
**Presidential Approval Rating**
- Scraped from website of the [American Presidency Project](https://www.presidency.ucsb.edu/statistics/data/presidential-job-approval-all-data)
- Aggregated at the weekly level
- Data collected by Gallup
  
**Reddit Comments**
- Comments and posts about presidents (Obama, Trump, Biden)
- Retrieved using the Reddit API
- Date range: 2009-2025


## Methodology: Model & Pipeline

### Databricks
![Pipeline Diagram](visuals/pipeline_databricks.png)

### XGBoost

## Findings
![XGboost - Weekly Lagged Model Performance](visuals/model_lag_weekly.png)
![XGboost - Daily Model Performance](visuals/model_daily.png)
