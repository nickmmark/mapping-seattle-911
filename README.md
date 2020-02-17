# mapping-seattle-911
Mapping and geospatial analysis of open source Seattle Fire Realtime 911 data, with a particular focus on out of hospital cardiac arrest (OHCA). 

![mapping cardiac arrest calls in Seattle, WA](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot%202.png)

_[live and interactive heatmap](https://jsfiddle.net/user/nickmmark/fiddles/) showing the locations of cardiac arrests in Seattle, WA_

### Background
[Out of Hospital Cardiac Arrest](https://www.cdc.gov/mmwr/preview/mmwrhtml/ss6008a1.htm) is a life threatening emergency. Prompt initation of high quality CPR, early defibrilation, and advanced life support and transport to a suitable medical center can dramatically improve outcomes. Because of the time sensitive nature of cardiac arrest resuscitation, geospatial analysis of where cardiac arrests occur is potentially useful. Thus, identifying 'hotspots' for OHCA can conceivable be used in several different ways:
- it can be used to determine where to place [AEDs](https://en.wikipedia.org/wiki/Automated_external_defibrillator)
- it can be used to determine staging locations for ambulances

https://jsfiddle.net/user/nickmmark/fiddles/

```html
<script async src="//jsfiddle.net/nickmmark/j6k2vhg0/embed/"></script>
```

### Details
* I pull data from the [Seattle Fire 911 API](https://data.seattle.gov/Public-Safety/Seattle-Real-Time-Fire-911-Calls/kzjm-xkqj) provided by the [Seattle Open Data Program](http://www.seattle.gov/tech/initiatives/open-data).
* I use the incident type '''Medical Response, 7 per rule''' to identify high acuity medical emergencies, of which OHCA is one particular subtype.
* I export the GPS coordinates of these events and load them into the [Google Maps Javascript API](https://developers.google.com/maps/documentation) where I display the events as a heatmap.
![incident type example](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/incident_type.png)

* The Google maps API makes it easy to zoom and translate on the map. You can adjust the color scheme, and the heatmap gradient, and 

### Examples
![example image](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot.png)


### Data Source(s)
- [Seattle Fire 911 Calls](https://data.seattle.gov/Public-Safety/Seattle-Real-Time-Fire-911-Calls/kzjm-xkqj) multi-year database updated every 5 minutes; available as an API or as a .csv for download
- [Seattle Fire Realtime 911 calls](http://www2.seattle.gov/fire/realtime911/getRecsForDatePub.asp?action=Today&incDate=&rad1=des) a near realtime feed of 911 dispatch information
- [Demographic Statistics by ZIP Code]() available as a .csv, .json, .rdf, or .xml file.

### Version/To-Do
v1.0 by Nick Mark, 7/16/2017
* [ ] need to load census data for population density to normalize
* [ ] would also be helpful to explore by ZIP and aggregate

### References
* [Public911 Seattle](http://www.public911.com/app/#/seattle)
* Similar work in other areas:
  * ***Houston, Texas***: Raun LH et al, [Geospatial analysis for targeting out-of-hospital cardiac arrest intervention](https://www.ncbi.nlm.nih.gov/pubmed/23867019), Am J Prev Med. 2013 Aug;45(2)
  * ***Mesa, Arizona***: Somers S, [Spatial Cluster Analysis of Out-of-Hospital Cardiac arrest in Mesa Arizona](https://nfa.usfa.fema.gov/pdf/efop/efo46779.pdf)
  * ***Singapore***: Tan M et al, [Geospatial Analysis of Out-of-hospital Cardiac Arrest (OHCA) in Singapore](https://www.researchgate.net/publication/292761719_GEOSPATIAL_ANALYSIS_OF_OUT-OF-HOSPITAL_CARDIAC_ARREST_OHCA_IN_SINGAPORE), Irish Journal of Medical Science 2015 184:560-561
  * ***Taiwan***: Chen CC et al, [Spatial Variation and Resuscitation Process Affecting Survival after Out-of-Hospital Cardiac Arrests (OHCA)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0144882), PLoS One 2015
  * ***Netherlands***: Balistreri G, [Spatial Analysis of Out-of-Hospital Cardiac Arrest Incidences in the Netherlands](https://essay.utwente.nl/74536/), 2017
