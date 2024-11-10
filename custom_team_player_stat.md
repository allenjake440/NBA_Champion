# Team and Player Rating Custom - The Science Behind the Statistic

- **Player Rating Custom** is a weight based formula, formula that assigns a season score to each player on a -50 to 150 scale. This rating takes into player regular season value over replacement, regular season points per game average, players total past mvp votes, player total past dpoy (defensive player of the year) votes, the player total mvp votes from the last 5 seasons, the player total past playoff games played in, and that player associated teams SRS score (average adjusted margin of victory).
- **Team Rating Custom** is simply the average of all Player Rating Custom values for players on that team for the given season. This score represents the overall performance level of the team by summarizing individual player contributions.
- [**Click Here**](https://www.basketball-reference.com/about/glossary.html) For information on the advanced statistics = VORP "Value over replacement"
   
## Methodology - Understanding whats important in the Formula

1. **Weighted Scoring**: Each feature is multiplied by a defined weight (detailed below), determined through insights, trial and error, and domain expertise.
2. **Feature Importance**: To assess feature significance within the player rating metric:
   - First, calculate the average value for each feature.
   - Next, multiply this average by the corresponding weight.
   - Finally, divide each weighted value by the sum of all weighted values to yield the relative importance of each feature.
3. **Pearson Correlation Coefficients**: Whats the PCC for each feature to the result of the metric.

The code and visualizations provided clarify each feature's weight (as a percentage) in calculating the Player Season Rating Custom metric. See the `nba_champ_data` file for complete code details.

### Feature Weights Breakdown

| Feature                           | Description                                                                                      
|-----------------------------------|---------------------------------------------------------------------------------------------------
| `rs_per_game_PTS`                               | Player's regular season points per game average                                                         
| `rs_advance_VORP`                         | Player's regular season value over replacement                                                     
| `SRS`        | Player's associated teams average adjusted margin of victory for the regular season                              
| `sum_mvp_shares_L5S`                         | Player's total past mvp votes amongst the last 5 seasons                                                       
| `sum_dpoy_shares`        | Player's total past dpoy (defensive player of the year) votes                             
| `sum_mvp_shares`                         | Player's total past mvp votes                                                      
| `sum_playoff_games`        | Player's total past playoff games played in                             

### Bar Charts

<div align="center">
  <img src="https://github.com/user-attachments/assets/262d423d-7b4d-461d-a2f7-f7544f28020b)" alt="player_rat_cus">
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/ecc1d909-9a09-40a0-83be-625a6749fce7" alt="player_rat_cus">
</div>

### Code for Player Custom Rating Calculation

```python
player_db['player_rating_custom'] = (
    (player_db['rs_advance_VORP'] * 5) +
    (player_db['sum_mvp_shares_L5S'] * 1) +
    (player_db['sum_dpoy_shares'] * 1) +
    (player_db['SRS'] * 2) +
    (player_db['sum_playoff_games'] * .0005) +
    (player_db['sum_mvp_shares'] *  .005) +
    (player_db['rs_per_game_PTS'] * 1.5)
)
```
