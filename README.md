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
   * *Flight Number vs. LaunchSite*
     
     The chart visually compares the launch activity and apparent success rates across three different Launch Sites over the sequence of Flight Numbers. CCAFS SLC       40 is the most frequently used site, while KSC LC 39A appears to have the highest success rate with fewer launches.

     <img width="2553" height="489" alt="image" src="https://github.com/user-attachments/assets/ecbd3ac1-af93-4b23-a1b5-e7296d3a17fc" />

   * *Payload vs. Launch Site*

      Now if you observe Payload Mass Vs. Launch Site scatter point chart you will find for the VAFB-SLC launch site there are no rockets launched for                   heavypayload mass(greater than 10000).

      <img width="1551" height="489" alt="image" src="https://github.com/user-attachments/assets/8a8b5845-009a-4184-902f-f10323bf93d2" />

   * *Launch Success Yearly Trend*
     
     You can observe that the success rate of launches has shown a steady upward trend since 2013, consistently improving year after year until 2020. This              indicates significant advancements in technology, precision, and operational efficiency over time, leading to a higher rate of successful missions by the end      of the period.

     <img width="567" height="432" alt="image" src="https://github.com/user-attachments/assets/fa7075db-bc94-4ad6-ae73-eff369153186" />

   * *Launch Sites Displayed on Global Map*

      Folium Circles and markers were used to mark different Launch sites onto the map that was created by the python library folium.
      All the given Launch sites are in proximity to the equator and all of these sites are very close to the coastal regions.

      <img width="1320" height="670" alt="image" src="https://github.com/user-attachments/assets/1a23dd17-c1d6-4a3b-9586-7355b630d32b" />

   * *Distances between launch sites and its proximities*

      The Polyline function in Folium was used to mark and connect key locations near the launch sites, including the nearest coastal areas, railway lines, and          nearby cities such as Titusville, providing a clear visual representation of their proximity to the launch sites.

      <img width="1004" height="381" alt="image" src="https://github.com/user-attachments/assets/dbc24a80-3727-4c92-bd65-dac53a051444" />

+ **EDA using SQL Queries**
  * *Launch Site Names Begin with 'CCA'*

    In this case, the LIKE keyword was used in the SQL query to search for the substring 'CCA' within the Launch_Site column. The wildcard symbol '%' was included     to indicate that the substring can appear anywhere within the cell’s value, allowing for flexible pattern matching in the query results.

    <img width="1133" height="670" alt="image" src="https://github.com/user-attachments/assets/aff4da13-8191-4639-8ce8-ee8e7db87cda" />

  * *Total Payload Mass*

    This SQL query retrieves the sum of all payload masses (in kilograms) from the column payload_mass__kg_ in the table SPACEXTBL. It only includes the rows          where the customer is 'NASA (CRS)', giving the total payload mass launched for that specific customer.

    <img width="942" height="192" alt="image" src="https://github.com/user-attachments/assets/b1e65842-eba3-415b-9d37-a70b016afcb4" />

  * *Average Payload Mass by F9 v1.1*

    The query first filters the rows in the SPACEXTABLE where the Booster_Version equals 'F9 v1.1', and then computes the average value of the payload_mass__kg_       column from those filtered rows.

    <img width="1022" height="198" alt="image" src="https://github.com/user-attachments/assets/814ad508-7ec2-46a1-b253-79342e0a6172" />

+ **Performing EDA Interactive Dashboards**
  * *Pie chart for success count overall*
    * KSC LC-39A (Blue) is the primary site for successful launches, accounting for the largest share at 41.7%.
    * CCAFS LC-40 (Red) is the second most common site for successful launches at 29.2%.
    * VAFB SLC-4E (Green) accounts for 16.7% of successful launches.
    * CCAFS SLC-40 (Purple) accounts for the smallest share at 12.5%.

      <img width="1900" height="912" alt="image" src="https://github.com/user-attachments/assets/a1d8fbb8-23e5-4f01-85b8-1ae652a77af9" />

  * *Pie Chart for The Launch Site with highest Success Ratio*
    
    KSC LC-39A Launch Site has the highest launch success ratio copared to the other Launch sites with a success of 73.9%

    <img width="1898" height="642" alt="image" src="https://github.com/user-attachments/assets/15cb49df-2ee5-4a68-a415-a96c4cbd8e38" />

  * *Payload vs. Launch Outcome scatter plot for all sites*
    
    The chart visually demonstrates the increase in launch reliability and success rate as SpaceX transitioned to newer and more capable Booster Versions (like        FT, B4, and B5), particularly highlighting the successful handling of heavier payloads by these later versions.

    <img width="1895" height="513" alt="image" src="https://github.com/user-attachments/assets/8f98501c-e37c-4f34-b3b4-e1e7b8561919" />

+ ### Model Selection
  * After completing data collection, cleaning, and EDA, the next step was model training. The target variable ‘Class’ was extracted from the dataset and stored       as a NumPy array named ‘Y’, representing the dependent variable to be predicted. Before training, the dataset was divided into training and testing sets using     train_test_split() to ensure proper evaluation of the model’s performance.
  * In this project, four machine learning models were trained and compared to identify the most accurate one. Each model was chosen for its ability to handle         classification tasks efficiently and was trained using the prepared data to predict rocket landing outcomes.
  * The training process utilized GridSearchCV for hyperparameter tuning, allowing the models to test various parameter combinations. This helped in finding the       best-performing configuration that achieved the highest accuracy and minimized overfitting.
  * The Models used were:
    * Support Vector Machine.
    * Classification Trees.
    * K Nearest Neighbors.
    * Logistic Regression.
  * The key insight from this image is that all four machine learning models (SVM, Logistic Regression, Decision Trees, and K Nearest Neighbors) achieved the          exact same accuracy of 84.0% for the SpaceX dataset they were evaluated on.


