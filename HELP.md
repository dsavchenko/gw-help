This interface provides the analysis of publicly available gravitational wave data of LIGO and VIRGO detectors available from https://gw-openscience.org. The data analysis workflows implemented as online services follow the methods of the tutorial analysis notebooks of https://www.gw-openscience.org/tutorials/ . The services provides a possibility to execute the tutorial notebooks for an arbitrary time interval 
(with or without known gravitational wave events) and detector. 
<!-- This is not true. Strain data exist only around events (4096 sec or so) -->

  
## Source query panel

The general MMODA interface for all instruments has a top-level selection panel that allows to specify sky position of an astronomical source and/or time interval for the analysis. For the gravitational wave events, it is the time interval that is most important. It provides unique identification of known events. The top common parameter panel of the MMODA interface allows to directly enter the time interval in the dedicated parameter windows.  
      ![](im/frontend_top_pane_gw.png)
      
Alternatively, the time intervals for the known gravitational wave events can be found using the name resolver. The user can enter the name of the event (e.g. GW170817) and click "resolve" button. If the event is known to the resolver, the time interval of the event will appear in the time selection parameter windows. By default, the sky direction will not be resolved (because of the limited sky localisation capability of the gravitationalwave detectors). The GW170817 event for which the direction is known is an exception. 

## Skymap and catalog

The interface allows to find known gravitational wave events within a specified time interval and visualise their sky localisations. This can be done by selecting the "skymap and catalog" in the side parameter panel. It is also possible to perform a cone search for events around a selected sky direction by selecting the "cone search" and specifying the angular width of the search cone. Otherwise, an all-sky search can be preformed:   
      ![](im/skymap_param.png)
The analysis uses the skymaps from
- https://dcc.ligo.org/LIGO-P1800381/public for the first Gravitational Wave Transient Catalog (GWTC1) events as well as "PublicationSamples" skymaps from https://dcc.ligo.org/LIGO-P2000223/public/ for GWTC2 events and mixed-model skymaps from https://zenodo.org/record/5546663 for GWTC3. The original skymap data are data cubes corresponding to the probability density function (PDF) for event localisation in RA-DEC-distance parameter space. The online data analysis service presents the integral of the PDF in distance in the form of a contour plot:
![](im/skymap.png)

The probability levels for the contour plot can be specified in the side parameter panel. The result display window has a number of buttons that allow to manipulate the skymap data products. The "Download" button provides a possibility to download the original skymap PDF for all the displayed events. The MMODA interface can be accessed from Python notebooks, using a an API. The API code for the skymap can be retreived by pressing the "API code" button. The result will be a piece of a Python code like this:



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
