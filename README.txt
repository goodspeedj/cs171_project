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
# The map implementation requires TopoJSON which in turn requires Node.js.  
#
# Node.js can be downloaded and installed from: http://nodejs.org/download/
#
# To install TopoJSON open the Node.js command prompt and type: npm install -g topojson
#
# ==============================================================================================



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
# ==============================================================================================

function getSelected()
	This function gets the selected item from the filter pull down 


function getDesc()
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


function selectConflict()
	This is the main function and is responsible for the rendering of the parallel coordinate
	graph.  The basic workflow is:

		1.  If there is already a parallel coordinate graph destroy it and recreate it based on
		    the filter pulldown.

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
	the original in the Michael Bostock example.


function drag()
	Function to drag the axis to a different order.  This function was not modified from 
	the original in the Michael Bostock example.


function dragend()
	Function to finish and re-order the axis.  This function was not modified from the original 
	in the Michael Bostock example.


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
	used to populate the data table with the records that are in the brush.





# ==========================================================================================
#
# Libraries
#
# ==========================================================================================

Our project makes use of the main d3.v3.min.js file and the d3.csv.js library.  Both libraries
are hosted locally within our project in the js folder.



# ==========================================================================================
#
# Data Files
#
# ==========================================================================================

Our project uses one data file called conflictPreCompute.csv.  It is located in the data
directory of our project and is loaded using d3.csv.  Much of the data clean-up for this file
was done with the proj2Transposer.py script.