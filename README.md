# Exploring the Relationship Between Property Prices and Education Quality in Manchester

## Overview
This is a data science project focusing on exploring the relationship between property prices in Manchester and the quality of nearby schools.

## Aim
The main aim of this project is to explore the relationship between property prices and education in Manchester and identify areas with property-investment potential, with the analytical aim focusing on inference.

## Objectives
1.	**“To investigate the relationship between property prices in Manchester and the education quality within the area, and the effect of having nearby schools within the area.”:** The correlation between these variables will be analysed, where a positive correlation indicates higher education quality can link towards property prices. Alternatively, some areas may contain no schools or no valid ratings/scores, so the effect of having valid schools within the area will be studied as well.
2.	**“To determine the suitability of doing property business in subregions within Manchester based on the surrounding area’s education quality.”:** Generally, investment-suitability is considered through property prices, where higher prices may reflect more-desirable/favourable locations, while acknowledging how other factors can influence outcomes.

## Methods
The model used in this project is multiple linear regression, because it allows visualising relationships between two main variables while considering other independent variables possibly affecting outcomes. In this case, the main independent variable is area-level education quality and the dependent variable is house prices.

Due to this project’s analytical aim being inference, interpreting p-value of variables can determine whether the relationship is statistically significant. Furthermore, the Adjusted Coefficient of Determination (R2) can be used to evaluate how well the model explains variation in house prices, but mainly this project focuses on understanding the relationship between education quality and house prices in Manchester rather than prediction. Additionally, model comparison involves interpreting Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) of each model to compare school quality and access, and using Akaike Information Criterion (AIC) to explore which model fits better. These metrics help decide whether education quality significantly affects house prices and/or whether having nearby/valid schools affects house prices, answering Research Objective 1.

Research Objective 2 is fulfilled with spatial mapping to highlight areas containing more investment potential where, expectedly, higher-quality education relates to higher property prices, also considering other control factors. Regression model results can also support investment insights/recommendations.

## Key Results
- Education quality has a coefficient of ~-0.043. This indicates that, given that other variables are constant, property prices decrease by ~4.3% with every one-unit increase in the MSOA's mean Ofsted score given that higher scores mean lower education quality. Therefore, higher education quality can be associated with higher property prices. Once control variables are considered, this association is statistically significant at 1% (p-value < 0.01).
- School presence has a coefficient of ~0.011. This indicates that, given that the other variables are constant, property prices decrease by ~1.1% when there is a school nearby (in the same MSOA) than when there are no schools. Therefore, the presence of schools can be associated with lower property prices. However, once control variables are considered, this association is not statistically significant at 5% (p-value = ~0.352).
- The education quality model (MAE ≈ 0.363; RMSE ≈ 0.647) and the school presence model (MAE ≈ 0.359; RMSE ≈ 0.641) have similar predictive accuracies. However, the former’s AIC (~67331.547) is considerably lower than that of the latter (~75487.622), signifying that the education quality model fits better, accounting for model complexity. This suggests that education quality provides a more-meaningful explanation of property price variation than school presence.

## Recommendations
- Findings from regression modelling and spatial mapping suggest areas within Manchester city with better property-investment opportunities tend to be those combining good-quality education, lower socioeconomic deprivation, and strategic positioning. These areas tend to have associations with higher property prices, which may suggest higher demand, and potential implications for rental yields too.
- These results also provide insights on identifying investment opportunities in areas where the factors studied are not reflected in their property prices as much. For instance, areas showcasing high-quality education but moderately-priced properties suggest that there may be value-growth potential.
- Conversely, areas showcasing lower-quality education but high-valued properties suggest that other factors relate to property prices stronger, which may indicate different risk-to-return considerations.

## Project Structure
```
manchester-property-vs-education/
├─ data/
│  ├─ processed
│  │  ├─ final_dataset.csv
│  ├─ raw
│  │  ├─ imd.xlsx
│  │  ├─ msoa_boundaries.geojson
│  │  ├─ onspd.csv
│  │  ├─ schools.ods
│  │  ├─ transactions_2020.csv
│  │  ├─ transactions_2021.csv
│  │  ├─ transactions_2022.csv
│  │  ├─ transactions_2023.csv
│  │  ├─ transactions_2024.csv
├─ notebooks/
│  ├─ manchester_property_vs_education.ipynb
├─ .gitattributes
├─ README.md
├─ requirements.txt
```

## Installation
**If the user has Git LFS installed in their system, they can properly pull this repository without any issues with datasets.**

It is acknowledged that users without Git LFS installed in their system may face issues with datasets being shown as Git LFS pointers when downloading this repository, causing errors in loading datasets. Therefore, users without Git LFS installed in their system or users facing other issues concerning the datasets will have to download the datasets from [this Google Drive Link](https://drive.google.com/drive/folders/1cqz7hCKyM13XY0amGJZ5wNIGdFnxS73a?usp=sharing).

## How to Run
After opening this repository locally in their system, users will have to run this command in the terminal to install dependencies required:
```pip install -r requirements.txt```

Afterwards, users can run the notebook ```/notebooks/manchester_property_vs_education.ipynb``` to run the full data pipeline, analysis, and modelling.

## Data Sources
### Price Paid Data
- Provider: HM Land Registry
- Description: Dataset containing residential property transaction data across England and Wales.
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
- Provider: Ministry of Housing, Communities and Local Government (MHCLG)
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
This project must practice proper data protection, especially from a privacy standpoint. This means that any personal and/or sensitive information, if any, should be omitted, especially from the final modelling dataset. Dataset-selection transparency must also be enforced, including using only credible, publicly-available datasets found online. Additionally, data/results bias may be unavoidable, so control variables including MSOA-level deprivation index and distance to the city centre help isolate education quality’s association with property prices. Additionally, p-values and confidence intervals will be used to show how certain the results are.

Furthermore, results may unintentionally suggest that access to good-quality education depends on financial status. Addressing this involves presenting results in a descriptive and analytic manner and aiming recommendations solely to investors, meaning that results will be interpreted in a neutral manner that avoids language portraying lower-priced areas negatively, and that differences across areas will be worded in an investment point-of-view.

Also, there may be limitations to data used, including Ofsted inspection data being periodical (addressable by using the latest inspection data) and property prices being aggregated based on MSOA (meaning that interpretations will be at the MSOA level).

This study overal also holds limitations, including having missing Ofsted data for some MSOAs which might reduce confidence in relationships between education quality and property prices, particularly where uneven data coverage exists. 2020-2024 deprivation data is also unavailable, so a proxy (IMD 2025) was used, which may reduce accuracy compared to actual data. Additionally, MSOA-level aggregation may hide variation/insights within smaller/more-granular regions, potentially decreasing the analysis’ precision. Furthermore, low R2 during modelling may be attributed to unincluded variables including crime/income levels that may also have substantial relationships. Lastly, results should be interpreted as associations rather than causal links.

Based on this study’s limitations, improvements by future studies may include exploring additional variables including crime/income data to provide a more comprehensive property price model. Analysing at more-granular levels like LSOA-level, conditional of data availability, will further boost the analysis’ precision. Finally, using more-advanced methods including panel data methods and spatial regression models will improve results by considering underlying temporal trends and spatial dependencies.

## Author
Marcellinus Jonathan Evanda
jonathanindarto1001@gmail.com
