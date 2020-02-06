<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100" align="right"/>


#   Project Ironhack Data Bootcamp

MIGUEL GARCÍA MELGAR

*Data Part Time Barcelona Dic 2019*


## Content
- [Project Description](#project)
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Results](#results)

<a name="project"></a>

## Project Description

### Overview

The goal of this project is to combine everything you have learned about data wrangling, cleaning, and manipulation with Pandas so you can see how it all works together. For this project, you will start with a messy data set. You will need to import it, use your data wrangling skills to clean it up, prepare it to be analyzed, and then export it as a clean CSV data file.

**You will be working individually for this project**, but we'll be guiding you along the process and helping you as you go. Show us what you've got!


### Technical Requirements

The technical requirements for this project are as follows:

* The dataset that we provide you is a significantly messy data set. Apply the different cleaning and manipulation techniques you have learned.
* Import the data using Pandas.
* Examine the data for potential issues.
* Use at least 8 of the cleaning and manipulation methods you have learned on the data.
* Produce a Jupyter Notebook that shows the steps you took and the code you used to clean and transform your data set.
* Export a clean CSV version of your data using Pandas.

### Necessary Deliverables

The following deliverables should be pushed to your Github repo for this chapter.

* **A cleaned CSV data file** containing the results of your data wrangling work.
* **A Jupyter Notebook (data-wrangling.ipynb)** containing all Python code and commands used in the importing, cleaning, manipulation, and exporting of your data set.
* **A ``README.md`` file** containing a detailed explanation of the process followed in the importing, cleaning, manipulation, and exporting of your data as well as your results, obstacles encountered, and lessons learned.

<a name="dataset"></a>

## Dataset
 
 The dataset we used was [Shark Attack](https://www.kaggle.com/teajay/global-shark-attacks/version/1).


<a name="workflow"></a>

## Workflow

### Prepare your IDE

- Download CSV
- Rename it as Shark_Attack
- Import the needed libraries
- Import CSV 

### Examine For Potential Issues
- Used .shape and .head() to obtain an overview
- Missing Values: Calculated the percentage of null values using .info and .isnull
- .shape and .head() to get a general overview of the contents
### Start Cleaning The Data
- Drop columns with more than 50% null values
- Drop rows that are still missing more than 33.33% values
- Check On Similarly Named Columns
  - Dropped rows with mistakes (non identical values in the row) in href & href formula
  - Dropped rows with mistakes (non identical values in the row) in "Case" columns
### Data manipulation
- Reorder Columns
- Rename Columns
- Extreme Values And Outliers
- Low Variance Columns
- Duplicates removal
- Data Type
- Remove columns I won't use
- Remove unknown years
### Fix Countries
- Created a dictionary to clasify countries by hemisphere
- Cleaned the data related to countries and sorted the values in Country alphabetically
- Created an hemisphere column indicating in which hemisphere is each country
### Seasons
- Used months indicated in the dates and the hemispheres info to get the seasons when the incidents were reported
<a name="results"></a>

## Results

At first we got a 5992x24 dataframe but after the cleaning and a bit of manipulation is a 5798x10 dataframe. If I had more time I'd like to clean much more and do it more carfully as I dropped some data that might have been corrected replacing info and using RegEx.

I feel that the oldest the information is the less precise it is and there were also more null values in those rows. It should be interesting to convert more columns data to numeric typs so as to makes some statistics analysis and decide properly on that since wich year we should keep the data and which variables should be dropped.



