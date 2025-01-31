# `bcdata.sh` and `background_layers.sh`
These are the scripts for creating projects ready for upload to mergin server.

To download and clip layers for an area of interest defined by a list of watershed groups:

  1. edit `bcdata.txt` as needed, listing all layers to be downloaded via bcdata/WFS
  2. Delete current .geojsons with `rm *.geojson`
  
  3. download these layers to .geojson, for given study area (optionally with timer):
  
  
  		$ time ./bcdata.sh "'BULK', 'KLUM'"
  
  3. define the `DIRPROJECT` variable at the top of the `background_layers.sh` script which will be the name of the directory where the spatial layers and styles will be burned to and will be turned into a mergin project on the cloud for collaboration.  
  
  4. download data from file sources and load all sources (including bcdata layers) to `background_layers.gpkg` with clip from watershed group polygons when necessary (`bcdata` layers):
  		
  		$ time ./background_layers.sh "'BULK', 'KLUM'"
  		
  		Or at the same time
  		time ./bcdata.sh "'CRKD', 'CARP', 'PARS'" && time ./background_layers.sh "'CRKD', 'CARP','PARS'"

If downloads in #2 fail, re-run `bcdata.sh` until downloads are complete (Only files that do not exist are re-downloaded). In event of a failed download, be sure to remove the .geojson file created by the failed download.







