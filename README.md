# Boston Accident Data Analysis

*HDAG Summer Fellowship 2021 - Kushal Chattopadhyay and Nina Lei*

[https://tinyurl.com/hdagnlkc21](https://tinyurl.com/hdagnlkc21)

## Introduction

It comes as no surprise that Boston is a dangerous place to drive, with the [worst](https://inrix.com/scorecard/#) traffic congestion in the United States (INRIX Global Traffic Scorecard) and some of the [worst](https://slate.com/technology/2014/08/which-city-has-the-worst-drivers-boston-baltimore-washington-d-c-miami.html) drivers in the country (Allstate Insurance). In our final project for the HDAG Summer Fellowship, we conducted a project to visualize pedestrian, bike, and car accidents in the city since January 1, 2015 and analyze which weather conditions most influenced accident count in the area.

## Visualizing Accident Counts

We obtained our data from publicly accessible Boston websites. Each row of our original DataFrame included:

- **Date / Time** of Accident
- **Mode Type** (Car, Pedestrian, or Bike)
- **Location Type** (Street, Intersection, etc.)
- **Street(s)**
- **Latitude / Longitude**

We were able to visualize some of this data in bar charts:

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled.png)

Mode type counts

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%201.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%201.png)

Location type counts

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%202.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%202.png)

Year counts

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%203.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%203.png)

Month counts

Some interesting things to note are that:

- There are more accidents per month in **May - October** than in **November - April**. ****
    - This could be a result of more pedestrians, bikes, and cars being outside during summer months, thus causing heightened accident counts in those months.
- There was a drastic decrease in accidents in **2020**.
    - This could be a result of COVID-19 and stay-at-home orders.

## Visualizing Accidents Geographically, Pt 1

After this, we wanted to visualize these accidents on a map. We first plotted the accidents on a map of Boston using latitude and longitude. We colored each accident either **green** for a motor vehicle accident, **blue** for a pedestrian accident, and **red** for a bike accident.

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_5.50.30_pm.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_5.50.30_pm.png)

[color_coded_map.html](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/color_coded_map.html)

- We noticed that the vast majority of accidents in residential neighborhoods such as **Dorchester** or **Roxbury** were motor vehicle accidents (green). Many of these accidents were concentrated on thoroughfares such as **Dorchester Ave**, **Washington St**, and **Blue Hill Avenue**.
    - There are less pedestrians and bikes in primarily residential areas as most commuting occurs by car, resulting in most accidents here being motor vehicle related. On major thoroughfares, higher amounts of cars result in more accidents.
- In **downtown Boston** and the **Financial District** there were much more pedestrian accidents, as evidenced by the high count of blue dots.
    - There are more pedestrians walking around this district, leading to more accidents involving pedestrians.
- Along **Commonwealth Avenue** (south of Cambridgeport) there were many bike accidents.
    - Commonwealth Avenue runs directly along Boston University, and so many of these bike accidents may have been from college students.

Another clustered map:

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_6.06.20_pm.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_6.06.20_pm.png)

[clustered.html](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/clustered.html)

- Some locations with abnormally high accident counts include:
    - the stretch of **John F Fitzgerald Surface Rd** between Sudbury St and Hanover St, with over **60 accidents**
    - Massachusetts Route 28 merging onto I-93 South, with over **70 accidents**
    - Exit 23 at **I-93 South,** with over **100 accidents**

These all are areas where many vehicles either have to **switch lanes** or **merge onto high-speed traffic.**

- Some other locations with high accident counts of bikes are **Cambridge Street** (no bike lane) and **State Street** (bike lane but multiple intersections where bikes must cross streets).

## Visualizing Accidents Geographically Pt 2

To make the visualization more readable, we used neighborhood maps. We first mapped out the different districts of Boston.

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_5.41.41_pm.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_5.41.41_pm.png)

[neighborhood_map.html](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/neighborhood_map.html)

We then calculated the densities of accidents in each of the Boston neighborhood and plotted them on a choropleth.

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_6.23.42_pm.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Screen_Shot_2021-08-05_at_6.23.42_pm.png)

[choropleth.html](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/choropleth_(1).html)

The highest densities of accidents are in urban Boston (**Downtown, Chinatown, West End, Leather District**) with >0.5 accidents / square meter over the six year timespan.

## Machine Learning Model

Next we obtained weather data of the area.

We ran Keras and sklearn RFR, the latter of which performed better with MAE of 2.9 in comparison with Keras models with MAE's of over 3.0.

***Mean Absolute Error: 2.9***

***Accuracy: 64.61 %.***

After training the model, we were able to obtain the following visualization:

![Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%204.png](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/Untitled%204.png)

This shows us the variables most responsible for accidents in the Boston area. Some interesting things to note are:

- **Wind speed and temperature** are most related to accidents.
- Surprisingly, **snow** is the lowest in importance in relation to accidents.
- **Year** has a high importance, indicating that differences in accident counts could be connected to the year it took place.

After training the model, we made it into a simple Flask API, as shown in a video below:

[Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/zoom_1.mp4](Boston%20Accident%20Data%20Analysis%2068749c773c224bb6b048a3c2d268665b/zoom_1.mp4)


## Next Steps
0. Data: Group by combination of 3 columns (date, rough time, neighborhood; eg "01/01/2019, morning, neighborhood") rather than only grouping by date and counting num occurance... (this way, user can also enter time and neighborhood(s) and get better predictions instead of general daily count things)
1. Modelling: Fine tune existing ML model.
2. Incorporation of geospatial data: Geohash longitude and latitude data; create geospatial ML model.
3. Development of Web Application: Utilize weather APIs to get current weather related info automatically and integrate with Twilio to provide warnings if expected accident count is high (define what is high) in geohashed zones at certain time.
4. Policy Insights: Finally, assess whether Boston’s Vision Zero strategies have equitably served different neighborhoods and addressed existing disparities.
