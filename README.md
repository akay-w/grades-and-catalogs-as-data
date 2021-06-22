# Grades and Catalogs as Data

## Overview

This is a project that I worked on with faculty at Furman University and helped present at the Analytics Day conference held by Appalachian State University on June 3, 2021.

The project was titled "Grades and Catalogs as Data." It showed three techniques for data mining course grades to understand the content of the curriculum, its difficulty, and the match between courses and students. 

## Details

Methods used include random effects linear models to estimate student ability and course difficulty, factor analysis of residuals to extract student learning outcomes, and text-mining techniques to cluster catalog course descriptions into content groups. 

Findings include the qualitative difference of F grades, relationship of course difficulty to learning, and clustering of disciplines by student learning. 

My contribution to the project was to show how text-mining techniques could be used to cluster catalog course descriptions into content groups. This acted as validation for the earlier conclusions in the presentation using other methods, and also served as an example of how various NLP (natural language processing) techniques can be used on academic data.

## Recording

A video recording of the presentation can be accessed from this Google Doc by clicking on "Grades and Catalogs as Data": https://docs.google.com/spreadsheets/d/1W-M3gX_xOynWObF21K5sH7XYyx3rKEUvSpnODRoY9-4/edit#gid=631779964

## Files

I've included the PowerPoint slides as well as the Python code (as Jupyter Notebook files) and Tableau visuals that I contributed to the project. (I  used Tableau for the first time for this project, so the visuals aren't very sophisticated.)

The Jupyter Notebook files should be viewed in the following order:

1) Data cleaning.ipynb: 

This file shows the initial data cleaning that I did in Pandas for the course name/description data, which was provided to me as an Excel file. I loaded the data into Pandas, eliminated rows with NA values, used regex to remove undesired characters/strings, and used the nltk library to tokenize and lemmatize the data and remove stopwords.

2) Data by subject.ipynb: 

In this file, I transformed the Pandas dataframe so that each course subject became a row with a bag of words containing all of the words used in course descriptions for courses within that subject. I split this up from the first file because it was getting long.

3) Analysis.ipynb: 

I used this file to analyze the data by subject. I found the most common words used in course descriptions, the longest and shortest course descriptions, the average course description lengths by subject, and the most common words used in descriptions for each subject.

4) Word matrix, LDA.ipynb: 
 
In this file, I showed how to create a document-word matrix in which each row was a subject and there was a separate column for each unique word that appeared in any course description (so there were around 6000 columns). The cells then contained the frequency of each word in the course descriptions for each subject. This was mostly for illustrative purposes, although one of my co-contributors then used this matrix to find correlations among the vectorized catalog descriptions by subject and create an igraph in R. 

Then, I ran the NLP topic-modeling method LDA (latent dirichlet allocation) on the data to see which subjects had similar topics. I showed the results for num_topics = 10 as a Tableau visual in LDA results.twbx.

5) Kmeans.ipynb: 
 
In this file, I ran K-means on the data, just to see what happened. It did an okay job, but K-means is not as well suited to high-dimensional data. I showed one example with wordclouds for k=6, and also output an excel file showing results for values of k from 5 to 12. I then used this file to create a Tableau visual (K-means results.twbx).

6) PLSA.ipynb: 
 
In this file, I ran the NLP topic modeling method PLSA (probabilistic latent semantic analysis) on the data for the sake of comparison to LDA. I created wordclouds for examples with num_topics=7 and 10, and created a Tableau visual for num_topics=10 (PLSA results (num_topics=10).twbx).


