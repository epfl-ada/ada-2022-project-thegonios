# Movies: today's time machine

#### Clara Scherrer, Noémie Chillier, Nathan Decurnex, Thibaut Hennel

## Data Story
Check it out [here](https://nltibo.github.io/agency-jekyll-theme/#portfolioModal2) ! 

## Abstract
At first, when asking 'what are movies made for?', the first answer that comes to mind is 'for entertainment!'. But movies are packed in diverse sources of information and are therefore rich objects of analysis. Often, only news articles or scientific publications are considered as reliable news sources and cinema seems to belong to fiction, they do not convey reality but its representation. In this project, we would like to focus on movies that portray History. Some try to represent historical events conscientiously and others just use them as a setting for their story plots. However, by bringing the biggest events of the past century to the screen, these movies fuel the heritage of the world's memory, so we never forget the events that shaped our existence. We therefore have an interest in the when and how movies have portrayed historical events. We will dive into the plot summaries to identify historical events and perform multi-step analysis to investigate the way these were handled over time by considering the genre of the movies, the plots. 

## Research questions
1. Can we relate a given movie to specific historical periods ?
2. To what extent can we extract historical information and evidence in movies ?
3. What is the relationship between movie genre and the event it portrayed ? 
4. Are there preferred actor ethnicity, age or gender distributions to cover an event?
5. Does the way of portraying a particular event change over time ?
6. What sentiment (good or bad) do movies talking about a certain historical event convey ?
7. Are there relations and similarities between different portrayed historical events ?

## Additional datasets
Wikidata - we extracted actor ethnicities corresponding to the freebase IDs found in character.metadata.tsv.

## Methods
To identify historical events, we created lexical fields (dictionaries) relating to each event using our personal knowledge and pre-existing lists of words on the web. Each movie plot summary was then parsed through these dictionaries, the number of words they have in common with the dictionary was counted as well as their occurrences. To avoid false positives we have setted a threshold of the number of common words to accept a movie as portraying a particular event or not. We then removed the dependency of our method to the length of the dictionary or the length of the plot summary to create a fully unbiased classification (the larger the dictionary, the more words are recognized in each summary and the higher the probability of classifying it into a historical category). To do so, the sizes of each dictionary were accounted for so larger movies related to an event given by larger dictionaries would need to reach a higher threshold to be held in its historical category. Therefore, a min-max normalization of the length of the dictionaries was performed and the norms were then used as weights for the thresholds. 

Then, to confirm that our method performed a relevant extraction of historical events, we plotted the word frequencies of each of the historically classified movie plot summaries using word cloud plots. The words appearing in the plots are specific to each historical event, without necessarily being present in the dictionaries used for classification. A performance analysis of a subgroup of the data was also done, for which some movies were labeled manually as portraying WWII or not for comparison with the dictionary threshold based labeling of movies. This allowed us to get a first sense of the relevance and precision of the classification of the movie plot summaries into each predefined historical event. 

Once the features are built, simple analysis using other variables present in the data set such as movie genre, box office revenue, gender proportions or ethinicities of actors playing in movies were conducted. The additional information acquired allowed us to characterize how each historical event was portrayed through our screens, and the evolution of these features with time illustrating different generations described a historical event differently. To dive into the core feelings of historical movies, engineered variables were built to explore which sentiments or values were expressed in films. History encapsulates themes which expose the human condition, our feelings, weaknesses, triumphs, and tragedies. Therefore, the sentiment analysis of movie plots relating to the major historical events presented, was done to understand if a given event was associated with a specific sentiment. 

Then, we searched for and attempted to identify the similarities between each historical period. The cosine distances between the mean TF-IDF vector representation of the movie plot summaries associated with each historical event were computed to quantify how far each historical movie summary embedding is from the others. To observe the correlation between the events, a three dimensional PCA was built, using each movie as a data point. 

Finally, a LDA topic analysis was performed on the labeled movies, to see if the historical events defined using the dictionaries were detected as the dominant topics for the movies categorized into each historical event. 

To summarize:
1. Data exploration and preliminary anaylsis
2. Historical event dictionary definitions
3. Unbiased threshold determination
4. Dictionary relevance assessment: word cloud plots and performance analysis (presion/recall)
5. Historical event characterisation (genres, box office revenue, number of movies, sentiment analysis)
6. Similarity and corrolation analysis between movies representing historical events (cosine distance, PCA)
7. Topic detection in labeled movies (LDA)

## Timeline
- 18.11.22 : Milestone P2, initial analysis and data handling/exploration pipeline. <br>
- 25.11.22 : Creation and testing of dictionaries of historical events of interest. <br>
- 02.12.22 : Homework 2. <br>
- 09.12.22 : Final plots, datastory planned on paper. <br>
- 18.12.22 : Datastory elaboration using plots, start design of the website and verify the notebook. <br>
- 23.12.22 : Milestone P3, full datastory and notebook submitting. <br>

## Milestones
1. Milestone P2, initial analysis and data handling pipeline. <br>
2. Define the historical periods/events of interest
3. Create the corresponding dictionnaries and test their specificity
4. Assess the quality of the dictionnaries
4. Create main datastory graphs
5. Try out sentiment analysis to identify and characterise historical events
6. Cross analysis between historical events
7. Create website for the datastory
8. Milestone P3, full datastory and notebook submitting

## The Gonios team member contributions
Clara: first analysis, world cloud plots, NLP research, LDA, Word2Vec, README
Noémie: first analysis, dictionary definitions, threshold, event characterizations
Thibaut: pre-processing, threshold, code optimization, web developer 
Nathan:  performance analysis, sentiment analysis, cosine matrix, PCA


![](https://www.epfl.ch/wp/5.5/wp-content/themes/wp-theme-2018/assets/svg/epfl-logo.svg)
