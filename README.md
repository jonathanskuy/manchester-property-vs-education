# Exploring the Relationship Between Property Prices and Education Quality in Manchester

## Overview
This is a data science project focusing on exploring the relationship between property prices in Manchester and the quality of nearby schools and educational institutes.

## Aim
The main aim of this project is to explore and analyse the relationship between property prices and education in Manchester and determine places suitable for doing property business, with the analytical aim focusing on inference. This project will also briefly analyse the effect of having a nearby school in the area on property prices in Manchester.

## Objectives
1.	**“To investigate the relationship between property prices in Manchester and the education quality within the area, and the effect of having nearby schools within the area.”:** The correlation between these variables will be analysed, where a positive correlation indicates higher education quality increases property prices. Alternatively, as some areas may contain no schools or no valid school ratings/scores, the effect of having nearby schools within the area will be studied as well.
2.	**“To determine the suitability of doing property business in subregions within Manchester based on the surrounding area’s education quality.”:** Generally, investment suitability here could be indicated by property prices, where higher prices can mean higher demand.


## Methods
TBD

## Results
TBD

## Recommendations
TBD

## Project Structure
TBD

## How to Run
TBD

## Data Sources
### Price Paid Data
- Provider: UK HM Land Registry
- Description: Dataset containing residential property transaction data across England and Wales
- Version: 2020-2024
- Key Variables Used:
  - Transaction Unique Identifier
  - Price
  - Date of Transfer
  - Property Type (Detached, Semi-Detached, Terraced, Flats/Maisonettes, Other)
  - Property Condition (Old, New)
  - Duration (Freehold, Leasehold)
  - Postcode
- Purpose: Provides data for the dependent variable (property prices in Manchester).
- Link: [Price Paid Data](https://www.gov.uk/government/statistical-data-sets/price-paid-data-downloads)
### Five-Year Ofsted Inspection Data
- Provider: Office for Standards in Education (Ofsted)
- Description: Dataset containing inspection results and ratings of educational institutes across England.
- Version: 2020-2024
- Key Variables Used:
  - As At Date
  - Postcode
  - Overall Effectiveness (1-4)
- Purpose: Provides data for the main independent variable (education quality in Manchester).
- Link: [Five-Year Ofsted Inspection Data](https://www.gov.uk/government/publications/five-year-ofsted-inspection-data)
### ONS Postcode Directory (August 2025)
- Provider: Office for National Statistics (ONS)
- Description: Dataset containing postcodes and their geographic coordinates.
- Version: August 2025
- Key Variables Used:
  - Postcode
  - Local Authority District Code
  - Latitude
  - Longitude
  - LSOA Code
  - MSOA Code
- Purpose: Used to aggregate data together at the MSOA level.
- Link: [ONS Postcode Directory (August 2025)](https://geoportal.statistics.gov.uk/datasets/295e076b89b542e497e05632706ab429/about)
### English Indices of Deprivation 2025
- Provider: UK Government (MHCLG)
- Description: Dataset containing measures of deprivation across areas in England.
- Version: IMD 2025
- Key Variables Used:
  - LSOA Code
  - Local Authority District Code
  - IMD Rank
  - IMD Decile
- Purpose: Serves as a control variable to consider socioeconomic differences between areas.
- Link: [English Indices of Deprivation 2025](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2025)
### Middle layer Super Output Areas (December 2021) Boundaries EW BGC (V3)
- Provider: Office for National Statistics (ONS)
- Description: Dataset containing the geographic boundaries of Middle layer Super Output Areas (MSOAs) in the UK.
- Version: December 2021
- Key Variables Used:
  - MSOA Code
  - Geometry
- Purpose: Used to enable spatial mapping of property transactions, education quality, and deprivation of areas across Manchester.
- Link: [Middle layer Super Output Areas (December 2021) Boundaries EW BGC (V3)](https://geoportal.statistics.gov.uk/datasets/295e076b89b542e497e05632706ab429/about)

## Limitations and Ethical Considerations
TBD

## Author
Marcellinus Jonathan Evanda
jonathanindarto1001@gmail.com
