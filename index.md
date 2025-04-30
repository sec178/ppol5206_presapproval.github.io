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


## Methodology: Model & Pipeline in Databricks
Once data were collected, we utilized Databricks for its cloud, Spark, and pipeline capabilities. This included the following steps:

Sentiment Analysis: Generate sentiment scores (-1 to 1) from comment texts (TextBlob package used)

Data Merging: Sentiment scores were aggregated by mean for subreddits and the daily and weekly level. This was then merged with approval rating by date

Model Training: An XGboost model was then trained using the subreddit sentiment and input features, with the target feature being approval rating

![Pipeline Diagram](visuals/pipeline_databricks.png)

## Exploratory Data Analysis
![Approval Ratings over time by President](visuals/pres_approval_overtime.png)
![Average Sentiment Scores (Rounded) for past 3 Presidents](visuals/pres_sentiment_avg.png)


## Findings
![XGboost - Weekly Lagged Model Performance](visuals/model_lag_weekly.png)
![XGboost - Daily Model Performance](visuals/model_daily.png)
