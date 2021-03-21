# API Challenge - What's the Weather Like?

## Background

Whether financial, political, or social -- data's true power lies in its ability to answer questions definitively. So let's take what you've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What's the weather like as we approach the equator?"

Now, we know what you may be thinking: _"Duh. It gets hotter..."_

But, if pressed, how would you **prove** it?

## WeatherPy
I have created a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To do this, I have utlized https://pypi.python.org/pypi/citipy and https://openweathermap.org/api.


# Data Setup
Google API: key used to pull 500 cities and their respective Latitiudes and Longitudes data

Openweather API: key used to pull respecitive weather data using Latitude and Longitude data from Google API

Used Google API to call in cities. Set up for loop to use Openweather API and create table of all the cities and their respective weather data.

Table (weather_df) is then exported to be used for VacationPy anaylsis. Going forward, weather_df is dataframe we will be using for anaylsis. 

Nex step is identify and take out any cities with Humidty > 100%.

Luckily, in my pull, I did not encounter any cities that had humidity over 100%.


# Analysis and Observations
I have created a series of scatter plots to showcase the below:
* Temperature (F) vs. Latitude
    * Observation: This scatter plot shows what most of know from common logic, the closer you are to the equator (latitide = 0, the hotter the max temperature of the given city.
* Humidity (%) vs. Latitude
    * Observation: It is difficult to draw a concrete conclusion and even more difficult to not say it has no correlation. However, there is suprisingly a small amount of plot points near the x-axis 10-40 (close to equator) where humidity is relatively lower than cities far away from the equator.
* Cloudiness (%) vs. Latitude
    * Oberservation: No real conclusion can be drawn from this plot. There seems to be no correlation between cloudiness and the latitiude of the given city
* Wind Speed (mph) vs. Latitude
    * Observation: Most of the cities in the random list is not much windy no matter what their latitude is. There seems to be no correaltion. 

I dug deeper to see if there is a difference between the Northern and Southern Hemisphere. To get a better anaylsis, a linear regression is also scripted so we can see the correlation

Below are my findings...
* Northern Hemisphere - Temperature (F) vs. Latitude
    * Linear regression: y = -1.24x + 95.86
    * Observation: there is clear correlation between the two. In the northern hemisphere, the further you are from the equator, the colder your max temperatures are
* Southern Hemisphere - Temperature (F) vs. Latitude
    * Linear regression: y = 0.38x + 81.18
    * Observation: As one could predict, the anylsis is similar to the Northern Hemisphere. In the souther hemisphere, the further you are from the equator, the colder your max temperatures are. Regardless of which hemisphere you select, Temeprature will always be correlated to Latitude.
* Northern Hemisphere - Humidity (%) vs. Latitude
    * Linear regression: y = 0.24x + 56.79
    * Observation: The r-squared calculated is 0.21, indicating that in the Northern Hemisphere, there is not a strong correlation between humidity and latitude
* Southern Hemisphere - Humidity (%) vs. Latitude
    * Linear regression: y = 0.39x + 84.16
    * Observation: Similar to the Northern Hemisphere, the r-sqaured is calculated to be 0.29, indicating that in the Southern Hemisphere, there is not a strong correlation between humidity and latitude
* Northern Hemisphere - Cloudiness (%) vs. Latitude
    * Linear regression: y = 0.36x + 38.72
    * Observation: The r-sqaure calculated is 0.18, indicating that in the Northern Hemisphere, there is not a strong correaltion between cloudiness and latitude
* Southern Hemisphere - Cloudiness (%) vs. Latitude
    * Linear regression: y = 0.62x + 65.79
    * Observation: The r-sqaure calculated is 0.21, indicating that in the Southern Hemisphere, there is not a strong correaltion between cloudiness and latitude
* Northern Hemisphere - Wind Speed (mph) vs. Latitude
    * Linear regression: y = 0.04x + 7.84
    * Observation: The r-sqaure calculated is 0.11, indicating that in the Northern Hemisphere, there is not a strong correaltion between wind speed and latitude
* Southern Hemisphere - Wind Speed (mph) vs. Latitude
    * Linear regression: y = -0.06 + 5.97
    * Observation: The r-sqaure calculated is -0.17, indicating that in the Southern Hemisphere, there is not a strong correaltion between wind speed and latitude

# In conclusion...
It seems that humidity, wind speed, and cloudiness are not really correlated or effected by the latitude of the respective city, only temperature is. 
Plots can be found in the 'Images' folder of the Git.


## VacationPy
Using the weather data frame csv, I will executing a code which will potentially help me plan future vacations/travels to the respective cities pulled from the previous excercise
Before starting, I had installed `jupyter nbextension enable --py gmaps` in my environment. I will be utilizing Jupyter-gmaps and the Google API for places.

# Data Setup
After importing the 'cities_new' file, I cleaned the date frame to drop any cities that did not meeting the following:
    * Temp between 70 and 80 degrees
    * Wind speed is less than 10 miles
    * there is no cloudiness
Using Google Places API, I located the first hotel for each city located within 5000 meters of the coordinates of the respective city.
I plotted the hotels on top of the humidity heatmap with each pin containing the Hotel Name, City, and Country.

# Analysis
The heat maps can be found in the 'Image' folder of the Git.

# In conclusion...
Based on the heat map of the hotel image, I think my next vacation will be in India!
