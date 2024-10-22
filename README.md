# Predicting the NBA Champion Using Machine Learning

<p align="center">
  <img src="https://github.com/allenjake440/NBA_Champion/assets/134075534/b7d724d9-5452-45d2-abac-81128c34a8f6" alt="NBA Champion Art">
</p>

## Overview

This project leverages machine learning to predict the NBA Champion for every upcoming season.

### [Read the Medium Article](https://medium.com/@allenjake440/predicting-the-nba-champion-with-machine-learning-25e3a45a82f9)

---

## Data Sources

Data has been acquired since 1950 from [Basketball Reference](https://www.basketball-reference.com/about/glossary.html).

---

## Project Details

This is a fully coded, automated NBA Champion Prediction Project. Follow the steps below to ensure your data is up-to-date and to run the prediction model.

### Steps to Set Up and Run the Project

1. **Update Franchise Index**:
   - Manually update the `custom_team_franchise_index` DataFrame if a new franchise enters the league.
   - Make sure to add the new data to the CSV file while keeping the data layout unchanged.

2. **Update Season Index**:
   - Every season, manually update the `custom_team_season_index` DataFrame following the format already in the file.
   - You can also add matchup values, but again, ensure that the data layout remains consistent.

3. **Run the Python Notebooks**:
   - Once the manual updates are complete, execute the Python notebooks in the following order:
     - `nba_web_scraper.ipynb`
     - `nba_champ_data.ipynb`
     - `nba_champ_ml.ipynb`

---

## The Project Outline

![Web Scraping](https://github.com/user-attachments/assets/2bef75b4-47e0-4ace-afe3-680b3ced56ef)

The project involves web scraping for real-time data acquisition from reliable sources, ensuring that the predictions are based on up-to-date stats.

---

### Notes

- Ensure the data layout in the CSV files remains unchanged when updating them.
- This project automates the data scraping, data preparation, and machine learning model execution.
