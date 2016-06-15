# tile-maker

## TopoJSON Tile Maker

The TopoJSON Tile Maker uses Node.js web services and an example browser front end to convert a collection of one or more ESRI shape files into a 
complete administrative geography. Multiple layers are supported so that an integrated set of census administrative geography layers can 
be created. To use USA as an example states, counties, census tracts, census block groups into are combined 
into layers of TopoJSON tiles optimised for a series to map zoom levels. Typically zoom levels 6-11 are supported. The web services 
contain a very simple tile server for testing; the user then downloads the tiles for deploying a OSM 'standard' style compliant 
map server. 

Tile Maker is integrates a number of commonly used Node.js modules to create a simple to use, yet powerful application for 
creating administrative geographies tile sets typically used in large scale Epidemiological studies. It has been deliberately built
to handle very large shape files; the principle test suites being US census geography 2014 to census block group and England and 
Wales 2011 census geography. A Node.js web architecture was chosen deliberately to avoid breaking web browsers with very large shape files.

Tile Maker was developed as part of the Rapid Inquiry Facility or RIF; a freely available software application that supports 
two types of environmental health activities: disease mapping studies and risk analysis studies. The RIF was designed to help 
epidemiologists and public health researchers to rapidly investigate potential environmental hazards, especially those 
related to industrial sites. The tool uses health, environmental, socio-economic, population and geographic data to calculate 
risks in relation to sources of exposure and to generate maps. The RIF, and Tile Maker, has been developed by the Small Area 
Health Statistics Unit at Imperial College, London.

SAHSU has developed a rapid inquiry facility (RIF) http://www.sahsu.org/content/rapid-inquiry-facility to permit fast and versatile exploration of the small area data held in 
national databases in response to urgent queries about environmental hazards. The RIF has been widely disseminated in Europe 
(with EU funding) and the USA (as part of the CDC Environmental Public Health Tracking (EPHT) Program). 
 
This repository is currently a stub; the actual code will be transferred from the RIF in Q3/Q4 2016.

### The RIF

![ Data Viewer prototpye for Disease mapping ](Images/RIF_disease_mapping_screenshot.png?raw=true "Data Viewer prototpye for Disease mapping")

### Graphical User Interface

Note: a much better JQuery-UI prototype that has the RIF look and feel will appear shortly.

![ Tiler Maker early prototype prototpye displaying US census data to County level, zoomed into the the South Esstern United States ](Images/Tile-Maker_screenshot.png?raw=true "Tile Maker prototpye")

#### Work flow

1. Select a set of shape files. Zip files are supported;
2. GUI unpacks zip files, processing DBF and ESRI extended attribute files (.shp.ea.iso.xml) to extract meta data;
3. The name of the administrative geography is defined (e.g. United States 2014 Census);
4. For each shape file select the field containing the administrative code (e.g. MT) and the administrative name (e.g. Montana);
5. The quantization, zoom level range and the inter zoom level simplification factor are defaulted. These can be changed;
5. The files are uploaded to the tile maker Node.js service for processing;
6. The GUI provides status on Node.js service processing until the initial simplification is complete;
7. The untiled topoJSON is fetched and displayed using Leaflet: http://leafletjs.com/; below zoom level 6 only shape files with less than 200 areas are displayed; shape files with more 
   than 10,000 area are suppressed. This is prevent browser crashes before tile production;
8. If all the require meta data is present then the Node.js service continues to process to produce the tiles for the required zoom levels;
9. When complete the GUI displays the tiles

The processing setup is savable to an XML file; this can be used in a "batch" mode to the Node.js web service and provide the interface for 
the RIF's own Java based data cleaning and loading tool or other tools.

The GUI and the web service will accept geoJSON files; if the XML file is provided the processing will also produce tiles. This allows very large shape files to be pre-shrunk using 
Mike Bostock's topojson program and there to reduce the server memory requirements.

### Node.js web service processing

To be added.

### Limits

1. Memory; the Node.js back end requires approximately 7x the uncompressed size of the shape files
2. Browsers; Internet Explorer 10+, the latest Chrome and Firefox will be tested. 
     a) Leaflet on IE has severe problerms with >20M of JSON data; it does work - it is just abysmally slow!
     b) Firefox 47.0 has a bad bug (1274010) which causes large xmlhttprequest POSTs to fail randomly . It apperars to be fix in beta. 
        Previous Firefox releases could handle multi GB file loads
     c) Chrome will barf with very large files, but is fine to 300-500 MB.
3. There is a hard limit of 255M per shape file record. This is the Node.js string limit.   
