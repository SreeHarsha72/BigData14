## ITCS 6100 Big Data Analytics for Competitive Advantage - Fall 2022
### First Street Foundation (FSF) Flood Risk Summary Statistics
### TEAM MEMBERS

Harika Moole – 801318334

Noel Vijay – 801274982

Ram Vishal Singh – 801307348

Ritvik Kondabathini – 801275238

Sarath Chillakuru – 801314925

### COMMUNICATION PLAN

 Methods of Communication: Slack for day-to-day conversation and syncing. Email for a more formal and documented way of communication.

 Communication response times: All team members try to communicate at the earliest possible time. Any absence or away-from-work status is intimated in the communication channel.

 Meeting attendance: Meeting attendance is not fully mandatory. This implies that it is not necessary for all team members to attend every meeting but at least 3 out of 5 members need to be present. The ones not attending shall inform the rest well in advance. It is appreciated if all can attend anyways.

 Version control: All changes by the team members are pushed to the artifact by raising pull requests which are first reviewed by the peers before merging.

 Division of work: Work is divided between the team members in the form modules. Any overload can be brought to the notice of the other members so it can be divided or redistributed.

### PROJECT ARTIFACT REPOSITORY

All of our work can be found in the public repository that has been created on GitHub. The link to the repository is - https://github.com/nvijay1/bigdata14

### BUSINESS PROBLEM, OPPORTUNITY, DOMAIN KNOWLEDGE BUSINESS PROBLEM 
The dataset presents CSV files of flood statistics for the 48 contiguous states at the congressional district, county, and zip code level. The CSV for each of these geographical extents includes statistics on the number of properties at risk according to FEMA, the number of properties at risk according to First Street Foundation. The flood statistics data can help us understand and gain insights on how well the government or an organization needs to be prepared to during floods and helps us to get an estimate of the damages that would incur. DOMAIN REFERENCES https://assets.firststreet.org/uploads/2020/06/first_street_foundation__first_national_flood_risk_assessment.pdf
https://firststreet.org/research-lab/

### SELECTION OF DATASET DATASET 
https://registry.opendata.aws/fsf-flood-risk/

### RESEARCH OBJECTIVES AND QUESTIONS

### RESEARCH OBJECTIVE

Using the historical data from FEMA and First street foundation, we aim to predict the number of properties that would be affected in case of floods with various risk factors. We also intent to study data from the two organizations and provide a comparative analysis of how each organization calculates the number of properties affected with floods of various risk scores.

### EXAMPLE DESCRIPTIVE QUESTIONS

Comparing the annual peak flows by regions (for a tenure of 10 years or more)
Where are there unexpectedly high building and content loss, given the number of structures?
Identifying areas of high potential losses.
What are the historic flood outlines for each state?
EXAMPLE PREDICTIVE QUESTIONS

We will forecast the likelihood of a 100-year flood in each state in any given year?
Find the zip codes with the highest percentage of properties at risk of flooding in the future.
Find the counties in each state that are most at risk.

### DELIVERABLE - 2

The Flood risk summary dataset is divided into four parts providing summary statistics correlating to each state, district, county, and zip code. Four files include the data collected by First street foundation and FEMA.

Fsf_flood_zcta_summary.csv
Fsf_flood_county_summary.csv
Fsf_flood_cd_summary.csv
Fsf_flood_state_summary.csv

We have utilized state, county, and district data for data visualization and as a part of data modeling we have utilized the zip code data. The dataset includes the number of properties damaged by floods with various flood risk factors ranging from 1-10. The data also includes the number of First Street properties with flooding in 30 years in the Return Period 500 scenario. A 30-year flood does not necessarily happen once in 30 years, it can happen more times or none at all. A 30-year flood has a 1-in-30 (30%) chance of happening in any one year.

### EXPLORATORY DATA ANALYSIS

We used the AWS Sage Maker Notebook instance for the exploratory data analysis and AWS Quick sight for data visualization which helps to gain insights on the data. Written code to perform null checks on rows and columns and see if there are any missing values from the four files in our Flood Risk Summary - Flood_risk_zipcodes; Flood_risk_cd; Flood_risk_county; Flood_risk_sate.

### Data Understanding

To understand the schema of our data source, we have used AWS Glue. AWS Glue discovers our schema and defines the data types for the data. After analyzing the data, it stores the data in the data source. The Crawler feature is used to find the dataset schema. After seeing the schema and data types defined using Glue, AWS Athena is used for querying the data and finding the insights from the dataset.


### AWS GLUE
![alt text](/Screenshots/Glue1.png)
![alt text](/Screenshots/Glue2.png)


### AWS ATHENA
![alt text](/Screenshots/Athena1.png)
![alt text](/Screenshots/Athena2.png)
![alt text](/Screenshots/Athena3.png)


### Data Preparation

For data modeling, we need to prepare the data and segregate it into three categories to set different levels of flood risks. We have used file - fsf_flood_zcta_summary to classify data. We have used AWS Sage maker Notebook Instance and using pandas, we have written the code to organize and group the data as required for the following data modeling steps. We have combined four columns- count_floodfactor1, count_floodfactor2, count_floodfactor3, and count_floodfactor4 to form a low-risk factor combined value. We combined count_floodfactor5, count_floodfactor6, and count_floodfactor7 cues data to derive a medium risk factor. Finally, for the high-risk factor value, we have used count_floodfactor8, count_floodfactor9, and count_floodfactor10.

Please find the link below for the data preparation and exploratory data analysis.
[Data Analysis and Preparation Steps](/Data%20Analysis.ipynb)



We also utilized Sagemaker studio Data Wrangler  to create a data flow by importing data from S3 bucket and performing data transformations, and visualizations.

![alt text](/Screenshots/Dataflow.png)



### DATA VISUALIZATION
As a part of data visualization, we have utilized AWS Quick Sight service for creating a dashboard.

### Properties damaged by state:

Here we use a map of America to visualize the number of properties damaged. This is indicated by the color tone of the state. A Histogram shows the Properties difference between FEMA and First Street by Count. We also have a Pie-chart that shows Properties difference between FEMA and First Street by Percentage.
![alt text](/Screenshots/Visualization1.jpg)


### Return period comparison for 30 years:
In the second visualization, we predicted the occurrence of 5,100 and 500 return period flood possibilities in the next 30 years for all the states and counties. Here we make use of Bar charts and a pie chart to visualize the Properties Damaged in 5 years, 100 years, and 500 years Return Periods for the Current Year vs 30 Years. We also use a stacked bar chart to compare all return periods for 30 years.

![alt text](/Screenshots/Viz2.jpg)



### Risk factor comparison:

This dashboard compares one risk factor each from high, medium, and low ranges. We have a line chart with risk factors 2, 5, and 10. There are also three treemaps for each of these separately.

![alt text](/Screenshots/viz3.jpg)



### DELIVERABLE - 3
For Deliverable 3, we explore various ML modeling through AWS Sagemaker Canvas and also AWS Sagemaker Notebook Instance. The data utilized is the zipcode data 

### ANALYTICS AND MACHINE LEARNING
We developed a regression model to predict the number of properties destroyed by utilizing other data columns as features. We make use of the AWS Sagemaker canvas service to design a suitable regression model to predict the number of properties damaged.

We begin the canvas by selecting the type of problem, which would be regression in our case. 
Next, we are required to connect the data source which would be our zip code data file.
Before modeling we are required to validate our data which would remove nulls and if required convert categorical variables into numeric vectors and also provide statistical analysis on various columns. We next select our target column which is to be predicted which in our case is the count property.

![alt text](/Screenshots/ML1.png)
![alt text](/Screenshots/ML2.png)


In the next step we are required to select columns that are required features for the regression model.

![alt text](/Screenshots/ML3.png)
![alt text](/Screenshots/ML4.png)

The tool provides various visualizations to understand the features that help with data modeling.

Below heat map represents the correlations among the various features:

![alt text](/Screenshots/ML5.png)


We then utilize the Quick build option, to generate a linear regression model which takes features as input data and fits the model to the data.

### EVALUATION AND OPTIMIZATION

The model evaluation is done on various metrics such as MAE, MSE, RMSE, etc. Among the various metrics, the best results are selected for the model.

![alt text](/Screenshots/ML6.png)
![alt text](/Screenshots/ML7.png)


Predictions are made using the selected model and the test score is evaluated on the selected metric.

### PREDICTIONS
Following are the model prediction results.
![alt text](/Screenshots/ML8.png)


The complete predictions file is available at [Flood_Summary_predictions](/Flood_Summary_predictions.csv)

### RESULTS

The model generated is a simple linear regression model and it is evaluated on RMSE. The value of RMSE for our model is 165.417

![alt text](/Screenshots/ML9.png)


### FUTURE WORK AND COMMENTS

It is important to clean the data sample in the modeling process to ensure that the observations best represent the problem. The presence of outliers in a dataset can result in a poor fit and lower predictive modeling performance. In the current data we had some columns which were not necessary for prediction of data. 

The steps we followed for cleaning as well as checking nulls in the data were
Standardizing  data
Checking Nan or nulls in the data
Validating the data
Analyzing data quality

We had to remove the rows which were falling in the outlier area so that it does not mess the prediction. This helped us a lot for visualizations as well. 
The four csv files used in our project were connected with each other with the primary key as fips. 

Two new columns were necessary for generating the visualizations for the other organization because only one of the columns was given. This data can be used for visualizing the current state of the country. This visualized data can be updated regularly if the upstream of the data link is updated.

The current project can be used with weather updation services on flood data analysis based on previous data. The design of the AWS services can be used for other projects as well.


