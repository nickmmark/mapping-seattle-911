# mapping-seattle-911
Mapping and geospatial analysis of open source Seattle Fire Realtime 911 data, with a particular focus on out of hospital cardiac arrest (OHCA). 
![mapping cardiac arrest calls in Seattle, WA](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot%202.png)

# Background
https://jsfiddle.net/user/nickmmark/fiddles/
<script async src="//jsfiddle.net/nickmmark/j6k2vhg0/embed/"></script>

# Details
We use the incident type '''Medical Response, 7 per rule''' to identify high acuity medical emergencies, of which OHCA is one particular subtype.
![incident type example](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/incident_type.png)

# Code
Uses the [Google Maps Javascript API](https://developers.google.com/maps/documentation) particularly the heatmap function.

# Examples
![example image](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot.png)


# Data Source(s)
- [Seattle Fire 911 Calls](https://data.seattle.gov/Public-Safety/Seattle-Real-Time-Fire-911-Calls/kzjm-xkqj) multi-year database updated every 5 minutes; available as an API or as a .csv for download
- [Seattle Fire Realtime 911 calls](http://www2.seattle.gov/fire/realtime911/getRecsForDatePub.asp?action=Today&incDate=&rad1=des) a near realtime feed of 911 dispatch information

# Version/To-Do
v1.0 by Nick Mark, 7/16/2017

# References
- [Public911 Seattle](http://www.public911.com/app/#/seattle)
