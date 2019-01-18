# NPD-Googletrends

This is a personal project to see if I can predict the top selling games of each month based on google search data from google trends.

## NPD and Google Trends Data 
[npd_data.ipynb](npd_data.ipynb)

From __[the NPD group website](https://www.interactive.org/npd/index.asp)__, I got either the top 10 or top 20 selling games of each month but no sales figures.

[gametrends_data.ipynb](gametrends_data.ipynb)

For all the games, I used __[pytrends](https://github.com/GeneralMills/pytrends)__, a google trends unofficial API to collect relative trend data over the past 10 years for all the games considered. Some example trend data is plotted below:

![google trends](https://raw.githubusercontent.com/henrystoltenberg/NPD-Googletrends/master/images/trendspng.png)

## Data Analysis
[getfeatures.ipynb](getfeatures.ipynb)

To generate rankings, I make pairwise comparisons of games. The labeled data has features derived from the trend data and the outcomes of the comparisons based on ranking (or lackthereof). Here are some scatterplots of a random subset of the data showing that classification between winning and losing comparisons using these features:

The features are: x_0: days since all time peak searches, x_1: all time peak in searches, x_2: peak in searches 1 month prior, x_3 peak in searches 2 months prior, x_4: peak in searches 3 months prior, x_5: derived from x_0, +1 if all time peak is 5-55 days ago, -1 otherwise. (Note: features plotted above are differences of these between 2 games.)

![scatter](https://raw.githubusercontent.com/henrystoltenberg/NPD-Googletrends/master/images/scatterfeature.png)

## Predictions
[rankSVMmodel.ipynb](rankSVMmodel.ipynb)

I trained a SVM classifier based on __[RankSVM](www.cs.cornell.edu/~tj/publications/joachims_02c.pdf)__. On a witheld test set, the trained model had an 
F1 score of: 0.9669968469439774

[nov_predict.ipynb](nov_predict.ipynb)

Then using an __[algorithm to fit a Bradley-Terry Model](https://projecteuclid.org/euclid.aos/1079120141)__, the games can be ranked. 
For example, here are predicted rankings for the (at the time) unreleased rankings for November:

Top November 2018 games:

Prediction  | Actual    
----------- | -----------
Spider-Man | Red Dead Redemption 2
Warframe | Call of Duty: Black Ops 4
Daylight | Battlefield V
Fallout 76 | Fallout 76
Spyro Reignited Trilogy | Pokemon: Let's Go Pikachu
Pokemon: Let's Go Pikachu | Pokemon: Let's Go Eevee
Pokemon: Let's Go Eevee | NBA 2K19
Battlefield V | Madden NFL 19
Overkill's The Walking Dead | Spyro Reignited Trilogy
Tetris Effect | FIFA 19
Hitman 2 | NBA 2K19
Civilization VI | Super Mario Party
Darksiders 3 | Spider-Man
Artifact | Mario Kart 8
Just Dance 2019 | WWE 2k19
Darksiders III | God of War
Call of Cthulhu | Shadow of the Tomb Raider
Fe | Just Dance 2019
Extinction | Grand Theft Auto V
1-2-Switch | Forza Horizon 4
