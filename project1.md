[Back to Projects](projects.md)

[Back to Main Page](index.md)

[Notebook](Ryan%20Williams%20-%20Portfolio%20Project%20One.ipynb)


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

### Code and AI Transparency
I computed and made the graphs myself in Python but I used ChatGPT to understand why some of the findings came out to be. 

### Sources

“Pubmed.Ncbi.Nlm.Nih.Gov.” National Center for Biotechnology Information, U.S. National Library of Medicine, pubmed.ncbi.nlm.nih.gov/9381060/. Accessed 13 Sept. 2026. 

Leota, Josh, et al. “Eastward Jet Lag Is Associated with Impaired Performance and Game Outcome in the National Basketball Association.” Frontiers in Physiology, U.S. National Library of Medicine, 16 June 2022, pmc.ncbi.nlm.nih.gov/articles/PMC9245584/. 

“Pubmed.Ncbi.Nlm.Nih.Gov.” National Center for Biotechnology Information, U.S. National Library of Medicine, pubmed.ncbi.nlm.nih.gov/32172667/. Accessed 13 Sept. 2026. 


# Field Goal Percentage and Fatigue Level (Back to Back Games)

I took all of the back-to-back games that the New York Knicks played during the 2024-2025 season and made a bar chart showing Jalen Brunson's field goal percentages to see if fatigue affects performance. Back-to-back games are games played on consecutive nights without a break, which turned out to be 10 sets of games (20 games total). The general idea of fatigue would say that a player is more likely to perform better on night one of a back-to-back considering the player is coming off more rest. For Jalen Brunson specifically, it turns out that 7 of the 10 sets of back-to-back games, he had a higher shooting percentage. He averaged roughly 46% in the first games and 53% in the second games. One way you could look at this is by determining that fatigue doesn't affect star players the same way it does to average players in the NBA. Star players like Brunson can get into rhythm as well as identifying coaching changes better and faster than average players, which can ultimately lead to fatigue changes. 

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


# How does time zone changes affect player performance?

For this visualization, I found all of the games from the 2025-2026 season that Jalen Brunson traveled through multiple time zones, so games in cities in Central, Mountain, and Pacific time zones. Jalen Brunson plays most of his games in New York City, EST, so I compared him to the three other time zones out west. I compared his field goal shooting performance through the different time zones to see if travel distance affects player performance. With just one time zone traveled through, aka games played in cities in Central time, his average shooting percentage was roughly 48%. His average shooting shooting percentage in Mountain time zone was roughly 43%, and his average shooting performance in Pacific time zones was over 50%, roughly 53%. So, it makes sense that Brunson shot better in Central time zones compared to Mountain time zones, as there is less distance traveled to the games. But, it is odd that the pacific time zone was his best shooting performance, as you would think that the more distance a player travels, the more it takes a toll on the body, which would decrease performance. 


<img width="2032" height="59" alt="image" src="https://github.com/user-attachments/assets/627bc1de-ff51-44f2-b778-bd063dc7a5b1" />


data = {

    "Games": [
    
        "Game 1",
        
        "Game 2",
        
        "Game 3",
        
        "Game 4",
        
        "Game 5",
        
        "Game 6",
        
        "Game 7",
        
        "Game 8",
        
        "Game 9",
        
        "Game 10",
        
        "Game 11",
        
        "Game 12",
        
        "Game 13",
        
        "Game 14",
        
        "Game 15",
        
    ],
    
    "Games away from EST": [
    
        "@ Milwaukee",
        
        "@ Chicago",
        
        "@ Dallas",
        
        "@ New Orleans",
        
        "@ San Antonio",
        
        "@ Phoenix",
        
        "@ Portland",
        
        "@ Sacramento",
        
        "@ Milwaukee",
        
        "@ Denver",
        
        "@ L.A. Lakers",
        
        "@ L.A. Clippers",
        
        "@ Utah",
        
        "@ Oklahoma City",
        
        "@ Houston",
        
    ],
    
    "Time_Zone": [
    
        "CT",
        
        "CT",
        
        "CT",
        
        "CT",
        
        "CT",
        
        "MT",
        
        "PT",
        
        "PT",
        
        "CT",
        
        "MT",
        
        "PT",
        
        "PT",
        
        "MT",
        
        "CT",
        
        "CT",
        
    ],
    
    "FG_Pct": [
    
        56.0,
        
        48.0,
        
        47.8,
        
        43.5,
        
        41.7,
        
        47.4,
        
        52.6,
        
        66.7,
        
        64.7,
        
        23.1,
        
        42.1,
        
        52.2,
        
        43.8,
        
        59.1,
        
        35.7,
        
    ],
    
}

df = pd.DataFrame(data)

time_zones_change = {"CT": "1 Zone", "MT": "2 Zones", "PT": "3 Zones"}

df["Time_Zones_Away"] = df["Time_Zone"].map(time_zones_change)

fig, ax = plt.subplots(figsize=(10, 6))

sns.boxplot(

    data=df,
    
    x="Time_Zones_Away",
    
    y="FG_Pct",
    
    order=["1 Zone", "2 Zones", "3 Zones"],  
    
    palette="Set2", 
    
    width=0.4,
    
    ax=ax,
)

sns.stripplot(

    data=df,
    
    x="Time_Zones_Away",
    
    y="FG_Pct",
    
    order=["1 Zone", "2 Zones", "3 Zones"],
    
    color="black",
    
    size=8,
    
    ax=ax,
    
)

ax.set_title(

    "Jalen Brunson FG% vs. Time Zones Away from EST (2025–26)",
    
    fontsize=14,
    
    fontweight="bold",
    
    pad=15,
    
)

ax.set_xlabel("Time Zones Away from EST", fontsize=12)

ax.set_ylabel("Field Goal Percentage (%)", fontsize=12)

ax.set_ylim(15, 75)

plt.tight_layout()

plt.show()

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/9fa5d81b-ad17-4a0f-aa66-e46abf948bc4" />


# How big of a difference does travel distance have on home games vs away games?

For this last graph, I computed the opposite of the previous graph above. I found all of the home games for Jalen Brunson in the 2025-2026 season and see how his performance changes. Considering these are home games and that there is no distance traveled to the games, you would think that his performance should raise. Among all of the home games he played in that season, his average field goal percentage was 46.9%. This percentage ranks 3rd out of 4 when comparing them to other stats from the central, mountain and pacific time zones. He shot better in pacific and central cities but worse in the mountain time zone. 


<img width="350" height="1074" alt="image" src="https://github.com/user-attachments/assets/fe6d4f7a-c3ac-4cd8-9055-4796222ade49" />

data = {

    "Games": [
    
        "1 ",
        
        "2 ",
        
        "3 ",
        
        "4 ",
        
        "5 ",
        
        "6 ",
        
        "7 ",
        
        "8 ",
        
        "9 ",
        
        "10 ",
        
        "11 ",
        
        "12 ",
        
        "13 ",
        
        "14 ",
        
        "15 ",
        
        "16",
        
        "17",
        
        "18",
        
        "19",
        
        "20",
        
        "21",
        
        "22",
        
        "23",
        
        "24",
        
        "25",
        
        "26",
        
        "27",
        
        "28",
        
        "29",
        
        "30",
        
        "31",
        
        "32",
        
        "33",
        
        "34",
        
        "35",
        
        "36",
        
    ],
    
    "Opponent": [
    
        "Cavaliers",
        
        "Celtics",
        
        "Bulls",
        
        "Wizards",
        
        "Timberwolves",
        
        "Nets",
        
        "Grizzlies",
        
        "Magic",
        
        "Bucks",
        
        "Raptors",
        
        "Hornets",
        
        "Jazz",
        
        "Magic",
        
        "76ers",
        
        "Heat",
        
        "Cavaliers",
        
        "Hawks",
        
        "76ers",
        
        "Clippers",
        
        "Mavericks",
        
        "Nets",
        
        "Kings",
        
        "Trail Blazers",
        
        "Lakers",
        
        "Nuggets",
        
        "Pacers",
        
        "Pistons",
        
        "Rockets",
        
        "Spurs",
        
        "Thunder",
        
        "Warriors",
        
        "Wizards",
        
        "Pelicans",
        
        "Bulls",
        
        "Celtics",
        
        "Raptors",
        
    ],
    
    "FG_Pct": [
    
        27.8,
        
        50.0,
        
        45.5,
        
        35.3,
        
        45.0,
        
        42.9,
        
        57.9,
        
        43.5,
        
        57.1,
        
        31.6,
        
        56.3,
        
        52.9,
        
        43.5,
        
        31.8,
        
        57.7,
        
        40.0,
        
        43.5,
        
        47.6,
        
        75.0,
        
        37.5,
        
        47.1,
        
        52.9,
        
        40.0,
        
        26.7,
        
        51.9,
        
        48.4,
        
        60.0,
        
        50.0,
        
        43.8,
        
        27.8,
        
        45.0,
        
        47.4,
        
        57.9,
        
        46.2,
        
        52.6,
        
        66.7,
        
    ],
    
}

df = pd.DataFrame(data)

fig, ax = plt.subplots(figsize=(8, 6))

sns.boxplot(

    data=df,
    
    y="FG_Pct",
    
    width=0.3,
    
    ax=ax,
    
    boxprops=dict(alpha=0.7),
    
)

sns.stripplot(

    data=df,
    
    y="FG_Pct",
    
    size=8,
    
    jitter=0.15,
    
    ax=ax,
    
)

mean_fg = df["FG_Pct"].mean()

ax.axhline(

    mean_fg,
    
    color="black",
    
    linewidth=1.5,
    
    label=f"Mean FG%: {mean_fg:.1f}%",
    
)

ax.set_title(

    "Jalen Brunson FG% Distribution — Home Games (2025–26)",
    
    fontsize=14,
    
    fontweight="bold",
    
    pad=15,
    
)

ax.set_ylabel("Field Goal Percentage (%)", fontsize=12)

ax.set_ylim(20, 80)

ax.legend(loc="upper right")

plt.tight_layout()

plt.show()


<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/d60b37e7-c27c-4ad0-b472-2461bbfa3bee" />

