# [Sample of a method section](https://aselshall.github.io/rm/m04/method-sample)

## Proposal title
Exploring the economic impacts of respiratory illnesses arising from red tides in Florida Gulf Coast under climate change scenarios

## Research Questions
Leveraging this environmental data science approach, our research questions include:
- Will climate change increase the costs of respiratory illnesses arising from red tides given different bloom levels?
- What are the potential trends of respiratory illnesses in the Florida Gulf Coast caused by pollen under different climate scenarios?
- What are the potential trends of respiratory illnesses in the Florida Gulf Coast due to increased air temperatures under different climate scenarios?

This study will not only address these questions but also pave the way for future research on the combined impacts of multiple environmental factors on public health.

---

## Method

### Statistical Model
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

The Granger causality test will be used as a statistical hypothesis test to determine whether one time series is useful in forecasting another. Equation (1) will be solved using vector autoregression (VAR), which captures the relationship between multiple variables over time. We will use VAR(p) with automatic selection of lag *p*, treating all variables as endogenous.

We will conduct this analysis using historic data from 2005 to 2014. A sample of one-year data was used, and the Python module `statsmodels` was employed to develop and test the VAR(p) model in Equation (1) ([source](https://bit.ly/HABs-Health)). Historic data will be used to parameterize the statistical model for future projections. 

Figure 1 illustrates the data inputs and outputs for both historic and scenario analyses.

### Future Projections
We will forecast monthly ED visits from 2015 to 2100, aggregated as five-year averages. Three bloom levels (low, medium, and high) based on historic data will be used, following the bloom level definition by Maze et al. (2015) and concentration levels by the Florida Fish and Wildlife Conservation Commission (FWC-FWRI 2022b). 

For air temperature and pollen, we will use CMIP6 scenarios of SSP2-4.5 and SSP5-8.5. Tourism activity trends will be projected using five-year periods of historic data. Influenza outbreaks will be modeled using historic data from Liu et al. (2020), suggesting that rapid weather variability in autumn could increase influenza risk by 20-50% in some regions. Corrected historic influenza data will be used to predict future conditions. 

Using the model in Equation (1), ED visits will be forecasted for six scenarios (three bloom levels crossed with two CMIP6 climate scenarios). 

### Economic Impact
We will estimate the economic impact of respiratory illnesses by calculating the sum of the marginal costs of ED visits and lost productivity during the illness period, based on hospitalized and recuperation days (Hoagland et al. 2009, 2014). Respiratory ailments will be considered for both aerosolized brevetoxins during the historic period and pollen during both historic and future periods. This model can also be adapted for future studies to estimate respiratory ailments due to aerosolized brevetoxins based on predictive red tide scenarios.

---

## Data Sources

- **Study Area**: Sarasota County, Florida.
- **ED Visit Data**: Daily ED visit data was collected from Sarasota Memorial Hospital (SMH) for 2005-2014. SMH serves about 63% of the county’s population (Hoagland et al. 2009).
- **Red Tide Data**: Karenia brevis cell count data from 2005-2022 were downloaded from NOAA Harmful Algal Blooms Observing System (HABSOS 2022) and supplemented by FWRI (FWC-FWRI 2022a).
- **Pollen Data**: Daily pollen counts (pollen grains per cubic meter) from 2005 to 2015 were obtained from the American Academy of Allergy Asthma & Immunology, collected using a Burkard 7-day pollen collector at the University of Florida Gainesville.
- **Air Temperature Data**: Daily air temperature data from 2004 onwards was sourced from the New Pass Weather Station (27.19°N, 82.34°W) (Mote Marine Laboratory 2022). Future air temperature projections (SSP2-4.5 and SSP5-8.5) for Sarasota County will be obtained from NASA Earth Exchange Global Daily Downscaled Projections (NEX-GDDP, Thrasher et al. 2022).
- **Influenza Data**: Weekly influenza virus outbreak data for the South Atlantic Region, spanning from 2005 to 2015, were sourced from the U.S. Centers for Disease Control and Prevention (CDC).
- **Tourism Data**: Monthly hotel occupancy rates and lodging unit counts for Sarasota County (2005-2015) were obtained from the Sarasota Convention and Visitors Bureau.

---

## References

- Hoagland, P. et al. (2009). Economic impacts of respiratory illnesses from red tides.
- Maze, E. et al. (2015). Bloom levels and their economic consequences.
- Florida Fish and Wildlife Conservation Commission (FWC-FWRI 2022b).
- Liu, Y. et al. (2020). Influenza outbreaks in the warming climate.

---

![Figure 1](path/to/figure.png)
*Figure 1. Data models and outputs of historic and scenario analyses.*

