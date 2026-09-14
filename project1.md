[Back to Projects](projects.md)

[Back to Main Page](index.md)

# How does rest and accumulated player fatigue affect individual player performance in the NBA?

### Background
NBA players regularly play multiple games per week while traveling across cities and time zones. Short rest periods, consecutive games, and accumulated playing time may limit physical recovery, while travel across many time zones may disrupt circadian rhythms and sleep. Previous research has found relationships between rest, schedules, travel, and overall performance. However, much of the existing research has focused on team-level outcomes. My project will examine these relationships for NBA Finals MVP Jalen Brunson. 

### Dataset
The primary data source will be NBA Stats on the ESPN NBA page. I can extract specific variables like field goal percentage and whether the team is home or away that game. I can also sort the data to show games that fall on back to back days.

### Data Cleaning and Preparation
Python and pandas will be used to code and clean the API data. The analysis will sort observations chronologically by player, calculate rest periods and recent workload from previous games, identify back-to-back games, merge team location information, and calculate estimated travel distance and time-zone changes. Missing values in which a player did not participate will be examined and handled clearly

### Key Independent Variables
Time Zone changes: the number of time zones changes player’s travel between the previous game and the next game. 

Travel: how many miles each player/team travels 

Back to back games: Whether a player plays on consecutive days

Recent workload: The number of minutes a player played in their previous 3 games and the number of games they played in the last 7 days

Home/Away: Whether the team is playing home vs away

Player performance: FG% 

### Dependent Variables
The primary measure of player performance will be true field goal shooting Percentage (FG%)

### Visualizations
Bar Plot comparing field goal percentages and fatigue level (Back to back games)

Box plot comparing shooting efficiency and time zone changes

### Ethics and Limitations
This project uses publicly available data. The analysis will not claim that travel directly causes changes in performance. Travel distance will be correlated to the number of time zones that are crossed for games. 



# Field Goal Percentage and Fatigue Level (Back to Back Games)

I took all of the back-to-back games that the New York Knicks played during the 2024-2025 season and made a bar chart showing Jalen Brunson's field goal percentages to see if fatigue affects performance. Back-to-back games are games played on consecutive nights without a break, which turned out to be 10 sets of games (20 games total). The general idea of fatigue would say that a player is more likely to perform better on night one of a back-to-back considering the player is coming off more rest. For Jalen Brunson specifically, it turns out that 7 of the 10 sets of back-to-back games, he had a higher shooting percentage. He averaged roughly 46% in the first games and 53% in the second games. One way you could look at this is by determining that fatigue doesn't affect star players the same way it does to average players in the NBA. Star players like Brunson can get into rhythm as well as identifying coaching changes better and faster than average players, which can ultimately lead to fatigue changes. 

import matplotlib.pyplot as plt

import pandas as pd

import seaborn as sns

field_goal_percentage = [

    "Set 1",
    
    "Set 2",
    
    "Set 3",
    
    "Set 4",
    
    "Set 5",
    
    "Set 6",
    
    "Set 7",
    
    "Set 8",
    
    "Set 9",
    
    "Set 10"
    
]

game_1 = [33, 21.4, 52.4, 39.1, 61.5, 66.7, 51.9, 36.4, 38.1, 33.3]

game_2 = [45, 60.0, 58.1, 55.0, 50.0, 38.9, 47.6, 61.9, 58.8, 52.9]


df = pd.DataFrame(

    {
        "Field Goal Percentage": field_goal_percentage,
        
        "Game 1": game_1,
        
        "Game 2": game_2,
        
    }
    
)

df["Game 1_Left"] = -df["Game 1"]

fig, ax = plt.subplots(figsize=(10, 6))

sns.barplot(

    data=df,
    
    x="Game 1_Left",
    
    y="Field Goal Percentage",
    
    label="Game 1",
    
    orient="h",
    
    ax=ax,
    
)

sns.barplot(

    data=df,
    
    x="Game 2",
    
    y="Field Goal Percentage",
    
    label="Game 2",
    
    orient="h",
    
    ax=ax,
    
)

ticks = ax.get_xticks()

ax.set_xticklabels([abs(int(tick)) for tick in ticks])

ax.set_title(

    "Field Goal Percentage Comparison", fontsize=14, fontweight="bold", pad=15
    
)

ax.set_xlabel("Game 1 vs Game 2 Field Goal Percentage")

ax.set_ylabel("Sets of Back to Back Games")

ax.axvline(0, color="black", linewidth=0.8)

ax.legend(loc="upper right")

plt.tight_layout()

plt.show()


<img width="1448" height="88" alt="image" src="https://github.com/user-attachments/assets/28ae235d-7ebd-4d99-8ca2-a4e535e895dc" />


<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/0acbfbd7-1180-424f-9313-95b291c9b012" />





