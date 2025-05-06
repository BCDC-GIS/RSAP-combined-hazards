# RSAP Combined Hazard Methodology
## Summary
The Bay Adapt Regional Shoreline Adaptation Plan utilizes combined hazard layers to support exposure analysis, guideline development and implementation. These layers represent the potential future flooding condition from sea level rise, groundwater rise, and storm surge/extreme tides. The four layers represent future flooding conditions based on scenarios described in the [2024 State of California Sea Level Rise guidance](https://opc.ca.gov/wp-content/uploads/2024/05/California-Sea-Level-Rise-Guidance-2024-508.pdf).
These layers combine hazard data from two sources, the [Adapting To Rising Tides Bay Shoreline Flood Explorer](https://explorer.adaptingtorisingtides.org/home) and [USGS Coastal Storm Modeling System (CoSMoS)](https://ourcoastourfuture.org/hazard-map/) shallow groundwater rise maps. 

These layers are intended to support Subregional Shoreline Adaptation Plan development. Coastal hazard assumptions are intended to: 
  - Inform planning, not intended to be used for project level design. 
  - Use precautionary assumptions which include higher risk scenarios.
  - Provide flexibility for assessing subregional vulnerability.

*The code included here is specialized for use within the ArcGIS environment. An ArcGIS Basic license is needed to replicate the analysis.*

## Description
The RSAP Combined Hazard layers combine hazard data from two sources, including the Adapting To Rising Tides Bay Shoreline Flood Explorer and the USGS CoSMoS shalow groundwater rise maps to represent future flooding from SLR, groundwater, and storm surge/extreme tides. 

ART flood maps use a Total Water Level (TWL) approach for estimating flood extent that differs from FEMA and other established engineering practices. For ART flood mapping, TWL refers to the combination of tides, storm surge, and sea level rise to contribute to a water level and flood extent above Mean Higher High Water (MHHW), but does not include waves. [You can read more about the ART flood mapping](https://www.adaptingtorisingtides.org/wp-content/uploads/2018/07/BATA-ART-SLR-Analysis-and-Mapping-Report-Final-20170908.pdf). 

Shallow groundwater mapping includes areas that will experience emergent (surface) groundwater flooding as well as estimates of the depth to groundwater (below surface) for future SLR scenarios. At the time of analysis, USGS CoSMoS is the only source of shallow groundwater maps for the whole region. [You can read more about the USGS CoSMoS Groundwater modeling](https://www.usgs.gov/centers/pcmsc/science/cosmos-groundwater). 

A key modeled parameter in the USGS shallow groundwater maps is a measure of groundwater geology called hydraulic conductivity (K) that effects how permeable the subsurface is. For purposes of the regional shallow groundwater rise hazard maps and exposure analysis, we assume a Moderate hydraulic conductivity value of K = 1.0 meter/day.

While mapped depth to groundwater exceeded 15ft in areas, for the purposes of the RSAP exposure analysis, groundwater depths deeper than 9ft were excluded from analysis as they were not considered to have a potential impact to the topic area asset data. To provide additional information to planners related to impact of a hazard on their particular asset for the purposes of a vulnerability assessment, we have broken “Shallow” groundwater into three depth classes: Very Shallow (0-3ft), Shallow (3-6ft), and Moderately Shallow (6-9ft). To further refine the accuracy of the groundwater rise data to areas where groundwater depth was most impacted by SLR, BCDC staff also confined the groundwater rise hazard maps based on methodology developed by [Hill et al. (2023)](https://datadryad.org/stash/dataset/doi:10.6078/D15X4N). This constrained the data set to areas where a change in groundwater between existing conditions and the future scenario was greater than 4in and areas where groundwater table is within 10m of surface.

Using ArcPy, the ART data and USGS COSMOS Groundwater data was combined to create the combined hazard maps for four sea level rise scenarios based around the OPC guidance statewide averages:
  - 1 foot (2050 Intermediate High)
  - 3.1 feet (2100 Intermediate)
  - 4.9 feet (2100 Intermediate-High)
  - 6.6 feet (2100 High)

Table 1.
| Sea Level Rise Scenarios | OPC Guidance | Sea Level Rise  | Groundwater Rise | 100 year Storm Surge |
|----------|----------|----------|----------|----------|
| 2050 | .8-1.2 ft | 1 ft (12”) ART  | .8 ft (9.6") USGS | 4.3 ft (52") ART |  
| 2100 INT | 3.1 ft | 3 ft (36") ART | 3.3 ft (39.6") USGS | 6.4 ft (77") ART |
| 2100 INT-HIGH | 4.9 ft | 4.3 ft (52") ART | 4.9 ft (58.8") USGS | 8 ft (96") ART |  
| 2100 HIGH | 6.6 ft | 6.4 ft (77") ART | 6.6 ft (79.2") USGS | 9 ft (108”) ART  |

However, OPC Guidance recommendations did not always perfectly reflect the water levels available in either ART or COSMOS data. In both cases, we chose the closest value to the recommended water level. All values for both were within half a foot of the OPC guidance value, with most being significantly closer (Table 1).

For each scenario we added a 100 year storm surge value that is approximately 3.5ft greater than the Sea Level Rise value. This value comes from the [AECOM 2016 Tidal Datums and Extreme Tides Study](https://www.adaptingtorisingtides.org/wp-content/uploads/2018/07/FINAL-Regional-Matrix-20180525.pdf) that was produced for the bay. Only goundwater rise data for SLR scenarios and not for the added storm surge water levels were included. This is due to a lack of scientific consensus of how acutely storm surge effects groundwater, how/if the effects of storm surge on groundwater diminish as you move inland, and variation in how quickly groundwater returns to pre storm depths.


These three hazards combined created the following 10 categories which show where multiple hazards are present in the same area:

  - Tidal Inundation + Emergent Groundwater 
  - Emergent Groundwater
  - Storm Surge + Emergent Groundwater
  - Storm Surge + Very Shallow Groundwater (0-3ft)
  - Storm Surge + Shallow Groundwater (3-6ft) 
  - Storm Surge + Moderately Shallow Groundwater (6-9ft) 
  - Storm Surge
  - Very Shallow Groundwater (0-3ft)
  - Shallow Groundwater (3-6ft) 
  - Moderately Shallow Groundwater (6-9ft)

## Credits
BCDC (2024). Bay Adapt Regional Shoreline Adaptation Plan Combined Hazards: SF Bay [spatial data file]. SF Bay Conservation and Development Commission. Accessed at RSAP Atlas.
