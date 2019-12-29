---
layout: post
title:      "Modern Olympic Games Analysis"
date:       2019-12-29 15:42:24 -0500
permalink:  modern_olympic_games_analysis
---

For hundreds of years, the Olympic Games have existed as a cornerstone of entertainment, culture, and international collaboration. Inspired by ancient Greek traditions, the International Olympic Committee (IOC) - founded in 1894 - hosted the first modern games in 1896 in Athens, Greece. Since then, the games have evolved to include the paraolympic games for athletes with disabilities, greater gender equality with in increase in female athletes, and alternating years for the summer and winter games. Able to adapt to changes in culture, technology, and economies, the Olympic Games have strengthened their relevance and impact in our modern world, an iconic symbol of the relationships and camaraderie that exist across political borders.

For my fifth project in Flatiron's data science program, I conducted a thorough exploratory data analysis (EDA) of the modern Olympic Games from 1986 to present day. Working with data from over 200,000 athletes, I synthesized this big data into engaging and insightful visualizations that provide us with a deeper look into the impact of the Olympic Games on our society and inform us as to the direction we are headed toward in the future. For our analysis, we divided the EDA into distinct sections - gender, types of athletes, Olympic medalists, participating countries, seasonal athletes, and additional trends over time - with clear research questions to guide each separate notebook. In the introductory notebook, we scrub the original dataframe, accounting for missing values primarily in the height, weight, and age features, and save this cleaned dataframe for use in the other notebooks. Throughout the remainder of the project, we continued with the OSEMN data science framework, proceeding from the "obtain" and "scrub" stages into exploratory analysis, occasional models, and most importantly - interpretation of the results.

Across the scope of the project, we evaluated the following problem statements:
* How have Olympic athletes changed over time?
* How have the Olympic Games changed over time?
* How do the Olympic Games reflect international relations, with regards to politics, economics, and human rights?

With these key questions in mind, we sought to evaluate how the Olympic Games affect our society. The answers to these questions possess tremendous value, as they highlight the Olympics as a catalyst for social and political change, allow us to develop policies to realize the full potential of the Olympics, and provide the foundation for future predicitve work with regards to athlete performance. 

The remainder of this post provides a glimpse into some of the visualizations created, and the insights that they provided with regards to our original research questions. For the full analysis, check out the project on my GitHub [here](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis).

**Gender**

Throughout our notebook exploring gender within the Olympic Games, we focused primarily on the development of greater gender equality in the competitions. The pie chart below shows the overall gender composition of the games throughout the past 124 years, with nearly a 1:3 female to male ratio.

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-27%20at%2011.41.40%20AM.png?raw=truehttp://)

However, the following bar chart reveals that this ratio has shifted over time. While the first Olympic Games in 1896 involved only male athletes, female athletes began fighting their way into the competition, slowly at first, with a very small porportion of female contestants, but by the most recent games, we see that they have nearly achieved a 50/50 gender equitable ratio.

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-27%20at%2011.43.38%20AM.png?raw=true)

Unfortunately, this developing gender equality is not consistent for all nations across the world. The choropleth map below illustrates that some countries are leading the way in female athlete participation, while many nations fall behind, with very low proportions of female athletes throughout their histories. This appears primarily in North African and Middle Eastern nations, likely do to cultural and religious norms that allow for female oppression to persist.

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-27%20at%2011.46.07%20AM.png?raw=true)

**Types of Athletes**

The heatmaps below demonstrate the changing number of athletes per sport in the summer and winter games. Based on the shading of these heatmaps, the top summer sports (by number of participants) are athletics (track & field), swimming, and gymnastics, whereas alpine skiing, cross country skiing, and the biathlon (ski shooting) are the top winter sports. Five summer sports - athletics, cycling, fencing, swimming, and gymnastics - and six winter sports - cross country skiing, figure skating, ice hockey, nordic combined, ski jumping, and speed skating - have been featured in every version of the Olympic Games since their beginning in 1896 (1924 for the winter games).

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-27%20at%2011.56.33%20AM.png?raw=true)

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-27%20at%2012.06.05%20PM.png?raw=true)

**Country**

With regards to participating countries, we explored a variety of research questions and relied heavily on choropleth maps to visualize the results. Below, the map displays the proportion of each country's athletes that have achieved medals. As is evident by the shading across the world, a clear division exists between developed nations (particularly in North America, Western Europe, and East Asia) and developing countries (overwhelmingly in Africa, South/Central America, and Southeast Asia), with a focus on the proportion of athletes winning medals. This divide leads us to wonder whether policies can be enacted to increase the accessibility of the Olympic Games for all countries, whether by the creation of different divisons based on a country's economic status or a limit to the number of athletes that each country may send to the games.

![](https://github.com/huntersapienza/Modern-Olympic-Games-Data-Analysis/blob/master/Visualizations/Screen%20Shot%202019-12-29%20at%203.58.26%20PM.png?raw=true)

**Summary**

These visualizations provide just a small window into the analysis covered across the entire project! Some of our biggest takeaways from the full EDA include:
* Gender composition is approaching equality!
* Nearly every nation now competes in the summer games
* USA, Germany, and Russia typically dominate the competition
* Clear divide between developed and developing nations

Moving foward, the future of the Olympic Games remains uncertain with regards to the direction of IOC policy and the role the games will play in our changing international political climate. Some recommendations based on our findings are:
* Enact measures for greater gender equity in athletes from all countries
* Restructure competition to increase access for all nations, both developed and developing → increase socioeconomic equity internationally!
* Continue to utilize the games as catalyst for social and political change

My hope is to build onto this intial foundation in our exploration of Olympic Games data, possibly with additional data from the coming games, as well as more in-depth data from the past. Future work may include:
* Training models that can differentiate types of athletes and likelihood of achieving a medal
* Detecting the presence of anomalous performances to catch athletes who use performance-enhancing tactics
* Further exploring the impact of economic status on a country’s ability to compete in the Olympic Games
* Exploring the differences between medalists and non-medalists of specific sports
