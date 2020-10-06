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

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.01.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.01.png?raw=true")


### Step 2

On the Home menu, select Create >> Story

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.02.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.02.png?raw=true")


### Step 3

On the Home menu, select Create >> Story

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.02.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.02.png?raw=true")


### Step 4

In the new story, select “Add a Canvas Page”.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.03.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.03.png?raw=true")


### Step 5

Let’s click the button to add some data!

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.04.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.04.png?raw=true")


### Step 6

When asked to choose where you would like to get your data, choose to upload a file.Important!  Choosing either to upload data or to connect to a source will create an new embedded dataset, where the dataset exists inside the story and is not accessible from anywhere else.   

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.05.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.05.png?raw=true")


### Step 7

Download AWOIS_Wrecks.csv if you have not already done so.  Click Select Source File to choose the file.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.06.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.06.png?raw=true")


### Step 8

Select the location where you have saved AWOIS_Wrecks.csv.  Click Import.Give your dataset a name when prompted.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.07.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.07.png?raw=true")


### Step 9

The dataset will load.  Progress bars will indicate the progress in loading and preparing the dataset import.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.08.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.08.png?raw=true")


### Step 10

When dataset import and preparation is done, you will see the smart wrangler screen.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.09.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.09.png?raw=true")


### Step 11

Before we venture any further, let’s take a tour of the various parts of the smart wrangler UI. 1- If your dataset is larger than 2000 rows, you will see a popup, informing you how big your dataset is and that the first 2000 rows have been sampled in the wrangler.  The wrangler samples large datasets for the sake of interactive responsiveness.2 – The Dataset Overview in the Details pane replaces the card view from the classic wrangler.  It lists the columns and groups measures and dimensions.  3 – Your data occupies the spreadsheet.4- Because you are working with an embedded dataset, you can freely toggle back and forth between the wrangler and story builder.5 – In the Actions group of the toolbar, you have the menu options specific to wrangling.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.10.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.10.png?raw=true")


### Step 12

Save your story and name it for the first time, so that you can save it as you work with hotkey commands.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.11.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.11.png?raw=true")


### Step 13

Have a look at your dataset in the Dataset Overview panel.Note that the columns with text columns have been flagged as dimensions and the ones with numerical values have been flagged as probable measures.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.12.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.12.png?raw=true")


### Step 14

LATDEC is latitude and LONDEC is Longitude.  You’ll want to use these as dimensions, so make them dimensions by dragging them down to the dimension area.Alternatively, you can select the “more” menu (the ellipsis, …) on individual columns in the Dataset Overview.

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex11/images/https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.13.png?raw=true "https://github.com/SAP-samples/teched2020-ANA363/blob/master/exercises/ex1/images/Ex1.13.png?raw=true")


### Step 15




### Step 16




### Step 17




### Step 18




### Step 19




### Step 20




### Step 21




### Step 22




### Step 23

Open …

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex21/images/Ww "Ww")


### Step 24

Click …


### Step 25

Click …


### Step 26

Select …


### Step 27

Choose Edit  …


### Step 28

…


### Step 29

…


### Step 30




### Step 31

Open …

![alt text](https://github.com/SAP-samples/teched2020-ANA363/raw/master/exercises/ex31/images/Ww "Ww")


### Step 32

Click …


### Step 33

Click …


### Step 34

Select …


### Step 35

Choose Edit  …


### Step 36

…


### Step 37

…


### Step 38






## Summary

You created a fun story for looking at shipwrecks around the coasts of the United States.  In the map, you and maneuver around and in the table, you can see details about the various wrecks.  The story still needs some polish and we’ll take it up again in Exercise 4.




Continue to - [Exercise 2](../ex2/README.md)
