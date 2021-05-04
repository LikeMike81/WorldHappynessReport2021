# WorldHappynessReport2021

In this repository I analyze the World Happyness Report 2021 for the Udacity Data Scientist Nanaodegree. Here is a link to the Data on Kaggle:
https://www.kaggle.com/ajaypalsinghlo/world-happiness-report-2021

We want to answer three questions:
1. Which country and which region is the happiest / least happy in 2021?
2. Which countries have changed the most in the last 15 years?
3. Which factors have the most impact for the happiness of a country?

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

There are also several missing values. After looking at the numbers I decided it is manageable to just delete rows, that have missing data. This way I go from 2098 rows to 1816 - still more than enough for my analysis. 

4. Modelling
To answer questions 1 and 2 I don't need to use any modelling. To find, which country and which region are the happiest, I can simply filter the data to the year 2021 and rank it and plot the result in a bar chart. For question 2, which country has changed the most, I group the data by Countryname and find the max and min value for their Ladderscore. Then I create a new column "diff" that contains the difference between the max and min value per country. By sorting the diff values I can see the countries with the most change. For the visualization I only use the 5 countries, that changed the most, and use a lineplot.

The 3d question is the most complicated one: which variable has the most impact on the Ladderscore. First I took a look at the correlation of each variable to our target variable - both as a plot and directly at the numbers. This already is a pretty good indicator, but to get a clearer picture I also wanted to create a linear model and compare the contributions of each variable. To be able to compare these contributions, I first scaled each variable with the MinMaxScaler of the Scikit Learn Package and then fitted a linear regression. The Model has a R2 of 0.75 which is good enough for my analysis. I then took a look at the coefficents to get to a findal answer.

5. Evaluation
So let's get back to our 3 questions and see, which answers we generated:

1. Which country and which region is the happiest / least happy in 2021?

Finland is the happiest country in 2021, follwed by Denmark and Switzerland. It is telling, that the scandinavian countries all rank pretty high - and that New Zealand is the only country not in Europe to make the top 10. Afghanistan is the unhappiest country in 2021, by a considerable margin. The other unhappy countries are mainly in Africa.

North America and ANZ is the happiest region - which might be surprising considering it only had one country in the top 10. But Western Europe seems to have too many lower ranking countries, that seem to weigh it down a bit. It is still pretty even and the margin to the next region (Central and Eastern Europe) is already considerable. South Asia and Sub-Saharan Africa are at the bottom of the list.

2. Which countries have changed the most in the last 15 years?
Venezuela actually had a pretty high Ladderscore in 2010- by 2016 the score was almost only half of that. That makes Venezuela the country, which happiness changed the most. Benin and Liberia take spots 2 and 3 and both of them managed to increase their happiness significantly (both almost doubled their happiness at one point).

3. Which factors have the most impact for the happiness of a country?
 
After looking at both the correlation and the coefficents of the linear model it is clear, that Logged GdP per capita is the most important factor. At the next tier we have Social Support and Healthy Life expectancy that both also play a big role. Freedom to make life choices and Generosity are of lesser importance and it would probably be fair to expect these factors to improve, if the other 3 factors also improve. Perceptions of corruption is the only factor with a negative impact, but it also seems to have the lowest overall impact.

6. Deployment

All these findings will be available as a Medium article.
