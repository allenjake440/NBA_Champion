# Team and Player Rating Custom - The Science Behind the Statistic

- **Player Rating Custom** is a regression-based, scaled formula that assigns a season score to each player on a -50 to 150 scale. This rating takes into player regular season value over replacement, regular season points per game average, players total past mvp votes, player total past dpoy (defensive player of the year) votes, the player total mvp votes from the last 5 seasons, the player total past playoff games played in, and that player associated teams SRS score (average adjusted margin of victory).
- **Team Rating Custom** is simply the average of all Player Rating Custom values for players on that team for the given season. This score represents the overall performance level of the team by summarizing individual player contributions.
- [**Click Here**](https://www.basketball-reference.com/about/glossary.html) For information on the advanced statistics = VORP "Value over replacement"
   
## Methodology 

1. **Feature Scaling**: Each feature is absoluated min-max scaled.
2. **Weighted Scoring**: Features are multiplied by specific weights (detailed below) based on insights, trial and error, and domain expertise.

The code and visualizations provided clarify each feature's weight (as a percentage) in calculating the QB Season Rating Custom metric. See the `nba_champ_data` file for complete code details.

### Feature Weights Breakdown

| Feature                           | Description                                                                                       | Weight (%) |
|-----------------------------------|---------------------------------------------------------------------------------------------------|------------|
| `rs_per_game_PTS`                               | Player's regular season points per game average                                                         | 42.99     |
| `rs_advance_VORP`                         | Player's regular season value over replacement                                                      | 35.54      |
| `SRS`        | Player's associated teams average adjusted margin of victory for the regular season                              | 16.70      |
| `sum_mvp_shares_L5S`                         | Player's total past mvp votes amongst the last 5 seasons                                                       | 2.43      |
| `sum_dpoy_shares`        | Player's total past dpoy (defensive player of the year) votes                             | 2.23      |
| `sum_mvp_shares`                         | Player's total past mvp votes                                                      | 0.03      |
| `sum_playoff_games`        | Player's total past playoff games played in                              | 0.08      |

### Bar Chart Feature Weights Breakdown

<div align="center">
  <img src="https://github.com/user-attachments/assets/eb280eb5-69f3-4723-afa9-88e6f00da373" alt="player_rat_cus">
</div>

### Code for Player Custom Rating Calculation

```python
player_db['player_rating_custom'] = (
    (player_db['rs_advance_VORP'] * 62.499999999999915) +
    (player_db['sum_mvp_shares_L5S'] * 4.265999999999985) +
    (player_db['sum_dpoy_shares'] * 3.9280000000000266) +
    (player_db['SRS'] * 29.359999999999957) +
    (player_db['sum_playoff_games'] * 0.1409999999998981) +
    (player_db['sum_mvp_shares'] *  0.04409000000000404) +
    (player_db['rs_per_game_PTS'] * 75.59999999999988)
)
```
