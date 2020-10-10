# Exercise 2


## Estimated Time: 10 minutes

## Objective

Get your hiking boots on!  In this exercise, you will create a public dataset, with visitation data at a large portion of the United States National Park system.  This kind of public dataset is re-usable in many artifacts; including not just stories, apps and boardrooms, but smart predict scenarios as well.  The dataset that you create in Exercises 2 and 3 is used in the demo portion of the session ANA200 to demonstrate scenario analytics.


## What You Learn

*The basics of creating a public dataset.

*How to create a Geo dimension based on area name.



### Step 1

When you first log into SAP Analytics Cloud, you should be presented with the home screen.

![][image-1]
### Step 2

On the Home menu, select Create >> Story

![][image-2]
### Step 3

On the Home menu, select Create >> Story

![][image-3]
### Step 4

In the new story, select “Add a Canvas Page”.

![][image-4]
### Step 5

Let’s click the button to add some data!

![][image-5]
### Step 6

When asked to choose where you would like to get your data, choose to upload a file.Important!  Choosing either to upload data or to connect to a source will create an new embedded dataset, where the dataset exists inside the story and is not accessible from anywhere else.   

![][image-6]
### Step 7

Download AWOIS_Wrecks.csv if you have not already done so.  Click Select Source File to choose the file.

![][image-7]
### Step 8

Select the location where you have saved AWOIS_Wrecks.csv.  Click Import.Give your dataset a name when prompted.

![][image-8]
### Step 9

The dataset will load.  Progress bars will indicate the progress in loading and preparing the dataset import.

![][image-9]
### Step 10

When dataset import and preparation is done, you will see the smart wrangler screen.

![][image-10]
### Step 11

Before we venture any further, let’s take a tour of the various parts of the smart wrangler UI. If your dataset is larger than 2000 rows, you will see a popup, informing you how big your dataset is and that the first 2000 rows have been sampled in the wrangler.  The wrangler samples large datasets for the sake of interactive responsiveness.The Dataset Overview in the Details pane replaces the card view from the classic wrangler.  It lists the columns and groups measures and dimensions.  Your data occupies the spreadsheet.Because you are working with an embedded dataset, you can freely toggle back and forth between the wrangler and story builder.In the Actions group of the toolbar, you have the menu options specific to wrangling.

![][image-11]
### Step 12

Save your story and name it for the first time, so that you can save it as you work with hotkey commands.

![][image-12]
### Step 13

Have a look at your dataset in the Dataset Overview panel.Note that the columns with text columns have been flagged as dimensions and the ones with numerical values have been flagged as probable measures.

![][image-13]
### Step 14

LATDEC is latitude and LONDEC is Longitude.  You’ll want to use these as dimensions, so make them dimensions by dragging them down to the dimension area.Alternatively, you can select the “more” menu (the ellipsis, …) on individual columns in the Dataset Overview.Repeat for every other measure, except for DEPTH.

![][image-14]
### Step 15

VESSELTERMS is usually the name of the ship, or a short description.  We will be adding it to a geo dimension, so that ship names show up in the map.  Because doing so will convert it to a property, it will no longer be available as a dimension and we’ll also want to add the ship name to a table, so let’s duplicate it before adding it to the hierarchy.Select the VESSELTERMS column header.  Select the context menu and mouse over the ellipsis ( … )Select Duplicate Column

![][image-15]
### Step 16

Select the new VESSELTERM_1 columns and click on the text to rename it

![][image-16]
### Step 17

Name it VesselName

![][image-17]
### Step 18

Select the Depth column

![][image-18]
### Step 19

Have a look at this measure in the Details pane.  Note that its default aggregation is SUM, the data type is decimal.  The statistical type is continuous.  This is only used by Smart Predict.  Also note the data distribution histogram.This dataset – and specifically this measure - has a lot of incomplete data.  Wrecks with no depth information are not very interesting to us, so we’ll get rid of those entries.What we do NOT want to do is actually delete this data.  We want to leave it in the fact table for use later.  We just don’t want it surfaced to stories with now and want to be able to reverse this decision later.  To so this, we’ll add a background filter.

![][image-19]
### Step 20

Navigate to the grid, select the context menu in the header row of the DEPTH column.Choose Create a Transform

![][image-20]
### Step 21

Choose Filter.

![][image-21]
### Step 22

We want to keep everything with a value; so, leave the operator to “not matching”.Note that the default text is not actually a value.  It is merely a display placeholder, indicating that you can enter a value here.  If you enter nothing, then it will be an empty string.  That is exactly what we want here.

![][image-22]
### Step 23

To execute the transform, click the checkmark button, at the right end of the transform bar.

![][image-23]
### Step 24

With any kind of transform, you see a short-lived success or error message at the bottom of the screen.  Trivia: UI designers call this sort of ephemeral popup a “toast”.

![][image-24]
### Step 25

Now we’ll create the geo dimension, that we alluded to when copying the VESSELTERMS dimension.To do this, Click the dropdown arrow on the geo-location icon, in the Actions group.Select Coordinates (because we have latitude and longitude dimensions on hand)

![][image-25]
### Step 26

The smart wrangler will try to guess which dimensions might be latitude and longitude.  In this case, you might need to assist it with one of the dimensions.Also make sure your dimension is called Location (the default name)

![][image-26]
### Step 27

You can do this by clicking the dropdown and choosing either LATDEC or LONDEC, as appropriate. 

![][image-27]
### Step 28

In the dimension properties, choose VESSELTERMS.  (we are choosing vesselterms, instead of VesselName, because the former’s name is less intuitive for end users.  This won’t matter in a geo dimension property)

![][image-28]
### Step 29

You can see the columns that participate in the geo dimension.  

![][image-29]
### Step 30

You will now want to work on the story a bit.  Navigate to the upper left and toggle from Data to Story.  Note!  Because this is an embedded dataset, you can go back to the wrangler at any time, by toggling to Data. Within the Data tab, the two buttons in the Mode group act as toggles between Explorer mode and the Wrangler. If you close, re-open the story in edit mode and then toggle to Data, it will default to Explorer.  You can get back to the wrangler by selecting the grid icon in the Mode group. 

![][image-30]
### Step 31

Add a geo chart to the canvas and size it to take up the entire left side of the story.

![][image-31]
### Step 32

Add a layer.  Choose Bubble Layer as your later type.

![][image-32]
### Step 33

Choose Location as your location dimension and choose the DEPTH measure as your Bubble Color.

![][image-33]
### Step 34

Let’s add a table, next to the geo map.

![][image-34]
### Step 35

Position it to take up the left half of the story.

![][image-35]
### Step 36

Select VesselName, YEARSUNK and FEATURE_TYPE as row members.

![][image-36]
### Step 37

Select the geo chart and in its context menu, select Linked Analysis.  The dimension will default to Location.

![][image-37]
### Step 38

Choose “All Widgets in Story” or “All Widgets on this Page”.  Either will work.

![][image-38]
### Step 39

We have a lot of data points… a LOT of wrecks.  Let’s see if we can trim the list to something more meaningful.

![][image-39]
### Step 40

Toggle back to the wrangler and select the FEATURE_TYPE dimension.

![][image-40]
### Step 41

Have a look at it in the Details pane.  Note that there are a lot of wrecks with no entry for FEATURE_TYPE.  Like DEPTH, FEATURE_TYPE has a lot of incomplete entries.

![][image-41]
### Step 42

Again, let’s filter out the empty values.

![][image-42]
### Step 43

The histogram looks a bit better now, but there is a Not Charted entry.  This indicates that the nature of the wreck is unknown (as opposed to simply not being maintained in the database).

![][image-43]
### Step 44

Filter out Not Charted, but creating a filter with the “not matching” operator and putting “Not Charted” in the selection string.

![][image-44]
### Step 45

At this point, you have made two consecutive transforms on FEATURE_TYPE.  Toggle from Details to Transform Log.  Here you can see (and delete) and of the individual transforms.

![][image-45]
### Step 46

In the Transform Log panel, you can toggle back and forth between the transforms made on the entire dataset and those made on just a particular column, by selecting the icons in the blue bar at the top of the pane.In the Dataset Transform Log, we can see (and delete) all transforms done on the dataset, regardless of column.

![][image-46]
### Step 47

Toggle back to the story.  In the geo map, choose the Polygon Filter, to filter to a specific geographic area.

![][image-47]
### Step 48

In our case, we’ll choose the mid-Atlantic Seaboard.

![][image-48]
### Step 49

If you refine your selection to the southern coast of New Jersey, you can see wrecks at various depths and of various ages.  

![][image-49]
### Step 50

Open …

![][image-1]
### Step 51

Click …

![][image-2]
### Step 52

Click …

![][image-3]
### Step 53

Select …

![][image-4]
### Step 54

Choose Edit  …

![][image-5]
### Step 55

…

![][image-6]
### Step 56

…

![][image-7]
### Step 57



![][image-8]
### Step 58



![][image-9]
### Step 59



![][image-10]
### Step 60



![][image-11]
### Step 61



![][image-12]
### Step 62



![][image-13]
### Step 63



![][image-14]
### Step 64



![][image-15]
### Step 65



![][image-16]
### Step 66



![][image-17]
### Step 67



![][image-18]
### Step 68



![][image-19]
### Step 69



![][image-20]
### Step 70



![][image-21]
### Step 71



![][image-22]
### Step 72



![][image-23]
### Step 73



![][image-24]
### Step 74



![][image-25]
### Step 75



![][image-26]
### Step 76



![][image-27]
### Step 77



![][image-28]
### Step 78



![][image-29]
### Step 79



![][image-30]
### Step 80



![][image-31]
### Step 81

Open …

![][image-1]
### Step 82

Click …

![][image-2]
### Step 83

Click …

![][image-3]
### Step 84

Select …

![][image-4]
### Step 85

Choose Edit  …

![][image-5]
### Step 86

…

![][image-6]
### Step 87

…

![][image-7]
### Step 88



![][image-8]


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

