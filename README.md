# FPL Points Prediction

## Objective
The goal of this project is to build a Machine Learning model to predict Fantasy Premier League (FPL) points for players in future gameweeks of the 2024-2025 Premier League Season. The predictions are designed to support decision-making for team selection and transfers in upcoming rounds.

## Approach
This project uses player-level game-by-game data from an FPL dataset to train and evaluate models. The entire analysis and modelling process is done in Python, within a Jupyter Notebook: `fpl_points_prediction.ipynb`.

## Project Workflow
1. Data Exploration & Cleaning
    
    Initial investigation and cleaning of the dataset, ensuring quality and consistency by removing nulls, fixing column names, and filtering out non-predictive rows.

2. Aggregated Stats Calculation

    * Aggregated team and player stats across the season to date.
    
    * Calculated both total and per-game statistics.
    
    These aggregated stats are used as predictive features, since they would be known before future fixtures.

3. Data Preparation for Modelling

    * Match-specific stats (e.g., goals, assists, xG) are excluded to prevent target leakage, as they wouldn't be available before a fixture is played.

    * The dataset was split based on gameweek in chronological order to reflect how predictions would be made in a real-world scenario (i.e., predicting future games using past data).

4. Position-Specific Modelling
    
    Players were split by position (goalkeepers, defenders, midfielders, forwards) as FPL awards points differently depending on the role. Separate models were trained for each group to account for these differences in scoring systems.

5. Machine Learning Models

    * Models tested include Multiple Linear Regression and Random Forest.

    * Assessed performance using metrics like R², MAE, and RMSE.

    Random Forest was ultimately chosen for final predictions due to its ability to capture non-linear relationships and its superior performance on the validation data.

6. Future Predictions
    
    The selected model was trained on the entire dataset (using season-to-date stats), and predictions were generated for upcoming fixtures across the next six gameweeks.

## Repository Contents

`fpl_points_prediction.ipynb`: Main notebook containing all data preparation, modelling, and predictions.

`merged_gw.csv`: CSV file which contains the FPL data for the first 23 gameweeks of the 2024-2025 season.

`fpl_fixtures.csv`: CSV file with the future 6 gameweek fixtures for each team

`README.md`: Project overview and methodology.

## Citation
@misc{anand2016fantasypremierleague,
  title = {{FPL Historical Dataset}},
  author = {Anand, Vaastav},
  year = {2022},
  howpublished = {Retrieved August 2022 from \url{https://github.com/vaastav/Fantasy-Premier-League/}}
}