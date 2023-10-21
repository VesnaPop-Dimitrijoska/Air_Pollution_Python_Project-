# Project Title:
Python Project on Air Pollution

#
# Project Description:
This project was developed as individual assignment at Brainster Data Science Academy. Detailed Air Pollution analysis in Skopje from a dataset taken from Kaggle.

## The Dataset
The following data has been taken from kaggle (https://www.kaggle.com/datasets/cokastefan/pm10-pollution-data-in-skopje-from-2008-to-2018) where data from the monitoring stations (https://air.moepp.gov.mk/?page_id=175) for the period from Janaury 2007 to December 2018 has been compiled in a single dataset. To make our task more managable, we will only be looking at data for the time period of five years, from January 2012 to December 2016.
#
## Data analysis, actions taken and conclusions:
After a detailed analysis of the data I decided to take several steps in order to prepare the data set in a suitable form for further work.
1) Adding a 'Pollutant' column
Since all files differ by pollutant type, it is necessary to add a pollutant column, as it does not exist in the data set ie. it is only in the title of the files.
2) Concatenation
There are 5 different .csv files with identical columns, which can be merged into one for easier further manipulation.
3) Deleting columns
After this it is necessary to delete the following columns: 'Unnamed: 0.1' and 'Unnamed: 0' which had the role of index columns in the original software from where the data was taken, but in our case they are not useful for us, because we merge the data according to rows, so when merging index columns are no longer unique values, ie. they will be duplicated 5 times. We also delete the 'Mobile' column because there is no data in it at all.
4) Renaming columns
There is one column that is inappropriately named and should be renamed, 'time' to 'Datetime', because it provides date and time data.
5) Deleting duplicates
During data analysis, I discovered 7315 duplicate data, which should be deleted.
6) Conversion to appropriate data types
All data is in the appropriate data type except the time column and it should be cast to datetime.
7) Creating time columns
Considering the requirements in the tasks, it is necessary to derive additional columns, to make it easier to make further groupings after some time intervals. For this purpose, additional columns for date, time, day, month, year and hour have been derived.
8) Creation of auxiliary lists
I create a list of locations and a list of polluters that can be used below in tasks to shorten code or use in loops.
9) Dealing with NaN values
A large percentage of NaN values (given in the calculations below) appear in the data set, but that percentage is not large enough to throw out the measurements without their further analysis. At this stage of developing the project, we do not have enough knowledge for their more detailed analysis, analysis of the patterns by which they appear and how to deal with such data.
What is obvious is that there is a continuous absence of data at some measuring points over several years. This indicates the fact that some sensors did not work, so the measurements for those parameters were not read.
Another very common case is the occurrence of random NaN values, which may be due to the inability of the sensors to detect the low values of the parameters they measure. Such cases should be approximated with 0 or some minimum value, but again a more detailed analysis is necessary to determine the accuracy of such assumptions, as well as for their interpolation.

Conclusion:
For the reasons stated above, ie. the impossibility to reliably confirm the stated findings as well as to properly deal with them, I decided NOT to change these data further. Of course, through the tasks I filter these values where necessary or use functions that ignore such values in the calculations themselves.

10) Data deviations
Analyzing the minimum and maximum values, in order to see if there are any major deviations or illogical measurements, I determined the following: In the file CO.cvs, location Rektorat, there are data that deviate greatly from the standard measurements for this parameter, it is about 250 measurements, in rows 203-448, in which very high measurements for this parameter were registered in a period of about 10 days. At the same time, sub-currents fail a few days before such measurements are registered and almost 1 year after them, which may indicate a possible failure of the sensor. The measured data in these 10 days have a value of 54,966 measuring units (according to WHO, the limit value for CO is 10 measuring units). The measured values in continuity are almost the same with a difference in the second or third decimal, which is a little illogical that the CO level in the air is almost constant during 10 days, considering the fact that there is no heavy traffic in parts of the night. However, CO pollution is not isolated and caused only by vehicle emissions in traffic. Measurements made in the same period at very close locations range on average from 0 to 3 measurement units.
This measuring station is located in the yard of the Rectorate of the University "St. Cyril and Methodius", that is, at the crossroads with the Court Palace. In this part of the city, there is extremely high traffic during the day, so according to that, and the fact that the results were obtained during the month of January, CO pollution is expected to be higher than the other locations. Automatic monitoring stations are purposely distributed in different types of locations in order to be able to measure the impact of different air pollutants. At the specific location Rectorate, the measuring station aims to measure pollution specifically from traffic (https://air.moepp.gov.mk/wp-content/uploads/2015/07/0204_202301VkupenIzvestaj.pdf).
Examining some scientific papers on the subject, from research done on some moles with frequent traffic (http://www.bioline.org.br/pdf?st04028, but also others), it has been concluded that CO levels, even at very frequent intersections, however, do not exceed the value prescribed by WHO.
Finally, I analyzed the full data set from the last 10 years, but I did not detect any other high levels of CO there.

Conclusion:
Carbon monoxide (CO) levels, measured at busy intersections, can vary depending on various factors such as: traffic volume, vehicle CO emissions, proximity to certain industrial centers, altitude, season, weather conditions : temperature, wind, air humidity, cloudiness and many others. Due to the impossibility to determine the accuracy of the measured data, the correctness of the sensors and the influencing factors in the specific case, it was decided to keep them in the data set for further analysis and not to exclude them.
#
## The cleaned data set contains:
• 219220 rows (43844 rows per pollutant) and
• 14 columns (6 location columns, time columns and pollutant column).

#



# Table of Contents:

  1. Data analysis, actions taken and conclusions
  2. Questions which were addressed in the project:
     - What location in Skopje has the highest average pollution for each of the pollutants?
     - For every year, for each of the pollutants, on what time stamp is the maximum pollution for every location? What time of the year seems to have the most pollution in Skopje?
     - In what month of the year is the average polution accross locations highest for each of the pollutants?
     - What is the average pollution accross locations in every hour during the day?
     - Calculate and display the average daily pollution accross locations on separate plots for each of the pollutants over time.
     - If the range of values for PM10 considered safe and unsafe is according to the following scale:
            Good 0-50
            Moderate 51-154
            Unhealthy for sensitive individuals 155-254
            Unhealthy 255-354
            Very unhealthy 355-424
            Hazardous 425-504
        On how many days in each year, was the average value of PM10 meauserd accross locations worse than moderate?
      - On how many days in each year, was the value of PM10 measured on at least one location worse than moderate?
      - Make a bar plot showing the average number of days per year when the measured value for PM10 was worse than moderate on at least one location
  3. Solution and conclusions

#
# License
MIT License
#
