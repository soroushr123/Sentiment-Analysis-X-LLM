# Twitter_Sentiment_Canada_Election
Prediction of Canadian presidential election result using machine learning techniques, data categorization, and sentimental analysis on Twitter data

<p align="center">
    <img width="800" src="https://www.acto.ca/production/wp-content/uploads/2021/09/Federal-election-blog-image.png" alt="Material Bread logo">
</p>

# Problem Statement:
The prediction of elections has been an area of interest for political scientists, data analysts, and social media experts. In recent years, social media platforms like Twitter have become a rich data source for understanding public opinion and sentiment toward political parties and candidates. In this study, we aim to predict the overall outcome of the 2015 Canadian federal election based on the sentiment of the tweets. This can only be done by properly categorizing the tweets based on the political party that they are talking about. Thus, we aim first to provide a machine learning-based technique to predict the category of each tweet based on the top three political parties of Canada (Liberal, Conservative, NDP) and estimate the public opinion from the sentimental analysis of the data for each political party. The party with the most positive sentiment shall get the most seats in the Parliament of Canada.
Background:
Twitter has over 300 million active users, and the platform generates over 500 million tweets per day. With such a vast amount of data, it is possible to analyze the sentiment of the tweets toward a particular political party or candidate. By analyzing the tweets' sentiment, we can determine the public's opinion towards a political party or candidate, which can help us predict their chances of winning the election.
In this study, we collect about 250 thousand Twitter data related to the 2015 Canadian federal election with the official election hashtag #elxn42, which was posted on Twitter during and after the campaign period (about 100 days). It is critical to be able to categorize and label the tweets based on the purpose of the research. As the goal of this research is to predict the overall outcome of the election and the most-desirable political party, we use machine learning algorithms and natural language processing (NLP) techniques to perform data labeling (to measure which tweet is talking about which political party) and sentimental analysis on the tweets to get the public opinion. This topic is important and can be helpful for the following reasons :
* Social media analysis is a new field that can provide insights into public opinion and sentiment.
* Findings can have practical implications for political campaigns by helping them develop more effective social media strategies.
* Applying machine learning to real-world data can help develop more accurate models for predicting election outcomes.

# Dataset Detail:
The dataset for this project containing about 250 thousand rows of raw data is collected through the official Application Programming Interface (API) of Twitter. The list of all tweet IDs for the 42nd Federal election of Canada with the official hashtag was provided on the Canadian Dataverse Repository  website. About tweets were randomly selected from the list of IDs. The model for data labeling is only trained on the 42nd Federal election dataset.
The same information has also been collected for the 43rd Federal election as another test dataset to see if the model can still provide correct overall public opinion on another Federal election campaign.

![image](https://github.com/soroushr123/Twitter_Sentiment_Canada_Election/blob/main/Diagram.png) 
<p align="center"> Figure 1. Overall pipeline of 2015 Canada Federal election result prediction </p>

# Data Cleaning and Preprocessing:	
Twitter data can be noisy and unstructured, making it challenging to analyze accurately. Data cleaning is, therefore, necessary to reduce noise and ensure that only relevant information is used for analysis. The major steps for the cleaning process of this project are lowercase the text, removing URLs and HTML tags, dealing with hashtags, etc. (More technical details are available in the notebooks).
The feature extraction is done through machine learning techniques for data categorization and tweet labeling (based on the political parties) and sentiment analysis which helps us in the final data aggregation, visualization, and prediction of the outcome. At a glance, the following overall features were added to the data dataset:
* Sentiment Scores
* Political party labels for each tweet
* A normalized version of quantitative features
* Impression of each tweet based on the sentiment score and other features

# Modeling:
To label and categorize the tweets based on the political parties, we come up with a semi-supervised  learning solution mixed. Generally speaking, we use the name of all the parliament members of Canada and check the whole tweet text in the dataset to see which row contains which parliament member name. The idea is if a tweet contains a name, then that tweet is talking about that political party (e.g. containing Justin Trudeau, the tweet is talking about liberals) By this way, about 50K of tweets were labeled. Then we used these amounts to train an ensemble learning model to contain three separate classification models (Figure 1) to predict the label and category for the rest of the data. The trained model will be used for future analysis, of the datasets from other Federal elections of Canada (e.g. 43rd Federal election tweet data).
Once the tweets were fully labeled, we pass them through a pre-trained large language model known as RoBERTa , which is trained on over 58 million tweets for sentimental analysis, to get the sentiment of the tweet in positive, negative, and neutral values. In parallel, the sentiment of the tweets was measured using a ruled-base library known as VADER. The results of the mentioned method associated with the political party categorization for each tweet lead to the following aggregated results for public opinion:

 ![image](https://github.com/soroushr123/Twitter_Sentiment_Canada_Election/blob/main/42nd_Impression_Density.png)
<p align="center"> Figure 2. Distribution of Tweet impressions for different political Parties for the 42nd Federal election campaign period </p>

![image](https://github.com/soroushr123/Twitter_Sentiment_Canada_Election/blob/main/42nd_cumulative_sum_impression.png)
<p align="center"> Figure 3. The cumulative sum of impressions over the 42nd Federal election campaign period </p>

# Conclusion:
The above Figures illustrate that the Density of positive impression and cumulative impression (public opinion) is inclined to the Liberal party in the 42nd Federal election both in the train set and set, which aligned well with the official results. The model also performs properly on 43rd Federal election data with more details in the notebook.
On the other hand, are also some potential drawbacks to this approach that need to be addressed and studied in future projects and research. Some of these drawbacks include:
* Limited sample size: Twitter data is a small subset of the population, and therefore, the analysis results may not be representative of the broader population's sentiment towards political parties and candidates.
* Bias in the data: Twitter users may not represent the broader population, and the analysis results may be skewed by the demographics of Twitter users.
* Difficulty in predicting election outcomes: While social media data analysis can provide insights into public opinion, predicting election outcomes is a complex task that requires consideration of several other factors beyond sentiment analysis.
