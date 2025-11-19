# Football xG Model
This project was created  by me, voluntarily, driven purely by my passion for data analysis and futsal. I decided to publish it on GitHub to document my learning process, demonstrate my interest in sports analytics, and show that I am committed to improving my skills through real, hands-on projects.

I still have a lot to learn, but this repository reflects my effort to build something meaningful from scratch and to keep growing as I explore the world of football and futsal analytics.
The project aims to build an Expected Goals (xG) model for futsal, using manually collected event data from matches.
Since no public futsal event datasets exist, the project includes a custom data collection process, feature engineering, and the first version of a machine learning model that predicts the probability that a shot becomes a goal.


**Project Overview**

  In football (soccer), xG models are widely used.
However, for futsal, similar resources are extremely limited.

This project:
Defines a custom futsal event dataset
Computes key features such as shot distance and shot angle
Trains a machine learning model (Logistic Regression)
Produces xG predictions for each recorded shot
Includes visualizations such as futsal pitch maps with shot markers
The goal is to create a foundation for deeper analytics in futsal.

📝 Dataset Description

Each shot is manually tagged with location and contextual data.

**Main Columns**
Column          	Description
x, y:	            Shot location on futsal pitch (0–40 width, 0–20 height)
distance:	        Distance from the shot location to the goal center
angle:            Shot angle toward the center of the goal (radians)
shot_type:	      Normal shot, header, volley, etc.
body_part:	      Foot used
pressure:	        Whether the shot was pressured
first_time	      First-time shot (0/1)
under_pressure:	  Under pressure from opponent (0/1)
goal:	            Target variable — goal scored (1) or not (0)


⚙️ Feature Engineering

The notebook contains Python code that calculates:

Distance

df['distance'] = np.sqrt((goal_x - df['x'])**2 + (goal_y - df['y'])**2)

Angle

df['angle'] = np.arctan2(goal_y - df['y'], goal_x - df['x'])

Model

The first version uses:

Logistic Regression

Train/Test split is used for evaluation, producing metrics such as:

Accuracy

ROC–AUC (if both classes exist)

Predicted xG values (probabilities)

The model outputs a new column: **xg_pred**

Visualizations

The project includes a custom futsal pitch drawing using Matplotlib.
Shots are plotted as:

🟢 green dots → goals

🔴 red dots → missed shots






