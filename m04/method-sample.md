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
A statistical exposure–response model will be used to explore the hypotheses about the relationship between respiratory illnesses and bloom events based on ED visits (Hoagland et al. 2009):

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
- *ε* is the residual error term.

The Granger causality test will be used as a statistical hypothesis test to determine whether one time series is useful in forecasting another. Eq. (1) will be solved using vector autoregression (VAR), which captures the relationship between multiple variables over time. VAR(p) with automatic selection of lag *p* will be used. All variables are endogenous variables, such that each variable is determined by its relationship with other variables. As such, the contribution of each variable (i.e., red tide cell counts, pollen, and air temperature) to the total number of ED visits can be estimated.

The analysis will be conducted from 2005 to 2014 using historic data for all variables. Using a sample of one-year data and the Python module statsmodels for statistical modeling, we developed and tested the VAR(p) model in Eq.1 ([https://bit.ly/HABs-Health](https://bit.ly/HABs-Health)). Historic data will be used to parameterize the statistical exposure-response model to be used for future projections. Figure 1 illustrates the data inputs and outputs for both historic and scenario analyses.

![image](https://github.com/user-attachments/assets/d5f78345-1513-45f8-9c88-551687a4f6f8)

*Figure 1. Data models and outputs of historic and scenario analyses.*


### Future projections
Monthly ED visits from 2015 to 2100, aggregated as five-year averages, will be forecasted. Three red tides bloom levels (low, medium, and high) based on historic data will be used, following the bloom level definition by Maze et al. (2015) and concentration levels by the Florida Fish and Wildlife Conservation Commission (FWC-FWRI 2022b).  For air temperature and pollen, CMIP6 scenarios of SSP2-4.5 and SSP5-8.5 will be used. Tourism activity trends will be projected using five-year periods of historic data. Influenza outbreaks will be modeled using historic data from Liu et al. (2020), suggesting that rapid weather variability in autumn could increase influenza risk by 20-50% in northern mid-latitudes in a warming climate. Corrected historic influenza data will be used to predict future conditions.  Using the model in Eq. 1, ED visits will be forecasted for six scenarios (three bloom levels crossed with two CMIP6 climate scenarios) as shown in Figure 1. 

### Economic impact
We will estimate the economic impact of respiratory illnesses by calculating the sum of the marginal costs of ED visits and lost productivity during the illness period, based on hospitalized and recuperation days (Hoagland et al. 2009, 2014). Respiratory ailments will be considered for both aerosolized brevetoxins during the historic period and pollen during both historic and future periods. This model can also be adapted for future studies to estimate respiratory ailments due to aerosolized brevetoxins based on predictive red tide scenarios.

### Historic and future data
We have access to all the data needed for the project as follows.

- **Study area**: Sarasota County, Florida.
- **ED visit data**: Daily ED visit data was collected from Sarasota Memorial Hospital (SMH) for 2005-2014. SMH serves about 63% of the county’s population (Hoagland et al. 2009).
- **Red tide data**: Karenia brevis cell count data from 2005-2022 were downloaded from NOAA Harmful Algal Blooms Observing System (HABSOS 2022) and supplemented by FWRI (FWC-FWRI 2022a). Cell count data are generally based on event responses sampling and can be non-systematic and non-uniform, Elshall (2021)  bloom data analysis  method was considered.
- **Pollen data**: Daily pollen counts (pollen grains per cubic meter) from 2005 to 2015 were obtained from the American Academy of Allergy Asthma & Immunology, collected using a Burkard 7-day pollen collector at the University of Florida Gainesville. For future pollen data, the Sarasota County data will be extracted from the dataset of Zhang and Steiner (2022), which is projected pollen magnitude over the continental US under the SSP2-4.5, and SSP5-8.5 scenarios.
- **Air temperature data**: Daily air temperature data from 2004 onwards was sourced from the New Pass Weather Station (27.19°N, 82.34°W) (Mote Marine Laboratory 2022). Future air temperature projections (SSP2-4.5 and SSP5-8.5) for Sarasota County will be obtained from NASA Earth Exchange Global Daily Downscaled Projections (NEX-GDDP, Thrasher et al. 2022). The outputs of all available downscaled projections for different global climate models with a simple ensemble average will be used.
- **Influenza data**: Weekly influenza virus outbreak data for the South Atlantic Region, spanning from 2005 to 2015, were sourced from the U.S. Centers for Disease Control and Prevention (CDC). The data is a measure of the percentage of specimens testing positive for influenza within a particular week, and the data is available for the epidemic period of October through May based on the assumption that the minimal outbreaks periods have little or no influenza cases(Hoagland et al., 2009).  
- **Tourism data**: Monthly hotel occupancy rates and lodging unit counts for Sarasota County (2005-2015) were obtained from the Sarasota Convention and Visitors Bureau.Assuming two residents per unit, we obtained a monthly estimate of the temporary resident population by summing the number of occupants in all units. We have access to all the data needed for the project.

## References 
- Elshall, A. S. (2021). Codes for the manuscript of prescreening-based subset selection for improving predictions of Earth system models for regional environmental management of red tide. Zenodo. https://doi.org/10.5281/zenodo.5534931
- FWC-FWRI. (2022a). HAB Monitoring Database. Retrieved November 15, 2022, from https://myfwc.com/research/redtide/monitoring/database/
- FWC-FWRI. (2022b). Red Tide Current Status. Retrieved November 15, 2022, from https://myfwc.com/research/redtide/statewide/
- HABSOS. (2022). National Centers for Environmental Information (NCEI Accession 0120767). NOAA National Centers for Environmental Information. Dataset. https://www.ncei.noaa.gov/archive/accession/0120767. Retrieved November 15, 2022, from
- Hoagland, P., Jin, D., Polansky, L. Y., Kirkpatrick, B., Kirkpatrick, G., Fleming, L. E., et al. (2009). The Costs of Respiratory Illnesses Arising from Florida Gulf Coast Karenia brevis Blooms. Environmental Health Perspectives, 117(8), 1239–1243. https://doi.org/10.1289/ehp.0900645
- Liu, Q., Tan, Z.-M., Sun, J., Hou, Y., Fu, C., & Wu, Z. (2020). Changing rapid weather variability increases influenza epidemic risk in a warming climate. Environmental Research Letters, 15(4), 044004. https://doi.org/10.1088/1748-9326/ab70bc
- Maze, G., Olascoaga, M. J., & Brand, L. (2015). Historical analysis of environmental conditions during Florida Red Tide. Harmful Algae, 50, 1–7. https://doi.org/10.1016/j.hal.2015.10.003
- Mote Marine Laboratory. (2022). Database Query for Newpass Weather Data. Retrieved November 15, 2022, from http://isurus.mote.org/newpass/newpass_get_weather.phtml
- Thrasher, B., Wang, W., Michaelis, A., Melton, F., Lee, T., & Nemani, R. (2022). NASA Global Daily Downscaled Projections, CMIP6. Scientific Data, 9(1), 262. https://doi.org/10.1038/s41597-022-01393-4
- Zhang, Y., & Steiner, A. L. (2022). Projected climate-driven changes in pollen emission season length and magnitude over the continental United States. Nature Communications, 13(1), 1234. https://doi.org/10.1038/s41467-022-28764-0


