
Description
===========

This is GIS/geospatial data that some of which is normal feature testing
other portions are edge cases for testing bugs in code. 

Goals
=====
* Test data shall use data that is freely shareable and reusable
   (public domain or otherwise.)
* Test data should be used for continuous unit testing to ensure new
code doesn't break already fixed code.
* Try to be a test resource to not have to reinvent the wheel.
* If test cases are not withing specification, they shall atleast be 
normative.

Test Cases
==========
* unicode/
    Formats: GeoJSON & Shapefile, ESRI Personal Geodatabase, 
        ESRI File Geodatabase version 10.3
        
    Global cities dataset are points with UTF-8/Unicode encoded 
    characters. "LocalName" field has the UTF-8/Unicode
    characters names.

* date/
    Formats: ESRI Shapefile
    
    US Historic capitals.  This is intended to be used to test the date
    handling capabilities.  This is not intended to be an exhuastive list.
    Dataset heavily inspired by Wikipedia:  
    https://en.wikipedia.org/wiki/List_of_capitals_in_the_United_States#Former_national_capitals


Original Data Sources
=====================
* dataset that are original work
   * edge/unicode/

Software Testing Tools
======================
GeoJSON
Use geojsonhint (requires nodejs & npm)
https://github.com/mapbox/geojsonhint

Usage:
$ geojsonhint < filename.geojson

OR GeoJSON Validation
https://github.com/craveprogramminginc/GeoJSON-Validation


GDAL's ogrinfo will use ogrinfo and search for the keyword 
"successful".



$ shopt -s globstar
$ ls -1 **/*.geojson

for file in **/*.geojson
do
  echo "Testing GeoJSON file \"$file\" is up to spec.".
  geojsonhint < $file
  # check exit status 
  if [ $? -gt 0 ] 
    then exit $?
  fi
done


Test character encoding is utf-8?

Notes
=====
Assume WGS84 unless a CRS is specified.

GeoJSON should conform to the standards presented by the GeoJSON
workgroup.  Which may or may not get approved and could be subject to 
change. I-JSON, which requires UTF-8 encoding is one of these changes.
https://datatracker.ietf.org/wg/geojson/charter/

License
=======
This work is licensed under the Creative Commons Attribution 4.0
International License. To view a copy of this license, visit
http://creativecommons.org/licenses/by/4.0/.
