![alt text](https://harfordcountyhealth.com/wp-content/uploads/2020/01/home-banner.jpg "COVID-19 Banner")
# COVID-19_UCD_Challenge
### Team LightYellowDress&amp;FluffyHair 
This repository contains all code files and data we used in the University of California, Davis, MSBA program COVID-19 Challenge Competition. In this project, we utlized web scraping techniques to collect data from multi-platforms, leveraged NLP techniques to process the text data, analyzed the data by sentiment analysis and topic modeling, and created Tableau dashboard to present the results. 

## Motivation
Understanding the social mental status helps us react faster and in a proper way during the COVID-19 period.

## Who will benefit by the analysis
- Twitter: As a social media, Twitter takes the responsibility to control negative rumors spreading during this period for the social good. Twitter can monitor the sentiment trends and study the abnormal emotion peaks like what we did. 

- Medical Institutions: Our analysis can help medical institutions know the emotion changes during the COVID-19. Doctors can provide help to people who potential have mental health problem.

- Business Owners: Keeping a watchful eye on trending topics and people’s emotion change can help business owners run marketing campaign appropriately and find out potential business opportunities, such as new services that needed by people. 

## The dataset can be used for 
- The study of people's interactions on Twitter during COVID-19 period
- The study of public media's behavior during COVID-19 period
- The study of people's emotion change during COVID-19 period
- More NLP data mining with plenty tweets during such specific period

## Our data source including:

Confirmed Cases:
1. Time searies data of confirmed cases: [Johns Hopkins CSSE](https://github.com/CSSEGISandData/COVID-19) (daily data from 01/16 to 04/11)

Twitter:
1. Tweets on Twitter retrieved with [TwitterScraper API ](https://github.com/taspinar/twitterscraper) (daily data from 01/20 to 04/08)\
  **warning**: the daily data is a sample from each day's tweets, not the population. We sampled out abough 13K tweets for each day, 1.1M in total.
2. Twitter trending topics retrieved by scraping [Trendogate.com](https://trendogate.com) (daily data from 01/20 to 04/11)
3. Number of tweets with #COVID-19 shared by [Tweet Binder](https://www.tweetbinder.com/blog/covid-19-coronavirus-twitter/) 

News:
1. #COVID-19 news scraped from [Fox News](https://www.foxnews.com/) (daily data from 01/20 to 04/08)
2. #COVID-19 news scraped from [CNN](https://www.cnn.com/) (daily data from 01/20 to 04/08)
![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/data_description.JPG)
The datasets can be found in folders. **P.S.** Due to the file size limitation set by Github, we did not upload the combined dataset. To combined the datasets in folders, please try:
```python
# Read raw datas from the raw data file
path = r'------path-------------'
files = os.listdir(path)
covid_twitter_data = pd.DataFrame()
# Concat the Twitters data into one-table
for file in files:
    data = pd.read_csv(str(path) + file)
    covid_twitter_data = covid_twitter_data.append(data, ignore_index=True)
```


## The Visualizations
1. [Twitter Trending Topics & Emotions](https://public.tableau.com/profile/jessica4482#!/vizhome/Book1_15869470914670/TwitterTrendsSenti)
2. [Twitter Sentiment Analysis & News](https://public.tableau.com/profile/willa.yu#!/vizhome/SentimentDashboardwithNewsTopics/Dashboard1?publish=yes)

## Analysis Framework
The framework of the data collection and analysis is shown below: 

![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/framework.JPG)
