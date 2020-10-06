# Exercise 3


## Estimated Time: 30 minutes

## Objective

This is the part of the workshop where the power of the smart wrangler starts to become apparent.  In this exercise, you will take the public dataset that you started working on in Exercise 2 and enhance it.  You may have noticed that there are no readily apparent column for dates.  There is a year column and a month column, but nothing that can easily be called a date.  You’ll fix this (and never worry about oddball date formats agiain).  You’ll also slip a calculation right into the dataset.  


## What You Learn

*Datatype conversions on columns

*The basics of using the wrangler expression language (WEL)

	


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

LATDEC is latitude and LONDEC is Longitude.  You’ll want to use these as dimensions, so make them dimensions by dragging them down to the dimension area.Alternatively, you can select the “more” menu (the ellipsis, …) on individual columns in the Dataset Overview.

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

Open …

![][image-1]
### Step 23

Click …

![][image-2]
### Step 24

Click …

![][image-3]
### Step 25

Select …

![][image-4]
### Step 26

Choose Edit  …

![][image-5]
### Step 27

…

![][image-6]
### Step 28

…

![][image-7]
### Step 29



![][image-8]
### Step 30

Open …

![][image-1]
### Step 31

Click …

![][image-2]
### Step 32

Click …

![][image-3]
### Step 33

Select …

![][image-4]
### Step 34

Choose Edit  …

![][image-5]
### Step 35

…

![][image-6]
### Step 36

…

![][image-7]
### Step 37



![][image-8]


## Summary

You now have a fairly robust dataset for examining visitation statistics in US National Parks, Monuments Recreation, Lakeshores and Seashores.  Have fun seeing what you can tease out of it.  


[image-1]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.01.png
[image-2]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.02.png
[image-3]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.03.png
[image-4]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.04.png
[image-5]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.05.png
[image-6]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.06.png
[image-7]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.07.png
[image-8]:    https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex3/images/Ex3.08.png

