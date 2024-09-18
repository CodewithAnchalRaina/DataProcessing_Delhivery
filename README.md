# Data_Processing_Delhivery

**Problem Statement:**

Delhivery wants to understand and process data from its data engineering pipelines. The goal is to clean, manipulate, and make sense of raw data to help the data science team build forecasting models. Key tasks include cleaning, sanitizing, and feature extraction from raw fields, particularly focusing on the trip data and delivery operations.

**Approach:**

**Step 1: Basic Data Cleaning and Exploration**

**Handling Missing Values:**

By filling missing values using the mean and mode, we ensured that no valuable data was lost. This improved the completeness of our dataset, making all columns usable for further analysis without bias caused by missing data.

**Analyzing the Structure of the Data:**

Understanding the structure of the data helped us identify the key columns (such as time, distance, and source/destination names) and plan the necessary transformations. This allowed for efficient preparation and aggregation of data later.

**Merging Rows:**

Merging rows by trip_uuid, source_center, and destination_center provided a unified view of the trips, combining segment-level data into meaningful totals. This reduced redundancy and made it easier to analyze the entire trip, rather than individual segments.

**Step 2: Feature Extraction**

**Splitting Source and Destination Names:**

Extracting city and state from source and destination names enabled us to perform region-specific analyses. This makes it easier to identify the most problematic routes or states where delivery times are longer, leading to better-targeted optimizations.

**Extracting Time-Based Features:**

Extracting month, year, day, and hour from trip_creation_time allowed us to spot potential seasonal patterns or peak times for deliveries. This can help in resource planning, such as allocating more vehicles during high-traffic periods or improving scheduling.

**Step 3: In-depth Analysis and Feature Engineering**

**Calculating Trip Duration:**

Calculating the trip duration between od_start_time and od_end_time provided a key metric for measuring delivery efficiency. With this, we can identify if certain routes or regions consistently take longer than expected, allowing for route improvements.

**Hypothesis Testing and Visual Analysis (Actual Time vs Trip Duration):**

By visually comparing actual_time and trip_duration, and conducting a t-test, we identified whether there were significant discrepancies between the two metrics. This helped us understand if the actual delivery time was in line with the trip duration, pinpointing inefficiencies where the times didn't match.

![output](https://github.com/user-attachments/assets/2aebe58d-9cbc-4535-a333-aaf8df3af145)

**Comparing Aggregated Actual Time vs OSRM Time:**

This comparison revealed how well the OSRM (open-source routing engine) time estimates match the actual delivery times. Identifying routes where OSRM time significantly underestimates or overestimates delivery times helps in improving predictions and overall planning.

![output (1)](https://github.com/user-attachments/assets/009cad70-822e-4098-9d26-5cd0f51f0ec4)

![output (2)](https://github.com/user-attachments/assets/dc1cf636-d92b-49a9-af10-e3111bdbda26)

**Outlier Detection Using the IQR Method:**

Detecting and visualizing outliers helped identify unusual deliveries that took much longer than expected. By flagging these outliers, we can investigate whether they were caused by system inefficiencies or external factors (such as weather or traffic incidents).

**Handling Outliers by Capping:**

Capping outliers ensured that extremely high or low values no longer skewed the analysis. This resulted in more accurate averages and trends, improving decision-making based on real-world, typical delivery times rather than rare anomalies.

**One-Hot Encoding for Categorical Columns:**

By converting categorical variables into numerical form using one-hot encoding, we made the dataset suitable for machine learning and analysis. This transformation was essential for including route types and city/state information in models without introducing bias from categorical values.

**Normalization and Standardization:**

Standardizing the continuous features (like actual_time and osrm_time) placed all features on the same scale, preventing any one feature from dominating the analysis. This ensures that models can learn from all features equally, improving performance.

**Recommendations:**

Fix Missing Data: Always ensure that missing values are handled properly, either by filling them or removing them, to avoid incomplete analysis.

Analyze Time-Based Trends: Look into delivery times by month, day, or hour to identify periods where deliveries slow down and find ways to speed them up.

Check for Inconsistent Data: Regularly compare actual and predicted times (like actual_time vs osrm_time) to find gaps where estimates are off.

Handle Outliers: Remove or cap outliers that could skew your analysis. They can come from unexpected delays or data entry errors.
Standardize Your Data: Make sure all your data is on the same scale, so different features don't overpower each other when doing any kind of analysis.

Automate Feature Extraction: Features like month, year, and city should be automatically extracted from date or text columns for easy analysis and modeling.

**Conclusion:**

Each step we completed helped clean, enhance, and standardize the dataset, making it more reliable for analysis. Through missing value handling, feature extraction, outlier detection, and normalization, we improved the quality and usability of the data. This directly translates into better insights for identifying operational bottlenecks, improving route efficiency, and ensuring accurate delivery time predictions.

These coding steps ensure that Delhivery's data is ready for in-depth analysis and can be used to develop accurate forecasting models, optimize delivery routes, and make data-driven decisions to enhance operational efficiency.
