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

## Analysis Framework
The framework of the data collection and analysis is shown below: 

![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/framework.JPG)
**IBM Watson Tone Analyzer**: We choose to use IBM's Tone Analyzer (a cloud service) to do the sentiment anlysis because it can provide 5 different tones of the text data which is more than positive-negative sentiment analysis. Through this way, we can study the tweets' emotion more specifically. The limitation of this service is that, for each account, we can only analyze 2,500 tweets/email for free, so this method cannot directly be deployed on the whole dataset we have. 

**Google BERT**: To overcome the limitation of IBM Tone Analyzer, we firstly registered multiple emails accounts and utlized the Tone Analyzer to  labeled a sample of data that we sampling randomly from the whole dataset. With adjustment and also combined with our manually labeled data, we used these data as trainning set for the Google BERT model, a state-of-art machine learning technique for classification. Compared to other alternatives, BERT requires much less time and less data to train, and yields better accuracy. It is a good fit for our case where we have limited training data.

**LDA Topic Modeling**: We leverage LDA topic modeling technique to summarise the news articles we scraped. We clustered news articles in to [9 topics](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/Topic_Modeling/LDA_fox_cnn_colab_topics.xlsx), including economical impact and political actions. Through this way, we can better understand how news articles responsed to COVID-19. 

**Limitation**: Besides the IBM's service limitation above, since evaluating a text tone is not a objective thing, the sentiment analysis we conducted is impacted by our subjectivity and the accuracy of IBM Tone Analyzer.

## The Visualizations
1. [Twitter Trending Topics & Emotions](https://public.tableau.com/profile/jessica4482#!/vizhome/Book1_15869470914670/TwitterTrendsSenti) In this dashboard, people can explore each day's Twitter Trendings and see how emotion of the tweets related to COVID-19 changed by clicking the the confirmed cases histogram or the number of tweets line. 
![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/Dashboard_pict_1.png)
2. [Twitter Sentiment Analysis & News](https://public.tableau.com/profile/willa.yu#!/vizhome/SentimentDashboardwithNewsTopics/Dashboard1?publish=yes) In this dashboard, people can see the Twitter sentiment trends and the news related to COVID-19 at the same day by clicking the tweets' sentiment line. 
![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/Dashboard_pict_2.png)
3. Word Cloud of Five Emotions in Tweets
![alt text](https://github.com/xxz-jessica/COVID-19_UCD_Challenge/blob/master/FiveEmotionsWordCloud.JPG)




