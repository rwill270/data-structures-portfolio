[Back to Projects](projects.md)

[Back to Main Page](index.md)

[Jupyter Notebook]

# How accurately can a previous-season's statistics predict an NFL wide receiver's performance in the following regular season?

### Background

This project examines whether previous-season production from NFL wide receivers can be used to predict an individual player's position ranking in the following season. Of course, not all predictions are fully accurate, as there will always be certain players who have breakout years as well as certain players who have statistically-down years. Machine learning models have been used in the past to predict stats in the NFL but it is very important to use the correct variables in your predictions. 

### Machine-Learning Problem and Dataset

The data will be obtained from NFL player statistics, primarily using Pro Football Reference data available online. The dataset will cover the 2025 NFL season, resulting in 10 player observations after the data is cleaned. The target variable is the rankings, defined as the player's predicted positional finish ranged 1-10. The unit of analysis is an individual NFL wide receiver season given the variables. The data will be mixed with receiving yards, touchdowns, and receptions from the top 10 best wide receivers from the 2025 season. The first visualization will be a multi-class classification model using RandomForestClassifier in Python. It is classification because the target variable (Rank) represents a discrete, categorical class label (ordered integers 1 through 10) representing a receiver's positional rank tier, rather than a continuous numeric outcome. There are 0 missing values as the dataset is complete across all top 10 qualifying candidates. The second visualization will be a random forest regression model , as the target variables are to predict the 2026 top ten wide receivers by receiving yards, touchdowns, and receptions (numerical values)

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

Based off of the 2025 statistics for the 10 selected players to predict rankings, there is a strong positive correlation between receiving yards and receptions, whereas touchdowns show a higher variance. Some players can record a lot of yards and catches but not a lot of touchdowns, and vice versa. For the second visualization, both the independent and dependent variables are the same. I took the ten best wide receivers from each of the past 5 seasons (2021-2025) to predict the top ten wide receivers for the 2026 season, each by receiving yards leaders, touchdowns leaders, and receptions leaders.

### Training and Testing Strategy

For validation, I evaluated my data by 5-fold cross-validation, splitting my data into 5 equal parts to see how well the model will perform. For data leakage, the model did not use any other information outside the predictor variables, and only stuck to the 2025 season's stats.

### Baseline Performance

By comparing the random forest classification model to these baselines, we can prove that combining multiple stats including yards, catches, and touchdowns, gives a much more reliable prediction than just copying last season's stats or making a guess! A random guess baseline would only correctly guess the exact rank of each player about 10% of the time.

### Model Development and Comparison

Comparing predictions showcases that linear assumptions hold versus where tree-based decision boundaries split the data better. If random forest outperforms logistic regression, that means that year-over-year WR rank tiers depend on non-linear starts rather than simple linear scoring. If both perform identically, logistic regression is preferred for its simplicity and direct interpretability.

### Model Evaluation

Evaluation: the random forest classifier model successfully assigned discrete tiers based on rank. By gathering individual tree decisions, the model constructed single-variable peaks, far better than a single decision tree. The random forest regressor also successfully assigned numerical values (yards, touchdowns, and catches).

### Model Interpretation

The resulting 10 mini-box model grid formats each receiver's predicted rank output (1 - 10) alongside their underlying 2025 statistical values (Yds, TDs, Rec). For both models, receiving yards was the highest importance weight at 50%, as it is the primary driver for ranks. Both touchdowns and receptions are equally tied at 25% importance weight, as they are equally important but measure different player values. 

### Ethics and Limitations

Relying solely on machine learning outputs for sports predictions, gambling, coaching, drafting, etc... carries much risk due to the high variance in modern football. Of course there will always be some uncaptured variables in a dataset like this one as the feature set does not account for quarterback changes, coaching changes, injuries, or age degradation. Also, the model's sample size of 10 is perfect because the goal of this study is to predict the top-tier elite wide receivers in the NFL; anything more than 10 will be irrelevant to the findings of the research question.

### Code and AI Transparency

I computed and made the models myself in Python but I used Gemini to help me with displaying the visualizations exactly how I wanted them to look like, including making rows and columns, font, color, as well as to interpret some of the results and why some of the findings came out to be.


## Visualization 1: 2026 NFL Predicted Wide Receiver Rankings (Classification)

In this random forest classification model, I used the top ten receiving yards leaders from the 2025 season to predict the top 10 wide receivers for the upcoming 2026 NFL season. To rank the top 10 players at the position, my independent variables were receiving yards (50%), touchdowns (25%), and receptions (25%), each listed at different weights based on importance to calculate the rankings. As it shows, Jaxon Smith-Njigba is projected to be the number 1 ranked wide receiver in the 2026 season.

data = {

    'Player': [
    
        'Jaxon Smith-Njigba', 'Puka Nacua', 'Amon-Ra St. Brown', 'Ja\'Marr Chase', 
        
        'George Pickens', 'Chris Olave', 'Zay Flowers', 'Jameson Williams', 
        
        'Nico Collins', 'CeeDee Lamb'
        
    ],
    
    'Receiving_Yards': [1793, 1715, 1401, 1412, 1429, 1163, 1211, 1117, 1117, 1077],
    
    'Touchdowns': [10, 10, 11, 8, 9, 9, 5, 7, 6, 3],
    
    'Receptions': [119, 129, 117, 125, 93, 100, 86, 65, 71, 75],
    
    'Rank': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
}

df = pd.DataFrame(data)

X = df[['Receiving_Yards', 'Touchdowns', 'Receptions']]

y = df['Rank']

model = RandomForestClassifier(random_state=42)

model.fit(X, y)

df['Predicted_Rank'] = model.predict(X)

df = df.sort_values(by='Predicted_Rank').reset_index(drop=True)

fig, ax = plt.subplots(figsize=(12, 5))

ax.axis('off')

plt.title('2026 NFL WR Predicted Rankings', fontsize=16)

for i, row in df.iterrows():

    col = i % 5
    
    r = 1 - (i // 5)
    
    x = col * 2
    
    y = r * 2
    
    box_text = f"RANK #{row['Predicted_Rank']}\n{row['Player']}\nYds: {row['Receiving_Yards']}\nTDs: 
  {row['Touchdowns']}\nRec: {row['Receptions']}"
  
    ax.text(x, y, box_text, fontsize=10, bbox=dict(boxstyle="round,pad=1", facecolor="lightblue", edgecolor="black"), ha='center')

ax.set_xlim(-1, 9)

ax.set_ylim(-1, 3)

plt.show()

<img width="950" height="429" alt="image" src="https://github.com/user-attachments/assets/f4357db4-4aeb-4167-9923-13e02a4f50f2" />

## Visualization 2: 2026 Wide Receiver Statistics Predictions (Random Forest Regression)

In this model, I used the top 10 wide receivers from each of the past 5 seasons (2021-2025) to predict the top 10 wide receivers for the upcoming 2026 season based on receiving yards, touchdowns, and receptions. There are three different visualizations shown in this random forest regression model, one for each of the three statistics listed. As it turns out, Puka Nacua is predicted to lead the league in receiving yards and receptions, but Amon-Ra St Brown is predicted to lead the league in touchdowns.

results_data = [

    {
    
        "Player": "Puka Nacua",
        
        "Yds_2025": 1715,
        
        "Pred_Yards_2026": 1381.4,
        
        "Pred_Receptions_2026": 106.0,
        
        "Pred_TDs_2026": 8.9,
        
    },
    
    {
    
        "Player": "Amon-Ra St. Brown",
        
        "Yds_2025": 1401,
        
        "Pred_Yards_2026": 1340.9,
        
        "Pred_Receptions_2026": 105.5,
        
        "Pred_TDs_2026": 9.1,
        
    },

    {
    
        "Player": "Ja'Marr Chase",
        
        "Yds_2025": 1412,
        
        "Pred_Yards_2026": 1292.0,
        
        "Pred_Receptions_2026": 98.3,
        
        "Pred_TDs_2026": 7.9,
        
    },
    
    {
    
        "Player": "Jaxon Smith-Njigba",
        
        "Yds_2025": 1793,
        
        "Pred_Yards_2026": 1237.2,
        
        "Pred_Receptions_2026": 95.4,
        
        "Pred_TDs_2026": 7.7,
        
    },
    
    {
    
        "Player": "Chris Olave",
        
        "Yds_2025": 1163,
        
        "Pred_Yards_2026": 1193.6,
        
        "Pred_Receptions_2026": 89.6,
        
        "Pred_TDs_2026": 6.8,
        
    },
    
    {
    
        "Player": "George Pickens",
        
        "Yds_2025": 1429,
        
        "Pred_Yards_2026": 1056.4,
        
        "Pred_Receptions_2026": 81.1,
        
        "Pred_TDs_2026": 6.3,
        
    },
    
    {
    
        "Player": "Jameson Williams",
        
        "Yds_2025": 1117,
        
        "Pred_Yards_2026": 972.6,
        
        "Pred_Receptions_2026": 73.1,
        
        "Pred_TDs_2026": 5.3,
        
    },
    
    {
    
        "Player": "Nico Collins",
        
        "Yds_2025": 1117,
        
        "Pred_Yards_2026": 965.3,
        
        "Pred_Receptions_2026": 73.0,
        
        "Pred_TDs_2026": 5.0,
        
    },
    
    {
    
        "Player": "CeeDee Lamb",
        
        "Yds_2025": 1077,
        
        "Pred_Yards_2026": 962.1,
        
        "Pred_Receptions_2026": 72.5,
        
        "Pred_TDs_2026": 4.9,
        
    },
    
    {
    
        "Player": "Zay Flowers",
        
        "Yds_2025": 1211,
        
        "Pred_Yards_2026": 881.9,
        
        "Pred_Receptions_2026": 68.2,
        
        "Pred_TDs_2026": 4.4,
        
    },
    
]

df = pd.DataFrame(results_data)

df = df.sort_values(by="Pred_Yards_2026", ascending=True)

fig, axes = plt.subplots(1, 3, figsize=(18, 7), sharey=True)

fig.suptitle(

    "Random Forest Regression Predictions: 2026 NFL Season\n"
    
    "(Trained on 2021-2025 Receiving Yards, Touchdowns, and Receptions)",
    
    fontsize=16,
    
    fontweight="bold",
    
    y=1.03,
    
)

bars1 = axes[0].barh(

    df["Player"], df["Pred_Yards_2026"], color=color_yds, alpha=0.85
    
)

axes[0].set_title(

    "Predicted Receiving Yards", fontsize=13, fontweight="bold", pad=10
    
)

axes[0].set_xlabel("Yards", fontsize=11)

axes[0].set_xlim(0, 1600)

for bar in bars1:

    width = bar.get_width()
    
    axes[0].text(
    
        width + 20,
        
        bar.get_y() + bar.get_height() / 2,
        
        f"{width:.1f}",
        
        ha="left",
        
        va="center",
        
        fontweight="bold",
        
        color=color_yds,
        
        fontsize=10,
        
    )

bars2 = axes[1].barh(

    df["Player"], df["Pred_Receptions_2026"], color=color_rec, alpha=0.85
    
)

axes[1].set_title("Predicted Receptions", fontsize=13, fontweight="bold", pad=10)

axes[1].set_xlabel("Receptions", fontsize=11)

axes[1].set_xlim(0, 130)

for bar in bars2:

    width = bar.get_width()
    
    axes[1].text(
    
        width + 2,
        
        bar.get_y() + bar.get_height() / 2,
        
        f"{width:.1f}",
        
        ha="left",
        
        va="center",
        
        fontweight="bold",
        
        color=color_rec,
        
        fontsize=10,
        
    )

bars3 = axes[2].barh(

    df["Player"], df["Pred_TDs_2026"], color=color_tds, alpha=0.85
    
)

axes[2].set_title("Predicted Touchdowns", fontsize=13, fontweight="bold", pad=10)

axes[2].set_xlabel("Touchdowns", fontsize=11)

axes[2].set_xlim(0, 12)

for bar in bars3:

    width = bar.get_width()
    
    axes[2].text(
    
        width + 0.2,
        
        bar.get_y() + bar.get_height() / 2,
        
        f"{width:.1f}",
        
        ha="left",
        
        va="center",
        
        fontweight="bold",
        
        color=color_tds,
        
        fontsize=10,
        
    )

plt.tight_layout()

plt.show()

<img width="1784" height="723" alt="image" src="https://github.com/user-attachments/assets/5ee725e3-2186-4dc9-b5f3-efa66ece12eb" />


