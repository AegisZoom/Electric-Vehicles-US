# Excel Project: Electric Vehicle Adoption Across Washington

## Personal Project

### Grade: N/A

## Introduction

This repository contains one of my custom data projects, which I had started shortly after my Graduate Diploma of Data Science. Using my newfound understanding of data along with my already strong experience with Microsoft Excel, 
I constructed a dashboard on electric vehicle (EV) adoption across Washington state in
the United States. This required employing rigorous data cleaning and exploration procedures before creating the final dashboard, which consisted of a choropleth map, a 
heat map, and an interactive bar chart.

## Skills Used

- 🔠 **Microsoft Excel**: Conducted all operations, analysis, cleaning, visualisation and dashboard design using Excel features. This required the use of formulas, filters, Power Query, Power Pivot, conditional formatting, and advanced charting features.
- 📈 **Data Analysis**: Performed statistical measures and constructed visualisations to identify trends in variables. Performed univariate and multivariate analyses to find trends and relationships in data.
- 📊 **Data Visualisation/Dashboard Design**: Used strong visualisation principles to design a dashboard that highlighted the significance of individual data visualisations using position and size, and guided users to naturally view them in the intended order.
Appropriately used visualisations and colours to present relevant information clearly without creating confusion to audiences.
- 🧼 **Data Cleaning**: Used Power Query to reduce data dimensionality and remove unused features. Used functions, filters, pivot tables, and scatter plots to identify outliers, missing values, impossible values, and univariate and multivariate errors to prevent low-quality data from affecting final project output.
- 📧 **Data Retrieval**: Identified suitable dataset of interest, and used Power Query operations to extract, load and transform the dataset for the project.
- 📐 **Problem-Solving**: Selected appropriate techniques and procedures for analysis, visualisation and preprocessing using a mixture of strong theoretical knowledge and natural intuition based on real life experience.
- 🔍 **Attention to Detail**: Identified the presence and implications of trends, relationships, and outliers in the data.
- 🔬 **Research/Self-Learning**: Performed background research in electric vehicles and American geography to better understand relationships between features and check coherence between location variables.

## Data Retrieval

I first encountered this dataset when I was looking for a suitable example to use in an assessment during my studies. Unfortunately it lacked the complexity to satisfy all elements of the rubric for the assessment, but I retained an interest in it and decided to analyse it outside of my studies. Because I started this personal analysis in 2025, it had been updated with 2025 data. I formally reference and acknowledge the dataset below.

State of Washington (2025), *Electric Vehicle Population Data* [data set], Data Gov website, accessed 13/03/2025. [https://catalog.data.gov/dataset/electric-vehicle-population-data](https://catalog.data.gov/dataset/electric-vehicle-population-data)

*Contains information from [State of Washington Open Data](https://data.wa.gov/), which is made available here under the [Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/1-0/).*

The following features of the original dataset are listed and explained below. Features marked with * were not used for the project and were discarded, while features marked with ^ were used for preprocessing and analysis but were removed in the final version to satisfy GitHub's file size constraints.

- **VIN (1-10)^** *[TEXT]*: Vehicle Identification Number - Used to identify different vehicle models (not unique per record)
- **County** *[TEXT]*: The territory that outlines a political division in a state of the US where the vehicle was registered
- **City^** *[TEXT]*: The town where the vehicle was registered
- **State^** *[TEXT]*: The US State where the vehicle was registered. It should only be Washington, but other states also appear.
- **Postal Code^** *[INTEGER]*: The postal code of the town where the vehicle was registered
- **Model Year^** *[INTEGER]*: The year the registered vehicle was designed (1999-2025)
- **Make** *[TEXT]*: The company that constructed the registered vehicle
- **Model** *[TEXT]*: The specific model of the registered vehicle
- **Electric Vehicle Type^** *[TEXT]*: Battery Electric Vehicle (BEV) vs Plug-In Hybrid (PHEV)
- **Clean Alternative Fuel Vehicle (CAFV) Eligibility^** *[TEXT]*: Indicates if the vehicle is eligibile for the American renewable scheme, which requires operating on renewable energy sources while satisfying an electric range threshold.
- **Electric Range*** *[INTEGER]*: The distance the vehicle can travel (miles) on one full battery charge
- **Base MSRP*** *[INTEGER]*: Manufacturer's Suggested Retail Price
- **Legislative District^** *[INTEGER]*: The group of counties that share the legislative district for vehicle legislation
- **DOL Vehicle ID** *[INTEGER]*: Washington State Department of Licensing ID (Unique per record, can use as ID column)
- **Vehicle Location^** *[GEOPOINT]*: Geospatial coordinates of where the vehicle was registrated
- **Electric Utility*** *[TEXT]*: Supplier of energy in the location where the vehicle was registrated
- **2020 Census Tract*** *[INTEGER]*: Likely some ID that uniquely identifies Electric Utility values

The features that remain in *Dashboard.zip* and their updated names are listed below:

**DOL Vehicle ID** -> **DOL_ID**

**County** -> **County**

**Make** -> **Manufacturer**

**Model** -> **Model**

## Data Cleaning

All data preprocessing, transformation, and feature changes are recorded in *Cleaning Log.xlsx*. Processes ranged from simple checks of missing values, duplicates, and sanity checks, to pivot table generation and multivariate scatter plot analysis. An example of a multivariate scatter plot is shown below to illustrate checks for multivariate location anomalies.

![CountyScatter](https://github.com/AegisZoom/Electric-Vehicles-US/blob/main/CountyScatter.PNG)

***Note**: If Python or R was used for this project instead, then checks for multivariate outliers between counties and locations would be as simple as checking if each point resides in the geographic polygon of their corresponding county. Unfortunately, this cannot be done in Excel, so this manual approach was used.*

## The Final Dashboard

As a result of the rigorous data cleaning and analysis procedures undertaken, a dashboard was constructed to visualise how the market for electric vehicles varies across Washington. The dashboard is shown below as a static image. It is not to scale, in reality the dashboard's proportions are designed so that all text and visual elements are easy to see and discern across the full width of the screen, with no need for tabs or scrolling.

![Dashboard](https://github.com/AegisZoom/Electric-Vehicles-US/blob/main/Dashboard.PNG)

Three separate questions were posited during the design phase of the dashboard that directed its intended objective, as well as the best visual elements to use for that purpose.

**1. How does each area in Washington vary in electric vehicle adoption?**

This is likely the most direct question the audience would ask in relation to the topic, and the most straightforward to answer. As such, it is positioned to the top-right of the dashboard as it will be the first area the audience would naturally look to. A choropleth map is employed, as it allows the audience to directly infer which areas of Washington are most receptive to electric vehicles. The colours used were of low saturation, as bright colours can be difficult or distracting. Red was selected for high values and blue was selected for low values, as that aligns with natural human intuition and colour theory. Purple is used as a middle-ground to better enable visual comparison and contrast between different values.

**2. How does each car brand and model vary in electric vehicle sales?**

Another prominent and straightforward question, particular for those aiming to understand which brands and models are worth purchasing. Unlike the previous question, location is irrelevant to understanding this question. As such, this can easily be resolved using a bar graph. Due to the presence of the third question below, it was possible to take liberties and opt
for an approach that compared car models under the same manufacturer to each other using interactive features, rather than creating a static comparison between different manufacturers. This allowed for the preventation of clutter and visual overload when comparing individual car model performance. A similar blue is used for the bar graph to the choropleth map to allow for visual harmony in the dashboard.

**3. Which brands see the most success in each area of Washington?**

This question is a union of the two previous questions, and was the most difficult to answer. Map-based representations of data struggle to show multiple simultaneous comparisons between locations without overloading audiences with imagery and generating confusion. As a result, instead of creating a geographical map, a heat map was used. The advantage was that it was easy and precise to compare different combinations of counties and manufacturers, and naturally set up for further exploration using the other two visualisations. As such, it made sense to position this to the right side of the dashboard as the secondary chronological experience for audiences. Its size also demonstrated its importance to the dashboard.

## Files and Specifications

In this repository, the only two files of interest are *EV Dashboard.zip* and *Cleaning Log.xlsx*. The former when unzipped contains the dashboard and relevant data used. The latter lists all data preprocessing procedures undertaken to cleanse the dataset of errors before use.

Note that *CountyScatter.PNG* and *Dashboard.PNG* are simple image files used to populate the repository description.

