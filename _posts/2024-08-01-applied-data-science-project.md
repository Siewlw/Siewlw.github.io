---
layout: post
author: Siew Leong Wai
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Investing in producing movies and television shows demands substantial capital investment and extensive manpower coordination. However, the reality is that not all projects achieve commercial success or profitability. 
Our team hopes to leverage machine learning techniques to discern audience preferences and trends. If successful, we can mitigate the risks of production failures. With the wealth of information now available, we aim to showcase how data-driven decisions that align closely with consumer preferences can be made, and subsequently maximize the potential for success.

Business Goal:
To be able to sustainably identify popular topics among audiences and predict the success of prospective films. 

Buisness Objectives:
1. Train a text classification model to predict the sentiment of a movie review, to automate the labeling of the sentiment for new movie reviews on IMDB.
2. Perform topic modeling on the movie reviews to uncover insights on the topics prevalent in positive reviews and likewise for negative reviews
3. Train a binary classification model to predict prospective films’ IMDB score and hence its potential popularity level
4. Train a regression model to predict prospective films’ IMDB votes and hence its potential audience engagement level

![image](https://github.com/user-attachments/assets/a9acbf7e-acff-4b99-abf4-ef034b3832a6)

Success Criteria:
1. To automate the classification of new movie reviews with an 80% accuracy
2. To identify at least 2 topics that are associated with positive sentiment
3. Predict a prospective film, at 60% accuracy rate or a normalized RMSE of 0.2 for its IMDB score and IMDB number of votes

I would be embarking on business objective #2, and attempt to identify at least 2 topics associated with positive sentiments

## Work Accomplished
I would be using topic modeling on a text dataset containing 50k reviews each tagged to a positive/negative sentiment. The Text Dataset would be obtained from: https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews. I would be performing pre-processing of the text data, followed by data transformation, and finally performing a Latent Dirichlet allocation (LDA) model to find out what topics are prevalent in positive and negative sentiments for movies. This is done in the hope of allowing movie producers to kick start their brainstorming process by narrowing down topics that viewers are interested in/have a positive sentiment with. 

Here is a brief timeline of how we collected data and eventually did our modelling
![image](https://github.com/user-attachments/assets/92e83de8-91c9-4036-9aa3-58302ad14c23)


### Exploratory Data Analysis (EDA) of text data
Data consisted of 50K rows and 2 columns. There were no empty data.
![image](https://github.com/user-attachments/assets/af93f9fb-b502-49c9-aa7b-d6c36b9bef51)

After this, we checked for duplicates and found that there were 824 duplicated reviews 

![image](https://github.com/user-attachments/assets/b8af473a-c1ea-4a17-8d3f-886e08fa28f9)



We removed duplicated rows 
![image](https://github.com/user-attachments/assets/967b2f2b-2c59-4954-bdac-9402f9120910)

### Data Preparation
Following re-processing of text data was done:
1. Converted all words to lower case and tokenised
2. Removed stop words, non-alphabetical words, and words less than 4 characters long
3. Perfomed lemmatization
![image](https://github.com/user-attachments/assets/d9334a3e-aaab-48dd-96a3-8d32bea8164b)

After this, we did a check for frequently appearing words and found that "movie" kept appearing.
We then updated our stop words to also include movie as we deemed it to be a domain stop word.

![image](https://github.com/user-attachments/assets/fc9d0eab-13cf-4a44-b001-7f1845505dad)

I then split data into positive and negative reviews so that I can perform topic modeling for each sentiment to get topics prevalent in each of the sentiments.
![image](https://github.com/user-attachments/assets/6b7143f5-0e20-4e6c-8b68-522bebb8a695)

Before embarking on the modeling, I created a bag of words for each of the sentiments.
![image](https://github.com/user-attachments/assets/9547829c-19b0-42e5-8844-9e074bccf023)

I also ran a coherence analysis to see what is the optimal number of topics to run the LDA model.
Number of topics was suggested to be 9 as the coherence score was the highest for both sentiments.
![image](https://github.com/user-attachments/assets/f1405224-52eb-4e12-9be7-009904a405f6)

### Modelling
LDA models we created for each sentiment to sieve out what are the topics prevalent
![image](https://github.com/user-attachments/assets/23bb8ad6-b715-4c68-a794-697d44b3a300)

A visualization was also done to help us have a visual aid on the topics prevalent.
![image](https://github.com/user-attachments/assets/be24cb3b-9931-4fab-b3be-6765a6ff77a1)

### Evaluation
There were still many topics that were clumped together in each of the positive and negative sentiments.
Perhaps might be good to look out for more domain-specific stop word customizations. In this case, stop words related to movie review. This would certainly improve the text preprocessing allowing for more accurate representation of topics.
It might also be better to include bigram, and trigram models to give more meaningful insights rather than just using single words for the analysis.


## Recommendation and Analysis
Based on the model, I was able to successfully identify 2 topics that are associated with positive sentiment. 
The 2 topics were related to:
1. Musical/Dance/Sinnging topics
2. Supernatural/Superhero topics
I was also able to identify 2 topics that were related to negative sentiments:
1. Religious topics
2. Family topics

With the results, we can highlight to movie writers what are the topics that they should or should not be focusing on during the preliminary brainstorming stage.
This will help them save time, money, and effort when planning, hence allowing for their attention to be channeled into other areas. 

## AI Ethics
No personal and confidential information was included in the dataset. Failure of the models ability to accurately prediction of movie/show success is not expected to bring about harm to society, albeit at the cost of the production company.
However, I do propose a human-in-the-loop arrangement as there is still a need for human decision to fine-tune and discuss what are the suitable topics for the audiences with vartious external factors kept in the decision-making process. Additional inputs needs to be collected from other sources to make a more informed and stratgic decision. This model should be intended for to support decision making, rather than to automate and draw conclusions on behalf of humans.
![Uploading image.png…]()


## Source Codes and Datasets

