
Diving into Montreal’s bus data to identify peak usage zones and recommend rebalancing strategies.

# Montreal Bus (STM) Transit Data Analysis

## Overview

This project analyzes **Montreal bus transit data** to understand **spatial demand patterns** and **temporal demand trends** during peak hours, specifically the **weekday morning (AM) and evening (PM) peaks**. The analysis is based on **GTFS (General Transit Feed Specification)** data, which is commonly used for public transportation analysis. The final result includes a **spatial visualization** of the bus demand hotspots and a **temporal distribution** of bus departures during peak hours.

## Data Source

- **Source:** The data is fetched from the **Montreal transit system's GTFS feed**.
- **URL:** [Montreal GTFS Data](https://www.stm.info/sites/default/files/gtfs/gtfs_stm.zip)

The data contains the following key files:
- **stops.txt**: Information about bus stops (ID, name, latitude, longitude, etc.)
- **stop_times.txt**: Details about bus stop times for each bus trip (arrival/departure times, stop sequences)
- **trips.txt**: Information about each bus trip (trip ID, route, direction, etc.)

## Workflow

### Step 1: Data Collection

The GTFS ZIP file is downloaded from the Montreal transit website, and the relevant CSV files (`stops.txt`, `stop_times.txt`, `trips.txt`) are extracted and loaded into **Pandas DataFrames**.

### Step 2: Data Preprocessing

- **Data Merging:** The datasets (`stops.txt`, `stop_times.txt`, `trips.txt`) are merged on `stop_id` and `trip_id` to create a consolidated dataframe that contains bus stop, trip, and time details.
- **Time Conversion:** The `departure_time` column, originally in **HH:MM:SS** format, is converted to the **hour** of the departure time (e.g., 7:00 AM → 7).
- **Filtering for Peak Hours:** The data is filtered to include only **departure times** within the **morning (07:00 - 09:00)** and **evening (16:00 - 18:00)** peak periods.

### Step 3: Analysis

- **Spatial Analysis:** The busiest bus stops during peak hours are identified by grouping the data by `stop_id` and `stop_name` and counting the number of bus departures at each stop.
- **Temporal Analysis:** A **bar plot** visualizes the **hourly departure distribution** during the peak periods, focusing on AM and PM peak hours.
- **Geographic Visualization:** A **heatmap** is created to visualize bus stop demand across Montreal using **geospatial data** (latitude and longitude). The map highlights busier stops during peak hours.

## Results

### Busiest Transit Hubs (Spatial Output)
- The top 10 bus stops with the highest number of departures during peak hours are displayed, representing the most **demanded transit hubs** in Montreal during these times.

### Hourly Departure Distribution (Temporal Output)
- A **bar plot** that shows the number of bus departures at each hour, specifically focusing on the **AM and PM peak hours**.

### Demand Hotspots (Geographic Output)
- A **geospatial heatmap** visualizing bus stop demand across Montreal, with larger markers representing busier stops during peak periods.

## Conclusion

The goal of this project is to provide an insightful, **data-driven analysis** of Montreal’s bus service, with a focus on peak demand hours and locations. The results of this analysis can help the **STM (Société de transport de Montréal)** improve services and optimize infrastructure in high-traffic areas.

## Installation

### Requirements
- Python 3.x
- Pandas
- Matplotlib
- Seaborn
- Geopandas
- Requests

### Setup

Data fetched from - 

1. https://mobilitydatabase.org/feeds/mdb-2126 
>>>>> https://www.stm.info/sites/default/files/gtfs/gtfs_stm.zip
2. https://donnees.montreal.ca/en/dataset/limites-administratives-agglomeration/resource/e18bfd07-edc8-4ce8-8a5a-3b617662a794 
>>>> https://donnees.montreal.ca/en/dataset/limites-administratives-agglomeration/resource/e18bfd07-edc8-4ce8-8a5a-3b617662a794/download
