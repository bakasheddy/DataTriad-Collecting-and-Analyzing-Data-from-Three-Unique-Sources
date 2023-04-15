# <center>DataTriad: Collecting and Analyzing Data from Three Unique Sources</center>
### <center>by</center>
## <center>Shedrack David</center>

## Dataset Overview

WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. WeRateDogs has over 4 million followers and has received international media coverage. we will wrangle 3 different data from this account for our analysis.

the wrangled data from the twitter_archive_enhanced.csv data has 2356 row and 17 columns holding values for

- tweet_id	
- in_reply_to_status_id	
- in_reply_to_user_id	
- timestamp	source	
- text	
- retweeted_status_id	
- retweeted_status_user_id	
- retweeted_status_timestamp	
- expanded_urls	rating_numerator	
- rating_denominator	
- name	
- doggo	
- floofer	
- pupper	
- puppo

the second dataset(image-predictions.tsv) contains 2075 rows and 12 columns holding information on

- tweet_id	
- jpg_url	
- img_num	
- p1	
- p1_conf	
- p1_dog	

the third and final dataset, i used tweepy(tweeter's API) to gather data from the WeRateDogs tweeter account, first, i added my personal tokens for authentifications then i looped through each tweet id in the twitter_archive_enhanced.csv file; for each id, i used the get_status and json.dump method to download the data in a new line everytime in json format, after this i opened the json as a txt file and created a dataframe for it conatining 2327 rows and 4 columns holding information on

- tweet_id
- created_at
- favorite_count
- retweet_count



## Objective
 For this project, i want to gathered three pieces of data and loaded them in the notebook. The methods used to gather each data was different. 
 - I directly download the WeRateDogs Twitter archive data (twitter_archive_enhanced.csv) which was provided by udacity.com 
 - I used the Requests library to download the tweet image prediction (image_predictions.tsv)
 - I used the Tweepy library to query additional data via the Twitter API and stored this data in newline for each tweet(tweet_json.txt)
 
 ## Dataset Issues
 #### Quality issues
 
 these quality issues cuts across all three datasets
 - Missing names in name column
 - wrong data type of timestamp column
 - Null values in expanded_url column
 - wrong date type on created_at column
 - Null values in in_reply_to_status_id and in_reply_to_user_id columns
 - Bad datatype for tweet_id
 - Bad column names 
 
 #### Tidiness issues
 - the dog stage is one variable and hence should form single column. But this variable is spread across 4 columns - doggo, floofer, pupper, puppo.
 - Information about one type of observational unit (tweets) is spread across three different files/dataframes.
 
 ### Accessing data, cleaning and storing data

Each of the quality and tidiness issues were adressed using the methods below

- Here, I checked for data quality and tidiness and it was done both programatically using pandas functions like .info(), .duplicated(), .sample() and through observation of the data
- In tidy data each variable forms a column, each observation forms a row, each type of observational unit forms a table. i made sure all dataframe followed these rules by removing retweets from each dataframe, renaming abigious columns, changing wrong datatypes of entries to their appropraite datatype.
- Before cleaning, a copy of each dataframe's original was made using the .copy() function.
- After cleaning each data with code, i wrote a test code to check or assert that my data was clean using assert statement.
- After the entire cleaning process and merging of the three dataframes into one, gathered, assessed, and cleaned master dataset was saved to a CSV file named "twitter_archive_master.csv".

## Key insights from dataset

- dogs which got high favoite counts tend to be highly retweeted
- Although almost every dog in the tweeter account usually get high rating, the most rated stage of dogs is doggo puppo
- since favorite count is strongly correlated to ratings, we expect that doggo puppo should also be the stage of dog which has the most favorite counts


## Resources

-  <a href="https://stackoverflow.com/">stackoverflow</a>
-   <a href="https://www.geeksforgeeks.org/ ">geekforgeeks</a>


## Notes
-  the image predictions file was downloaded [here](https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv)

- the wrangled tweeter account is [WeRateDogs](https://twitter.com/WeRateDogs?s=20&t=__jBLy8rt4fu4toO3XJyXQ)
 
 
