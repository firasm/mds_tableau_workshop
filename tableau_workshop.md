# Tableau Workshop

- Make sure you have downloaded Tableau and obtained a Tableau Academic License.
- Open Tableau Desktop

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

We are going to make a bar chart for the number of trees in each genus. 

### Step by Step Instructions 
1. Since we are interested in the tree genus, we are going to drag from the left-hand side under the heading "**Tables**" the column named `genus_name` to the "**Column**" toolbar. 
1. Since we are interested in the count of the trees in each genus, I like to use the index to count the rows but you can use multiple different columns here. Drag the `tree_id` to the "**Rows**" toolbar.
1. We are counting the number of trees in each genus, so we need to convert this variable to a "**measure**" specifically a "**count**". We can do this by right-clicking on it. 
1. Voila! A bar chart! 
1. Let's change the colour. Go to the mark card and select a new colour. 
1. Let' edit our y-axis label. Right-click on the axis and click "**Edit Axis...**" Under "**Axis**", you can edit your axis "**Title**".
1. You can edit the title in two ways by editing the sheet name or by editing the title. I prefer to edit the sheet name by double-clicking the sheet at the bottom. 
1. You can sort the bars by clicking the icon beside the axis title. 
1. Let's convert it to a verticle bar chart. On the toolbar right above "**Columns**" you'll see a "Swap rows and columns" icon. This transposes your graph. 

Make a new worksheet by going to the menu bar under "**Worksheet**" and clicking "**New Worksheet**" (Or command T on a Macbook).   

## Making a Time Series 

We are now interested in the number of trees planted and the date they were planted so our two columns of interest are `date_plated` and `tree_id`.

### Step by Step Instructions 
1. Drag the `date_planted` variable to the "**Columns**" toolbar and again the `tree_id` to "**rows**". We are again interested in the amount of trees planted at selected dates so once again we want to transform this to a "**Count**" type "**Measure**".  
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

- Making the dashboard 
- Filters 
- 1 filter for multiple graphs
- Using a graph as a filter


## Making Dashboard Tabs 



## Where to Diploy 

