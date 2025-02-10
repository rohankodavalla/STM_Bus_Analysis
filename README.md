# STM_Bus_Analysis
Diving into Montreal’s bus data to identify peak usage zones and recommend rebalancing strategies.


📝 Summary of the Code
1️⃣ Objective & Purpose
This code aims to analyze Montreal bus transit data to understand spatial demand patterns and temporal demand trends during peak hours, specifically the weekday morning (AM) and evening (PM) peaks. It does so by processing GTFS (General Transit Feed Specification) data, which is commonly used for public transportation analysis. The final result is a spatial visualization of the bus demand hotspots and a temporal distribution of bus departures during peak hours.

2️⃣ How It Works
The process unfolds in several key steps:

Step 1: Data Collection
Data Source:
The data is fetched from the Montreal transit system's GTFS feed, available at the following URL:
Montreal GTFS Data.

Downloading & Extracting the ZIP File:
The code downloads the GTFS ZIP file and extracts the following CSV files:

stops.txt: Information about bus stops (ID, name, latitude, longitude, etc.).
stop_times.txt: Details about bus stop times for each bus trip (arrival/departure times, stop sequences).
trips.txt: Information about each bus trip (trip ID, route, direction, etc.).
Step 2: Data Preprocessing
Data Merging:
The extracted datasets (stops.txt, stop_times.txt, trips.txt) are merged on the common columns stop_id and trip_id to create a consolidated dataframe (df), combining stop, trip, and time details.

Time Conversion:
The departure_time column, which is in HH:MM:SS format, is converted to an integer representing the hour of departure (e.g., 7:00 AM → 7).

Filtering for Peak Hours:
The code filters the data to include only departure times that fall within the morning (07:00 - 09:00) and evening (16:00 - 18:00) peak periods.

Step 3: Analysis
Spatial Analysis:
The code identifies the busiest bus stops during peak hours by grouping the data by stop_id and stop_name and counting the number of bus departures for each stop. The busiest stops are ranked based on departure frequency.

Temporal Analysis:
A bar plot is created to visualize the hourly departure distribution during the peak periods. It shows the number of bus departures by hour and highlights the AM and PM peak hours.

Geographic Visualization:
A heatmap is generated using geospatial data (latitude and longitude of the stops). This shows the concentration of bus demand at various stops across Montreal, with larger markers representing busier stops.

3️⃣ Where the Data Comes From
Data Source:
The data is sourced from the STM (Société de transport de Montréal), Montreal's public transportation provider. The GTFS data is publicly available and provides comprehensive details about bus routes, schedules, and stops.

Accessing the Data:
The code fetches the GTFS data from a URL, extracts the ZIP file, and loads the necessary CSV files (stops.txt, stop_times.txt, trips.txt) into Pandas DataFrames for analysis.

4️⃣ Final Result
Busiest Transit Hubs (Spatial Output):
The top 10 bus stops with the highest number of departures during peak hours are displayed, representing the most demanded transit hubs in Montreal during these times. This is shown in a styled Pandas DataFrame with a color gradient for easier visual comparison.

Hourly Departure Distribution (Temporal Output):
A bar plot that shows how many bus departures occur at each hour, specifically focusing on the AM and PM peak hours. The plot helps identify the departure frequency during those time frames.

Demand Hotspots (Geographic Output):
A geospatial heatmap that visualizes bus stop demand across Montreal. It uses marker size to represent the departure frequency at each bus stop. This provides a spatial view of bus demand hotspots during the peak periods.

5️⃣ Key Insights from the Results
Peak Time Analysis:
You can identify which hours see the most bus departures, giving insights into bus usage during rush hours.

Demand by Location:
The spatial heatmap highlights areas with high demand, which could be valuable for urban planners or the STM to improve services and infrastructure in specific areas.

🚀 End Goal:
The goal is to produce an insightful, data-driven analysis of Montreal’s bus service, focusing on peak demand hours and locations. This analysis can help improve the efficiency and coverage of the bus network during high-traffic times.

Data fetched from - 

1. https://mobilitydatabase.org/feeds/mdb-2126 
>>>>> https://www.stm.info/sites/default/files/gtfs/gtfs_stm.zip
2. https://donnees.montreal.ca/en/dataset/limites-administratives-agglomeration/resource/e18bfd07-edc8-4ce8-8a5a-3b617662a794 
>>>> https://donnees.montreal.ca/en/dataset/limites-administratives-agglomeration/resource/e18bfd07-edc8-4ce8-8a5a-3b617662a794/download
