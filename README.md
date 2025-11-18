# SpaceX Rocket Predictions
## Overview
This project focuses on analyzing historical SpaceX launch data to predict the success of rocket landings using data science and machine learning techniques. By leveraging data from past missions, the project aims to uncover patterns and build a predictive model that can estimate the likelihood of successful recovery based on various mission parameters such as payload mass, launch site, orbit type, and booster version.
## Objectives
Most of the Space Related Organizations cost a lot more finance to send their rockets into the earth's orbit like around 165 mil, whereas the rockets by SpaceX only costs 65mil we find the reason to that in this project.
## Dataset Details
For this project, data was gathered from multiple sources such as:
* SpaceX’s official website
* Wikipedia page titled “List of Falcon 9 and Falcon Heavy Launches.”
## Methodology
+ ### Data Collection:
  As it has been mentioned above that data was collected mainly from the official spaceX website and through web scraping wikipedia this section will go deeper into explaing how the data was gathered and processed.
  * SpaceX API:
    
    The SpaceX API data was collected by integrating the API into the codebase using Python’s Requests module. The retrieved data, initially in JSON format, was then converted into a Pandas DataFrame for further        analysis and model prediction.
  * WebScraping Wikipedia:
    
    Data was also collected by web scraping the Wikipedia page containing historical SpaceX launch information using Python’s BeautifulSoup library and the Requests module.
  
+ ### Data Warngling
The first step in the data wrangling process was to filter out rockets identified as Falcon 9. The dataset initially contained multiple rocket types, but Falcon 9 was chosen as it had the largest amount of available data. Focusing on a single rocket type helped ensure consistency and reduced potential bias during model training.

Additionally, the dataset contained missing values in the “LandingPad” and “PayloadMass” columns. The null values in PayloadMass were replaced with the column’s mean to maintain data integrity and ensure smoother model performance.
+ ### Exploratory Data Analysis/SQL
+ ### Model Selection

