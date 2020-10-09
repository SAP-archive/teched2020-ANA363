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

Before we venture any further, let’s take a tour of the various parts of the smart wrangler UI. 1- If your dataset is larger than 2000 rows, you will see a popup, informing you how big your dataset is and that the first 2000 rows have been sampled in the wrangler.  The wrangler samples large datasets for the sake of interactive responsiveness.2 – The Dataset Overview in the Details pane replaces the card view from the classic wrangler.  It lists the columns and groups measures and dimensions.  3 – Your data occupies the spreadsheet.4- Because you are working with an embedded dataset, you can freely toggle back and forth between the wrangler and story builder.5 – In the Actions group of the toolbar, you have the menu options specific to wrangling.

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



![][image-15]
### Step 16



![][image-16]
### Step 17



![][image-17]
### Step 18



![][image-18]
### Step 19



![][image-19]
### Step 20



![][image-20]
### Step 21



![][image-21]
### Step 22



![][image-22]
### Step 23



![][image-23]
### Step 24



![][image-24]
### Step 25



![][image-25]
### Step 26



![][image-26]
### Step 27



![][image-27]
### Step 28



![][image-28]
### Step 29



![][image-29]
### Step 30



![][image-30]
### Step 31



![][image-31]
### Step 32



![][image-32]
### Step 33



![][image-33]
### Step 34



![][image-34]
### Step 35



![][image-35]
### Step 36



![][image-36]
### Step 37



![][image-37]
### Step 38



![][image-38]
### Step 39



![][image-39]
### Step 40



![][image-40]
### Step 41



![][image-41]
### Step 42



![][image-42]
### Step 43



![][image-43]
### Step 44



![][image-44]
### Step 45



![][image-45]
### Step 46



![][image-46]
### Step 47



![][image-47]
### Step 48



![][image-48]
### Step 49



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

Open …

![][image-1]
### Step 59

Click …

![][image-2]
### Step 60

Click …

![][image-3]
### Step 61

Select …

![][image-4]
### Step 62

Choose Edit  …

![][image-5]
### Step 63

…

![][image-6]
### Step 64

…

![][image-7]
### Step 65



![][image-8]


## Summary

You created a fun story for looking at shipwrecks around the coasts of the United States.  In the map, you and maneuver around and in the table, you can see details about the various wrecks.  The story still needs some polish and we’ll take it up again in Exercise 4.




Continue to - [Exercise 2](../ex2/README.md)

















































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
[image-49]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.49.png

