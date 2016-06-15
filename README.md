# tile-maker

## TopoJSON Tile Maker

Node web services and example front end to convert a collection of ESRI shapefiles into a complete administrative geography; 
e.g USA, states, counties, census tracts, census block groups into TopoJSON tiles optimised for a series to map zoomlevels. 
Typically zoomlevels 6-11 are supported. The web services contain a very simple tile server for testing; the user then 
downloads the tiles for deploying a OSM 'standard' style compliant map server.

Tile Maker is integrates a number of commonly used Node.js modules to create a simple to use, yet powerfull application for 
creating adminsitrative geographies tilesets typically used in large scale Epidemiological studies. It has been deliberately built
to handle very large shapefiles; the principle test suites being US census geopgraphy 2014 to census block group and England and 
Wales 2011 census geography.

Tile Maker was developed as part of the Rapid Inquiry Facility or RIF; a freely available software application that supports 
two types of environmental health activities: disease mapping studies and risk analysis studies. The RIF was designed to help 
epidemiologists and public health researchers to rapidly investigate potential environmental hazards, especially those 
related to industrial sites. The tool uses health, environmental, socio-economic, population and geographic data to calculate 
risks in relation to sources of exposure and to generate maps. The RIF, and Tile Maker, has been developed by the Small Area 
Health Statistics Unit and Imperial College, London.

SAHSU has developed a rapid inquiry facility (RIF) to permit fast and versatile exploration of the small area data held in 
national databases in response to urgent queries about environmental hazards. The RIF has been widely disseminated in Europe 
(with EU funding) and the USA (as part of the CDC Environmental Public Health Tracking (EPHT) Program). 
 
This repository is currently a stub; the actual code will be transferred from the RIF in Q3/Q4 2016.

[Add reference to RIF; standardise RIF text]

### Graphical User Interface

[Add mock up]

[Add work flow]

### Node web service processing

