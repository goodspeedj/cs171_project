cs171_project III
=================

Jim Goodspeed - jgoodsp@fas.harvard.edu
Devin Shackle - devin.shackle@fas.harvard.edu


# ==============================================================================================
#
# Running locally
#
# ==============================================================================================

Please note that to run this visualization locally you must run the Python SimpleHTTPServer:
python -m SimpleHTTPServer 8888 &


# ==============================================================================================
#
# Required files and libraries.
#
# ==============================================================================================
All libraries are included in the projct files, but are listed here for reference:

d3.v3.min.js: http://d3js.org/d3.v3.min.zip
d3.csv.js: https://github.com/mbostock/d3/wiki/CSV
queue.v1.min.js: https://github.com/mbostock/queue
topojson.js: https://github.com/mbostock/topojson
intro.js: http://usablica.github.io/intro.js/


# ==============================================================================================
#
# References and citations
#
# ==============================================================================================
All references and citations are included at the end of our process book and also on our project 
site in the citations.html file.  Additionally code citations are included in a comment section 
in the index.html file.


# ==============================================================================================
#
# The model for the parallel coordinate graph was based on the Iris parallel coordinate graph.
#
# Michael Bostock, "Edgar Anderson's Iris data set parallel coordinates," accessed April 1, 2013, 
#   http://mbostock.github.io/d3/talk/20111116/iris-parallel.html.
#
# The code for the map is based on the D3 World Maps: Tooltips, Zooming, and Queue and the click-to-zoom
# via transformation example by Mike Bostock
#
# "D3 World Maps: Tooltips, Zooming, and Queue," Techslides, accessed April 24, 2013, 
#   http://techslides.com/d3-world-maps-tooltips-zooming-and-queue/
#
# Michael Bostock, "click-to-zoom via transformation," Gallery - mbostock / d3, accessed April 23, 2013,
#   http://bl.ocks.org/mbostock/2206590
#
# The annotation code/introduction code is provided by intro.js written by Afshin Mehrabani
#
# Afshin Mehrabani, "Intro.js: Better introductions for websites and features with a step-by-step guide 
#   for your projects," usabli.ca, accessed April 28, 2013, http://usablica.github.io/intro.js/
#
# ==============================================================================================

function click(d)
	Allows the user to click on a country in the map.  On click will zoom the map and highlight
	the country in red.  Bostock, "click-to-zoom via transformation."


function reset()
	This function will return the map to it's original state (zoomed out, no highlighting).
	"D3 World Maps: Tooltips, Zooming, and Queue."


function ready() 
	This function prepares the map and does the actual drawing as well as adding the tooltip 
	functionality.  "D3 World Maps: Tooltips, Zooming, and Queue."


function getSelected()
	This function gets the selected item from the filter pull down 


function addDesc()
	This function will add the conflict description to the head of the parallel coordinate 
	graph.


function detailTable()
	This function displays the data table below the parallel coordinate graph.  The function
	builds the table rows and cells as new data is passed to it.  Old data is exited and 
	removed from the stage.


function highlight()
	This function will highlight a corresponding line in the parallel coordinate graph when 
	the same data record is moused over on the data table below.


function unhighlight()
	This function will return the line called out in the highlight function to its original
	color, width and opacity.


function clearFill()
	This function will clear the fill on the countries by removing any CSS classes from the 
	country objects.


function selectConflict()
	This is the main function and is responsible for the rendering of the parallel coordinate
	graph.  The basic workflow is:

		1.  If there is already a parallel coordinate graph destroy it and recreate it based on
		    the filter pulldown.

		2.  Determine which countries are involved in the conflict based on the selection from 
		    the pull down.  Zoom the map to those countries and fill the countries with matching
		    colors to the parallel coordinate lines.

		2.  Open the data csv file and filter it based on the conflict from the getSelected 
		    function

		3.  Get a list of the countries for this conflict to be used in the legend

		4.  Check to see if the data table exists - if so destroy it and recreate it based on 
		    the pull down selection

		5.  For each economic indicator set up a y axis and brush

		6.  Create the legend

		7.  Create the foreground paths for each country

		8.  Setup a svg group for each y axis for calling the drag functions allowing the axis
		    lines to be re-ordered

		9.  Add the axis and brush


function dragstart()
	Function to register the index of the axis being moved.  This function was not modified from 
	the original in the Michael Bostock example. Bostock, "Edgar Anderson's Iris data set parallel 
	coordinates."


function drag()
	Function to drag the axis to a different order.  This function was not modified from 
	the original in the Michael Bostock example.  Bostock, "Edgar Anderson's Iris data set parallel 
	coordinates."


function dragend()
	Function to finish and re-order the axis.  This function was not modified from the original 
	in the Michael Bostock example.  Bostock, "Edgar Anderson's Iris data set parallel coordinates."


function redrawAxis()
	Function to redraw the axis lines for new data.  This is not called in the current version,
	but was left in as it may be implemented as part of project 3.


function redrawPath()
	Function to redraw the path lines for new data.  This is not called in the current version,
	but was left in as it may be implemented as part of project 3.


function brush()
	Function to create the brush for each axis line.  The items that are not in the brush are 
	given a light gray color.  This function also maps back the coordinates of the brushed lines
	to data and adds this filterd data to the filterData array.  That filterData array is then
	used to populate the data table with the records that are in the brush.  This is partially based
	on the Michael Bostock parallel coordinate example.  Bostock, "Edgar Anderson's Iris data set parallel 
	coordinates."




# ==========================================================================================
#
# Data Files
#
# ==========================================================================================

Our project uses several data files.  The main data file containing the conflict data is called 
conflictPreCompute.csv.  It is located in the data directory of our project and is loaded using 
d3.csv.  Much of the data clean-up for this file was done with the proj2Transposer.py script.

There are two data file for the map visualization.  The world-110.json file contains the SVG 
paths for countries in the map and can be obtained from the following location:

https://github.com/mbostock/topojson/blob/master/examples/world-110m.json

The second map data file is for the country names called world-country-names.tsv.  This file is 
located in the data directory and can also be obtained from the following location:

https://github.com/mapmeld/flightmap/blob/gh-pages/world-country-names.tsv




