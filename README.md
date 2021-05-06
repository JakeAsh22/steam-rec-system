# Steam Recommendation System:

by Jake Ash

<p align="center"><img src="images/steam_pic.jpeg" width="400" height="250" /></p>

# Overview
This project contains the work of developing a recommendation system for the video game digital distribution site, Steam.

# Business Problem
The summer months are when video games sales tend to drop off. This is no exception to Steam. This recommendation system was created to help keep profits up for steam during these months, when there are seldom new game releases. This brings the need for players to find new games based off the games they have olayed in the past.

# Data
The data was provided by Julian McAuley, an associate professor at University of California San Diego. The website provides 4 datasets in JSON format, which include:
* reviews
* purchases, plays, recommends ("likes")
* product bundles
* pricing information
This data can be reformatted to recommend new games based on the games the user already owns.

# Data Cleaning
The data provided is saved in JSON format, however it uses ' instead of " when saving information. However, professor McAuley includes a short code snippit that properly retrieves the information for you. Then, save this data to a pandas DataFrame. From here, I then reformat the data to retrieve the game id, and create a new user_id. Following this, I then merge explode the game id list in the dataframe, so each game gets its own row in the dataframe. We can then work with this new dataframe for modeling

# Model Selection

I create a SVD model for the predictions, and utilize a grid search to get the best parameters. The grid search determines that n_factors of 20 and reg_all of 0.1 achieves the lowest RMSE score of 0.0012.

# Predictions

Now, lets create the predictions. First off, I create a new user with 4 random values of the top 50 games. Then, I add this new user into a surprise dataset, and then train that new data. After creating this new dataset, I can then make the predictions for the new user. Next, I order these predictions from highest to lowest, to find the best predictions. Finally, instead of returning the game id, I retrieve the game title and return that to the user. 
 


# Next steps
First, I would like to create visualizaitions for this project. After creating these visuilaztions, I would like to create more models for these recommendations. After this, I would like to display more information about these recommended games, like the game image. Finally, I would like to create a simple front end so users can input games they own and see what new games to try!

# Citation:

* Self-attentive sequential recommendation
Wang-Cheng Kang, Julian McAuley
ICDM, 2018

* Item recommendation on monotonic behavior chains
Mengting Wan, Julian McAuley
RecSys, 2018

* Generating and personalizing bundle recommendations on Steam
Apurva Pathak, Kshitiz Gupta, Julian McAuley
SIGIR, 2017