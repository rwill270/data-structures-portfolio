# How do time zone changes and accumulated player fatigue affect individual player performance in the NBA?

## Dataset
NBA players regularly play multiple games per week while traveling across cities and time zones. Short rest periods, consecutive games, and accumulated playing time may limit physical recovery, while travel across many time zones may disrupt circadian rhythms and sleep. Previous research has found relationships between rest, schedules, travel, and overall performance. However, much of the existing research has focused on team-level outcomes. My project will examine these relationships at the individual player-game level.

## Data Preparation
Python and pandas will be used to code and clean the API data. The analysis will sort observations chronologically by player, calculate rest periods and recent workload from previous games, identify back-to-back games, merge team location information, and calculate estimated travel distance and time-zone changes. Missing values in which a player did not participate will be examined and handled clearly

## Key Independent Variables
Rest days: Number of days between the player's previous game and current game.
Back-to-back: Whether the player played in a game on the previous calendar day.
Recent workload: Total minutes played across the player's previous three games.
Games in previous seven days: Number of games played by the player during the seven days preceding the current game.
Time-zone change: Difference in time zones between the player's previous game location and current game location.
Travel distance: Estimated geographic distance between the locations of the player's previous and current games.
Home/away: Whether the player's current game is played at home or away.
Player age: Player age during the season.
Opponent strength: A measure of the opponent's quality, such as winning percentage.

## Dependent Variables
The primary measure of player performance will be True Shooting Percentage (TS%), which accounts for field goals, three-point field goals, and free throws

## Planned Visualizations
Scatter plot of time zone changes vs individual field goal percentage
Box plot comparing shooting efficiency and recent workload

## Ethics
This project uses publicly available sports data. The analysis will not claim that travel directly causes changes in performance because observational sports data cannot establish causation on its own. Estimated travel distance will represent geographic distance between game locations rather than the actual route or flight taken by a team. Other factors, including injuries, coaching decisions, player rest decisions, opponent strategy, sleep, and individual health, may not be observable in the dataset and could influence performance.
