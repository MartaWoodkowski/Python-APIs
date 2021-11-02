# Python-APIs

# What's the Weather Like?

## Background

Using Python requests, APIs, and JSON traversals let's answer a fundamental question: "What's the weather like as we approach the equator?"

Now, you may be thinking: _"Duh. It gets hotter..."_

But, if pressed, how would you **prove** it?

![Equator](Images/equatorsign.png)


## Part I - Weather

Visualized the weather of 500+ random cities across the world of varying distance from the equator. To accomplish this, I utilized the citipy module, the [OpenWeatherMap API](https://openweathermap.org/api), and a little common sense to create a representative model of weather across world cities.

Created a series of scatter plots to showcase the following relationships:

* Temperature (F) vs. Latitude
* Humidity (%) vs. Latitude
* Cloudiness (%) vs. Latitude
* Wind Speed (mph) vs. Latitude

Then I ran linear regression on each relationship, only this time separating them into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude):

* Northern Hemisphere - Temperature (F) vs. Latitude
* Southern Hemisphere - Temperature (F) vs. Latitude
* Northern Hemisphere - Humidity (%) vs. Latitude
* Southern Hemisphere - Humidity (%) vs. Latitude
* Northern Hemisphere - Cloudiness (%) vs. Latitude
* Southern Hemisphere - Cloudiness (%) vs. Latitude
* Northern Hemisphere - Wind Speed (mph) vs. Latitude
* Southern Hemisphere - Wind Speed (mph) vs. Latitude

Interesting to know:

* Every time I run my code, it randomly selects **at least** 500 unique (non-repeat) cities based on latitude and longitude.
* Performs a weather check on each of the cities using a series of successive API calls.
* Includes a print log of each city as it's being processed with the city number and city name.
* Saves a CSV of all retrieved data and a PNG image for each scatter plot.

### Part II - Vacation

Then I decided to work with weather data to plan future vacations. Used jupyter-gmaps and the Google Places API (part of Google Cloud).
(I had trouble displaying the maps, so I ran `jupyter nbextension enable --py gmaps` in my environment.)

* Created a heat map that displays the humidity for every city from the Part I.

  ![heatmap](Images/heatmap.png)

* Narrowed down the DataFrame to find my ideal weather condition. Set:

  * Range of temperature for my perfect vacation (min and max).

  * Wind speed range.

  * Cloudiness range.

  * Dropped any rows that didn't contain all three conditions. I wanted to be sure the weather was ideal.

* Using Google Places API, I found the first hotel for each city located within 5000 meters of my coordinates.

* Plotted the hotels on top of the humidity heatmap with each pin containing the **Hotel Name**, **City**, and **Country**.

  ![hotel map](Images/hotel_map.png)
