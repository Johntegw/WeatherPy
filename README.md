# WeatherPy
Background
Jack loves the PlanMyTrip app. Beta testers love it too. And, as with any new product, they've recommended a few changes to take the app to the next level. Specifically, they recommend adding the weather description to the weather data.

For this challenge, you will use the weather description data you've already retrieved in this module to enhance the PlanMyTrip app. Then, you'll have the beta testers use input statements to filter the data for their weather preferences, which will be used to identify potential travel destinations and nearby hotels. The beta tester will choose four cities from the list of potential travel destinations to create a travel itinerary. Finally, using the Geoapify Routing API, you will create a travel route between the four cities and a marker layer map.

What You're Creating
This new assignment consists of three technical analyses. You will submit the following deliverables:

Deliverable 1: Retrieve Weather Data

Deliverable 2: Create a Customer Travel Destinations Map

Deliverable 3: Create a Travel Itinerary Map

Files
Use the following link to download the Challenge starter codes.

Module 6 challenge starter codeLinks to an external site.
Instructions
Deliverable 1: Retrieve Weather Data
For this deliverable, you'll generate a set of 2,000 random latitudes and longitudes, retrieve the nearest city, and perform an API call with OpenWeatherMap. In addition to the city weather data you gathered in this module, use your API skills to retrieve the current weather description for each city. Then, create a new DataFrame containing the updated weather data.

Create a folder called Weather_Database to save all the files related with this deliverable.

Save the Weather_Database_starter_code.ipynb starter code to the Weather_Database folder and rename it as Weather_Database.ipynb.

Use the np.random.uniform function to generate a new set of 2,000 random latitudes and 2,000 longitudes.

Use the citipy module to get the nearest city for each latitude and longitude combination.

Import your OpenWeatherMap's API key and assemble the API call URL as a string variable. Recall to edit the config.py file to add your API key; also, it's critical to avoid publishing your API key on your GitHub repository.

Retrieve the following information from the API call:

Latitude and longitude

Maximum temperature

Percent humidity

Percent cloudiness

Wind speed

Weather description (for example, clouds, fog, light rain, clear sky)

Add the weather data to a new DataFrame.

Before continue to the next step, take a moment to confirm that the DataFrame looks similar to the image below (note that cities and countries may vary):
The new cities_data DataFrame summarizes the current weather description.

Export the DataFrame as a CSV file, and save it as WeatherPy_Database.csv in the Weather_Database folder.

Deliverable 2: Create a Customer Travel Destinations Map
In this deliverable, you'll employ input statements to retrieve customer weather preferences. Next, you'll use those preferences to identify potential travel destinations and nearby hotels. Finally, you'll show those destinations on a map.

Create a folder called Vacation_Search to save all the files related with this deliverable.

Download the Vacation_Search_starter_code.ipynb Jupyter notebook,save it into your Vacation_Search folder, and rename it as Vacation_Search.ipynb.

In the Vacation_Search.ipynb file, ensure that the dependencies and the Geoapify API key is imported correctly.

From the Weather_Database folder you created in the "Deliverable 1," import the WeatherPy_Database.csv file as a Pandas DataFrame named city_data_df.

Write two input statements that prompt the user to enter their minimum and maximum temperature criteria for their vacation.

Create a new Pandas DataFrame by using the loc Pandas method to filter the city_data_df DataFrame for temperature criteria collected. Name the DataFrame as preferred_cities_df.

Create a new Pandas DataFrame named clean_travel_cities by using the Pandas dropna function on the preferred_cities_df to drop any empty rows.

Use the copy Pandas function to create a new DataFrame, called hotel_df, by copying the following columns from the clean_travel_cities DataFrame: "City", "Country", "Max Temp", "Current Description", "Lat", "Lng".

Add a new empty column named Hotel Name to the hotel_df DataFrame.

Review the hotel search parameters provided. These parameters are the same we used in this module; you'll use them to search for a hotel for each city.

Use a for loop to iterate through the hotel_df DataFrame. Retrieve the latitude and longitude of each city and use the Geoapify API to find the nearest hotel based on the search parameters provided, then add the hotel name to the hotel_df DataFrame. If a hotel isn't found, set the hotel name as "No hotel found".

Drop any rows in the hotel_df DataFrame where a hotel name is not found and store the resulting data into a new DataFrame named clean_hotel_df.

Take a moment to confirm that your clean_hotel_df DataFrame looks similar to the image below (note that the data may vary).
The new hotel DataFrame has the Hotel Name column completed where hotels are found.

Create an CSV file to store the clean_hotel_df DataFrame as WeatherPy_vacation.csv in the Vacation_Search folder.

Use GeoViews to create a map that displays a point for every city in the clean_hotel_df DataFrame. In the point for each city add:

The city name
The country code
The weather description
The point's size should be the maximum temperature for the city
Take a screenshot of your map and save it to the Vacation_Search folder as WeatherPy_vacation_map.png.

The map should look similar to the following image:
The new hotel DataFrame includes point markers for each city.

Deliverable 3: Create a Travel Itinerary Map
For this deliverable, you'll use the Geoapify Routing API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, you'll create a map with a pop-up marker for each city on the itinerary.

Create a folder called Vacation_Itinerary to store all the files for this deliverable.

Download the Vacation_Itinerary_starter_code.ipynb file into your Vacation_Itinerary folder and rename it Vacation_Itinerary.ipynb.

Make sure the initial dependencies and the Geoapify API key are imported.

From your Vacation_Search folder from Deliverable 2, import the WeatherPy_vacation.csv file as a DataFrame named vacation_df.

Use GeoViews to create a map that shows all the cities in the vacation_df DataFrame. Configure the map as follows:

The point's size should be the maximum temperature for the city

The point's color should be the city's name

Use the hover_cols parameter to the the "Hotel Name", "Country", and "Current Description" columns to each point as additional information.

From the map, choose four cities that a customer might want to visit. They should be close together and in the same country. Use the loc method to create separate DataFrames for each city on the travel route.

HINT
Use the Pandas concat function to merge the DataFrame from each city in the itinerary to create a new DataFrame named itinerary_df to store the itinerary details. Your final DataFrame should look as in the image below.

Sample itinerary DataFrame with Italian cities

Use the Pandas copy function to create a new DataFrame named waypoints_df to store the longitude and latitude for each city in itinerary_df.

HINT
Use GeoViews to create a map that shows the four cities in the itinerary. You may end with a map similar to the image below.

Sample map

Next, you'll use the Geoapify Routing API to find a route between the cities in the itinerary. Review the code that sets the initial parameters and fetches the coordinates from each city to define the waypoints parameter by using a for loop.

HINT
Use the Geoapify Routing API to retrieve the route's directions for your itinerary.

From the JSON response, store the route's legs coordinates in a variable called legs.

Loop through the route legs coordinates to fetch the latitude and longitude for each step. Store the latitude and longitude values into two Python lists named longitude and latitude.

Use the longitude and latitude Python lists to create a new DataFrame named route_df.

Use the GeoViews Path function to configure a line plot by using route_df. Set a custom color and width for the line that may contrast with the map.

Use the asterisk operator to display a composed plot that shows the itinerary's route over the map containing the cities. Your map may look as in the following image.

Sample itinerary map

Save your map to the Vacation_Itinerary folder as WeatherPy_travel_map.png.
