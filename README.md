# Applied Data Science Capstone Project Report

## Introduction
The use case is simple. Our customer has to relocate from Manhattan to Seattle beacuse of work. They love their current residence at 319, Avenue C, New York and were wondering if they could find a similar locality in Seattle.

They have a list of areas they are considering in Seattle based on recommendations by friends. 

The goal of this project is to help find our customer areas in Seattle that are similar in terms of attractions nearby to their current residency in Manhattan.

## Data

To achieve this we:
  1. Locate the users home address.
  2. Find all attractions nearby thir current home using the [FourSquare Developer API](https://developer.foursquare.com/).
  3. Similarly, find all attractions near each area the user is considering in Seattle.
  4. Cluster the areas by using unsupervised K-means clustering.
  5. Find the cluster which contains their current home address and recommend areas similar in Seattle.
  
 To make things more interesting we will be using the [GeoPy](https://geopy.readthedocs.io/en/) library to find the geographical co-ordinates of all these places and plotting them on a map using [Folium](https://python-visualization.github.io/folium/)!

For example, after getting all the nearby attractions of the customer's home we get a table like this which contains the attraction name and the attraction category.
![Manhattan Data](img/manh.png)


When this is repeated for all areas including the ones in Seattle, we get a table like this,  after summing all the attraction categories.
![All_areas_attractions](img/2.png)

## Methodology

Since we will be using the [GeoPy](https://geopy.readthedocs.io/en/) library a lot we create a function like below to call it whenever we need the Latitude and Longitude.
![GeoPy](img/3.png)

### Store your API credentials in a separate file.

We read the Foursquare developer API credentials from a json file and set other parameters required for calling the API.

![FS](imng/4.png)

Now we can call the above API which internally calls the GeoPy function and we are able to aggregate and create a data frame like:
![All_areas_attractions](img/2.png)

Doing some more analysis we can find some interesting aspects such as the most common category of attraction around a given location.
![Most_common](img/5.png)


We can consolidate this information in a data frame like:
![df_common](img/6.png)

## Results

After performing K-means clustering we get a cluster belonging to each area. If we take a look at the Seattle region we see:
![Seattle](img/7.png)

We then check what cluster our home belongs to:
![NY](img/8.png)


## Discussion

The customer not has 3 options to move into: Beacon Hill, Capitol Hill or Lake Union in Seattle. The most common feature in these areas and the users current home include Parks, Ice Cream Shops, Coffee Shops, Bakeries and Cocktail Bars.

## Conclusion

![answer](img/9.png)

We are happy to report that there are 3 areas which are similar to the customer's current address in Manhattan!

