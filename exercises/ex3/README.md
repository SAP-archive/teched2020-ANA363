# Exercise 3


## Estimated Time: 30 minutes

## Objective

This is the part of the workshop where the power of the smart wrangler starts to become apparent.  In this exercise, you will take the public dataset that you started working on in Exercise 2 and enhance it.  You may have noticed that there are no readily apparent column for dates.  There is a year column and a month column, but nothing that can easily be called a date.  You’ll fix this (and never worry about oddball date formats again).  You’ll also slip a calculation right into the dataset.  


## What You Learn

*Datatype conversions on columns

*The basics of using the wrangler expression language (WEL)



### Step 1


Go back to the file browser and re-open the dataset.

![][image-1]
### Step 2


Open the custom expression editor.

This is where you edit wrangler expression language (WEL) scripts/expressions.  Note!  You are always editing and executing single expressions; which can be nested inside each other.  For this reason, the terms script and expression can be used interchangeably in the context of the wrangler expression language.

![][image-2]
### Step 3


Before we go any further, let’s take a moment to familiarize ourselves with the UI of the custom expression editor.  

*Let’s start with the editing pane.  This is where you’ll be writing and editing the code for your WEL expressions.

*There are buttons for execute and cancel; just as with transforms.

*The Format button is your friend and helper!  It pretty prints expressions to make them easier to understand and edit.

*Lastly, there is the help button, which toggles the help dictionary on in the Details pane.



![][image-3]
### Step 4


Toggle the Help button on and have a look.

Inside the Custom Expression Help panel, you can access documentation for all available expression functions.

![][image-4]
### Step 5


We will begin adding a date dimensions to the dataset.  We’ll  start by combining Close the Custom Expression Help panel, by clicking the Help Button again.

*Begin creating your first expression by typing in:

*“[CalMonth] =”

*The square brackets indicate a column.  Since there is no column named CalMonth, you are creating a new one.

*Note that as soon as you put the = sign in, code completion will automatically pop up.


![][image-5]
### Step 6


CalMonth will eventually become a date dimension. It will begin life as a string dimension.  

The first step is to create a concatenated column, combining the Year and Month columns.
Type “conc” into the editor and select concatenate when it surfaces in the popup.

![][image-6]
### Step 7


Take a moment to have a look at the input parameters of the concatenate function.  It takes two column names and a delimiter as input.

![][image-7]
### Step 8


Add the Year and Month columns as parameters, with a period as the delimiter.  

![][image-8]
### Step 9


The execute the new expression, click the execute button (the one with the checkmark)

![][image-9]
### Step 10


You should see a toast, indicating that the expression has executed successfully.  You will also see a new column, called CalMonth.

![][image-10]
### Step 11


Look in the Details pane of the CalMonth dimension.  Note that its default Data Type is string and you can see the histogram of the value distribution.

![][image-11]
### Step 12


Switch the data type to Date.

![][image-12]
### Step 13


Navigate to the ParkName dimension and have a look at it in the Details pane.  

Note that park names all have a suffix; an abbreviation of the Park Service unit type.  E.g. NS refers to National Seashore and NP means National Park.

![][image-13]
### Step 14


This suffix in the name is redundant, as we have a ParkType dimension; which is more useful than a bit of free text in the name field.  Let’s investigate removing the suffix.

*Start by creating a new ParkNameSuffix dimension.

*It is created using the substr() function (substring).  Substr takes three parameters; a string, the start position and end position.  

*The ParkName column can give us our string.

*For the start position, we’ll need a formula.  These strings can vary in length.  Let’s use the length() function to get the length of the string.  Then step 2 indices back.

*Lastly, let the length be 3.


![][image-14]
### Step 15


Our expression has nested functions and can be a bit hard to read.  

Use the Format button to pretty print it and make it more readable. 

![][image-15]
### Step 16


Our strings are three characters long. 

![][image-16]
### Step 17


Let’s add a new substring, taking the existing ParkNameSuffix and taking the slice from position 1 to 3.  

Note!  This won’t actually change anything in ParkNameSuffix, because we are taking three characters from the first position (1 is the start position, not 0).  Essentially, the returned slice is the same as what we started with…

![][image-17]
### Step 18


… BUT if we toggle on the transform log for the dimension, we see both expressions.  The second expression occurs after the first one executes.  

If we were to go back and increate the length of the slice in the initial expression, the second would be taking the first three characters of the new version.

Feel free to try this out yourself.

![][image-18]
### Step 19


As for ParkNameSuffix, lets toggle off the Transform Log and look at its histogram in the Details pane.

Go ahead and click on the “and 1 other value” text; which will expand the histogram.

![][image-19]
### Step 20


Note that we do not uniformly have two-character suffixes.  We could investigate this further, but we want to turn our attention to another problem.  Feel free to play around on your own if you wish.

![][image-20]
### Step 21


We are going to create a calculated column.  We could do this via formula in the story, but we’ll do it here in wrangling.
*The new column is called [BackcountryPercentage].  It will represent the percentage of total visitors per month, per unit, that had a backcountry permit.  We’ll use this as a proxy for the percentage of visitors who slept in the wilderness, because most parks require a backcountry permit, in order to control traffic in wild parts of the park.

*This will be the number of Backcountry Campers, divided by the sum of all of the visitor measures.

*This quotient is then multiplied by 100.


![][image-21]
### Step 22


Have a look at your new BackcountryPercentage measure.  Note that the histogram leans FAR to the left.  Also note in the table, that many of the values are in fact zero.

![][image-22]
### Step 23


In prerelease versions of the smart wrangler, if the denominator was zero, there would be a divide by zero error and the formula would fail.  It now falls back on null if this happens and no longer throws an error, but defensive programming is always a good practice.

You can couch the expression in an IF statement.  If the sum of all of the visitation types is zero, the BackcountryPercentage is null.  Otherwise it is calculated.
This happens in the dataset, because some parks had 0 visitation in some months, due to closure.

![][image-23]
### Step 24


You can have another look in the Details.  Not much has changed, as the smart wrangler was already catching the divide by zero error for you.

![][image-24]
### Step 25


Let’s change the AggregationType to None.  We don’t want this measure to be aggregated.


![][image-25]
### Step 26


We will have a large number of zeros.  Many park units, such as Acadia, don’t have any backcountry.

![][image-26]
### Step 27


Let’s add a background filter to filter them out.

![][image-27]
### Step 28


In the transform menu, select Filter.

![][image-28]
### Step 29


Select not matching 0.  This cleans up the BackcoutryPercentage column quite a bit.

![][image-29]
### Step 30


Save it.  Note that you’ll be warned about the effects of changes on existing stories and apps where it is used.

![][image-30]
### Step 31


Open the story that you were working on before.

![][image-31]
### Step 32


Go into Edit mode.

![][image-32]
### Step 33


Add a new canvas page.

![][image-33]
### Step 34


Add a chart.

![][image-34]
### Step 35


Change the chart type to Time Series.

![][image-35]
### Step 36


Set the measure to be BackcountryPercentage

The Time dimension should be CalMonth.

![][image-36]
### Step 37


Resize the chart to taste (remembering to leave room at the top for input controls).  You should a graph for all years, in all units with backcountry.

![][image-37]
### Step 38


Let’s add an input control.

![][image-38]
### Step 39


Choose ParkName as the filter dimension.

![][image-39]
### Step 40


Again, click the All Members checkbox, to enable app parks. 

Enable either single or multiple selection, as you wish.

![][image-40]
### Step 41


Save your story.

![][image-41]
### Step 42


Switch back to view mode.

![][image-42]
### Step 43


Play around with your filter selections.

![][image-43]
### Step 44


You now have a story page, where you can explore the backcountry visitation statistics of US national parks.  

![][image-44]


## Summary

You now have a fairly robust dataset for examining backcountry overnight statistics in US National Parks, Monuments Recreation, Lakeshores and Seashores.  Have fun seeing what you can tease out of it.  There are some interesting patterns.  
For example, the backcountry camping percentage at Assateague Island National Seashore peaked at 0.15% in May 2019.  This makes sense.  There are a handful of backcountry sites at Assateague and it is the only place on the East coast of the US where you can camp on a wilderness beach.  However, between Memorial and Labor days, total visitation skyrockets, as Assateague has large numbers of normal beachgoers. 
Yellowstone meanwhile has a peak BackcountryPercentage of just over 1% and that peak falls at the height of summer.  This seems small, but Yellowstone had over 800,000 visitors and over 13,000 backcountry campers in August of 2019.  














































[image-1]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.01.png
[image-2]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.02.png
[image-3]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.03.png
[image-4]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.04.png
[image-5]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.05.png
[image-6]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.06.png
[image-7]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.07.png
[image-8]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.08.png
[image-9]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.09.png
[image-10]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.10.png
[image-11]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.11.png
[image-12]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.12.png
[image-13]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.13.png
[image-14]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.14.png
[image-15]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.15.png
[image-16]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.16.png
[image-17]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.17.png
[image-18]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.18.png
[image-19]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.19.png
[image-20]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.20.png
[image-21]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.21.png
[image-22]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.22.png
[image-23]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.23.png
[image-24]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.24.png
[image-25]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.25.png
[image-26]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.26.png
[image-27]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.27.png
[image-28]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.28.png
[image-29]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.29.png
[image-30]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.30.png
[image-31]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.31.png
[image-32]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.32.png
[image-33]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.33.png
[image-34]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.34.png
[image-35]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.35.png
[image-36]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.36.png
[image-37]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.37.png
[image-38]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.38.png
[image-39]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.39.png
[image-40]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.40.png
[image-41]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.41.png
[image-42]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.42.png
[image-43]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.43.png
[image-44]:    https://github.com/SAP-samples/teched2020-ANA363/raw/main/exercises/ex3/images/Ex3.44.png

