# Twitter Raw Date
The data was retrieved by [TwitterScraper API ](https://github.com/taspinar/twitterscraper). We retrieved about 13,000 tweets each day from Jan. 20th to April 8th (80 days), using search query "#COVID2019 OR #COVID19 OR coronavirus". The total tweets we obtained is 1,100,069 tweets. The raw dataset can be found in the "Raw Data" folder.

Due to the file size limitation of Github, the combined dataset need to be found in [Google Drive](https://drive.google.com/file/d/1K6PsLctv9bALkfbGmBGNw1s6sLF9cKB9/view?usp=sharing).

Or, combine the raw datasets in local system using
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
# Twitter API Code
Besides the [TwitterScraper API ](https://github.com/taspinar/twitterscraper) we used to retrieve data, we also explored the [Twitter Standard Search API ](https://developer.twitter.com/en/docs/tweets/search/api-reference/get-search-tweets) and [Twitter Trending API](https://developer.twitter.com/en/docs/trends/trends-for-location/api-reference/get-trends-place). We did not use these two APIs due to the 7-Day limitation on request set by Twitter. Code refer to http://docs.tweepy.org/en/latest/api.html and http://socialmedia-class.org/twittertutorial.html. 

# Tweets per Day
Data retrieve from [Tweet Binder](https://www.tweetbinder.com/blog/covid-19-coronavirus-twitter/)

