## Project 3: Classifying between Bitcoin and Ethereum

###  Problem Statement
1. Use natural language processing (NLP) to analyze the text data in each of the subreddits,
2. Use machine learning (ML) classifiers to correctly classify the subreddit a submission is likely to originate from,
3. Evaluate the ML classifiers against our baseline model using accuracy as the key metric and,
4. Propose a suitable optimal ML classifier that could be used to develop a minimum viable product (MVP) for the chatbot and make other recommendations.

### Background Info
We work for a cryptocurrency trading platform startup company. In the recent months, the customer service team has received an increasing number of enquries on the the cryptocurrencies available on our platform. On closer look, they found that a large proportion of these enquiries are related to what those cryptocurrencies are and their applications. Faced with increasing workload and resource constraints, the head of customer service has engaged our team to develop a real time chatbot for the company website to automate the process of responding to such simple enquiries. A real time chatbot will not only enable the customer service team to focus on complex enquiries or feedback, it can also help to educate users more timely and accurately on our products and hence enhance their user experience.
 
 ###  Executive Summary
 1. The datasets was made up of the most 5000 most recently comments from both r\bitcoin and r\ethereum as of 22 July 2021, scraped using the [PushShift API](https://github.com/pushshift/api)
 2. The dataset was then cleaned, removing comments that 
	* were removed / deleted, 
	* had character_count less than 100 (majority were generic and did not add to the context)
	* were maintenance / warning comments from moderators
	* were from spam bots
	* were rogue comments from users arguing with one another

3. Further processing was done on the comments such as removing punctuation, tokenisation, removal of stopwords as well as lemmatization.
4. Next, feature extraction was done on the comments through the use of either the Count Vectorizer or the TF-IDF vectorizer.
5. 3 models fitted after a 70%-30% train-test split.  
	* Multinomial Naive Bayes
	* Logistic Regression
	* Support Vector Machine
* None of the models were selected at the end due to issues of overfitting or underfitting
 
### Data Dictionary


|Feature|Type|Description|
|---|---|---|
|author|text| username of author| 
|link_id|text|id of thread containing comment| 
|parent_id|text|id of comment replied to 
|num_awards|int|awards awarded to author. More info [here](https://reddit.zendesk.com/hc/en-us/articles/360043034132-What-are-awards-and-how-do-I-give-them-)| 
|score|int|score assigned to comment| 
|permalink|text|url link to the comment 
|subreddit|text|subreddit the comment belongs to| 
|body|text|body text of the comment| 


### Findings and Conclusion

* All models tested did not fare well with the task of classifying between bitcoin and ethereum due to issues with overfitting or underfitting
* This is likely due to the low quality of the data. Although with comments, the text tend to be long, the probability of getting generic comments, with little or no signal, is high. 
    * A case in point, the removal of comments below 100 character lead to a 10% increase in accuracy!
* On the training end, this interferes with the model's learning process in identifying signals that are important for classification.
* On the testing end, the test set do not provide a good representation of reality as users who use the chatbot are often looking for something. Hence, their messages will tend to be filled with signals that will be useful for classification.

### Next Steps
* **Better Data Quality**: Moving on, we will need to tap on richer sources of data, with better data quality. For example, we could look at reddit posts or cryptocurrency news.
* **Bigger Data Volume**: we will also need to increase the time scope to at least the last 6 months. In this study, only 9 days of data was used