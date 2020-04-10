<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100" align="right"/>


#   Project Ironhack Data Bootcamp

KRISTINA KUNCEVICIUTE

*Data Part Time Barcelona Dic 2019*


## Content
- [Project Description](#project)
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Results](#results)

<a name="project"></a>

## Project Description

The goal of this project is to combine data wrangling, cleaning, and manipulation with Pandas. Start with import the dataset, use the data wrangling skills to clean it up, prepare it to be analyzed, and then export it as a clean CSV data file.

<a name="dataset"></a>

## Dataset

Dataset [Shark Attack](https://www.kaggle.com/teajay/global-shark-attacks/version/1).

<a name="workflow"></a>

## Workflow

- Examine the data and try to understand what the fields mean
- Import the dataset (importing Date, Type, Country, Activity columns as string, to be able to use regex on them later)

1. Doing the FIRST CLEANING: Cleaning column names and removing first duplicates

    - clean the spaces from column names
    - change values that are strings to uppercase in all dataframe and also strip the empty spaces
    - check for duplicates in all dataframe
    - check and clean duplicates based on Case Number column
    - choosing only one column for Case Numbers and renaming the column
    
2. Cleaning MISSING DATA: Cleaning column by column, checking incorrectly submitted data, deleting NaN
    - check in which columns and how many rows of Null have
    - delete columns with more than 5000 rows empty, almost all the rows are empty, useless info

    2.1 Cleaning more complicated cases of invalid data column by column
        - checking unique values per column and preparing the list of changes
        - Applying changes per column (listed in the fixable list):
            
    'Date' Invalid data:
    
    - Extract only the year, create new column, later merge this column with the column year
    - The rest with regex extract what needed (dd-mmm-yy and dd-mmm-yyyy, unify to dd-mmm-yyyy) and create a new column
    - Check how many NaN have this new column
    - When done, deleting the old column
    
    'Year' Invalid data:

    - Extract with column rules only the year >1500, create new column
    - Delete old column
    - Check how many NaN this new column has
    - Merge Year with Year that was extracted from Date
    
    'Type' Invalid data:

    - All that is not Unprovoked or Provoked change to NOT SPECIFIED
    
    'Name' Invalid data:

    - Extract using regex all variations of male, female, boy, girl, woman, man and create new column
    - With this info recover some Nulls from Sex column
    - Clean gender values from Name column
    
    'Sex' Invalid data:

    - Change what is not M or F to NOT SPECIFIED
    - Replace NOT SPECIFIED with possible values from columns that got from Name
    - Delete additional columns: male from names and female from names
    
    'Age' Invalid data:

    - Extract only one integer values, craete new column
    - Check how many Nulls have in this new column
    - Delete old column
    
    'Injury' Invalid data:

    - Extract all variations of FATAL and create new column, update column Fatal with it
    - Extract all variations of SURVIVED and NO INJURY, MINOR INJURY and create new column, update column Fatal with it

    'Fatal' Invalid data:

    - Rename the column to Fatal
    - All that is not N or F, change to NOT SPECIFIED
    - Update some not specified values from the info from Injury
    
    'Time' Invalid data:

    - Extract only the format ddHdd, create new column
    - Check how many Nulls are in this new column
    - Delete old column
    
    'Country' Invalid data:

    - At this point only filtered some similar names in the column Country to later unify them
    
    2.2 Changing all Null values to NOT SPECIFIED
    
3. FINAL EDITS and export

    - Changing column order
    - Exporting clean dataframe
    
4. AGGREGATING DATA

    - YEAR - checking the years when had the most injuries
    - YEAR - showing histogram to see when had the most injuries
    - MONTH - calculating injuries per month
    - MONTH - checking the average number of injuries per month

Libraries used: Pandas and matplotlib.pyplot

<a name="results"></a>

## Results

1. Found and cleaned 32 duplicates
2. Deleted 2 columns with more than 5000 rows empty, almost all the rows are empty, useless info
3. Recovered 792 values in Date column
4. Invalid entried in Year changed to correct ones from the column Date, have 100% of years correct
5. In the column Name found extra 1234 incorrect values, changed to NOT SPECIFIED, later used them to recover values in Sex column
6. Recovered 52 values in column 'Sex' from column 'Name'
7. After cleaning 'Age' column discovered that have only 3151 clean ages, which is 53.0% of all data, it is only representing the half of all the cases
8. Recovered 4 values in column 'Fatal' from column 'Injury'
9. Cleaned Type column to change incorrect data to NOT SPECIFIED
10. Extracted Month from the Date column
11. From the created histogram discovered that the most of the injuries happened in 2015 and 2011
12. Found out that the average number of injuries per month (taking all years together) is 332
