#Customer Behavioral Analysis for a Wearable Tech Company - Bellabeat
- Github repository at: https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis
- File name: Bellabeat customer trend analysis.ipynb
- Dataset Name: Fitabase Data
- Dataset Link: <a name="dataset_link"></a> https://www.kaggle.com/datasets/michaelpetersen2022/fitabase-data-31216-41116

## Project Description
In this case study, we will perform data analysis for Bellabeat, a high-tech manufacturer of health-focused products for women. We will follow the steps of the data analysis process: **ask, prepare, process, analyze, share, and act**.

## Table of Contents
1. [Introduction](#introduction)
    1. [Problem Statement](#sec1p1)
    2. [Thought Procedure](#sec1p2)
    3. [Questions to answer](#sec1p3)
2. [Description of the dataset](#section2)
    1. [Introduction to dataset](#sec2p1)
    2. [Table of dataset and contents](#sec2p2)
3. [Procedure and Code Snippets](#section3)
    1. [Loading libraries](#sec3p1)
    2. [Reading files/ loading datasets](#sec3p2)
    3. [Inspecting Dataframes](#sec3p3)
	    - Inspecting column names
	    - Inspecting datatypes for columns
	    - 5 Number Summary
4. [Data Processing](#section4)
    1. [Correcting the datatype of features](#sec4p1)
    2. [Removing duplicates](#sec4p2)
    3. [Removing nulls](#sec4p3)
    4. [Imputing outliers](#sec4p4)
5. [Feature Engineering](#section5)
    1. [Feature creation](#sec5p1)
    2. [Feature extraction](#sec5p2)
    3. [Feature transformation](#sec5p3)
6. [Analysis, visualizations and Observations](#section5)
7. [Key Suggestions](#key_suggestions)
8. [References](#references)

## 1. Introduction <a name="introduction"></a>
- The analysis has been carried out in Jupyter notebook with file name given above. To view this file, download it from [this](https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/Bellabeat%20customer%20trend%20analysis.ipynb) repository and start Jupyter notebook in the folder containing the file.
- Alternatively, view a static version of the notebook (by providing its GitHub url) using [Jupyter Nbviewer](https://nbviewer.org/).

### 1.1. Problem Statement <a name="sec1p1"></a>
Analyze smart device usage data in order to gain insight into how consumers use non-Bellabeat smart devices.

### 1.2. Though Procedure <a name="sec1p2"></a>
We will follow the steps of the data analysis process: *ask, prepare, process, analyze, share, and act*.
- Ask: We brainstorm by asking SMART questions that help us solve the business problem.
- Prepare: In this phase we gather the required data for the purpose of analysis. In this case the data has been collected from Kaggle the [link](https://www.kaggle.com/datasets/michaelpetersen2022/fitabase-data-31216-41116) has been mentioned above.
- Process: We begin with understanding the raw data such as identifying the data available, nature of data, data type of features, and data inconsistancoes and errors. Then we clean the data - droping / imputing null values, droping the duplicate entries(if any), making datatype conversions wherever needed, imputing any outliers.
- Analyse: Once the data has been process and ready for analysis, we carry out various analytical operations on the data. Such as 5 Number summary, aggregation, merging of datasets, identifying trends, visualising data, etc.
- Share: In this phase we share the insights/ observations gained from the analysis and from the visualizations. These observations and analysis serve as the foundations for the act phase where we give key recommendations to the planning and executive team  based on the insights obtained during the analysis.
- Act: We give key recommendations based on the insights uncovered that will help address the problem statement.

### 1.3. Questions to ask <a name="sec1p3"></a>
- 1. What is the average steps covered by people each day?
- 2. What percentage of people cover steps less than the population mean?
- 3. What percentage of people cover steps greater than the recommended average 8000 daily steps?
- 4. Which day of the week people are least active physically?
- 5. What are the durations in a day where people's activity levels go down.
- 6. How much additional calories on an average are burnt by people who achieve their daily target of 8000 steps when compared to those who do not achieve the daily target?
- 7. What is the general heart rate trend throughout the day?
- 8. Is there any relationship between total sleep time and calories burnt?
- 9. Which days does people sleep the least? 
- 10. What time of the day does people usually sleep?

## 2. Description of the dataset <a name="section2"></a>
The dataset consists of total 18 .csv files that provide details regarding steps taken, distance covered, very active duration, fairly active duration, light active duration, calories burnt, hear rate, sleep patterns,etc.

### 2.1. Introduction to dataset<a name="sec2p1"></a>
- [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/michaelpetersen2022/fitabase-data-31216-41116) (CC0: Public Domain, dataset made available through Mobius): This Kaggle data set contains personal fitness tracker from thirty fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore users’ habits.
- Refer the attached link [here](https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/fitabasedatadictionary102320.pdf) for the data dictionary. 

### 2.2. Table of datasets and contents <a name="sec2p2"></a>
- Below table consists of details of table name and its features. For better understanding of features of each table please refer the [data dictionary](https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/fitabasedatadictionary102320.pdf).

| Table Name                    | Features |
| ----------------------------- | --------------------------------------------------------------- |
| dailyActivity_merged          | "Id,ActivityDate,TotalSteps,TotalDistance,TrackerDistance,LoggedActivitiesDistance,VeryActiveDistance, ModeratelyActiveDistance, LightActiveDistance, SedentaryActiveDistance, VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes, SedentaryMinutes, Calories" |
| dailyCaloriies_merged         | Id, ActivityDay, Calories                                        |
| dailyIntensity_merged         | "Id, ActivityDay, SedentaryMinutes, LightActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryActiveDIstance, Lifght ActiveDIstance, VeryActiveDistance, ModerateActiveDistance" |
| dailySteps_merged              | Id, ActivityDay, StepTotal                                       |
| heartrate_seconds_merged       | Id, Time, Value                                                 |
| hourlyCalories_merged          | Id, ActivityHour, Calories                                      |
| hourlyIntensity_merged         | Id, ActivityHour,TotalIntensity, AverageIntensity              |
| hourlySteps_merged             | Id, ActivityHour, StepsTotal                                    |
| minuiteCaloriesNarrow_merged   | Id, ActivityMinute, Calorie                                     |
| minuiteCaloriesWide_merged     | Id, ActivityHour, Calory00, …..................,Calory60          |
| minuiteIntensityNarrow_merged  | Id, ActivityMinute, Intensity                                   |
| minuiteIntensityWide_merged    | Id, ActivityHour, Intensity00,---------------,Intensity60        |
| minuteMETsNarrow_merged        | Id, ActivityMinute, METs                                         |
| minuteSleep_merged             | Id, Date, Value, LogID                                           |
| minuteStepsNarrow_merged        | Id, ActivityMinute,Steps                                         |
| minuteStepsWide_merged          | Id, ActivityHour, Steps00,….......................,Steps60       |
| sleepDay_merged                | Id, SleepDay, TotalSleepRecords, TotalMinuteAsleep, TotalTimeInBed |
| weightLogInfo_merged           | Id, Date, WeightKg, WeightPounds, Fat, BMI, Ismanual Report, LogId |


## 3. Procedure and Code Snippets <a name="section3"></a>
The ususal procedure is - loading of libraries required for the analysis; Reading files/ loading datasets; Exploratory Data Analysis which covers- Inspecting column names, Inspecting datatypes of each column, 5 Number Summary.

### 3.1. Loading of Libraries <a name="sec3p1"></a>
In order to carry out analysis in python, the very first step is to load the necessary libraries for various operational purposes
- pandas library: to load data sets and for carrying out basic dataframe operations
- datetime library: to carryout out feature extractions from the date type columns
- matplotlib and seaborn: for making visualizations

> Code Snippet

```python
#import os library to interact with the operaing system
import os

#import libraries to load data into dataframe and for operations
import pandas as pd
import numpy as np

#import library to get day names of the week
from datetime import datetime

#import seaborn and matplotlib.pyplot to create visualizations
import matplotlib.pyplot as plt
import seaborn as sns
```

### 3.2. Reading Files/ Loading Datasets <a name="sec3p2"></a>
Pandas is a very versatile library that allows us to import and load data from various sources. In this analysis we are dealing with .csv files, therefore we will be using **pd.read_csv()** function from pandas library to load the csv files into respective Dataframes.

> Code Snippet

```python
#loading the .csv files into dataframes

daily_activity = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\dailyActivity_merged.csv")
heartrate = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\heartrate_seconds_merged.csv")
sleep = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\sleepDay_merged.csv")
sleep_type = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\minuteSleep_merged.csv")
heartrate = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\heartrate_seconds_merged.csv")
hourly_steps = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\hourlySteps_merged.csv")
heart_rate = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\heartrate_seconds_merged.csv")
```

### 3.3. Inspecting Dataframes <a name="sec3p3"></a>
It is of utmost importance to ensure that the data is uniform and has high data integrity. Therefore for the purpose of ensuring the same we carry out below activities.

- Inspecting the columns of the dataframes to check the data types and column names
> Code Snippet

```python
#inspecting the data in daily_activity dataframe
daily_activity.head()
```
<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/check%20col%20names1.PNG">

- Data types of the column can be inspected using the .info() method from pandas library.
> Code Snippet

```python
#inspect the data type of features of the dataframe
daily_activity.info()
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/data%20type.PNG">

- 5 Number Summary refers to the method of calculating the minimum value, 1st quartile, mean, 3rd quartile, and maximum value for the numeric features of dataframes.
This can be easily achieved with the help of .info() method of pandas library.
> Code Snippet

```python
#carry out 5 value summary for the dataframe
daily_activity.describe()
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/describe.PNG">

## 4. Data Processing <a name="section4"></a>
Data processing phase consists of activities such as correcting the data types wherever necessary, removing duplicates, removing nulls and imputing outliers. In this section we will look into all these aspects of data processing.

### 4.1. Correcting the datatype of features <a name="sec4p1"></a>
In this project there are multiple instances where we have to convert the data type of date type features from object (default data type of feature in python after reading a file) to datetime data type. This is achieved with the help of .to_datetime() method of the datetime library.

> Code Snippet

```python
#convert the data type of ActivityDate column to datetype from object data type
daily_activity['ActivityDate'] = pd.to_datetime(daily_activity['ActivityDate'])
```
### 4.2. Removing duplicates <a name="sec4p2"></a>
The data was checked for duplicates in the initial phase of project in excel itself, therefore there was no need to handle duplicates in this case.

### 4.3. Removing nulls <a name="sec4p3"></a>
The data was checked for nulls with the help of microsoft excel and there was no instance of nulls or missing values in the data. Therefore, there is no need to handle the dataframe for nulls. However, in python nulls can be handles in two ways, i.e either imputing the mean; median; mode whatever suits the requirement of the project, or to drop the rows with missing values. The values can be imputed using boolean masking with the help of lambda function, whereas the rows with missing values can be dropped with the .drop(axis=1) method of pandas library.

### 4.4. Imputing outliers<a name="sec4p4"></a>
The data had few outliers but since the quantum of data is not significant altering the outliers may significantly impact the insights of the analysis. Therefore I have decided not to alter the observations with outliers. 

## 5. Feature Engineering <a name="section5"></a>
In this phase of project we have extracted, and transformed the new features for the purpose of analysis.

### 5.1. Feature creation <a name="sec5p1"></a>
In this project we havent deployed creation of a new feature as most of the analysis was possible with either the existing features or by extracting sub features from the existing features. Therefore, feature creation is out of scope for this project

### 5.2. Feature extraction <a name="sec5p2"></a>
In this project we have extracted features such Dayofweek, Hourofday, etc. This can be done with the various methods of datetime library such as dt.dayofweek();  dt.hour(), and with the help of .map() from pandas library.

> Code Snippet

```python
# add a column day_no of the week to dataframe daily_activity
daily_activity['day_no'] = daily_activity['ActivityDate'].dt.dayofweek

# add a column day of the week to dataframe daily_activity
daily_activity['day_of_week'] = daily_activity['day_no'].map({
    0: 'Monday',
    1: 'Tuesday',
    2: 'Wednesday',
    3: 'Thursday',
    4: 'Friday',
    5: 'Saturday',
    6: 'Sunday'
})
```

### 5.3. Feature transformation <a name="sec5p3"></a>
In order to carry out the visualization we sometimes have to aggreagate the data. By aggregating the data with the help of .groupby() the pandas usually change the index of the aggregated dataframe. therefore there is aneed to reseting the index in order for the python to recognise the dataframe rows and index. therefore we usually reset the index after aggregation.

> Code Snippet

```python
day_activity_agg = daily_activity.groupby(['day_no','day_of_week']).agg({'TotalSteps': 'mean', 'TotalDistance': \
                                                       'mean', 'VeryActiveMinutes': 'mean', 'FairlyActiveMinutes': 'mean'})
#resetting the index for the aggregated table

d = {'TotalSteps_mean':'TotalSteps_mean',
     'TotalDistance_mean':'TotalDistance_mean',
     'VeryActiveMinutes_mean':'VeryActiveMinutes_mean',
     'FairlyActiveMinutes_mean':'FairlyActiveMinutes_mean'
     }
day_activity_agg = day_activity_agg.rename(columns=d).reset_index()
print(day_activity_agg)
```

## 6. Analysis, visualizations and Observations <a name="section5"></a>
In this section we will try to find the answer to the questions we described above in the intoduction section:

- 1. What is the average steps covered by people each day?

People cover average 7637 steps on a day to day basis. Some days, the minimum steps covered is zero. Zero value can be justified in two situations, one - if the user was absolutely dormant for the entire day sleeping throughout the day which is less liekly, second reason which makes more sense is that either the device did not gather the steps correctly or the user did not wear the watch entire day. This is most likely to happen on weekends or holidays.

> Below shows the statistical summary of steps covered by people on average

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/describe.PNG">

- 2. What percentage of people cover steps less than the population mean?

54.55% of users cover steps below the average steps of total population.

- 3. What percentage of people cover steps greater than the recommended average 8000 daily steps?

42.42% of users cover more than the recommended 8000 daily steps

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/steps%20below%20average..PNG"> 

- 4. Which day of the week people are least active physically?

On an average people's activity levels seems stable. There is only a slight difference on Saturdays and Tuesdays where the activity levels seem slightly above the threshold, whereas on thursdays and fridays the activily levels are relatively low.

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/steps%20taken%20each%20day.png">

- 5. What are the durations in a day where people's activity levels go down.
From the visualizations it can be said that people's activity levels usually take a dip at 11 am, 1 pm, 3 pm, and then falls steeply after 7 pm.

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/steps%20taken%20each%20hour.png">

- 6. How much additional calories on an average are burnt by people who achieve their daily target of 8000 steps when compared to those who do not achieve the daily target?

Mean(calories burn) for people who covered less than 8000 steps: 1991.99
Mean(calories burn) for people who covered greater than 8000 steps: 2668.49
People who covered 8000 steps daily, burnt 676.5 calories more on an average than people who covered less than 8000 steps daily.

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/calories%20vs%20sleep.png">
<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/steps%20below%20average..PNG">

- 7. What is the general heartrate trend throughout the day?

- A healthy heart has a operational hearbeat range of 60 bpm to 80 bpm. A well trained heart can even lower it to 50 bpm to 70 bpm. A lower average bpm indicates a healthy heart. The average heartrate trend throughout the day is within the resting heart rate limits of **60 bpm to 80 bpm**. 
- Peaks are observed at few instances every day. For example, first peak is observed at **9 am** which is ususlly the reporting time at offices. Then, from **12 pm** onwards there is a relatively higher heart rate. This has to be due to the reason that people are focused in their work where the heart rate might reach the upper limits of resting heart rate which is 100 bpm. Anything above 100 bpm can be a sign of stress.
- We again see heartrake peaking from **4 pm till 6 pm**. The most probable reason for this can be the period when people start to packup for the day and head back home or engage in a physical activity.
- We see a steep decline in heartrate from **00 am till 4 am**. This is due to the reason that people enter the phase of REM sleep during which the heartbeat slows down drastically. There is a slight dip in heartrate at **11 am, 1 pm and 3 pm**. This might be due to the reason that people take breaks from work, have lunch and snacks between work.

> Code Snippet:
```python
heart_rate = pd.read_csv("E:\Data Analytics stuff\Coursera Data analytics and Adv Data Analytics\Google Data Analytics Project\Capstone 2\Fitabase_Data_04122016_05122016\heartrate_seconds_merged.csv")
heart_rate_agg = heart_rate.groupby(['hour'])['Value'].mean()
heart_rate_agg = heart_rate_agg.reset_index()

#create a line chart to show the general trend of heartbeat each hour.
fig,axes = plt.subplots(figsize=(10,4))
sns.lineplot(heart_rate_agg,x='hour',y='Value').set_xticks(range(0,24,1))
plt.axhline(y= 60, color = 'green', ls = '--')
plt.axhline(y= 80, color = 'orange', ls = '-.')
plt.text(0,60.5,'Lower resting heart rate')
plt.text(0,80.5,"Upper resting heart rate")
axes.set_title("Genral trend: Heartbeat each hour")
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/heartbeat%20each%20hour.png">

- 8. Is there any relationship between the total sleep time and calories burnt ?

From the scatterplot no concrete inferece can be derived that people who slept between 300 min to 600 min burnt more calories comapred to those who slept more than 600 minutes or less than 300 minutes. Though, major concentration is observed between 400 min to 500 min which can also be seen in the histogram.
>Code Snippet:
```python
#merge the daily activity and daily sleep dataframe
sleep_cal_joined = pd.merge(daily_sleep_agg, daily_activity,on = ['Id','SleepDay'],how = "inner")

#create a scatterplot to visualize the total sleep vs calories burnt
sns.scatterplot(sleep_cal_joined,x='TotalMinutesAsleep',y='Calories')

#create a distribution plot to understan how many people sleep between 6 to 8 hours
sns.displot(sleep_cal_joined['TotalMinutesAsleep'], kde = False )
plt.grid()
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/calorie%20vs%20sleep..png">
<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/sleep%20hist.png">

- 9. Which days does people sleep the least? 

There isnt a significant difference in the average sleep hours on a day to day basis. But, people seem to get more sleep on Saturdays and Sundays. Also there is an unusally greater sleep duration on Wednesdays as compared to other weekdays.
>Code Snippet:
```python
#create a new column to save the day name for each date
daily_sleep_agg['dayno_of_sleep'] = daily_sleep_agg['SleepDay'].dt.dayofweek
daily_sleep_agg['day_of_week'] = daily_sleep_agg['dayno_of_sleep'].map({
    0: 'Monday',
    1: 'Tuesday',
    2: 'Wednesday',
    3: 'Thursday',
    4: 'Friday',
    5: 'Saturday',
    6: 'Sunday'
})

#create a barplot to see daywise sleep patterns
sns.barplot(daywise_sleep_agg,x='day_of_week',y='TotalMinutesAsleep')
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/sleep%20days.png">

- 10. What time of the day does people usually sleep?

From the bar graph, it can be seen that people begin to go to bed by 9 pm, and by 9 am most of the people are awake. It should be noted that the graph does not show bar graphs for awake state. This can be due to the fact that the device does not capture awake state effectively, or that asleep is the default data caputred and is contrary to awake and therefore not captured by the device.
>Code Snippet:
```python
#create a new column to extract and save the sleep hour
sleep_state['date'] = pd.to_datetime(sleep_state['date'])
sleep_state['hour'] = sleep_state['date'].dt.hour
#Aggregating Sleep State dataframe on hourly level to understand the sleep states at different hour
#value column has values: 1 = Asleep, 2= Restless, 3=Awake

#count the number of observations for various sleep values for each hour of the day
sleep_state_agg = sleep_state.groupby(['hour','value'])['Id'].count().reset_index()

#Map the sleep state to value column for easier understanding
sleep_state_agg['value'] = sleep_state_agg['value'].map({1:"Asleep",2:"Restless",3:"Awake"})

#rename the id column to Count 
sleep_state_agg.rename(columns = {'Id':"Count"})

#Create a multi bar plot to see what time does people wake up and go to sleep
fig,axes = plt.subplots(figsize=(12,3))
sns.barplot(sleep_state_agg,x='hour',y='Id', hue='value').set_xticks(range(0,24,2))
axes.set_ylabel("Count")
axes.set_title("Count of hourwise sleep state"
```

<img src="https://github.com/AnalyticsAndOm/DA_Project_Bellabeat_Customer_Behavioral_Analysis/blob/main/sleep%20hours.png">

## 7. Key Suggestions <a name="key_suggestions"></a>

Based on the insights from the analysis, below are the key suggestions:
- 1. Since 54.5% of people covered steps less than the average steps covered by the population and only 42% of population cover steps more than the recommended 8000 steps daily, Bellabeat products can incorporate a feature that sends a nudge or a notification that prompts the users to achieve their hourly steps target which shall help the users to achieve their daily steps target.
  2. Bellabeat app can have a blog session that educates the users about comparative calorie burn achieved by people who successfully achieve daily steps target of 8000 steps vs people who fialed to achieve daily 8000 steps target.
  3. It is observed that people's hear rate tend to increase slightly during work hours. Bellabeat app can remind the users to take short zen moments where the users can focus on their breathing, and meditate in order to control their heart rates.
  4. The bellabeat app can also post educational post on its blog, informing users about the benefits of short zen moments between work along with various short duration meditation and breathing techniques that can help users calm themselves and focus better.
  5. Since the general trend indicates that people go to bed around 9 pm, bellabeat products can nudge the customers to have their dinner 2 hours before the sleep as it is proven to improve the quality of sleep. Also, the app can notify the customers to have ample water intake 30 min before they go to bed as it improves gut health and improves overall health.

## 8. References <a name="references"></a>

**General:**

- [1]  Anaconda Distribution
https://www.anaconda.com/

- [2] Python Software Foundation
https://www.python.org/

- [3] Project Jupyter
https://jupyter.org/

- [4] Sharing Jupyter notebooks
https://nbviewer.jupyter.org/

- [5] seaborn: statistical data visualization
https://seaborn.pydata.org/index.html#

- [6] matplotlib: Python plotting library
https://matplotlib.org/

- [7] The Tips data set from Michael Waskom
https://github.com/mwaskom/seaborn-data/blob/master/tips.csv

- [8] Description of what is contained in the tips set
https://www.kaggle.com/ranjeetjain3/seaborn-tips-data set

- [9] scikit-learn: Machine Learning in Python
https://scikit-learn.org/stable/index.html

- [10] statsmodels: Statistics in Python
https://www.statsmodels.org/stable/index.html

- [11] scipy.stats : Statistics with SciPy
https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html

**Exploratory data analysis:**

- [12] Exploratory Statistical Data Analysis with a Real data set using Pandas
https://towardsdatascience.com/exploratory-statistical-data-analysis-with-a-real-data set-using-pandas-208007798b92

- [13] How to investigate a data set with Python
https://towardsdatascience.com/hitchhikers-guide-to-exploratory-data-analysis-6e8d896d3f7e

- [14] Data analysis with Python
https://medium.com/@onpillow/01-investigate-tmdb-movie-data set-python-data-analysis-project-part-1-data-wrangling-3d2b55ea7714

- [15] Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython. 
Wes McKinney. ISBN-13: 978-1491957660 ISBN-10: 1491957662

- [16] Pandas In 10 Minutes || Wes McKinney
https://www.youtube.com/watch?v=1MGCD8SQp3k

- [17] Good description of quartiles on Seaborn plots
https://towardsdatascience.com/analyze-the-data-through-data-visualization-using-seaborn-255e1cd3948e
