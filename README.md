# Roadmap

Research on Southern California wildfires.

---

## Math Model

   - **Layer Interactions**: Formalize bidirectional feedback between layers using **coupled dynamical systems**:
     $$
     \begin{aligned}
     	\frac{\mathrm{d}E_{h}}{\mathrm{d}t}&=f_h(H, W)\\
     	W_r&=g_r(E, H)\\
     	P(x,y,t)&=\exp\left(\beta_0 + \beta_1 H(x,t) + \beta_2 E(x,t) + \phi(x,t)\right)
     \end{aligned}
     $$
     
     
     - **Human Activities (H)**: Migration density, energy consumption (e.g., per capita kWh), land-use policies
     - **Environmental Factors (E)**: Temperature, humidity, NDVI (vegetation health), soil moisture
     - **Wildfire Dynamics (W)**: Ignition probability, fire spread rate, burn severity
       - Wildfire probability of *Spatio-Temporal Bayesian Hierarchical Model* where $\phi(x,t)$ is a spatial random effect (e.g., Gaussian process)
       - Wildfire probability of pair interpretable model: Cox Proportional Hazards Model with ML (Random Forests) for non-linearities (e.g., humidity thresholds for ignition)
     
     
     
   - **Spatio-Temporal Granularity**: data over <u>30m-1km resolution</u> 2D grids (potentially 3D in future) and time to capture microclimates

   - **Layer Feedback Loops**: system dynamics with stock-flow diagram analysis

---

## H2W Data

> [Google Dataset Search](https://datasetsearch.research.google.com/)

   - **Human Layer**
     - Migration & population density
       - [U.S. Census, LODES - employment](https://lehd.ces.census.gov/data/)
       - [U.S. Census servey](https://www.census.gov/programs-surveys.html)
       - [Comprehensive CA Department of Finance Data](https://dof.ca.gov/forecasting/demographics/projections/)
       - [CA Department of Finance Estimates](https://dof.ca.gov/forecasting/demographics/estimates/)
     - Energy
       - [California Energy Commission - electricity generation](https://www.energy.ca.gov/data-reports/energy-almanac/california-electricity-data)
       - [California Independent System Operator](https://www.caiso.com/)
   - **Environmental Layer**
     - [EU Climate Data Store](https://cds.climate.copernicus.eu/datasets)
       - [ERA5-Land hourly data from 1950 to present](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land?tab=download)
     - [NASA USGS - Soil Moisture Active Passive](https://smap.jpl.nasa.gov/data/)
     - [North America CMIP6 climate projections](https://adaptwest.databasin.org/pages/adaptwest-climatena/)
       - [U.S. Climate Projections - Mean Projections](https://climateknowledgeportal.worldbank.org/country/united-states/climate-data-projections-general)
       - [Program for Climate Model Diagnosis & Intercomparison](https://pcmdi.llnl.gov/CMIP6/)
       - [Access to next generation climate data](https://cal-adapt.org/blog/climate-data-access/)
       - [How well have CMIP3, CMIP5 and CMIP6 future climate projections portrayed the recently observed warming](https://www.nature.com/articles/s41598-022-16264-6)
       - [Summary for Policymakers](https://www.ipcc.ch/report/ar6/wg1/downloads/report/IPCC_AR6_WGI_SPM.pdf)
       - [CMIP6: the next generation of climate models explained](https://www.carbonbrief.org/cmip6-the-next-generation-of-climate-models-explained/)
   - **Wildfire Layer**
     - [CalFire Fire Perimeters - historical data](https://www.fire.ca.gov/what-we-do/fire-resource-assessment-program/fire-perimeters)
     - [NASA FIRMS - realtime data](https://firms.modaps.eosdis.nasa.gov/map/)
   - **Grid Data**
     - [NASA Landsat Data](https://landsat.gsfc.nasa.gov/data/)
     - [NASA MODIS Data](https://modis.gsfc.nasa.gov/data/)


---

## W2H Impact Analysis

* Wildfire mediated impacts on human activity
  * **Drinking Water**: burn severity correlating with watershed sediment load via *HEC-HMS hydrologic models*
  * **Energy Prices**: infrastructure damage (e.g., power lines) with *input-output networks*; correlate with [PG&E price volatility data](https://marketchameleon.com/Overview/PCG/IV/), [additional data](https://www.ferc.gov/industries-data/electric/electric-power-markets/caiso)
  * **Land Use**: post-fire rezoning via *cellular automata* (e.g., transition from residential to restricted zone)

* Policy Suggestion

   - **WUI Building Restrictions**: reduce ignition sources (by 40%?)
   - **Renewable Energy Adoption**: simulate decarbonization altering regional temperature trends via [WRF-Chem](https://www2.acom.ucar.edu/wrf-chem) climate simulations

---

## Methodology

* Rank drivers (e.g., humidity vs. migration) via *Sobol Sensitivity Analysis*
* Build **Environmental Layer** using *Python's xarray* (climate data), *Google Earth Engine* (NDVI/soil moisture), etc.
* Develop the Bayesian model for probabilistic inference in *Stan*, *PyMC*, etc.
* Propagate climate/model uncertainty into risk maps via *Monte Carlo Ensemble*
* Couple with system dynamics for policy testing in *Vensim*, *AnyLogic*, etc.

---

## Journals

* *Environmental Research Letters* (focus on impact of fires on water/energy)
* *Spatial Statistics* (focus on model methodology)
* *Nature Sustainability* (focus on policy implications)
