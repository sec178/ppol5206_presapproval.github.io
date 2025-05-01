---
layout: default
title: Predicting presidential approval ratings with Reddit comments
---
![image](/visuals/download.png)
![image](/visuals/president_seal.jpg)

## Motivation & Background
Many politicos and pundits complain about the accuracy of polls during presidential, state, and federal election cycles. While issues with public perception of polling accuracy are nothing new, some of the unconventional and non-traditional ways to predict outcomes nowadays are: For instance, Polymarket–an online betting platform–outperformed most traditional pollsters in predicting Donlad Trump as the winner of the 2024 presidential election. 

For this project, we wanted to employ a similar non-traditional prediction method, and see if a model trained on the sentiment of reddit comments about sitting presidents could yield similar approval rating results to actual polls. Findings could potentially produce a way to gauge approval rating without the need for extensive polling more broadly, or at the very least, augment pollsters’ findings. 

Our GitHub repository containing the code used for this project can be found [here](https://github.com/holtcochran/PPOL5206-FinalProject/tree/main). 

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

Final data sets were compiled at the weekly (n=796) and daily level (n=5,885)

## Methodology: Model & Pipeline in Databricks
Once data were collected, we utilized Databricks for its cloud, Spark, and pipeline capabilities. This included the following steps:

*Sentiment Analysis*: Generate sentiment scores (-1 to 1) from comment texts (TextBlob package used)

*Data Merging*: Sentiment scores were aggregated by mean for subreddits and the daily and weekly level. This was then merged with approval rating by date

*Model Training*: An XGboost model was then trained using the subreddit sentiment and input features, with the target feature being approval rating. The XGboost algorithm was chosen for its accuracy and ability to handle null values

![Pipeline Diagram](visuals/pipeline_databricks.png)

## Exploratory Data Analysis
![Approval Ratings over time by President](visuals/pres_approval_overtime.png) 
![Average Sentiment Scores (Rounded) for past 3 Presidents](visuals/pres_sentiment_avg.png)


## Findings

The lagged weekly model had an Mean Absolute Error of 3.4, with a Root Mean Squared Error of 4.36:  
![XGboost - Weekly Lagged Model Performance](visuals/model_lag_weekly.png)

The daily model had a Mean Absolute Error of 3.1, with a Root Mean Squared Error of 4.08:
![XGboost - Daily Model Performance](visuals/model_daily.png)

Both models had relatively high R-squared values (0.54 and 0.42, respectively), indicating a relatively high proportion of variance explained by the model. 

---
Despite some clear drawbacks to this model pipeline and project (relatively low number of observations, sparsity, inability to guage representative samples, online bias, etc.), the scope of this project is promising: it is relatively easy to scale up this pipeline, and to continually enhance the model over time. In addition, due to the cloud and use of big data architecture through Databricks, it can be scaled upward if necessary. Findings and predictions can lead to more responsive governance, early warnings for political shifts, and improved public engagement.

