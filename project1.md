# How does rest and accumulated player fatigue affect individual player performance in the NBA?

### Background
NBA players regularly play multiple games per week while traveling across cities and time zones. Short rest periods, consecutive games, and accumulated playing time may limit physical recovery, while travel across many time zones may disrupt circadian rhythms and sleep. Previous research has found relationships between rest, schedules, travel, and overall performance. However, much of the existing research has focused on team-level outcomes. My project will examine these relationships at the individual player-game level.

### Dataset
The primary data source will be NBA Stats on the ESPN NBA page. 

### Data Cleaning and Preparation
Python and pandas will be used to code and clean the API data. The analysis will sort observations chronologically by player, calculate rest periods and recent workload from previous games, identify back-to-back games, merge team location information, and calculate estimated travel distance and time-zone changes. Missing values in which a player did not participate will be examined and handled clearly

### Key Independent Variables
Time Zone changes: the number of time zones changes player’s travel between the previous game and the next game. 
Travel: how many miles each player/team travels 
Back to back games: Whether a player plays on consecutive days
Games in last 7, 14 days: 
Recent workload: The number of minutes a player played in their previous 3 games and the number of games they played in the last 7 days
Home/Away: Whether the team is playing home vs away
Player age: The players age during the season, age may affect recovery and fatigue
Strength of schedule: Winning percentage or ranking of opposing teams
Player performance: PPG, APG, RPG, FG% 

### Dependent Variables
The primary measure of player performance will be True Shooting Percentage (TS%), which accounts for field goals, three-point field goals, and free throws

### Visualizations
Scatter plot of time zone changes vs individual field goal percentage
Box plot comparing shooting efficiency and recent workload

### Ethics and Limitations
This project uses publicly available sports data. The analysis will not claim that travel directly causes changes in performance because observational sports data cannot establish causation on its own. Estimated travel distance will represent geographic distance between game locations rather than the actual route or flight taken by a team. 
