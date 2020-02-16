# mapping-seattle-911
Mapping and geospatial analysis of open source Seattle Fire Realtime 911 data, with a particular focus on out of hospital cardiac arrest (OHCA). 

![mapping cardiac arrest calls in Seattle, WA](https://github.com/nickmmark/mapping-seattle-911/blob/master/figures/screenshot%202.png)

_[live and interactive heatmap](https://jsfiddle.net/user/nickmmark/fiddles/) showing the locations of cardiac arrests in Seattle, WA_

# Background
[Out of Hospital Cardiac Arrest](https://www.cdc.gov/mmwr/preview/mmwrhtml/ss6008a1.htm) is a life threatening emergency. Prompt initation of high quality CPR, early defibrilation, and advanced life support and transport to a suitable medical center can dramatically improve outcomes. Because of the time sensitive nature of cardiac arrest resuscitation, geospatial analysis of where cardiac arrests occur is potentially useful. Thus, identifying 'hotspots' for OHCA can conceivable be used in several different ways:
- it can be used to determine where to place [AEDs](https://en.wikipedia.org/wiki/Automated_external_defibrillator)
- it can be used to determine staging locations for ambulances

https://jsfiddle.net/user/nickmmark/fiddles/

```html
<script async src="//jsfiddle.net/nickmmark/j6k2vhg0/embed/"></script>
```

# Details

I use the incident type '''Medical Response, 7 per rule''' to identify high acuity medical emergencies, of which OHCA is one particular subtype.
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
