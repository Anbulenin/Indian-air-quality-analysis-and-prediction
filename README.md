Introduction:

Air quality of a particular state or a country is a measure on effect of pollutants on the respected regions, these air quality indexes indicates the levels of major pollutants on the atmosphere. There are various pollutants Computation of the AQI requires an air pollutant concentration over a specified averaging period, obtained from an air monitor or model. Taken together, concentration and time represent the dose of the air pollutant. Health effects corresponding to a given dose are established by epidemiological research.  Air pollutants vary in potency, and the function used to convert from air pollutant concentration to AQI varies by pollutant. Its air quality index values are typically grouped into ranges. Each range is assigned a descriptor, a colour code, and a standardized public health advisory.
Air pollution has been a matter of environmental and health concerns, particularly in urban areas. Central Pollution Control Board along with State Pollution Control Boards has been operating National Air Monitoring Program (NAMP) covering 240 cities of the country. In addition, continuous monitoring systems that provide data on near real-time basis are also installed in a few cities. Traditionally, air quality status has been reported through voluminous data. Thus, it was important that information on air quality is put up in public domain in simple linguistic terms that is easily understood by a common person. Air Quality Index (AQI) is one such tool for effective dissemination of air quality information to people. An Expert Group comprising medical professionals, air quality experts, academia, advocacy groups, and SPCBs was constituted and a technical study was awarded to IIT Kanpur. IIT Kanpur and the Expert Group recommended an AQI scheme.
 There are six AQI categories, namely Good, Satisfactory, Moderately polluted, Poor, Very Poor, and Severe.  The proposed AQI will consider eight pollutants (PM10, PM2.5, NO2, SO2, CO, O3, NH3, and Pb) for which short-term (up to 24-hourly averaging period) National Ambient Air Quality Standards are prescribed.
 Based on the measured ambient concentrations, corresponding standards and likely health impact, a sub-index is calculated for each of these pollutants. The worst sub-index reflects overall AQI. Associated likely health impacts for different AQI categories and pollutants have been also been suggested, with primary inputs from the medical expert members of the group. The AQI values and corresponding ambient concentrations (health breakpoints) as well as associated likely health impacts for the identified eight pollutants are as follows:



Table 1:-
AQI Category, Pollutants and Health Breakpoints
AQI Category (Range)	PM10
24-hr	PM2.5
24-hr	NO2
24-hr	O3
8-hr	CO
8-hr (mg/m3)	SO2
24-hr	NH3
24-hr	Pb
24-hr
Good (0-50)	0-50	0-30	0-40	0-50	0-1.0	0-40	0-200	0-0.5
Satisfactory (51-100)	51-100	31-60	41-80	51-100	1.1-2.0	41-80	201-400	0.5 –1.0
Moderately polluted
(101-200)	101-250	61-90	81-180	101-168	2.1- 10	81-380	401-800	1.1-2.0
Poor
(201-300)	251-350	91-120	181-280	169-208	10-17	381-800	801-1200	2.1-3.0
Very poor
(301-400)	351-430	121-250	281-400	209-748*	17-34	801-1600	1200-1800	3.1-3.5
Severe
(401-500)	430 +	250+	400+	748+*	34+	1600+	1800+	3.5+



we obtained the monthly/yearly ambient Air Quality Data from different monitoring stations across India from Indian government data website (https://data.gov.in). Details of ambient air quality with respect to air quality parameters, like Sulphur dioxide, Nitrogen dioxide, Respirable Suspended Particulate Matter (RSPM) and Suspended Particulate Matter (SPM) etc. are given in the datasets. Few of the data from the stations have been shifted/closed/during the period, are noisy. During1987-2013, SPM has been represented by PM 2.5 (PM2.5 was not being monitored during that period).
We have designed a model to predict the air quality index of every available data points in the dataset, our model is capable of forecasting the air quality of India in any given area. By predicting the air quality index, we can backtrack the major pollution causing pollutant and the location affected seriously by the pollutant across India.

Methodology:

We acquired the dataset with various columns of sensor data from various places in India. we have the average readings of ambient air quality with respect to air quality parameters, like Sulphur dioxide (So2), Nitrogen dioxide (No2), Respirable Suspended Particulate Matter (RSPM) and Suspended Particulate Matter (SPM).Data acquired from the source has more noisy data since few of the data from the stations have been shifted/closed/during the period were marked as NAN or not available.so we have to pre-process the data in order to remove the outliers.

Sample data: -
 
In this dataset we have the pollutant concentration levels occurring on each place. Now our problem has four parameters (so2, no2, rspm, spm). These parameters should be reduced show that our model learning and predicting rate will be better. So, we have calculated the air quality index (AQI) for all the available data points.to calculate the AQI we have to find the individual indexes of each pollutant. Each index of pollutant represents the level of damage caused by the pollutant. Each indexes such as SI, NI, SPI, RPI.
The worst sub-index reflects overall AQI. For instance, if the sub index of PM2.5 =75, SO2 = 63, NO2 =38 then the AQI will be 75 which is the same as the value of the sub index of PM2.5. The excel sheet for calculating AQI, as uploaded by CPCB. The Sub-indices for individual pollutants at a monitoring location are calculated generally using its 24-hourly average concentration value (8-hourly in case of CO and O3) and health breakpoint concentration range (e.g. AQI at 6 am on a day will incorporate data from 6am on previous day to the current day).  However, all the eight pollutants may not be monitored at all the locations. Hence, overall AQI is calculated only if data are available for minimum three pollutants out of which one should necessarily be either PM2.5 or PM10. Else, data are considered insufficient for calculating AQI. But the sub-indices for monitored pollutants are calculated and disseminated, even if data are inadequate for determining AQI. Further, a minimum of 16 hours’ data is considered necessary for calculating sub index.

AQI index values can vary depending on the time of the day. AQI reflects the status of the worst pollutant in that city. i.e. higher reading in one city can be due to high concentration of PM whereas in some other city it may be due to SO2. Even if the other 7 pollutants have a benign reading, if one pollutant is in the “poor” category then AQI will be in the “poor” category.


 

Calculating individual index of so2: - 


Calculating the individual index of no2:-
 



Calculating the individual index of rspm: -

  Calculating the individual index of spm:- 


Calculating air quality index (AQI) : -
The air quality index of a particular data point is the aggregate of maximum indexed pollutant on that particular area. That pollutants index is taken as the air quality index of that particular location. This maximum value of the pollutants is taken as a air quality index because to backtrack the pollutant levels from the air quality index.
 

 

After calculating air quality index, we now have a meaningful data from our acquired dataset, in order to predict the air quality index of the whole India each and every data points of historical data of pollutant index are needed. Since we have the sampling date of every datapoints we can use time series analysis to predict the data points. 




Data visualization: -
Plotting the heatmap from matplot library for all the available data points to identify the pre-processing measures to remove the outliers.

Graph 1: -
 









Plotting a graph between average AQI and sample date: -
In this graph AQI is the average value of aqi of each year across India. These is a huge seasonal variations and trend on out graph.


Graph2: -

 



Pre-processing the Data: -
In this dataset the outliers are mainly of faulty sensor or transmission errors, these errors have huge variation than the normal valid results. We know the standard range of pollutants occurs on a particular area.so to remove the outliers from the data we use boundary value analysis. By using BVA we found the upper quartile range and lower quartile range of a given data.
 
 


Analysing the data points: -

Naïve forecast method: -
We splitted the dataset into two parts of first 75% and rest 25% data into test and train datasets to identify the huge seasonal variations and trend.
We calculated the moving average of our datapoints and plotted the moving average. We identified the moving average varies one the year (2010-2011) i.e. before 2010 there are variations at x minum and x maximum and after 2011 the variations are y minimum and y maximum.

Plotted the graph of train and test dataset with their moving average: -

  Graph 3 : -
 









Time series statistics graph: -

Graph4:-
 


By this data analysis we came to know that there are seasonal variations and trend, in order to reduce these metrics, we resample the data month wise to predict it month wise. By resampling the data, we can reduce the outlier more efficiently than raw data.
By the moving average graph, we can see there is a huge drop in air quality index between the years 2010-2011. So, we split the data into two parts and try predict the equivalent air quality values.

Outlier Removal by Parts: -
Dataframe 1: -(year: 1989-2010)
Boxplot analysis
 



Dataframe 2: -(year:2011-2015)
Boxplot analysis
 

After removing the outlier’s linear regression is applied to the filtered data and to fit the trent line on the data points gradient descent hyper parameters are used to optimize the model. We set random values to our slope equation and change according to the learning rate and position of data points.

Applying Linear regression with Gradient decent: -


our linear regression model is defined as follows:
y = B0 + B1 * x
we took random values for both coefficients.
B0 = 0.0
B1 = 0.0
y = 0.0 + 0.0 * x

We can calculated the error for a prediction by: -
error = p(i) – y(i)
p(i) is the prediction for the i’th instance in our dataset and y(i) is the i’th output variable for the instance in the dataset.
We can now calculate he predicted value for y using our starting point coefficients for the first training instance:
x=1, y=1
p(i) = 0.0 + 0.0 * 1
p(i) = 0

Using the predicted output, we can calculate our error:
error = 0 – 1
error = -1
We can now use this error in our equation for gradient descent to update the weights. We will start with updating the intercept first, because it is easier.
We can say that B0 is accountable for all of the error. This is to say that updating the weight will use just the error as the gradient. We can calculate the update for the B0 coefficient as follows:
B0(t+1) = B0(t) – alpha * error

Where B0(t+1) is the updated version of the coefficient we will use on the next training instance, B0(t) is the current value for B0 alpha is our learning rate and error is the error we calculate for the training instance. Let’s use a small learning rate of 0.01 and plug the values into the equation to work out what the new and slightly optimized value of B0 will be:

B0(t+1) = 0.0 – 0.01 * -1.0
B0(t+1) = 0.01

Now, let’s look at updating the value for B1. We use the same equation with one small change. The error is filtered by the input that caused it. We can update B1 using the equation:

B1(t+1) = B1(t) – alpha * error * x

Where B1(t+1) is the update coefficient, B1(t) is the current version of the coefficient, alpha is the same learning rate described above, error is the same error calculated above and x is the input value.

calculating the updated value for B1:

B1(t+1) = 0.0 – 0.01 * -1 * 1
B1(t+1) = 0.01

We have just finished the first iteration of gradient descent and we have updated our weights to be B0=0.01 and B1=0.01. This process must be repeated for the remaining ‘x’ number of instances from our dataset. (x=3000)


Calculating the cost function of current data values: -

Cost function is plotted to improve the efficiency of our model, cost function graph is used to find the minimum number of iterations for the maximum accurate results. The accuracy of our model will not increase rapidly if we increase the number of iterations.

Graph6:-
 


Results: -
For Dataframe 1:-
Scatter plot of datapoints of AQI vs year: -
 

Gradient decent for this Dataframe: -
 


Plotting the Linear regression of the data points: -

 

Predictions and error rate: -
 
For Dataframe 2: -
Scatter plot of datapoints of AQI vs year: -
 

Gradient decent for this Dataframe: -

 



Plotting the Linear regression of the data points: -
 
Predictions and error rate: -

 

Conclusion: -
Since our model is capable of predicting the current data with 95% accuracy it will successfully predict the upcoming air quality index of any particular data within a given region. With this model we can forecast the Aqi and alert the respected region of the country also it a progressive learning model it is capable of tracing back to the particular location needed attention provided the time series   data of every possible region needed attention.
