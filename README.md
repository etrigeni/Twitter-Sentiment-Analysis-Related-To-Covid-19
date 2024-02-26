# Twitter-Sentiment-Analysis-Related-To-Covid19

The project was held in mid-2022 where Covid was still a trending topic on Twitter. People expressed their opinions both generally about vaccines and specifically about the 3 popular vaccines (Pfizer, Moderna, AstraZeneca). The goal of this study was to classify people who are in favor or against vaccination, as well as people’s preferences for these three types of vaccines.



**METHODOLOGY**

**1. Data Collection:**

Tweets related to Covid-19 Vaccination collected from 13 April 2022 to 16 May 2022. They imported from the Twitter using the API keys provided by the Twitter Developer Account. **Python** and the library **Tweepy** were determinant in order to retrieve them. Data in the form of raw tweets is extracted by specifying keywords to search for in the tweets. Defining a function named get_Tweets(keyword) and calling it thirteen times with the keywords: “#vaccine”, “#GetVaccinated”, “#CovidVaccine”, “#Pfizer”, “#antivaxx”, “#Antivax”, “#antivaxxers”, “#Covidiots”, “#VaccineSideEffects”, “#Moderna”, “#AstraZeneca”, “#COVID19Vaccination” and “#VaccineDeath” a dataset of 54850 tweets was created with aim to implement this study.


**2. Data Storing**

After collecting these data and merged them into a panda’s data frame, we saved it in a pickle file just to be sure that we don’t lose our data. Then, we connected with MySQL and created a database to store our twitter data. A cursor object is created allowing us to execute SQL statements. We used df.to_sql() command to insert the data into the correct table in our database using the sqlalchemy library. The columns “hashtags” and “urls” were converted from lists to strings, so as to be inserted correctly in the database table.


**3. Data Preprocessing**
      
      1)Removing duplicate tweets in case the same tweet was posted multiple times accidentally or we could define the tweet_id as primary key to prevent duplicates.
        
      2)Converting datetime to date for the columns “created_at” and “account_creation_date” of our data frame.
        
      3)Expand Contractions. They are words or combinations of words that are shortened by dropping letters and replacing them by an apostrophe. It is a useful preprocessing step as the words play an important role in sentiment analysis
        
      4)Applying lowercase which means convert all letters to lower case.
        
      5)Removing URLS, user’s mentions, hashtags, punctuations, digits & emojis using regular expressions, since those terms don’t really provide meaningful context for discovering inherent topics from the tweet.
        
      6)Removing stop words, which are basically a set of commonly used words that don’t contribute much to the machine learning model. This allows us to focus on the important words instead.
        
      7)A necessary Natural Language Processing (NLP) technique that we used is Tokenization. It is the process of breaking down a tweet into words.
        
      8)Another significant Natural Language Processing (NLP) technique was Lemmatization. It is a method that converts words to their lemma or dictionary form by using vocabulary and morphological analysis of words. To achieve an effective lemma or root meaning of the word using WordNetLemmatizer, it is really important that the input word must be passed in lower case to the WordNetLemmatizer algorithm to achieve accuracy.
  
  
  **4. Sentiment Analysis:**
  
Three Lexicon-Based methods (TextBlob, Vader and Afinn) were used to find the polarity of the text (positive text, negative text, neutral text). They have differences in the way they calculate the polarity scores of a text, which makes them have different results. An exhaustive comparison of these three methods was applied.


**5. Vectorization of the tweets** : 

TF-IDF word embedding approach was used.



**6.Data Splitting**:

The next step was to split the dataset into training and test sets. 80% for training set and 20% for testing was chosen after running multiple variations of these percentage thresholds and checking the output results.


**7.Models Training – Classifier Selection – Models Evaluation:**

For the training of the Machine Learning models, the labeled tweets dataset, that was created from the three different Lexicon-Based approaches, was used. The TF-IDF features were extracted from the labeled dataset and the performance of the following prominent classifiers was reviewed in our research. More specifically, the experiments were performed using TextBlob, AFINN and VADER sentiments as target classes with the selected Machine Learning models to determine the best method in terms of accuracy, precision, recall and F1 score.
