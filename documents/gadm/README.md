#GADM file formats

The "geopackage" format is the a very good general spatial data file format (for vector data). It is based on the SpatiaLite format, and can be read by software using GDAL/OGR, including R (with the 'sf' package), QGIS and ArcGIS. 

A "shapefile" consist of at least four actual files (.shp, .shx, .dbf, .prj). This is an obsolete, but still commonly used format that can be directly used in a lot of software such as ArcGIS and DIVA-GIS, and many other programs. 

A "R sp" (.rds) file has a "SpatialPolygonsDataFrame" object as defined in the sp package. It can be used in R. To use it, first load the sp package using library(sp) and then use readRDS("filename.rds") (replacing "filename.rds" with the actual filename). See http://www.rspatial.org/ to learn about using spatial data in R.

A "R sf" (.rds) file has a "sf" object as defined in the sf package. It can be used in R. To use it, first load the sp package using library(sp) and then use readRDS("filename.rds") (replacing "filename.rds" with the actual filename). See http://www.rspatial.org/ to learn about using spatial data in R.

A "Google Earth .kmz" file can be opened in Google Earth. 