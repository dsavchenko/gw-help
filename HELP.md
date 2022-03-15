This interface provides the analysis of publicly available gravitational wave data of LIGO and VIRGO detectors available from https://gw-openscience.org. The data analysis workflows implemented as online services follow the methods of the tutorial analysis notebooks of https://www.gw-openscience.org/tutorials/ . The services provides a possibility to execute the tutorial notebooks for any time interval 
(with or without known gravitational wave events)  
<!-- This is not true. Strain data exist only around events (4096 sec or so) -->
and any detector. 

It also uses skymaps from
- https://dcc.ligo.org/LIGO-P1800381/public for GWTC1 events
- "PublicationSamples" skymaps from https://dcc.ligo.org/LIGO-P2000223/public/ for GWTC2 events
- Mixed-model skymaps from https://zenodo.org/record/5546663 for GWTC3
  
## Source query panel

The general MMODA interface for all instruments has a top-level selection panel that allows to specify sky position of an astronomical source and/or time interval for the analysis. For the gravitational wave events, it is the time interval that is most important. It provides unique identification of known events. The top common parameter panel of the MMODA interface allows to directly enter the time interval in the dedicated parameter windows.  
      ![](im/frontend_top_pane_gw.png)
      
Alternatively, the time intervals for the known gravitational wave events can be found using the name resolver. The user can enter the name of the event (e.g. GW170817) and click "resolve" button. 

## Skymap and catalog
To plot the probability contours of the GW events in the specified time range:
   1. Specify the time range in general parameter form.
   
      ![](im/common_long.png)
   
   2. Select contour levels to plot.
   
      ![](im/skymap_param.png)

The result is as follows:

![](im/skymap.png)

Use Download button to get tar archive with raw MOC skymaps and event catalog ascii file. 

The Catalog button shows the list of events with basic parameters
![Catalog view](im/catalog_view.png)

### Cone search
In more advanced mode one can restrict the returned events to those, whose probabilty contours intersect with circular region on sky:
   1. In addition to the time range specify coordinates of sky direction
   2. Select cone-search mode
   3. Set probability level and radius

![Cone search parameters](im/conesearch_param.png)

The resulting skymap contains only subset of events:

![Cone search result example](im/skymap_cone.png)

## Time series data
This mode is used to obtain strain time-series for some GW event.
1. Specify GW event name and press Resolve button – the time interval will be filled accordingly
   ![](im/resolve.png)
2. Select GW detector and specify bandpass limits
   ![](im/strain_param.png)
   

The result is:

![Strain timeseries](im/strain.png)

Upper plot shows raw data and the bottom one shows bandpassed and whitened data. The corresponding .h5 files can be downloaded.

## Spectrogram
It is also possible to obtain the Constant-Q transform of the data. The steps are similar to the time-series case. 

The result looks like the following:
![](im/sgram.png)
