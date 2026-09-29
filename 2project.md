[Back to Projects](projects.md)

[Back to Main Page](index.md)

[Jupyter Notebook]

# How accurately can a previous-season's statistics predict an NFL wide receiver's performance in the following regular season?

### Background

This project examines whether previous-season production from NFL wide receivers can be used to predict an individual player's position ranking in the following season. Being able to estimate a player's future receiving production can provide useful information for sports analysts, fantasy football players, coaches, scouts, and other people interested in evaluating player performance. Of course, not all predictions are fully accurate, as there will always be certain players who have breakout years as well as certain players who have statistically-down years. Machine learning models have been used in the past to predict stats in the NFL but it is very important to use the correct variables in your predictions. 

### Dataset

The data will be obtained from NFL player statistics, primarily using Pro Football Reference data available online. The dataset will cover the 2025 NFL season, resulting in approximately 10 player observations after the data is cleaned. The target variable is next-season receiving yards, defined as the total number of receiving yards recorded by the player during the regular season following the season used to calculate the predictor variables. This is a regression problem because the target variable, next-season receiving yards, is a continuous numerical value. The model is not predicting a category such as "high performer" or "low performer." 
