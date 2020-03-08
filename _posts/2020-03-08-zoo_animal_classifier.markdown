---
layout: post
title:      "Zoo Animal Classifier"
date:       2020-03-08 20:13:09 +0000
permalink:  zoo_animal_classifier
---


Since I was a kid, I've always loved animals. Whether it was visiting the zoo in a new city while on family vacation, or watching episode after episode of Animal Planet shows, animals - and our connection to them as a fellow species - have continued to fascinate and inspire me into my adult life (as nerdy as that might make me!). Thus, practicing my machine learning classification algorithm skills on a zoo animal classifier seemed like a no brainer.

This project was my first experience with a multi-variate classifier, meaning that my target variable (species class) consisted of seven different outcomes (based on class categories of mammal, bird, reptile, fish, amphibian, bug, and invertebrate). The pie chart below displays the breakdown of our 101 zoo animal species into these classifications.

![](https://github.com/huntersapienza/Zoo-Animal-Classifier/blob/master/Images/class_composition.png?raw=truehttp://)

In this project we aimed to create the most accurate multivariate classifier for 101 species of zoo animals. Throughout this project, we followed  the OSEMN (Obtain, Scrub, Explore, Model, aNalyze) data science framework. Our objectives consist of answering the following questions:

- What is the overall class composition of all the zoo animals?
- How do different models perform with regards to the greatest accuracy of class classification?
- What features most significantly influence classification of these animals?

While the data was nicely pre-processed and easy to use upon uploading, attempting to obtain a highly accurate multivariate classifier required me to further develop modeling skills that I had previously used strictly in binary classification problems. Throughout the modeling process, I created the following classifiers in my attempt to find the best fit: linear regression, decision tree (with and without gridsearch optimized parameters), k-nearest neighbors, SVC (with and without PCA-transformed features), bagging, and random forest.

Throughout my first round of models, I obtained fairly high accuracy ratings across the board, with nearly all models performing above 90% for both the training and test sets. For some models, the training set accuracy was even 100%, although the predictions for the test set would misclassify one or two animals each time. When I analyzed these results, it was usually some combination of the same animals that were misclassified: tortoise, seasnake, or newt. In most cases, they were misclassifed into that class that shared many characteristics with their actual class, such as eggs for both reptiles and birds, or lack of legs for both snakes and fish. While I was satisfied with the results, I wondered if further modeling could uncover a way to properly classify these common sources of error.

Upon running through the features once more, I realized that the 'legs' feature, classified as an integer type, and treated as such throughout the modeling process, might be better suited as a categorical variable, separated into additional features using one-hot encoding. When I altered the treatment of this feature in our 'X' dataframe and ran through the models once more, I found that, with the exception of only a couple models, we were able to obtain 100% accuracy for both the training and test sets!

While the logistic regression, decision tree, support vector classifier, and random forest models all obtained a 100% accuracy score for both the training and test sets, the decision tree and random forest classifiers allowed us to best visualize the importance of each feature in the classification process.

![](https://github.com/huntersapienza/Zoo-Animal-Classifier/blob/master/Images/decision_tree_vizualization.png?raw=true)

The decision tree model above reveals that 'milk' is the primary feature allowing us to classify zoo animals. The bar chart of random forest features below provides additional evidence to support this argument as well. This makes sense, as the ability to produce milk distinctly separates mammals from the other classes of animals. Thus, 'milk' serves as the root node for our decision tree model. For the next decision node, the model splits any animals that have two legs, placing these in the terminal node for the class 'bird'. With the exception of some mammals (already split via 'milk') and birds, all other classes of animals have more than two legs, or zero legs. 'backbone' is the final primary decision node in our decision tree model, allowing for the separation of bugs and invertebrates from fish, reptiles, and amphibians. After this node, different combinations of a few features allows for the accurate classification of animals from each of these five remaining classes.

In addtion to our decision tree map, the feature importance in our random forest model illustrated below provides a different perspective on those predictors that are most significant. While 'milk' still claims precedence over the model, 'hair', 'feathers', and 'eggs' rise to higher significance than those that we observed as most important in our decision tree. The first two of these features tend to characterize exclusively mammals and birds, respectively, while eggs characterize a much larger number of classes (birds, amphibians, reptiles, bugs, and fish).

![](https://github.com/huntersapienza/Zoo-Animal-Classifier/blob/master/Images/random_forest_top_features.png?raw=true)

Ultimately, this project proved extremely successful in two regards: (1) the high accuracy scores of several different classfier models, and (2) the experience gained in multivariate classification. Based on the models produced, we were able to analyze the features of top importance in classifying zoo animals, and identified some signifcant trends that closely correlated to our knowledge of class characteristics.

Future work of importance would involve expanding the number of animals involved in the modeling process, or including classfication models not only for animal classes, but also for the specific families within each class as well. This work closely aligns to that of evolutionary biologists and can both support preexisting work with regards to taxonomy, as well as expanding our understanding of the entire animal kingdom (the human race included!).
