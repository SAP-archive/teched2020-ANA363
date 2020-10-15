# Exercise 2


## Estimated Time: 10 minutes

## Objective

Get your hiking boots on!  In this exercise, you will create a public dataset, with visitation data at a large portion of the United States National Park system.  This kind of public dataset is re-usable in many artifacts; including not just stories, apps and boardrooms, but smart predict scenarios as well.  The dataset that you create in Exercises 2 and 3 is used in the demo portion of the session ANA200 to demonstrate scenario analytics.


## What You Learn

*The basics of creating a public dataset.

*How to create a Geo dimension based on area name.

*



### Step 1


On the Home menu, select Create >> Dataset

![][image-1]
### Step 2


When asked to choose where you would like to get your data, choose to upload a file.Unlike in Exercise 1, we will be creating a public dataset.

![][image-2]
### Step 3


Download NationalParkService_VisitationStats.csvif you have not done so already.Click Select Source File to choose the file.

![][image-3]
### Step 4


Click Import.

![][image-4]
### Step 5


Give your dataset a name when prompted.

![][image-5]
### Step 6


The dataset will load.  Progress bars will indicate the progress in loading…

![][image-6]
### Step 7


… and preparation the dataset import.

![][image-7]
### Step 8


When dataset import and preparation is done, you will see the smart wrangler screen.

![][image-8]
### Step 9


As we did in the embedded wrangling case, let’s start with a tour of the smart wrangler.  As in the embedded case. If your dataset is larger than 2000 rows, you will see a popup, informing you how big your dataset is and that the first 2000 rows have been sampled in the wrangler. The wrangler samples large datasets for the sake of interactive responsiveness.Again, the Dataset Overview in the Details pane replaces the card view from the classic wrangler. It lists the columns and groups measures and dimensions. Your data occupies the spreadsheet. In the Actions group of the toolbar, you have the menu options specific to wrangling.Because you are working with a public dataset, the Data/Story toggle is missing.

![][image-9]
### Step 10


Year and Month have been flagged as probable measures, because they are numeric.  You’ll want them to be dimensions, so drag them down into the dimensions area.

![][image-10]
### Step 11


Have a look at either of these dimensions in the Details pane.  Note the distribution of the data and the fact that both are Integer.

![][image-11]
### Step 12


Switch them to string.  Note how the data distribution histogram changes.

![][image-12]
### Step 13


We are going to create our first hierarchy.  Only level hierarchies can be created with the smart wrangler.  Start by selecting the Region dimension

![][image-13]
### Step 14


From the Actions menu, click the Hierarchy button, to begin creating a new level hierarchy.

![][image-14]
### Step 15


Region should already be in the hierarchy.  Add it if it is not already there and then add ParkType and ParkName.  Use the Select Dimension dropdown to add to levels to the hierarchy.

![][image-15]
### Step 16


We’ll add a new Geo dimension.  This time, we’ll use Area Name to create it, instead of coordinates.Start by going to the Geo dimension icon and selecting Area Name from the dropdown.

![][image-16]
### Step 17


You can choose to either assign a column as the country, or specify a single country.

![][image-17]
### Step 18


Since all of our data is from the United States, choose Specify from a list of countries and choose United States from the dropdown.To add states to the Geo dimension, select the dropdown on Region and then assign the State column. Our data does not go down to the county level, so leave this blank.

![][image-18]
### Step 19


Right away, you’ll notice that there is a validation issue.  Click on “1 issues” to look into it.

![][image-19]
### Step 20


The smart wrangler does not like the state “VI”, which occurs 80 times in the initial sample of 2000 rows.  Click the Supported Locations link to download a csv file with all supported country, regions and sub regions. If you look in the csv, you’ll see that VI is not listed.  That’s because the supported regions for the US includes states only and not territories.  VI refers to Virgin Islands; specifically, the territory of the US Virgin Islands.  

![][image-20]
### Step 21


There might be data beyond the samples with territories in the state name.  Click Validate Full Dataset to check this.  There are National Parks in three territories; Virgin Islands, American Samoa and Puerto Rico.

![][image-21]
### Step 22


You’ll want to remove VI, AS (American Samoa) and PR (Puerto Rico)

![][image-22]
### Step 23


Start by adding a filter transform, with the not matching operator (to keep values that don’t match)

![][image-23]
### Step 24


Write “AS” as the value and click the checkmark to activate the filter.Repeat for VI and PR

![][image-24]
### Step 25


After cleaning up the geo locations, you might notice a toast, indicating that there are issues elsewhere.

![][image-25]
### Step 26


There are issues with the Recreation Visits and Recreation Hours measures.

![][image-26]
### Step 27


We won’t be using the RecreationHours and NonRecreationHours measures, so you can go ahead and delete them.  This spares us from having to troubleshoot RecreationHours.Start by selecting both.  

![][image-27]
### Step 28


From the more menu (the one with the ellipsis), select Delete Column.

![][image-28]
### Step 29


This leaves us with only Recreation Visits as a problematic measure.

![][image-29]
### Step 30


Have a look at RecreationVisits’ Details pane.  You’ll note two related issues.  The datatype is decimal and the values that the validator is complaining about all contain multiple periods.  The csv that you uploaded is in European format; with semicolons in place of the commas as dividers.  This in turn, is because the comma and not the period is used as the decimal separator in Europe.  The default Conversion Format presumes a North Amercan number format (comma for thousands separator and comma for decimal)You have two possible options for fixing this; both available from the Details panel:  You can change the Conversion Format to use the European format, or you can switch the Date Type to Decimal.  Don’t fix this problem yet.  Let’s just leave it for now.

![][image-30]
### Step 31


Save your dataset and start creating a new story, to use it.

![][image-31]
### Step 32


Select Add a Canvas Page

![][image-32]
### Step 33


Click on Add Data

![][image-33]
### Step 34


Select Data acquired from an existing dataset or model.

![][image-34]
### Step 35


Select the dataset that you juts created.

![][image-35]
### Step 36


When you add the dataset, SAP Analytics Cloud will automatically switch to the Data tab.  

![][image-36]
### Step 37


Switch back to the Story tab.

![][image-37]
### Step 38


Add a new map layer and make it fill the left side of the canvas.

![][image-38]
### Step 39


Go to the Builder panel and select Add a Layer.

![][image-39]
### Step 40


Choose Choropleth/Drill Layer.

![][image-40]
### Step 41


Make sure that the layer type is Choropleth/Drill and the Style is Choropleth.

![][image-41]
### Step 42


In the Location Dimension dropdown, choose the Geo Hierarchy that you created earlier.

![][image-42]
### Step 43


For Choropleth Color, choose RecreationVisits.

![][image-43]
### Step 44


This is what your geomap setup should look like.

![][image-44]
### Step 45


Make sure that there is space above the map for an input control.

![][image-45]
### Step 46


Add the Input Control.

![][image-46]
### Step 47


In the popup that opens when you add a new input control, choose Dimensions

![][image-47]
### Step 48


You’ll want to filter by year in the story, so choose Year.

![][image-48]
### Step 49


Click the All Members box to select all years.  This will make all years available in the filter control.

![][image-49]
### Step 50


Save your story. 

![][image-50]
### Step 51




![][image-51]
### Step 52


Navigate to view mode, by clicking on the View button.

![][image-52]
### Step 53


You should see a geomap, generated on North America.Everything is red, because you have not drilled down and you are aggregating over all years.

![][image-53]
### Step 54


Filter to 2019.

![][image-54]
### Step 55


The map will now be filtered to 2019 figures.

![][image-55]
### Step 56


Let’s drill down one level, to state.  Mouse over the red area, until the hover menu comes up.  Select Drill Down on Geo Hierarchy

![][image-56]
### Step 57


You should see visitation differences.  California had the most national park visitors in 2019.  

![][image-57]
### Step 58


We are now going to fix the problem identified in step 30.  The easy thing to do is to simply switch the conversion type, but we’ll show you another way; by stripping the original thousands separator out of the data.Start by going back to the dataset.And move RecreationVisits from the measures to the dimensions group.

![][image-58]
### Step 59


Take a look at the data distribution and the Data Type.

![][image-59]
### Step 60


Switch the Data Type to String.

![][image-60]
### Step 61


Create a Transform in RecreationVisits.

![][image-61]
### Step 62


Choose Replace.

![][image-62]
### Step 63


Change cell to content.

![][image-63]
### Step 64


…matching “” with should be changed.  Put a comma in place of the empty string.

![][image-64]
### Step 65


Create another transform and do the same with periods.

![][image-65]
### Step 66


Now move RecreationVisits back to the measures group.

![][image-66]
### Step 67


Note that the issues are gone.  Your data is a bit cleaner and you can go back to touring your story.

![][image-67]


## Summary

You created the beginnings of a dataset for examining visitation statistics in US National Parks.





































































[image-1]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.01.png
[image-2]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.02.png
[image-3]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.03.png
[image-4]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.04.png
[image-5]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.05.png
[image-6]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.06.png
[image-7]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.07.png
[image-8]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.08.png
[image-9]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.09.png
[image-10]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.10.png
[image-11]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.11.png
[image-12]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.12.png
[image-13]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.13.png
[image-14]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.14.png
[image-15]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.15.png
[image-16]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.16.png
[image-17]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.17.png
[image-18]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.18.png
[image-19]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.19.png
[image-20]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.20.png
[image-21]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.21.png
[image-22]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.22.png
[image-23]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.23.png
[image-24]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.24.png
[image-25]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.25.png
[image-26]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.26.png
[image-27]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.27.png
[image-28]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.28.png
[image-29]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.29.png
[image-30]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.30.png
[image-31]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.31.png
[image-32]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.32.png
[image-33]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.33.png
[image-34]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.34.png
[image-35]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.35.png
[image-36]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.36.png
[image-37]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.37.png
[image-38]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.38.png
[image-39]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.39.png
[image-40]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.40.png
[image-41]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.41.png
[image-42]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.42.png
[image-43]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.43.png
[image-44]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.44.png
[image-45]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.45.png
[image-46]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.46.png
[image-47]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.47.png
[image-48]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.48.png
[image-49]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.49.png
[image-50]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.50.png
[image-51]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.51.png
[image-52]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.52.png
[image-53]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.53.png
[image-54]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.54.png
[image-55]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.55.png
[image-56]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.56.png
[image-57]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.57.png
[image-58]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.58.png
[image-59]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.59.png
[image-60]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.60.png
[image-61]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.61.png
[image-62]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.62.png
[image-63]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.63.png
[image-64]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.64.png
[image-65]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.65.png
[image-66]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.66.png
[image-67]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex2/images/Ex2.67.png

