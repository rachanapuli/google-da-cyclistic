# Google Data Analytics Capstone Project

## Overview

As a junior data analyst on the marketing team at Cyclistic, a fictional bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members.

## Data Range and Sources
The data used for the analysis ranges from trips made in January 2023 to December 2023 i.e. 12 months. The source data can be found [here](https://divvy-tripdata.s3.amazonaws.com/index.html).

## Tools Used
- PostgreSQL for data cleaning, manipulation and aggregation
- Tableau for data visualisation

## Process
### 1. Data Combining
The trip data from Jan 2023 to Dec 2023 was downloaded to be accessed locally. The data was categorised by month and was available across 12 CSV files.

At first the data was imported into MS Excel for a basic review however, the files were too big so the spreadsheets were heavy and laggy to navigate.

The files were then imported into the local PostgreSQL server individually. The tables were joined to form a new table with the data for the entire year of 2023 for the purpose of cleaning and analysis.

### 2. Data Cleaning
The resultant table was reviewed for any inconsistencies and nulls. This was achieved by exploring each column individually. Any records with nulls were removed and field lengths were checked for ride_id to make sure there were no discrepancies.

For rideable_type, the different ride types were reviewed and I found that there were 3 different ride types. The start_time and end_time columns were checked for nulls and if the start and end times were captured properly. For 272 records the end time occured before start time which is not possible. So these records were removed too.

Any station names with 'Temp' in their names were removed as those repairs. The coordinates were also checked and the records with nulls were removed.

To make it easier to categorise and visualise the data, the days and months were extracted from the start time to analyse usage trends across weeks and months.

The ride duration is calculated in minutes using the start and end times of the trips. Trips with duration shorter than 1 minute and longer than 1 day i.e. 1440 minutes were filtered out as these were either maintenance trips or the bikes were misplaced.

I then had the table with the data needed for the analysis.

### 3. Data Analysis and Visualisation
As the goal of the analysis is to identify how casual riders and annual members use Cyclistic bikes differently, I started by calculating the average ride duration and the count of trips by user type. I see that casual riders take longer trips on overage with their average ride duration being 23.21 minutes while members' average ride duration being 12.38 minutes. 

However, the majority of the trips are taken by the members with them taking 2739039 trips and casual riders taking 1505256 trips.

Next, I broke down the average ride duration and number of trips by month and user type to understand the difference in the usage by the time of the year.

The months were categorised into seasons and the hours were categorised as time of the day to better understand how members and casual riders were using the service.

The table was prepared for visualisation and imported into Tableau. The data types were checked to ensure the data was accurate before creating a dashboard.

I started by creating charts for user trends across hour of the day, day of the week and month with usage for both members and casual riders highlighted separately. And finally, a [dashboard](https://public.tableau.com/views/GoogleDACapstone_17087127278210/Dashboard1?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link) with the relavant information was created.

## Insights

- From the dashboard, we notice that members take more trips during the week and less on the weekends while the converse is true for casual riders. The average ride duration for the members remain steady across the week but it increases significantly over the weekend.

- Most trips by members start around the morning hours and then again around the evening hours, indicating usage for typical office hours commute. Most trips by casual riders start around late afternoon and evening. This indicates more recreational use. The average ride duration for members remains steady but for casual riders it peaks around late in the morning and early afternoon.

- When looking at monthwise data we see that both members and casual users use the bikes more often during Summer i.e. during favourable weather for outside activities while it is the least during winter months. The average trip duration again remains steady for members while it peaks during Summer for casual riders.

## Recommendations
- As casual users tend to ride for longer nearly twice as long when compared with members, discounts can be offered for longer duration trips. This will draw more casual members to use the service and use them for longer.

- Casual users are most active during the weekends and during Summer and Spring seasons. So new types of subscriptions can be offered, such as one for weekends-only which would be applicable for Friday, Saturday and Sunday and another one being seasonal subscription for Spring and Summer or a quarterly subscription to bridge the gap between no subscription and annual subscription.

- Targeted marketing campaign for the above mentioned plans can be carried out in the recreational hotspots in the city to drive more engagement from casual members.
