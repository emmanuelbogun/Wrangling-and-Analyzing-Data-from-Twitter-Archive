# Wrangling-and-Analyzing-Data-from-Twitter-Archive
This project involves gathering, wrangling and analyzing data from the archives of a twitter account called WeRateDogs, a page that rates peoples dog in their tweets. 

The data wrangling process involves:
- Data Gathering
- Assessing Data
- Data Cleaning

## Data Gathering

Here the three datasets were gathered from the provided sources and converted into a Pandas DataFrame.
- I was provided with the archive of WeRateDogs tweets that stored in a csv file('twitter-archive-enhanced.csv'), so I downloaded it manually and loaded it into a Pandas DataFrame, **df_archive**.
- The url to the tweet image predictions('image_predictions.tsv') was provided, so I downloaded the file programmatically by passing the url to the get() method of the request library. This was also loaded into a Pandas DataFrame, **df_image**.
- The third dataset was gotten by querying Twitter API with the tweepy library. Using the tweet_id from the first dataset, I was able to get retweet count and favorite count in a JSON file, 'tweet_json.txt' and needed tweet information were accessed like a dictionary. Then it was loaded into a DataFrame, **df_tweets**.

## Assessing Data

Each of the datasets were assessed manually and programmatically. Both quality and structural issues were checked for and duly noted. 

## Data Cleaning

The quality and structural issues observed during the assessment were then corrected by following the steps below:
<br> **1.** First of all, the cleaning process to be used were described using simple words</br>
<br> **2.** Then followed by programmatically using codes to effect the described steps to make the data ready for analysis.</br>
<br> **3.** Finally, several tests were performed to confirm if the issues have been truly corrected.</br>


**Quality Issues and actions taken in cleaning them**

*Dataset 1 - df_archive*

- Timestamp is a string; so the datatype was changed to datetime.
- Tweet source  is not visible enough; it was extracted from the url.
- Only original tweets are needed for our analyses; so the retweeted tweets were dropped.
- Rating_numerator contains erroneous values; they were replaced with random numbers between 11 and 14.
- Rating_denominator contain different values; so I standardized all to 10.
- The name column contains some inappropriate name; these names were dropped from the dataset.
- The name column has some values as None; they were replaced with null values.
- The doggo, floofer, pupper amd puppo columns contained 'None'; the 'Nones' were replaced with null values.
- Some of the columns are not needed for our analyses; so I dropped them. 

*Dataset 2 - df_image*

- Contain unwanted columns; the column(s) were dropped.

**Structural Issues and actions taken in cleaning them**
- In **df_archive** dataset, the various stage of dog (doggo, floofer, pupper and puppo) are variables so they were unpivoted and stored as records under one column named  dog_stage.
- The timestamp column in the **df_archive** dataset was split into months and years columns.
- The **df_archive**, **df_image** & **df_tweets** datasets was merged into one DataFrame.
