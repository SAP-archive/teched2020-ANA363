# Exercise 1


## Estimated Time: 30 minutes

## Objective

Shipwrecks Ahoy!  In this exercise, you will create a new story, with a linked map and table, containing NOAA shipwreck data.  Your story will have an embedded dataset. An embedded dataset is created when data is awaited from inside the story builder.


## What You Learn

*Working with embedded datasets in stories.  This exercise demonstrates the fluid switching between working on your storytelling and data preparation.

*You will learn how to navigate around the various UI elements of the SAP Analytics Clous smart wrangler.

*The basic workflow skills needed for effectively wielding the smart wrangler

*How to create a Geo dimension in the smart wrangler



### Step 1


When you first log into SAP Analytics Cloud, you should be presented with the home screen.

![][image-1]
### Step 2


On the Home menu, select Create >> Story

![][image-2]
### Step 3


In the new story, select “Add a Canvas Page”.

![][image-3]
### Step 4


Let’s click the button to add some data!

![][image-4]
### Step 5


When asked to choose where you would like to get your data, choose to upload a file.Important!  Choosing either to upload data or to connect to a source will create an new embedded dataset, where the dataset exists inside the story and is not accessible from anywhere else.   

![][image-5]
### Step 6


Download AWOIS_Wrecks.csv if you have not already done so.  Click Select Source File to choose the file.

![][image-6]
### Step 7


Select the location where you have saved AWOIS_Wrecks.csv.  Click Import.Give your dataset a name when prompted.

![][image-7]
### Step 8


The dataset will load.  Progress bars will indicate the progress in loading and preparing the dataset import.

![][image-8]
### Step 9


When dataset import and preparation is done, you will see the smart wrangler screen.

![][image-9]
### Step 10


Before we venture any further, let’s take a tour of the various parts of the smart wrangler UI. If your dataset is larger than 2000 rows, you will see a popup, informing you how big your dataset is and that the first 2000 rows have been sampled in the wrangler.  The wrangler samples large datasets for the sake of interactive responsiveness.The Dataset Overview in the Details pane replaces the card view from the classic wrangler.  It lists the columns and groups measures and dimensions.  Your data occupies the spreadsheet.Because you are working with an embedded dataset, you can freely toggle back and forth between the wrangler and story builder.In the Actions group of the toolbar, you have the menu options specific to wrangling.

![][image-10]
### Step 11


Save your story and name it for the first time, so that you can save it as you work with hotkey commands.

![][image-11]
### Step 12


Have a look at your dataset in the Dataset Overview panel.Note that the columns with text columns have been flagged as dimensions and the ones with numerical values have been flagged as probable measures.

![][image-12]
### Step 13


LATDEC is latitude and LONDEC is Longitude.  You’ll want to use these as dimensions, so make them dimensions by dragging them down to the dimension area.Alternatively, you can select the “more” menu (the ellipsis, …) on individual columns in the Dataset Overview.Repeat for every other measure, except for DEPTH.

![][image-13]
### Step 14


VESSELTERMS is usually the name of the ship, or a short description.  We will be adding it to a geo dimension, so that ship names show up in the map.  Because doing so will convert it to a property, it will no longer be available as a dimension and we’ll also want to add the ship name to a table, so let’s duplicate it before adding it to the hierarchy.Select the VESSELTERMS column header.  Select the context menu and mouse over the ellipsis ( … )Select Duplicate Column

![][image-14]
### Step 15


Select the new VESSELTERM_1 columns and click on the text to rename it

![][image-15]
### Step 16


Name it VesselName

![][image-16]
### Step 17


Select the Depth column

![][image-17]
### Step 18


Have a look at this measure in the Details pane.  Note that its default aggregation is SUM, the data type is decimal.  The statistical type is continuous.  This is only used by Smart Predict.  Also note the data distribution histogram.This dataset – and specifically this measure - has a lot of incomplete data.  Wrecks with no depth information are not very interesting to us, so we’ll get rid of those entries.What we do NOT want to do is actually delete this data.  We want to leave it in the fact table for use later.  We just don’t want it surfaced to stories with now and want to be able to reverse this decision later.  To so this, we’ll add a background filter.

![][image-18]
### Step 19


Navigate to the grid, select the context menu in the header row of the DEPTH column.Choose Create a Transform

![][image-19]
### Step 20


Choose Filter.

![][image-20]
### Step 21


We want to keep everything with a value; so, leave the operator to “not matching”.Note that the default text is not actually a value.  It is merely a display placeholder, indicating that you can enter a value here.  If you enter nothing, then it will be an empty string.  That is exactly what we want here.

![][image-21]
### Step 22


To execute the transform, click the checkmark button, at the right end of the transform bar.

![][image-22]
### Step 23


With any kind of transform, you see a short-lived success or error message at the bottom of the screen.  Trivia: UI designers call this sort of ephemeral popup a “toast”.

![][image-23]
### Step 24


Now we’ll create the geo dimension, that we alluded to when copying the VESSELTERMS dimension.To do this, Click the dropdown arrow on the geo-location icon, in the Actions group.Select Coordinates (because we have latitude and longitude dimensions on hand)

![][image-24]
### Step 25


The smart wrangler will try to guess which dimensions might be latitude and longitude.  In this case, you might need to assist it with one of the dimensions.Also make sure your dimension is called Location (the default name)

![][image-25]
### Step 26


You can do this by clicking the dropdown and choosing either LATDEC or LONDEC, as appropriate. 

![][image-26]
### Step 27


In the dimension properties, choose VESSELTERMS.  (we are choosing vesselterms, instead of VesselName, because the former’s name is less intuitive for end users.  This won’t matter in a geo dimension property)

![][image-27]
### Step 28


You can see the columns that participate in the geo dimension.  

![][image-28]
### Step 29


You will now want to work on the story a bit.  Navigate to the upper left and toggle from Data to Story.  Note!  Because this is an embedded dataset, you can go back to the wrangler at any time, by toggling to Data. Within the Data tab, the two buttons in the Mode group act as toggles between Explorer mode and the Wrangler. If you close, re-open the story in edit mode and then toggle to Data, it will default to Explorer.  You can get back to the wrangler by selecting the grid icon in the Mode group. 

![][image-29]
### Step 30


Add a geo chart to the canvas and size it to take up the entire left side of the story.

![][image-30]
### Step 31


Add a layer.  Choose Bubble Layer as your later type.

![][image-31]
### Step 32


Choose Location as your location dimension and choose the DEPTH measure as your Bubble Color.

![][image-32]
### Step 33


Let’s add a table, next to the geo map.

![][image-33]
### Step 34


Position it to take up the left half of the story.

![][image-34]
### Step 35


Select VesselName, YEARSUNK and FEATURE_TYPE as row members.

![][image-35]
### Step 36


Select the geo chart and in its context menu, select Linked Analysis.  The dimension will default to Location.

![][image-36]
### Step 37


Choose “All Widgets in Story” or “All Widgets on this Page”.  Either will work.

![][image-37]
### Step 38


We have a lot of data points… a LOT of wrecks.  Let’s see if we can trim the list to something more meaningful.

![][image-38]
### Step 39


Toggle back to the wrangler and select the FEATURE_TYPE dimension.

![][image-39]
### Step 40


Have a look at it in the Details pane.  Note that there are a lot of wrecks with no entry for FEATURE_TYPE.  Like DEPTH, FEATURE_TYPE has a lot of incomplete entries.

![][image-40]
### Step 41


Again, let’s filter out the empty values.

![][image-41]
### Step 42


The histogram looks a bit better now, but there is a Not Charted entry.  This indicates that the nature of the wreck is unknown (as opposed to simply not being maintained in the database).

![][image-42]
### Step 43


Filter out Not Charted, but creating a filter with the “not matching” operator and putting “Not Charted” in the selection string.

![][image-43]
### Step 44


At this point, you have made two consecutive transforms on FEATURE_TYPE.  Toggle from Details to Transform Log.  Here you can see (and delete) and of the individual transforms.

![][image-44]
### Step 45


In the Transform Log panel, you can toggle back and forth between the transforms made on the entire dataset and those made on just a particular column, by selecting the icons in the blue bar at the top of the pane.In the Dataset Transform Log, we can see (and delete) all transforms done on the dataset, regardless of column.

![][image-45]
### Step 46


Toggle back to the story.  In the geo map, choose the Polygon Filter, to filter to a specific geographic area.

![][image-46]
### Step 47


In our case, we’ll choose the mid-Atlantic Seaboard.

![][image-47]
### Step 48


If you refine your selection to the southern coast of New Jersey, you can see wrecks at various depths and of various ages.  

![][image-48]


## Summary

You created a fun story for looking at shipwrecks around the coasts of the United States.  In the map, you and maneuver around and in the table, you can see details about the various wrecks.  Congratulations, you have learned the first basics of using the smart wrangler to get answers quickly.


















































[image-1]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.01.png
[image-2]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.02.png
[image-3]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.03.png
[image-4]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.04.png
[image-5]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.05.png
[image-6]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.06.png
[image-7]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.07.png
[image-8]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.08.png
[image-9]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.09.png
[image-10]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.10.png
[image-11]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.11.png
[image-12]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.12.png
[image-13]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.13.png
[image-14]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.14.png
[image-15]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.15.png
[image-16]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.16.png
[image-17]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.17.png
[image-18]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.18.png
[image-19]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.19.png
[image-20]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.20.png
[image-21]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.21.png
[image-22]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.22.png
[image-23]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.23.png
[image-24]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.24.png
[image-25]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.25.png
[image-26]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.26.png
[image-27]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.27.png
[image-28]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.28.png
[image-29]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.29.png
[image-30]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.30.png
[image-31]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.31.png
[image-32]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.32.png
[image-33]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.33.png
[image-34]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.34.png
[image-35]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.35.png
[image-36]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.36.png
[image-37]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.37.png
[image-38]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.38.png
[image-39]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.39.png
[image-40]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.40.png
[image-41]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.41.png
[image-42]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.42.png
[image-43]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.43.png
[image-44]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.44.png
[image-45]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.45.png
[image-46]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.46.png
[image-47]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.47.png
[image-48]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.48.png

