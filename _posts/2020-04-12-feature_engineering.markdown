---
layout: post
title:      "Feature Engineering"
date:       2020-04-12 20:15:19 +0000
permalink:  feature_engineering
---

This week, I started a new project by joining the [open Kaggle competition](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview) for housing price predictions via regression analysis for residential houses in Ames, Iowa. Housing analysis continues to be a topic that I find deeply fascinating, as it draws on my passion for economic and human geography, the topic of much of my undergraduate work. This the first active competition I have joined, as opposed to simply pulling datasets from Kaggle for use in Flatiron School curriculum projects and for personal use, so I was excited to get started!

However, the competition emphasized the focus on **feature engineering**, and while I felt this encompassed much of the material I learned at Flatiron School, I found myself wondering what exactly this term refers to. Does it mean creating new features of interest from existing variables in a dataframe? Is it the practice of scraping the internet for relevant data and creating dataframe features nearly from scratch? Or is it more simply the practice of filling missing values and removing irrelevant features in efforts to mold dataframes into their most usable format? As we will see below, the answer is a resounding *Yes!* to all of the above.

![](https://github.com/huntersapienza/Blogging/blob/master/Feature%20Engineering/3.jpg?raw=true)

**Feature engineering** is a general term that applies to a whole collection of data science practices encompassed with the first two steps of the OSEMN data science framework, obtaining and scrubbing the data. Medium writer Amit Shekhar describes it as "the process of transforming raw data into features that better represent the underlying problem to the predictive models, resulting in improved model accuracy on unseen data." While oftentimes tedious and not as sexy as other aspects machine learning modeling and analysis, the quality of feature engineering conducted dictates the quality of the subsequent models created, and thus, is an essential - if not *the* essential step - in the data science process. As the dataset used for the Ames housing analysis was previously prepared by and obtained from another Kaggle user, the feature engineering completed focused primarily on the scrubbing phase, ensuring that the quality of the data is sufficient for further use in the exploratory and modeling phase.

In efforts to learn more about feature engineering specifics, I turned to [The Hundred Page Machine Learning Book](http://themlbook.com), my go-to resource for accurate, succinct information on all things data science. The section of the book dedicated to feature engineering divides the concept into six sub-topics: one-hot encoding, binning, normalization, standardization, dealing with missing features, and data imputation techniques. Using these categories as a foundation, I'll summarize some of what I've learned about feature engineering below:

**One-Hot Encoding**

This vital step of feature engineering transforms categorical variables into additional features, with one boolean variable for each category in the original variable. This enables our models to treat each category as a separate feature, in order to analyze its impact individually in our modeling process. For example, in the Ames housing dataset, the categorical variable 'SaleCondition' will eventually be one-hot encoded into separate feature vectors for each category: Normal, Abnormal, AdjLand, Alloca, Family, and Partial. These six separate features will make it easier for each model to extract the individual influence of each category on the target feature, 'SalePrice.'

**Binning**

Binning refers to the transformation of a numeric feature into a categorial one, through the process of grouping (or *binning*) the numeric data into specific ranges, i.e. 0-5 yrs old, 6-10 yrs old, 11-19 yrs old, etc. for the numeric feature age. Once binned, this categorical variable is often one-hot encoded additionally prior to the modeling process.

**Normalization and Standardization**

The next two aspects of feature engineering are often considered together, as they involve a similar process. Both take pre-existing features and simply transform their ranges to make them more suitable for modeling, as well as more comparable to other features in the dataframe.

We'll start with the latter of the two: standardization. Regression models especially thrive on normally distributed variables, and thus, standardization refers to the process of recasting the values of a specific feature so that it has a standard normal distribution, instead of the skewed distribution it often has initially. This allows our model to work more quickly, and oftentimes, more effectively in predicting our target variable. Standardization for a given variable is achieved by utilizing the following formula for each value of the feature: std value = (value - mean) / standard deviation.

Normalization requires a similar process, but results in the conversion of a feature's values so that they have the range of [0, abs(1)]. Depending on the original values this range is typically either [-1, 1] or [0, 1]. The purpose of normalization is so that features with oftentimes drastically different magnitudes of value (given the context of each feature) are more comparably weighted in our modeling process. Thus, slight changes in one feature do not more significantly influence the outcome of our model simply due to increased vulnerability to these changes given a more narrow range of values. When each feature possesses a similar range, our model can more accurately compare the influence of each feature, and our learning speed is drastically increased. Normalization for a given variable is achieved by utilizing the following formula for each value of the feature: normal value = (value - min) / (max - min).

**Missing Features and Data Imputation Techniques**

The process for dealing with missing features is much less defined than the aforementioned methods of feature engineering. With missing features, or missing values within given features, each case must be dealt with individually, and the required code depends on the demands of the missing information. Common methods of dealing with missing information include:
* Removing examples with missing values. This is acceptable if the number of missing values is small and the number of total examples is large enough to spare some removals. However, this solution is not ideal for smaller datasets, or when a large number of examples have null values.
* Often, the null value represents key information, such as the absence of a pool in the feature 'PoolQa' in our Ames housing dataset. In situations such as this, we replace all null values using .fillna() with 'None' or another comparable value.
* Data imputation techniques refer to the process of filling null values with either an arbitrary value or an average that will not affect the original distribution of values (usually the median).

**Summary**

The above sub-topics represent a sliver of the options available to data scientists when it comes to feature engineering. The possibilities for molding the data are limited only by a coder's imagination and creativity, which makes this a daunting and rigorous process for many, and an often overlooked cornerstone of any data science project. As I continue to work through the Ames housing data regression analysis, I am eager to apply my solidified knowledge of feature engineering, and hopefully, I can prepare some promising results for a future blog post! Until then, stay safe and take care out there.

