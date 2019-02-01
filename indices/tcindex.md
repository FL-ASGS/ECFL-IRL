## About

Real time coastal wind, wave, and water level guidance is presented here for the East Central Florida Coast with high resolution in the Indian River Lagoon and Brevard County. These predictions were made by the physics-based ADCIRC+SWAN numerical model using NOAA's North American Mesoscale (NAM) model or the latest forecast/advisory from the National Hurricane Center (NHC). You can also have access to an **operational, ensemble-based, probabilistic wind setup forecasting for the Indian River Lagoon** via [probabilistic real-time forecasts of coastal estuarine setup](https://fit-winds.github.io/IRLSetup/). 

This guidance is for use by official decision makers and does not represent an official forecast. All private citizens are advised to seek information from their local National Weather Service Weather Forecast Office or local Emergency Manager. 

<img src="http://www.nhc.noaa.gov/xgtwo/two_atl_2d0.png">
source [National Hurricane Center (NHC)](http:\\nhc.noaa.gov)

# Tropical Cyclone (Atlantic Basin): Storm stormname
*Real time [hydrographs and wind speed plots](/latest/tclatest_cycle.md) at Melbourne, Virgina Key, Lansing Island in South Banana River, and Sebastian are also available.*

Predicted water Levels (m NAVD88), and overlaid wind (m/s) in Atlantic Basin
<p align="center">
  <img src="/ECFL-IRL/plots/TC/elev_wind.gif">
</p>

**Trident Pier:** Hydrograph (m NAVD88) (Top) / Wind Speed (m/s) (Bottom)

*Small-amplitude, high-frequency oscillations in water level are associated with numerical instability. We are currently working on solving this issue*

<p align="center">
  <img src="/ECFL-IRL/plots/TC/EW_Trident_Pier.png">
</p>

<img align="left" src="/ECFL-IRL/plots/TC/plot20001.jpg" height="660">
<img align="right" src="/ECFL-IRL/plots/TC/plot30001.jpg" height="660" >
Left: Peak Water Levels (m NAVD88) / Right: Max Significant Wave Height (m)

*Real time [hydrographs and wind speed plots](/latest/tclatest_cycle.md) at Melbourne, Virgina Key, Lansing Island in South Banana River, and Sebastian are also available.*

# Guidance Based on NAM Model 
### Three and a half days forecast results
*Real time [hydrographs and wind speed plots](/latest/namlatest_cycle.md) at Melbourne, Virgina Key, Lansing Island in South Banana River, and Sebastian are also available.*

Predicted water Levels (m NAVD88), and overlaid wind (m/s) in Atlantic Basin
<p align="center">
  <img src="/ECFL-IRL/plots/NAM/elev_wind.gif">
</p>

**Trident Pier:** Hydrograph (m NAVD88) (Top) / Wind Speed (m/s) (Bottom)

*Small-amplitude, high-frequency oscillations in water level are associated with numerical instability. We are currently working on solving this issue*

<p align="center">
  <img src="/ECFL-IRL/plots/NAM/EW_Trident_Pier.png">
</p>

<img align="left" src="/ECFL-IRL/plots/NAM/plot20001.jpg" height="660">
<img align="right" src="/ECFL-IRL/plots/NAM/plot30001.jpg" height="660" >
Left: Maximum Surface Elevation (m)   Right: Maximum Wave Height (m)

*Real time [hydrographs and wind speed plots](/latest/namlatest_cycle.md) at Melbourne, Virgina Key, Lansing Island in South Banana River, and Sebastian are also available.*

## Models
### ADCIRC
The ADvanced CIRCulation (ADCIRC) model [[8](/reference/ref.md), [9](/reference/ref.md)] is a system of computer programs commonly used by the Federal Emergency Management Agency ([FEMA](https://www.fema.gov/)), the U.S. Army Corps of Engineers ([USACE](www.usace.army.mil/)), academic research groups, and local agencies. The system computes sea surface elevations, currents, and wind generated waves due to mesoscale processes such as tides and hurricane storm surge. 

### SWAN
To predict wave characteristics, Simulating Waves Nearshore (SWAN), is tightly coupled with ADCIRC (ADCIRC + SWAN) [[4](/reference/ref.md), [3](/reference/ref.md), [2](/reference/ref.md)]. SWAN is a third generation, phase-averaged wave model that employs finite difference method [[1](/reference/ref.md), [6](/reference/ref.md)].

### Models Coupling
In ADCIRC+SWAN, the ADCIRC model passes water level, current velocities, wind velocities, and friction roughness lengths to the SWAN model. SWAN then computes water depth, wave propagation, depth-induced breaking, and other wave processes. These wave characteristics are passed back to ADCIRC where the radiation stress gradients are evaluated at each vertex and used to compute the water level and current velocity at the next time step [[4](/reference/ref.md), [3](/reference/ref.md), [2](/reference/ref.md)].This data passing back-and-forth represents true two-way coupling, producing guidance that takes into account the relevant coastal physics. 

### ADCIRC Surge Guidance System 
The SWAN+ADCIRC coupled model is normally run manually, one run at a time. As a result, in order to make this real time guidance available around the clock, the ADCIRC Surge Guidance System was used to efficiently and reliably automate the process of downloading the latest meteorological data, creating input files, running ADCIRC+SWAN, and post processing the output. The ASGS is open source software with many Official users and contributors, including the US Army Corps of Engineers (USACE), the National Hurricane Center (NHC), and the US Coast Guard (USCG) [[5](ECFL-IRL/reference/ref.md)]. More information is available at the [ASGS GitHub site](https://github.com/jasonfleming/asgs). 

### Visualization
[FigureGen](https://ccht.ccee.ncsu.edu/) is a FORTRAN program that acts as an interface between the SWAN+ADCIRC simulation files and the resulting illustrations. FigureGen is incorporated within the ASGS, and it is used to visualize forecast guidance. The visualization cores read the SWAN+ADCIRC files, convert the data into appropriate formats, and then call the [GMT](https://gmt.soest.hawaii.edu/) tools to generate contours, vectors, etc. Command-driven interactive plotting program; [gnuplot](http:\\www.gnuplot.info/), is also used to plot times series results at specific locations.
click [here](/reference/ref.md) for references.

## Computational Resource

Meteorological force | Computer
-------------------- | -------------
North America Meso-scale (NAM) model | Pelican with 24 nodes
Tropical Cyclone                     | Coconut with 48 nodes

## Contributors

Peyman Taeb, PhD Candidate

Robert J Weaver, PhD

This project is operated and maintained by [FL-ASGS](https://github.com/FL-ASGS/ECFL-IRL), contact us
[email](mailto:fl-asgs@fit.edu)

<img align="left" src="/ECFL-IRL/logo/FIT_logo.jpg" height="150">
<img align="left" src="/ECFL-IRL/logo/IRLIR_Logo.jpg" height="150" >

.
