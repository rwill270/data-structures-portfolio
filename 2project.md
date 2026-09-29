[Back to Projects](projects.md)

[Back to Main Page](index.md)

[Jupyter Notebook]

# How accurately can a previous-season's statistics predict an NFL wide receiver's performance in the following regular season?

### Background

This project examines whether previous-season production from NFL wide receivers can be used to predict an individual player's position ranking in the following season. Of course, not all predictions are fully accurate, as there will always be certain players who have breakout years as well as certain players who have statistically-down years. Machine learning models have been used in the past to predict stats in the NFL but it is very important to use the correct variables in your predictions. 

### Machine-Learning Problem and Dataset

The data will be obtained from NFL player statistics, primarily using Pro Football Reference data available online. The dataset will cover the 2025 NFL season, resulting in 10 player observations after the data is cleaned. The target variable is the rankings, defined as the player's predicted positional finish ranged 1-10. The unit of analysis is an individual NFL wide receiver season given the variables. The data will be mixed with receiving yards, touchdowns, and receptions from the top 10 best wide receivers from the 2025 season. The first visualization will be a multi-class classification model using RandomForestClassifier in Python. It is classification because the target variable (Rank) represents a discrete, categorical class label (ordered integers 1 through 10) representing a receiver's positional rank tier, rather than a continuous numeric outcome. There are 0 missing values as the dataset is complete across all top 10 qualifying candidates.

### Context and Supporting Research

Being able to estimate a player's future receiving production can provide useful information for sports analysts, fantasy football players, coaches, scouts, and other people interested in evaluating player performance. 

APA Citations

- [2025 NFL Receiving | Pro-Football-Reference.Com, www.pro-football-reference.com/years/2025/receiving.htm. Accessed 29 Sept. 2026.](https://www.pro-football-reference.com/years/2025/receiving.htm))
  
- [staff, Fantasy, and Multiple Authors. “Fantasy Football Draft Rankings 2026: Wide Receiver.” ESPN, ESPN Internet Ventures, www.espn.com/fantasy/football/story/_/page/FFPreseasonRank26WR/nfl-fantasy-football-draft-rankings-2026-wr-wide-receiver. Accessed 28 Sept. 2026.](https://www.espn.com/fantasy/football/story/_/page/FFPreseasonRank26WR/nfl-fantasy-football-draft-rankings-2026-wr-wide-receiver))

- [“NFL Wide Receiver Stats.” SumerSports, sumersports.com/players/wide-receiver/?season=2025. Accessed 28 Sept. 2026. ](https://sumersports.com/players/wide-receiver/?season=2025))

### Data Preparation

No estimated values were needed as I verified and computed all the data needed for my variables and research question. For categorical encoding, the target variable rank was formatted as an ordinal discrete integer ranged 1-10. In terms of feature scaling, raw numeric values were kept for everyone to interpret directly inside the model's display.

### Data Understanding and Feature Selection

I took 3 independent variables (receiving yards, touchdowns, and receptions) and gave them different weights, judging by how important each statistic is, to find my projected rankings for 2026. These three statistics are the top 3 most important features to measure success for a wide receiver, as receiving yards establish player production, touchdowns measure scoring, and receptions measure value and opportunity for each player.

- Receiving yards: 50% weight (most important stat). Ranged from 1,077 to 1,793 yards.

- Touchdowns: 25% weight. Ranged from 3 to 11 touchdowns.

- Receptions: 25% weight. Ranged from 65 to 129 catches.

Based off of the 2025 statistics for the 10 selected players to predict rankings, there is a strong positive correlation between receiving yards and receptions, whereas touchdowns show a higher variance. Some players can record a lot of yards and catches but not a lot of touchdowns, and vice versa. 

### Training and Testing Strategy


