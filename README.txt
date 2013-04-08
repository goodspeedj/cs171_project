cs171_project II
================

Jim Goodspeed
Devin Shackle


# ==========================================================================================
#
# Running locally
#
# ==========================================================================================

Please note that to run this visualization locally you must run the Python SimpleHTTPServer:
python -m SimpleHTTPServer 8888 &



# ==========================================================================================
#
# Code overview
#
# ==========================================================================================

function getSelected()
	This function gets the selected item from the filter pull down 


function detailTable()
	This function displays the data table below the parallel coordinate graph.  The function
	builds the table rows and cells as new data is passed to it.  Old data is exited and 
	removed from the stage.


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
	Function to register the index of the axis being moved


function drag()
	Function to drag the axis to a different order


function dragend()
	Function to finish and re-order the axis


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
directory of our project and is loaded using d3.csv.



