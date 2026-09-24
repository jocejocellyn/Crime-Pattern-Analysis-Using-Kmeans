# Crime-Pattern-Analysis-Using-Kmeans
An unsupervised learning project that applies **K-Means clustering** to identify patterns among crime incidents based on demographic, environmental, temporal, and facility-related characteristics.

## Project Workflow
Dataset → EDA → Feature Selection → Feature Engineering → Encoding → Scaling → Baseline K-Means → Tuning → Cluster Profiling

## Dataset
The project uses a crime dataset containing information related to:
* Crime incidents
* Time-related characteristics
* Population and demographic features
* Environmental conditions
* Public facilities
* Geographic divisions

## Exploratory Data Analysis
EDA was performed to examine:
* Dataset structure
* Duplicate records
* Feature correlations
* Categorical consistency
* Missing values
* Potentially redundant features

Several redundant or overlapping variables were removed before modeling, including `incident_week`, `weekend`, `visibility`, `male_population`, `female_population`, `incident_district`, and `season`.

The `incident_division` column was also standardized by converting values to lowercase and removing unnecessary whitespace.

## Feature Engineering
Several public facility-related variables were combined into a single **facility index**:
* Religious institution
* Playground
* Park
* Police station
* School
* College

The facility variables were standardized first, then their standardized scores were summed to create the facility index.

This feature was used to represent the overall availability of public facilities within an area.

## Data Preparation
The clustering features included:
* `incident_month`
* `incident_weekday`
* `part_of_the_day`
* `precip`
* `heatindex`
* `total_population`
* `gender_ration`
* `average_household_size`
* `density_per_kmsq`
* `literacy_rate`
* `facility_index`

Categorical variables such as `incident_weekday` and `part_of_the_day` were transformed using **One-Hot Encoding**.

The resulting features were standardized using **StandardScaler** before being used for K-Means clustering.

## Baseline Model
A baseline K-Means model was created using:
```text
n_clusters = 3
random_state = 42
n_init = 10
```

The baseline clustering result was evaluated using the **Silhouette Score** and visualized using PCA.

## Model Tuning
The number of clusters was evaluated across:
```text
k = 2 to 10
```

Two methods were used:
### 1. Elbow Method
The **inertia** value was calculated for each value of k to identify potential points where adding additional clusters provided diminishing improvements.

### 2. Silhouette Score
Silhouette scores were calculated for each value of k to evaluate how well-separated the resulting clusters were. Based on the evaluation, **k = 2** was selected as the final number of clusters.

## Final Model
The final K-Means model was configured as:
```text
n_clusters = 2
random_state = 42
n_init = 10
```

The resulting clusters were visualized using **Principal Component Analysis (PCA)**.

## Cluster Profiling
After clustering, each group was profiled using:

### Numerical Features
* Population
* Population density
* Literacy rate
* Average household size
* Weather-related variables
* Facility index

### Categorical Features
* Day of the week
* Part of the day
* Incident division
* Crime type

Cluster profiles were analyzed using averages, distributions, and the most frequent categorical values to understand the characteristics of each group.

## Evaluation
The project uses:
* Inertia
* Silhouette Score
* PCA visualization
* Cluster profiling

These methods were used to evaluate the clustering structure and interpret the resulting groups.
