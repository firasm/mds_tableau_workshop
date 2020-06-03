# Tableau Workshop

- Make sure you have downloaded Tableau and obtained a Tableau Academic License.
- Open Tableau Desktop

Table of Contents
=================

   * [Tableau Workshop](#tableau-workshop)
      * [Load in your Data](#load-in-your-data)
         * [Step by Step Instructions](#step-by-step-instructions)
      * [Making a Bar Chart](#making-a-bar-chart)
         * [Step by Step Instructions](#step-by-step-instructions-1)
      * [Aggregation plots](#aggregation-plots)
         * [Step by Step Instructions](#step-by-step-instructions-2)
      * [Making a Time Series](#making-a-time-series)
         * [Step by Step Instructions](#step-by-step-instructions-3)
      * [Maps](#maps)
         * [Step by Step Instructions](#step-by-step-instructions-4)
      * [Putting it all Together](#putting-it-all-together)
         * [Making a Dashboard](#making-a-dashboard)
         * [Filters](#filters)
            * [One Filter For Multiple Graphs](#one-filter-for-multiple-graphs)
            * [Using a Graph as a Filter](#using-a-graph-as-a-filter)
      * [Making Dashboard Tabs](#making-dashboard-tabs)
      * [Where to Deploy](#where-to-deploy)

## Load in your Data 
We have provided you with [data](https://github.com/firasm/mds_tableau_workshop/blob/master/data/street_trees.csv)  obtained from [The City of Vancouver's Open Data Portal](https://opendata.vancouver.ca/explore/dataset/street-trees/information/?disjunctive.species_name&disjunctive.common_name&disjunctive.height_range_id)
with minimal data wrangling done by the R package [DatateachR](https://github.com/UBC-MDS/datateachr).

### Step by Step Instructions 
1. On the left-hand side in the blue bar, you'll see a "Connect" heading. This is where you can connect Tableau to your data.      
1. Since we are using a `.csv` file we are going to click on "**More...**" under the "**To a File**" subheading.           
 _💡You can connect to many different things such as Microsoft SQL, PostgresSQL, Google Sheets, MongoDB BI Connector, etc. This is all accessible in "**More...**" under the sub-heading "**To a Server**"._
1. Locate the data and click "**Open**". This should connect your data and you should see a table. (You may need to click the "**Update Now**" button at the bottom)
1. Tableau automatically assigns variable types to your columns, however, if you click on the column icon, you can change it. We need to change the last 3 columns in our data `date_planted`, `latitude` and `longitude`. 
    - Scroll to the right and click on the icon (ABC) to the left of `date_planted` and convert it to **Date**. 
    - Next, convert `longitude` and `Latitude` to a **Number (decimal)** and the under the **Geographic Role** we can assign it to  **Longitude** and **Latitude** respectively.     
      _💡If we do not convert these columns to decimals first, Tableau will give you the **Latitude** and **Longitude** options under **Geographic Role**_ 
1. You can choose to rename your data source by clicking the title at the top.
1. To start creating plots you can click "**Sheet 1**" at the bottom left of the window. 


## Making a Bar Chart

We are going to make a bar chart for the number of trees in each neighbourhood. 

### Step by Step Instructions 
1. Since we are interested in the neighbourhood, we are going to drag from the left-hand side under the heading "**Tables**" the column named `neighbourhood_name` to the "**Column**" toolbar. 
1. We are interested in the count of the trees in each neighbourhood, so I like to use the index to count the rows but you can use multiple different columns here. Drag the `tree_id` to the "**Rows**" toolbar.
1. We need to convert this variable to a "**Measure**" specifically a "**Count**". We can do this by right-clicking on it. 
1. Voila! A bar chart! 
1. Let's change the colour. Go to the mark card and select a new colour. 
1. Let' edit our y-axis label. Right-click on the axis and click "**Edit Axis...**" Under "**Axis**", you can edit your axis "**Title**".
1. You can edit the title in two ways by editing the sheet name or by editing the title. I prefer to edit the sheet name by double-clicking the sheet at the bottom. 
1. You can sort the bars by clicking the icon beside the axis title. 
1. Let's convert it to a verticle bar chart. On the toolbar right above "**Columns**" you'll see a "Swap rows and columns" icon. This transposes your graph. 

Make a new worksheet by going to the menu bar under "**Worksheet**" and clicking "**New Worksheet**" (Or command T on a Macbook).   

## Aggregation plots 

This is very similar to how you would make a bar plot with one minor different we no longer are using a "**Count**" "**Measure**" but instead perhaps "**Average**", "**Median**", "**Max**" or "**Min**". 

We are going to make a plot showing the average `diameter` of the tree trunks of each `genus_name` type.


### Step by Step Instructions 
1. Drag from the left-hand side under the heading "**Tables**" the column named `genus_type` to the "**Column**" toolbar. 
2. We want the mean diameter for each genus so we can drag `diameter` to the "**Rows**" toolbar.
3. This is where things differ. We right click the `diameter`  and transorm the "**Measure**" to "**Average**". 
4. Instead of using a bar chart, Maybe using a dot plot would be more ideal. We can convert it by clicking the dropdown menu under the "**Marks**" card. Selecting "**Circle**" or "**Shape**" will instantly convert it.     

_💡You can add your own shape icons by adding a folder to your "My Tableau Repository" folder under "Shapes"_ 



## Making a Time Series 

We are now interested in the number of trees planted and the date they were planted so our two columns of interest are `date_plated` and `tree_id`.

### Step by Step Instructions 
1. Drag the `date_planted` variable to the "**Columns**" toolbar and again the `tree_id` to "**Rows**". We are again interested in the amount of trees planted at selected dates so once again we want to transform this to a "**Count**" type "**Measure**".  
1. Since `date_planted' is a continuous variable, it's a good idea to right-click and transform this into a **Continuous** Dimension. 
1. This automatically generates the number of trees planted at each year (but there are null values!)
1. We can change this to:
    - month - discrete (Top month choice when right-clicking)  which aggregates months together for all years 
    - month - continuous (Bottom month choice when right-clicking) which will make a sequential plot.
1. Combining scatterplot onto our line graph by adding an identical `tree_id` to rows and converting it to a counting measurement again. At first, we should get 2 graphs on top of each other. We can right-click one of them and select "**Dual Axis**".
This will superimpose one on another with a left and a right axis title. We can hide the one on the right by right-clicking the axis and unticking the "**Show Header**" option. 
1. To change the colour of the line and the points, we need to make sure we change the colour of both measures by selecting the "**All**" tab under the "**Marks**" card on the right.      
1. Don't forget to give it a title and edit the y-axis label as we did earlier.  

_💡Tableau also has a forecasting option. We can obtain it by right-clicking the plot and selecting "**Forcast**" then "**Show Forcast**". You can customize this by right-clicking again and Selecting "**Forcast Options ..**". I am going to stop here because this is NOT recommended. It's here but we can do better than this._

Make a new worksheet by going to the menu bar under "**Worksheet**" and clicking "**New Worksheet**" (Or command T on a Macbook).  


## Maps 

Remember how difficult it can be to make maps using leaflet, python and R. Well get ready where Tableau Shines. 

### Step by Step Instructions 
1. Drag `Longitude` to the "**Columns**" toolbar.
2. Drag `Latitude` to the  "**Rows**" toolbar.
3. You have essentially made your map but let's tidy it up. 
4. Decrease the size of your markers by clicking the "**Size**" icon under the "**Marks**" card. 
5. Click "**Map**" on the top toolbar and select "**Map Layers...**". This gives you the ability to customize the appearance of your map. You may want to:
    - Change the map style 
    - Add opacity to the map with "**Washout**"
    - Add different Map Layers
6. Add a title as before and you've got a functioning map in < 5 mins. 


## Putting it all Together 

### Making a Dashboard 
1. Create a new dashboard by clicking "**Dashboard**" in the top menu bar and selecting "**New Dashboard**"
2. Before you do absolutely anything, under the "**Size**" heading, click the triangle beside "Desktop Browser (1000x800)". Change "**Fixed Size**" to "**Automatic**". This will now make sure your dashboard adjusts to all monitor sizes. 
3. Let drag our sheets in using Tiled objects. Under "**Sheets**" on the left-hand side, drag and drop the sheets you want to include in you dash. 


### Filters 
1. Decide which filters you want for each plot. 
2. Go to the sheet my navigating on the bottom and selected the worksheet of interest.
3. Under "**Tables**" Drag the column you wish to filter, in our case `Diameter`, `root_barrier` and `neighbourhood_name`  to the "**Filters**" card above "**Marks**". 
    - For `diameter`, since it is a continuous variable we want to select "**All Values**". We can decide on what kind of filtering we want but we are sticking to a "**range**". 
    - For `root_barrier` we want to select all values and then "**OK**".
    - The same applies for `neighbourhood_name`.
4. Repeat this step for each of your worksheets. (OR wait and follow the next section) 
5. To obtain filters, on the side of the dashboard you will see a ▼ icon. Click this  and under "**Filter**" Select one of the column names. 
6. We can edit the filter style by clicking the "**More Options**" ▼ icon and changing the style. 
    - If it's filtering categorical data there are options like "**Single value (list)**", "**Single value (dropdown)**", "**Single value (slider)**", "**Multiple value (dropdown)**", etc. 
7. You can "**Customize**" The filter styles to include certain features as well. 
 
 
#### One Filter For Multiple Graphs
- If you want to use a single filter for multiple plots, you can do so using the "**Apply to Worksheet**" option. 
- This gives you the ability to select which sheet to also be filtered on this column or you can apply to "**All Using This Data Source**". 


#### Using a Graph as a Filter

If  you want to use a highlight something on a plot and have it act as a filter on other sheets in the dashboard, this can be done with a single mouse click. 
- Simply find the funnel icon on the side. When you hover over it, it should say "**Use Sheet as Filter**". 
- Done! 

## Making Dashboard Tabs 

FILL IN HERE 

## Where to Deploy 

- Tableau Online 
- Tableau Public 
- Tableau Server

 All options available in the menu bar under "**Server**"


