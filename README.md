# Chicago Armed Robbery Spatiotemporal Analysis (2002-2023)

A comprehensive econometric analysis exploring the spatial and temporal factors related to armed robbery occurrences in Chicago from 2002 to 2023.

## Overview

A Chicago armed-robbery spatiotemporal analysis pipeline that processes 2002–2023 incident data to quantify temporal patterns, neighborhood clustering, and relationships with socioeconomic, policing, and weather indicators. It features a Python/Jupyter workflow using pandas + GeoPandas for geospatial analysis and statsmodels/linearmodels + scikit-learn (decision trees, random forests) for inference and prediction.

## Research Questions

The analysis addresses several key questions:

- **Spatial Patterns**: How do armed robberies distribute across Chicago's neighborhoods and districts? Is there evidence of a North-South divide?
- **Temporal Dynamics**: What hourly, daily, and seasonal patterns exist in armed robbery occurrences?
- **Location Types**: Which types of locations (commercial zones, residential areas, public spaces, etc.) are most susceptible to armed robberies?
- **Socioeconomic Factors**: How do income inequality (Gini coefficient), unemployment, median income, foreign-born population, and other demographic variables correlate with armed robbery rates?
- **Environmental Conditions**: Do weather patterns and temperature influence armed robbery frequency?
- **Predictive Modeling**: Can we build reliable models to predict armed robbery occurrences based on economic, policing, and crime-related factors?

## Data Sources

The analysis integrates multiple datasets:

- **Chicago Crime Data**: Subset of the Chicago Police Department's crime dataset, filtered specifically for armed robberies (2002-2023) - **included in this repository as `Crimes_-_2001_to_Present.csv`**
- **Socioeconomic Data**: Census data including median income, Gini coefficient, unemployment rates, education levels, and demographic information
- **Housing Data**: Property values and housing prices across Chicago neighborhoods
- **Weather Data**: Temperature and weather pattern data for temporal correlation analysis
- **Policing Data**: Chicago Police Department budget appropriations and arrest rates

### Required Data Files

**Included in Repository:**
- `Crimes_-_2001_to_Present.csv` (35.9 MB) - Chicago crime dataset from the [Chicago Data Portal](https://data.cityofchicago.org/), pre-filtered and ready for analysis

**External Requirements:**
- Chicago neighborhood shapefiles (if running geospatial visualizations) - available from the [Chicago Data Portal](https://data.cityofchicago.org/)
- Socioeconomic and weather data can be sourced from US Census Bureau and NOAA as needed

## Methodology

### Data Cleaning & Organization
- Filtered Chicago crime dataset for armed robberies from 2002-2023
- Excluded incomplete records and outlier year 2001 (only 25 incidents)
- Categorized location descriptions into condensed groups (Commercial Zone, Public Transportation, Education Zone, Residential Area, etc.)
- Divided time into morning, afternoon, and evening/night periods
- Split Chicago districts into North vs. South regions

### Exploratory Data Analysis
- Visualization of crime frequency by year, location type, time of day, and region
- Geospatial mapping using GeoPandas with shapefile integration
- Spatial analysis showing armed robbery clustering patterns
- Correlation analysis between socioeconomic indicators and crime rates

### Statistical Modeling
- **Panel Regression**: Examining relationships between economic factors, policing variables, and armed robberies using statsmodels/linearmodels
- **Decision Trees**: Identifying key predictive features and variable importance
- **Random Forest Models**: Ensemble methods for improved prediction accuracy and robustness

### Key Variables Analyzed
- Economic: Median income, Gini index, unemployment rate
- Policing: Budget appropriations, arrest rates
- Crime: Total crimes, armed robbery trends
- Demographic: Foreign-born population, education levels
- Environmental: Temperature, weather patterns
- Spatial: Geographic coordinates, district classifications

## Key Findings

### Temporal Patterns
- Armed robbery frequency is higher during warmer weather
- Specific time-of-day patterns identified (details in analysis)

### Spatial Distribution
- Evidence of crime clustering in certain southern and peripheral community areas
- North-South divide confirmed when controlling for other factors
- Street-level patterns show concentration in high-crime neighborhoods

### Socioeconomic Correlations
- Weak positive correlation between total crimes and armed robberies
- Moderate relationship between foreign-born population and armed robberies
- Moderate positive correlation with Gini coefficient (income inequality)
- Inequality effects may reflect disproportionate wealth increases

### Predictive Models
1. **Economic Model**: Median income, Gini index, and police appropriations explain some crime variability
   - Unemployment rate lacked statistical significance
   
2. **Policing & Crime Model**: Strong predictive performance
   - Key features: Total crimes, armed robbery arrest rate
   - Southern Chicago shows higher armed robberies when controlling for policing/crime factors
   - Random Forest outperformed regression trees in reliability

## Installation

### Prerequisites
- Python 3.8+
- pip package manager

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/chicago-armed-robbery-analysis.git
cd chicago-armed-robbery-analysis
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Data is included:
   - The `Crimes_-_2001_to_Present.csv` file is included in the repository (35.9 MB)
   - Optional: Download Chicago neighborhood shapefiles from the [Chicago Data Portal](https://data.cityofchicago.org/) for geospatial visualizations
   - Additional socioeconomic and weather datasets may be sourced from US Census Bureau and NOAA as needed for extended analysis

## Usage

Open and run the Jupyter notebook:

```bash
jupyter notebook chicago_armed_robbery_analysis.ipynb
```

Or use JupyterLab for an enhanced experience:

```bash
jupyter lab chicago_armed_robbery_analysis.ipynb
```

The notebook contains all analysis code organized in sequential cells with markdown explanations throughout.

## Project Structure

```
.
├── chicago_armed_robbery_analysis.ipynb  # Main analysis notebook (5.4 MB)
├── Crimes_-_2001_to_Present.csv         # Chicago crime dataset (35.9 MB)
├── requirements.txt                      # Python dependencies
├── README.md                            # This file
├── LICENSE                              # MIT License
└── .gitignore                           # Git ignore rules
```

## Dependencies

Key libraries used:
- **Data Processing**: pandas, numpy, pyarrow
- **Visualization**: matplotlib, seaborn
- **Geospatial**: geopandas, shapely, cartopy
- **Machine Learning**: scikit-learn
- **Statistical Analysis**: statsmodels, linearmodels
- **Web Scraping**: beautifulsoup4, requests
- **Reporting**: stargazer

See `requirements.txt` for complete list with version specifications.

## Literature Context

This research builds upon and extends prior work:

- **Brown (1982)**: Established spatial patterns of suburban crime in Chicago, identifying distance decay from downtown and neighborhood spillover effects
- **Schnell, Braga, & Piza (2017)**: Found street-segment level variability in violent crime and documented temporal decline in overall rates
- **Schnell, DeWitt, & Spencer (2022)**: Identified robbery clustering in southern/peripheral areas and concentration patterns in high-crime neighborhoods
- **Lochner (2007)**: Demonstrated negative relationship between education (high school completion) and crime rates
- **Anser et al. (2020) & Jawadi et al. (2021)**: Highlighted socioeconomic reforms (reducing inequality, unemployment) as crime mitigation strategies

This analysis specifically focuses on armed robberies—a distinct crime category—providing contemporary insights across a 22-year period to inform targeted prevention strategies.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Willis Yorick Zambo Zambo

## Acknowledgments

- Chicago Police Department for public crime data
- US Census Bureau for demographic and economic data
- Academic researchers whose prior work informed this analysis
- Open-source Python data science community

---

**Disclaimer**: This analysis is for educational and research purposes only. The findings should not be used as the sole basis for policy decisions without further validation and expert consultation.
