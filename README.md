# SpaceX Rocket Predictions
## Overview
This project focuses on analyzing historical SpaceX launch data to predict the success of rocket landings using data science and machine learning techniques. By leveraging data from past missions, the project aims to uncover patterns and build a predictive model that can estimate the likelihood of successful recovery based on various mission parameters such as payload mass, launch site, orbit type, and booster version.
## Objectives
Most of the Space Related Organizations cost a lot more finance to send their rockets into the earth's orbit like around 165 mil, whereas the rockets by SpaceX only costs 65mil we find the reason to that in this project.
## Dataset Details
For this project, data was gathered from multiple sources such as:
* SpaceX’s official website
* Wikipedia page titled “List of Falcon 9 and Falcon Heavy Launches.”
* The dataset containes attributes that are:
  
    * `FlightNumber`: Indicates the continuous launch attempts.
  
    * `Date`: The date at which the launch was scheduled.
  
    * `BoosterVersion`: The Booster Version of the Rocket that was launched.

    * `PayloadMass`: The payload mass of the rocket that was launched.
  
    * `Orbit`: The orbit that the rocket was launched to.
  
    * `LaunchSite`: The launch site of the rocket

    * `Outcome`: The outcome of the launch.
  
    * `Flights`: Binary variable that indicates the successful launch of the rocket.
  
    * `GridFins`: Binary variable that indicates the presence or absence of grid fins.
  
    * `Reused`: Boolean variable that indicates whether the rocket was reused.
  
    * `Legs`: Boolean variable indicating the presence or absence of Legs in the rocket.
  
    * `LandingPad`: Informing that does the rocket had a landing pad or not.
  
    * `ReusedCount`: Indicating the amount of times a rocket has been reused.
  
    * `Serial`: Gives information about the Serial number given to each rocket.

    * `Longitude`: Provides information related to the longitude.

    * `Latitude`: Provides information related to the latitude.

    * `Class`: The target variable that is to be predicted. Its a Binary variable that indicates whether the rocket landed successfully or not.
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
+ ### Exploratory Data Analysis
Exploratory Data Analysis (EDA) was performed using Python libraries such as Pandas, Matplotlib, and Seaborn. These tools were primarily used to create scatter plots between various parameters, including Launch Site, Booster Version, Orbit Type, Flight Number, and Payload Mass. The main goal of this phase was feature engineering—to identify which variables most strongly influenced the prediction of launch outcomes.

Additionally, bar charts were utilized to analyze the success rate across different orbit types, while line charts were used to observe yearly trends in rocket success rates, providing valuable insights into SpaceX’s performance over time.

+ **EDA using python libraries**
  
Exploratory Data Analysis (EDA) was performed using Python libraries such as Pandas, Matplotlib, and Seaborn. These tools were primarily used to create       scatter plots between various parameters, including Launch Site, Booster Version, Orbit Type, Flight Number, and Payload Mass. Here are few of the plots that were created during the project:-

+ *Flight Number vs Launch Site*

    The chart visually compares the launch activity and apparent success rates across three different Launch Sites over the sequence of Flight Numbers. CCAFS SLC       40 is the most frequently used site, while KSC LC 39A appears to have the highest success rate with fewer launches.

    <img width="2553" height="489" alt="image" src="https://github.com/user-attachments/assets/3a0aa7c9-1432-448f-bab8-0e2d301b8fba" />

+ **EDA using SQL Queries**
+ **Performing EDA Interactive Dashboards**
+ ### Model Selection

