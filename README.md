**Temperature Analysis and Station Mapping near Ann Arbor, Michigan**
-----------------------------------------------------------------------
**Project Overview**

*This project analyzes temperature trends near Ann Arbor, Michigan, using NOAA dataset records from 2005-2015.*
The primary goal is to:
- Identify record high and low temperatures from 2005-2014 for each day of the year.
- Overlay 2015 temperature data to identify any broken records.
- Visualize the weather stations on a map centered around Ann Arbor, Michigan.
- Generate a temperature summary for 2015.


*Here’s a brief note on every step of the analysis and logical implementation:*

**1.Loading and Familiarizing with the Dataset**
- *Files Loaded:* `temperature.csv` and `BinSize.csv`.  
- *Purpose:* Understand the structure of the data to extract relevant insights.
- *Action:* Converted the `date` column to *datetime format* and added `year` and `month-day` columns for easier grouping.

**2. Removing Leap Day (February 29)**
- *Reason:* Since not every year has a leap day, it was reasonable to **exclude February 29** to ensure consistent comparisons across years.  
- *Action:* Filtered out all rows corresponding to **'02-29'**.

**3. Splitting Data (2005-2014 vs. 2015)**
- *Purpose:* The task requires finding **record high and low temperatures for each day from 2005-2014** and **overlaying the 2015 data** to see if any records were broken.  
- *Action:* Separated the dataset into *2005-2014 data* (baseline) and *2015 data* (for comparison).

**4. Calculating Record Highs and Lows (2005-2014)**
- *Goal:* For each *day of the year*, identify the *highest and lowest temperatures* from 2005 to 2014.  
- *Logic:* Used *groupby* on the `month-day` column and applied `max()` and `min()` to find the record high and low values, respectively.

**5. Plotting Record Highs and Lows with Shading**
- *Goal:* Create a **line graph** to display the record highs and lows by **day of the year**.
- *Shading:* Used `fill_between()` to shade the area between the highs and lows, making the range visually distinct.  
- *Action:* Labeled the plot with *axis labels, a title, and a legend* for clarity.

**6. Overlaying 2015 Data for Broken Records**
- *Purpose:* Identify any points in **2015** where the temperature exceeded the record high or fell below the record low (from 2005-2014).  
- *Logic:* Used a conditional filter to compare the **2015 values** with the **record highs and lows**.
- *Action:* Overlayed these points using *scatter plots* (with different markers for high and low breaks) on the line graph.

**7. Mapping Stations Near Ann Arbor, Michigan**
- *Goal:* Visualize the stations listed in the *`BinSize.csv`* file on a *map* centered on **Ann Arbor, Michigan**.
- *Action:* Used **`folium`** to create an **interactive map**, adding markers for each station’s **latitude and longitude** with the **station ID** as a popup.
- *Output:* Saved the map as *`ann_arbor_station_map.html`*, viewable in a browser.

**8. Plotting Temperature Summary for 2015**
- *Goal:* Create a **line graph** showing the temperature trends for **2015** (both **TMAX** and **TMIN**).
- *Logic:* Filtered the *2015 data* to keep only *TMAX* and *TMIN* elements, and used *seaborn* to plot the daily temperature trends.
- *Formatting:* Added *axis labels, a title, and a legend* to make the graph clear.

**Summary of Tools and Libraries Used:**
- **`pandas`**: Data manipulation (loading, filtering, and grouping data).
- **`matplotlib` and `seaborn`**: Plotting graphs for temperature trends.
- **`folium`**: Creating an interactive map of stations near Ann Arbor.
- **Reason for Libraries:**  
   - `seaborn` simplifies data visualizations with useful formatting.
   - `folium` provides easy-to-use mapping capabilities for geospatial data.
