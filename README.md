# mapping-seattle-911
The purpose of this data exploration is an answer a simple question: Where do cardiac arrests occur in Seattle, WA?
This type of analysis can be useful for staging ambulances, positioning AEDs, and targeting community enagagement.
![animated time series map of seattle 911 dispatched for Medical emergencies](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/animated_911_calls.gif)

The purpose of this project is to faciliate mapping and geospatial analysis of open source Seattle Fire Realtime 911 data, with a particular focus on out of hospital cardiac arrest (OHCA). 

[Out of Hospital Cardiac Arrest](https://www.cdc.gov/mmwr/preview/mmwrhtml/ss6008a1.htm) is a life threatening emergency. Prompt initation of high quality CPR, early defibrilation, and advanced life support and transport to a suitable medical center can dramatically improve outcomes. Because of the time sensitive nature of cardiac arrest resuscitation, geospatial analysis of where cardiac arrests occur is potentially useful. Thus, identifying 'hotspots' for OHCA can conceivable be used in several different ways:
- it can be used to determine where to place [AEDs](https://en.wikipedia.org/wiki/Automated_external_defibrillator)
- it can be used to determine staging locations for ambulances

### initial data exploration
* You can see the [realtime feed of 911 dispatches](https://www2.cityofseattle.net/fire/realTime911/getRecsForDatePub.asp?action=Today&incDate=&rad1=des) which is a fairly unique level of transparency provided by the City of Seattle. In another repository, I show you we can use this near-realtime feed to predict ED visits.
* I pull data from the [Seattle Fire 911 API](https://data.seattle.gov/Public-Safety/Seattle-Real-Time-Fire-911-Calls/kzjm-xkqj) provided by the [Seattle Open Data Program](http://www.seattle.gov/tech/initiatives/open-data).
* I use the incident type ```"Medical Response, 7 per rule"``` to identify high acuity medical emergencies, of which OHCA is one particular subtype. This is not quite perfect (it also includes medical emergencies like 'person not breathing' but it's a good first pass approximation.

![incident type example](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/incident_type.png)


* Next I loaded the flat file (.csv) into powerBI and used [ArcGIS esri](https://powerbi.microsoft.com/en-us/power-bi-esri-arcgis/) to explore the data. Unfortunately, there are so many events it can be hard to identify patterns, even if we create an automated time slicer:

![animated time series map of seattle 911 dispatched for Medical emergencies](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/animated_911_calls.gif)

* We can use alternative visualization tools, such as [MapBox](https://docs.mapbox.com/help/tutorials/power-bi/) to build simple heatmaps. This starts to show us some more subtle patterns in the data.

![](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/heatmap_seattle_2.png)
![](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/heatmap_seatle_2_closeup.png)

* But what if we want more nuanced control of the visualization? For this it helps to use the [GoogleMaps API](https://developers.google.com/maps/documentation) directly.
 * I export the GPS coordinates of these events and load them into the [Google Maps Javascript API](https://developers.google.com/maps/documentation) where I display the events as a heatmap.
 * The Google maps API makes it easy to zoom and translate on the map. You can adjust the color scheme, and the heatmap gradient, and other parameters
```javascript
var map, heatmap;\
// load map centered on Seattle, default is roadmap\
function initMap() \{\
  map = new google.maps.Map(document.getElementById('map'), \{\
    zoom: 11,\
    center: \{lat: 47.63, lng: -122.35\},\
    mapTypeId: 'roadmap'\
  \});\
\
// ideally would like to have multiple different heatmaps, for now just one\
  heatmap = new google.maps.visualization.HeatmapLayer(\{\
    data: getPoints(),\
    map: map\
  \});\
\}\
\
// default = red/green, alternative = red/blue\
function toggleHeatmap() \{\
  heatmap.setMap(heatmap.getMap() ? null : map);\ 
\}\
function changeRadius() \{\
  heatmap.set('radius', heatmap.get('radius') ? null : 19);\
\}\
\
function changeOpacity() \{\
  heatmap.set('opacity', heatmap.get('opacity') ? null : 0.2);\
\}\
```
 ![example image](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot.png)

* This is a much more efficient way to specify some of the parameters for visualization. We can also make it more user friendly and interactive.
* The final live map of OHCA in Seattle can be found here:
 * https://jsfiddle.net/user/nickmmark/fiddles/
 
```html
<script async src="//jsfiddle.net/nickmmark/j6k2vhg0/embed/"></script>
```


* Additional examples:
_[live and interactive heatmap](https://jsfiddle.net/user/nickmmark/fiddles/) showing the locations of cardiac arrests in Seattle, WA_

![mapping cardiac arrest calls in Seattle, WA](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot%202.png)


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
* Raun LH et al, [Geospatial analysis for targeting out-of-hospital cardiac arrest intervention](https://www.ncbi.nlm.nih.gov/pubmed/23867019), Am J Prev Med. 2013 
* Similar work in other geographic regions:
  * ***Houston, Texas***: Raun LH et al, [Geospatial analysis for targeting out-of-hospital cardiac arrest intervention](https://www.ncbi.nlm.nih.gov/pubmed/23867019), Am J Prev Med. 2013 Aug;45(2)
  * ***Mesa, Arizona***: Somers S, [Spatial Cluster Analysis of Out-of-Hospital Cardiac arrest in Mesa Arizona](https://nfa.usfa.fema.gov/pdf/efop/efo46779.pdf)
  * ***Singapore***: Tan M et al, [Geospatial Analysis of Out-of-hospital Cardiac Arrest (OHCA) in Singapore](https://www.researchgate.net/publication/292761719_GEOSPATIAL_ANALYSIS_OF_OUT-OF-HOSPITAL_CARDIAC_ARREST_OHCA_IN_SINGAPORE), Irish Journal of Medical Science 2015 184:560-561
  * ***Taiwan***: Chen CC et al, [Spatial Variation and Resuscitation Process Affecting Survival after Out-of-Hospital Cardiac Arrests (OHCA)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0144882), PLoS One 2015
  * ***Netherlands***: Balistreri G, [Spatial Analysis of Out-of-Hospital Cardiac Arrest Incidences in the Netherlands](https://essay.utwente.nl/74536/), 2017
