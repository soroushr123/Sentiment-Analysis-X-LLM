# Twitter_Sentiment_Canada_Election
Prediction of Canadian presidential election result using machine learning techniques for data labeling, and sentimental analysis on Twitter data

<p align="center">
    <img width="800" src="https://www.acto.ca/production/wp-content/uploads/2021/09/Federal-election-blog-image.png" alt="Material Bread logo">
</p>

## 1. Project Description
The prediction of elections has been an area of interest for political scientists, data analysts, and social media experts. In recent years, social media platforms like X( previously known as Twitter) have become a rich data source for understanding public opinion and sentiment toward political parties and candidates. In this study, we aim to predict the overall outcome of the 2015 Canadian federal election based on the sentiment of the tweets. 

The goal is to label randomly chosen posts (previously known as Tweets) based on the political party that the user is writing about directly or indirectly. The Tweets were collected both from old twitter API and [Borealis](https://borealisdata.ca/), The Canadian Dataverse Ripository dataset related to 42nd and 43rd general election.

The 42nd election used to train the model by splitting data (over 250k tweets) into train-test set. After a process of data cleanup, manipulation and transformation, a portion of data labeled and used as a baseline for ensemble learning to label and categorized the rest of the tweets. 43rd election data used for final prediction step.

Finally, using logic-based VADER sentiment analysis model and RoBERTa model, a upscaled version of BERT LLM which trained on many social media texts, used to predict the sentiments on each tweets.

The aggregative results from total sentiments can provide a rough understanding of the public inclination idea of the dominant political party.
Below is the chart illustrating the process:

![image](https://github.com/soroushr123/Twitter_Sentiment_Canada_Election/blob/main/Diagram.png) 
<p align="center"> Figure 1. Overall pipeline of 2015 Canada Federal election result prediction </p>

## 2. Tech Stack
- Python
- NLTK
- Statistics
- LLM
- Visualization Tools

## 3. Modeling:
To label and categorize the tweets based on the political parties, we come up with a semi-supervised  learning solution mixed. Generally speaking, we use the name of all the parliament members of Canada and check the whole tweet text in the dataset to see which row contains which parliament member name. The idea is if a tweet contains a name, then that tweet is talking about that political party (e.g. containing Justin Trudeau, the tweet is talking about liberals) By this way, about 50K of tweets were labeled. Then we used these amounts to train an ensemble learning model to contain three separate classification models (Figure 1) to predict the label and category for the rest of the data. The trained model will be used for future analysis, of the datasets from other Federal elections of Canada (e.g. 43rd Federal election tweet data).
Once the tweets were fully labeled, we pass them through a pre-trained large language model known as RoBERTa , which is trained on over 58 million tweets for sentimental analysis, to get the sentiment of the tweet in positive, negative, and neutral values. In parallel, the sentiment of the tweets was measured using a ruled-base library known as VADER. The results of the mentioned method associated with the political party categorization for each tweet lead to the following aggregated results for public opinion:

 ![image](https://github.com/soroushr123/Twitter_Sentiment_Canada_Election/blob/main/42nd_Impression_Density.png)
<p align="center"> Figure 2. Distribution of Tweet impressions for different political Parties for the 42nd Federal election campaign period </p>

## 4. Project File Struture:
1. "Twitter_API_Data_Extraction.ipynb" is the first notethat should be run and is for the purpose of extracting data from Twitter API
2. "Parties_labels_definition.ipynb" is for processing another dataset for labeling and categorizing the tweets
3. "Data_Cleaning_and_labeling.ipynb" this note should be run after step 1 and 2 and the process of Data labeling and tweet categorization is done in it.
4. "Sentimental_Analysis_Transformer_RoBERTa.ipynb" this notebook should be run after Step 3 and it is for the purpose of sentimental analysis only
5. "Visualizations.ipynb" is should be run at the end and it contains all the visualizations


