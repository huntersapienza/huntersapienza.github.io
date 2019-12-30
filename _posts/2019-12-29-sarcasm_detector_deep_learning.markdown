---
layout: post
title:      "Sarcasm Detector: Deep Learning"
date:       2019-12-30 02:35:21 +0000
permalink:  sarcasm_detector_deep_learning
---


Sarcasm is defined to be "the use of remarks that clearly mean the opposite of what they say, made in order to hurt someone's feelings or to criticize something in a humorous way" by The Cambridge Dictionary. Used for a varitey of purposes in the media, sarcasm can portray strong opinions and extreme perspectives of current events to provide comic relief and culturally-relevant dialogue.

The dataset utilized in this project derived news headlines from two sources: (1) TheOnion for sarcastic articles, and (2) HuffPost for non-sarcastic articles. The objective of this project was to explore characteristics of our headline data overall, as well as in the context of sarcastic and non-sarcastic subsets. Furthermore, we attempted to develop deep neural networks and other classifiers that provide accurate classification models for determining whether a given headline is sarcastic or not. In order to fulfill these objectives, we focused on the following two problem statements:
* What keywords differentiate sarcastic and non-sarcastic article headlines?
* Which classification model performs most accurately in predicting sarcasm within headlines?  

This project and the subsequent models developed provide relevant information about how to distinguish between real news and fake news in a world increasingly characterized by mass amounts of news every second of every day. As our society becomes more and more polarized and partisan in our efforts to enact policies and reach solutions for the many issues that plague our world, it becomes increasingly necessary to sort out fact from fiction. Thus, further work of importance may include expanding these models and data exploration in attempts to determine the level of objectivity and bias in a given headline, somewhere on a scale from perfectly factual to perfectly sarcastic.

Throughout the scope of the project, we followed the OSEMN data science framework. For this project, we obtained our dataset from Kaggle. The author of the dataset asserted the importance of a sarcasm dataset utilizing news headlines devoid of the excess noise present in many prior works drawing upon twitter for the presence of sarcasm. Additionally, news headlines are far less likely to contain grammatical and spelling errors, and do not necessitate additional context to tease out sarcastic elements. We pre-define two distinct groups by pulling sarcastic articles from the Onion and non-sarcastic asticles from Huffpost. The articles within our dataset come from actual news published within the past year, and thus reflect cultural trends important and relevant to our current society. Though no missing values existed within the dataset, it was necessary to conduct additional processing procedures in order to make best use of the headline titles. By tokenizing the headlines and removing all superfluous stopwords, we were able to conduct the most insightful EDA and modeling process.

**Headline Characteristics**

While we conducted a variety of exploratory data analysis - concerning primarily the volume of the tokens as well as the most frequent tokens, bigrams, and trigrams - we found that the bigram analysis revealed the most interesting insights about the headline data.

The pie chart below, created during our EDA, shows the composition of our dataset.
![](https://github.com/huntersapienza/Sarcasm-Detector/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%207.23.13%20PM.png?raw=true)

*All Headlines*

Across all headline bigrams , we noticed the following remarkable trends:
* "donald trump" appears most frequently; while we as American citizens witness the immense presece of news about our current president on a daily basis, the dominance of his name reflected within the data is truly baffling.
* The following bigrams reflect important current political trends (listed in order of frequency): "white house", "hillary clinton, "supreme court", "bernie sanders", "ted cruz", "paul ryan", "mike pence", "trump administration", "fox news", "jeb bush", "marco rubio", and "michelle obama".
* Key social issues: "climate change", "health care", "sexual assault", and "mental health"
* Cultural trends: "taylor swift", "social media", "super bowl", "star wars", and "game thrones"
* Places of interest: "new york", "north korea", "middle east', "north carolina"

While I identified these categories and lists using my best judgment, other methods of classifying these bigrams are welcome. However, it appears that political themes dominate our new headlines, with several key social issues emerging as most frequent. This may be skewed by the news source, as HuffPost is much more likely to cover political issues than those of pop culture. However, despite that bias, Taylor Swift still appears in the top half of the list, indicating her dominance in our cultural arena, at least during the time at which these article headlines were obtained. The places mentioned in our list indicate important trends within 21st century foreign policy, as our country continues to focus substantially on our relationship with North Korea and the Middle East. Domestically, New York and North Carolina emerge as epicenters of political and social relevance (on both sides of our political lines), as they have for much of the past decade.

*Sarcastic Headlines*

In sarcastic headlines specifically , the following bigrams emerged as most insightful:

* Political trends: "white house", "supreme court", "hillary clinton", "pope francis", "paul ryan", "mike pence", "john kerry", "ted cruz", "jeb bush", michelle obama", "tim kaine", "bernie sanders", "bin laden", "john kelly", "secret service", "kim jong-un", "mitt romney", and "queen elizabeth".
* Common sarcastic tropes: "area man", "study finds", "introduces new", "area woman", "new study", "unveils new", "releases new", "local man", "report finds", "area dad", "poll finds", "majority americans", "announces plans", "first time", "new line", "average american", "report majority", "report americans", "last night"
* Social/Cultural trends: "video game", "climate change"
* Places of importance: "new york", "north korea"

Many of the same bigrams appear in our sarcastic headlines as in our overall headlines dataset. Within the list of politically-relevant bigrams, many minor political figures appear that (in my opinion) would otherwise be absent from the real media. However, I expect that some bigrams for people in sarcastic articles will also appear in the list of bigrams for real news, including Hillary Clinton, Bernie Sanders, Ted Cruz, and others important within the non-sarcastic news headlines of recent years.

The list of common sarcastic tropes sheds light on the nature of satire, particularly within the Onion. Most of these bigrams represent a vague generality that allows the headlines to be more relateable and applicable to a wide variety of people. They avoid focusing on a specifc place or person in order to instead illuminate specific cultural, political, and social trends that may be relatable to the vast majority of Americans, despite our differences in geographic area, political leanings, or educational background. Many of these bigrams emphasize the hyperpole used in satire, with the words "new", "majority", and "average" appearing many times. The satirical certianty of the Onion emerges within the tokens "study", "poll", and "report". These common themes weave themselves throughout the majority of satire, and coupled with references to widely-known key political figures and social issues, sets their newspaper up for success as a related source for a diverse audience.

*Non-Sarcastic Headlines*

In real news headlines, the following bigrams appear most frequently:
* Political trends: "donald trump", "hillary clinton", "white house", "supreme court", "bernie sanders", "ted cruz", "trump administration", "pope francis", "steven colbert", "trevor noah", "paul ryan", "fox news", "marco rubio", "mike pence", "roy moore", "joe biden", "chris christie", "elizabeth warren" (my girl woop woop!),
* Places of interest: "new york", "north korea", "north carolina", "puerto rico"
* Key social issues: "health care", "climate change", "sexual assault", "mental health", "travel ban", "planned parenthood", "gun violence"
* Cultural trends: "taylor swift", "kim kardashian", "social media", "super bowl", "james corden", "star wars", "chrissy teigen", "funniest tweets", "kylie jenner", "red carpet", "box office"

Much of the same trends emerge here in real news as we observed in the bigrams for overall headlines. Key differences or additions include:
* Smaller key political figures that had brief surges within the news due to key political events, or in the case of Elizabeth Warren, those who have since the of these headlines obtained a much greater news presence.
* Additional key social issues including planned parenthood, the travel ban, and gun violence
* More pop culture figures such as Kim Kardashian, Kylie Jenner (rise and shine!), Chrissy Teigen, and references to awards shows (red carpet, box office)
* The substanial impact of social media (also "funniest tweets") on the cultural character of our society

**Modeling the Data**

*NLP Classification with Word Embeddings*

To create foundational classifier models from which to work, we utilized word embeddings in attempts to create word associations based on the GLoVE (Global Vectors for Word Representation) model created by the Stanford NLP Group. As this model has been trained based on massive datasets beyond the scope of our headline data in this project, we are able to draw upon vast amounts of word associations that improve the performance of our Word2Vec models within our relatively small dataset here. Word embeddings allow us to train a neural network that takes into account the semantic meaning between words within the high-dimensional embedding space, based upon their relative positions in the vector space. Once we have  created this baseline embedding space, we can apply the word embeddings and their semantic associations to our present dataset. The results below show the accuracy of models created using pipelines that utilize this Word2Vec vectorizer and create optimal (hopefully!) classifiers using decision trees, logistic regression, and support vector machines.

![](https://github.com/huntersapienza/Sarcasm-Detector/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%207.36.38%20PM.png?raw=true)


As we can see above, all three classifiers created using Word2Vec vectorization preformed very well for initial models! We find above 70% accuracy for all three in predicting whether or not a headline is sarcastic. Moving forward, our goal was  to create recurrent neural networks that would perform with even higher accuracy.

*Recurrent Neural Networks*

Recurrent neural networks (RNNs) are vital to modeling with NLP because RNNs rely primarily on sequences to make predictions, and the sequence of our words is integral to every language function. Thus, within the structure of a RNN, an output from a given point will be passed into the next point as an input, as each point in our process is dependent on those points around it.

To start, we created a deep neural network (DNN) that made use of embedding information similar to that of the previous models. After importing all the necessary packages and processing the data as needed for the models, we created and initial structure of this DNN below. After the input layer, we added an embedding layer with dimensions corresponding to the specified size of our vocab and the chosen embedding size. Once our data has passed through an embedding layer, we fed this data into a LSTM/GRU layer, followed by a Dense layer, followed by output layer. We also added some Dropout layers after each of these layers, to help fight overfitting.

Once we designed our model, we still had to compile it, and provide important parameters such as the loss function to use ('binary_crossentropy', since this is a binary classification problem), and the optimizer to use. Following these specifications, we observed a summary of the model and prepare to train/test our network classifier. In our project, we create both a LSTM and GRU model to see if either performed better than the other, and hopefully, better than our baseline models from before. Both LSTMs and GRUs function by remembering the important information and forgetting anything that it deems irrelevant to the context of the tokens (take the best and leave the rest!). Since neither is necessarily superior to the other, we will tested both and evaluated the results!

![](https://github.com/huntersapienza/Sarcasm-Detector/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%209.29.41%20PM.png?raw=true)

![](https://github.com/huntersapienza/Sarcasm-Detector/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%209.29.49%20PM.png?raw=true)

Unfortunately based on the results of both our models (the LSTM model results are shown above), neither performed better than the other, and they seem to be relatively ineffective in predicting whether or not headlines are sarcastic, as less than 50% of the predictions are correct. Thus, we tested whether a final type of RNN model would perform better instead.

*Bidirectional Sequence Models*

One flaw within the RNN models tested above remains their reliance on the forward sequence of data. Sometimes, words may indicate different messages based upon the tokens that follow them, but our prior RNN models cannot see into the future. That's where bidirectional sequence models come in hand! Instead of solely focusing the forward sequence, the model's neurons are split in half, with one group analyzing the forward sequence and the other charting the reverse. Thus, our model can gather a more comprehensive understanding of our text when making predictions, and this allows it to perform much better with more complex language processes such as speech recognition and even sarcasm!

![](https://github.com/huntersapienza/Sarcasm-Detector/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%207.28.49%20PM.png?raw=true)

When we fit, train, and validate our bidirectional sequence model, run on 5 epochs, we achieve accuracy scores of approximately 86% and 82%, for the training set and validation set, respectively. Run on our test set as well, this high level of accuracy is maintained at 82.3%. These results are shown above. Thus, our birectional sequence model provides the most effective predictions of sarcasm within headlines.

**Summary**

Within our exploration of over 26,000 article headlines, we discovered the following:
* Our dataset was comprised of 43.9% sarcastic articles and 56.1% non-sarcastic articles.
* Across all headlines, there were over 280,000 tokens and over 29,000 unique tokens.
* Trump, Obama, and Clinton were the most mentioned people across all article headlines.
* References to men were 3x as likely as references to women.
* Climate change, health care, sexual assault, and mental health were the top social issues.
* Most of the sarcastic bigrams represent a vague generality that allows the headlines to be more relateable and applicable to a wide variety of people.
* New York and North Korea are the most frequently mentioned places.
* Donald Trump appears in nearly all the top lists of words, bigrams, and trigrams.

When modeling the data, we found:
* Baseline models utilizing Word2Vec vectorization and word embeddings performed well, with over 70% accuracy.
* LSTM and GRU models using RNN structure performed poorly, with under 50% accuracy.
* Our bidirectional sequence model performed the best, with 82.3% accuracy for the test set, after training the model on the train and validation sets.

**Future Work**

Future work within this field may involve training models that are able to differentiate between real news and fake news. While the validity and objectivity of news remains a matter of opinion, no matter which way you lean, our media has become more and more subjective and influenced by bias, whether from those biases of the brodcasting network or the ways in which technology employs as usage data to feed us content that further supports our preexisting beliefs. These practices further fortify the political barriers that divide our nation, and thus, measures that aide in the transparency and true objectivity of the state of our government and society will enable us to properly tackle the issues that we face in the 21st century. While our project here scratches the surface of language processing and NLP data management, the possibilities for future work within this arena are endless.
