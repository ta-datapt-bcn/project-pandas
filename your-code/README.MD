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

* Download CSV
* Rename it as Shark_Attack
* Import the needed libraries
* Import CSV 

### Examine For Potential Issues
* Used .shape and .head() to obtain an overview
* Missing Values: Calculated the percentage of null values using .info and .isnull
* .shape and .head() to get a general overview of the contents
### Start Cleaning The Data
* Drop columns with more than 50% null values
* Drop rows that are still missing more than 33.33% values
* Check On Similarly Named Columns
** Drop rows with mistakes in href & href formula
** Drop rows with mistakes in "Case" columns
### Data manipulation
* Reorder Columns
* Rename Columns
* Extreme Values And Outliers
* Low Variance Columns
* Duplicates removal
* Data Type
* Remove columns I won't use
* Remove unknown years
### Fix Countries
### Fix Ages

<a name="results"></a>

## Results






