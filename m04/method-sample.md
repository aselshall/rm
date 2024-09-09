# [Sample of a method section](https://aselshall.github.io/rm/m04/method-sample)

## Proposal title
Exploring the economic impacts of respiratory illnesses arising from red tides in Florida Gulf Coast under climate change scenarios

## Research questions
Leveraging this environmental data science approach, our research questions include:
- Will climate change increase the costs of respiratory illnesses arising from red tides given different bloom levels?
- What are the potential trends of respiratory illnesses in the Florida Gulf Coast caused by pollen under different climate scenarios?
- What are the potential trends of respiratory illnesses in the Florida Gulf Coast due to increased air temperatures under different climate scenarios?

This study will not only address these questions but also pave the way for future research on the combined impacts of multiple environmental factors on public health.


## Method

### Statistical model
We will use a statistical exposure–response model to explore the hypotheses about the relationship between respiratory illnesses and bloom events based on ED visits (Hoagland et al. 2009):

<p align="center">
ED<sub>t</sub> = f(H<sub>t-1</sub>, W<sub>t</sub>, D<sub>t</sub>, T<sub>t</sub>, ε<sub>t</sub>)
</p>

Where:
- *t* indexes time intervals
- *ED* is the number of ED visits due to respiratory illness in a local hospital
- *H* is the red tide cell count in the study area
- *W* is a vector of environmental and weather variables (pollen and air temperature)
- *D* is a measure of regional respiratory disease outbreaks (influenza)
- *T* is a measure of intra-annual population change (due to tourist visits)
- *ε_t* is the residual error term.

The Granger causality test will be used as a statistical hypothesis test to determine whether one time series is useful in forecasting another. Equation (1) will be solved using vector autoregression (VAR), which captures the relationship between multiple variables over time. We will use VAR(p) with automatic selection of lag *p*. All variables are endogenous variables, such that each variable is determined by its relationship with other variables. As such, we can estimate the contribution of each variable (i.e., red tide cell counts, pollen, and air temperature) to the total number of ED visits. 

We will conduct this analysis from 2005 to 2014 using historic data for all variables. Using a sample of one-year data and the Python module statsmodels for statistical modeling, we developed and tested the VAR(p) model in Eq.1 ([https://bit.ly/HABs-Health](https://bit.ly/HABs-Health)). Historic data will be used to parameterize the statistical exposure-response model to be used for future projections. Figure 1 illustrates the data inputs and outputs for both historic and scenario analyses.

![image](https://github.com/user-attachments/assets/d5f78345-1513-45f8-9c88-551687a4f6f8)

*Figure 1. Data models and outputs of historic and scenario analyses.*


### Future projections
We will forecast monthly ED visits from 2015 to 2100, aggregated as five-year averages. Three bloom levels (low, medium, and high) based on historic data will be used, following the bloom level definition by Maze et al. (2015) and concentration levels by the Florida Fish and Wildlife Conservation Commission (FWC-FWRI 2022b). 

For air temperature and pollen, we will use CMIP6 scenarios of SSP2-4.5 and SSP5-8.5. Tourism activity trends will be projected using five-year periods of historic data. Influenza outbreaks will be modeled using historic data from Liu et al. (2020), suggesting that rapid weather variability in autumn could increase influenza risk by 20-50% in northern mid-latitudes in a warming climate. Accordingly,  corrected historic influenza data will be used to predict future conditions. 

Using the model in Equation (1), ED visits will be forecasted for six scenarios (three bloom levels crossed with two CMIP6 climate scenarios). 

### Economic impact
We will estimate the economic impact of respiratory illnesses by calculating the sum of the marginal costs of ED visits and lost productivity during the illness period, based on hospitalized and recuperation days (Hoagland et al. 2009, 2014). Respiratory ailments will be considered for both aerosolized brevetoxins during the historic period and pollen during both historic and future periods. This model can also be adapted for future studies to estimate respiratory ailments due to aerosolized brevetoxins based on predictive red tide scenarios.

### Historic and future data
We have access to all the data needed for the project as follows.

- **Study Area**: Sarasota County, Florida.
- **ED Visit Data**: Daily ED visit data was collected from Sarasota Memorial Hospital (SMH) for 2005-2014. SMH serves about 63% of the county’s population (Hoagland et al. 2009).
- **Red Tide Data**: Karenia brevis cell count data from 2005-2022 were downloaded from NOAA Harmful Algal Blooms Observing System (HABSOS 2022) and supplemented by FWRI (FWC-FWRI 2022a). Cell count data are generally based on event responses sampling and can be non-systematic and non-uniform, Elshall (2021)  bloom data analysis  method was considered.
- **Pollen Data**: Daily pollen counts (pollen grains per cubic meter) from 2005 to 2015 were obtained from the American Academy of Allergy Asthma & Immunology, collected using a Burkard 7-day pollen collector at the University of Florida Gainesville. For future pollen data, the Sarasota County data will be extracted from the dataset of Zhang and Steiner (2022), which is projected pollen magnitude over the continental US under the SSP2-4.5, and SSP5-8.5 scenarios.
- **Air Temperature Data**: Daily air temperature data from 2004 onwards was sourced from the New Pass Weather Station (27.19°N, 82.34°W) (Mote Marine Laboratory 2022). Future air temperature projections (SSP2-4.5 and SSP5-8.5) for Sarasota County will be obtained from NASA Earth Exchange Global Daily Downscaled Projections (NEX-GDDP, Thrasher et al. 2022). The outputs of all available downscaled projections for different global climate models with a simple ensemble average will be used.
- **Influenza Data**: Weekly influenza virus outbreak data for the South Atlantic Region, spanning from 2005 to 2015, were sourced from the U.S. Centers for Disease Control and Prevention (CDC). The data is a measure of the percentage of specimens testing positive for influenza within a particular week, and the data is available for the epidemic period of October through May based on the assumption that the minimal outbreaks periods have little or no influenza cases(Hoagland et al., 2009).  
- **Tourism Data**: Monthly hotel occupancy rates and lodging unit counts for Sarasota County (2005-2015) were obtained from the Sarasota Convention and Visitors Bureau.Assuming two residents per unit, we obtained a monthly estimate of the temporary resident population by summing the number of occupants in all units. We have access to all the data needed for the project.

## References

