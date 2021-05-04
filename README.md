# WorldHappynessReport2021

In this repository I analyze the World Happyness Report 2021 for the Udacity Data Scientist Nanaodegree. Here is a link to the Data on Kaggle:
https://www.kaggle.com/ajaypalsinghlo/world-happiness-report-2021

We want to answer three questions:
1. Which country and which continent is the happiest / least happy?
2. Which countries have changed the most in the last 15 years?
3: Which factors have the most impact for the happiness of a country?

The following libraries are used:
Pandas
Plotly
Scikit Learn
Numpy
Matplotlib

The code is formatted via the nb_black extension. Here is how I got to my findings:

1. Business Understanding
For this I will copy the explanation from Kaggle:

Context

The World Happiness Report is a landmark survey of the state of global happiness . The report continues to gain global recognition as governments, organizations and civil society increasingly use happiness indicators to inform their policy-making decisions. Leading experts across fields – economics, psychology, survey analysis, national statistics, health, public policy and more – describe how measurements of well-being can be used effectively to assess the progress of nations. The reports review the state of happiness in the world today and show how the new science of happiness explains personal and national variations in happiness.

Content

The happiness scores and rankings use data from the Gallup World Poll . The columns following the happiness score estimate the extent to which each of six factors – economic production, social support, life expectancy, freedom, absence of corruption, and generosity – contribute to making life evaluations higher in each country than they are in Dystopia, a hypothetical country that has values equal to the world’s lowest national averages for each of the six factors. They have no impact on the total score reported for each country, but they do explain why some countries rank higher than others.

2. Data Understanding
The World Happiness report has Data from 2005 to 2021. The happyness is found in the column "Ladder Score". The other columns of interest to me are the six factors mentioned above plus the Region and the year. The score in each column is a float that measures the corresponding values. I can use this later for my modelling.

3. Data Preparation
I have two csv-files: one for only the year 2021 and one for the years 2005-2020. I need to merge those two files and create a year column for the new data. The old data doesn't have the region column, so I will try to merge the region from the new data to the old data (since the countries should be identical in both dataframes and I am only interested in countries present in the 2021 data).
