# ORNL DAAC MODIS Land Product Subsets - Perl Tool

This is a perl client for the Oak Ridge National Laboratories (ORNL) MODIS Land Product Subsets project. It allows for the extraction of time series of several pixels around geographic locations for select MODIS products. The service makes use of the Simple Object Access Protocol (SOAP) web service provided by ORNL (see requirements below).

Code contributions have been made by Stef Lhermitte (stef.lhermitte@knmi.nl) to include a geographic header in function 4 and 5 (see below) and to allow a date gap > 10 observations in function 5.

## Installation

Download and unzip the project in a local directory.

## Use

This perl script has five functions:

1) query the available products with argument 'list'

	./DAAC-LPS.pl list

2) query the available bands of a product (e.g. MCD12Q1)

	./DAAC-LPS.pl MCD12Q1

3) query the available dates of a product at a location (latitude, longitude)

	./DAAC-LPS.pl MCD12Q1 40 -110

4) extract subsets of a product and band for a list of locations and this for all available dates.

	./DAAC-LPS.pl MCD12Q1 Land_Cover_Type_1 1 1 T input.csv

first parameter is the product name (see 1.)
second parameter is the band name (see 2.)
third parameter are the # km north south of the location
fourth parameter are the # km east west of the location
fifth parameter is a header flag 
(T: print data with georeferencing header)
(F: print no georeferencing header)
sixth parameter is a csv file containing locations
 
The file format of the csv file is location name, latitude, longitude with no header and with !!! UNIX UTF-8 line endings !!!

5) extract subsets of a product and band for a certain location and interval of dates

	./DAAC-LPS.pl Site MCD12Q1 Land_Cover_Type_1 40 -110 1 1 A2001001 A2002001 

first parameter is the site name
second parameter is the product name (see 1.)
third parameter is the band name (see 2.)
fourth and fifth parameter are the latitude longitude
sixth parameter are the # km north south of the location
seventh parameter are the # km east west of the location
eight parameter is a header flag 
(T: print data with georeferencing header)
(F: print no georeferencing header)
nineth and tenth parameter are the start and enddate of the query
(see 4.)

## Requirements

[SOAP lite for perl](http://www.soaplite.com/) should be installed

