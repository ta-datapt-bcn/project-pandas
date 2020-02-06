<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100" align="right"/>


#   Project Pandas Ironhack Data Bootcamp

Dinis Oliveira Costa

*Data Part Time Barcelona Dic 2019*


## Content
- [Project Description](#project)
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Results](#results)

<a name="project"></a>

## Project Description

Data cleaning is the process of detecting and correcting inaccurate records from a record set, table, or database and refers to identifying incomplete, incorrect or inaccurate parts of the data and then replacing, modifying, or deleting the dirty or coarse data.

It is important to be able to deal with messy data, whether that means missing values, inconsistent formatting, malformed records, or outliers.

The goal of this project is to practice the concepts of collecting, cleaning and preparing data for analysis and to get some hands-on experience working with Pandas and data sets.

The commands assume a basic understanding of the Pandas and NumPy libraries, including Panda’s DataFrame objects, common methods that can be applied to these objects, and familiarity with NumPy’s NaN values.


<a name="dataset"></a>

## Dataset

The data used in this project comes from a Kaggle set called [Shark Attack](https://www.kaggle.com/teajay/global-shark-attacks/version/1). The goal is to clean it up, prepare it to be analyzed, and then export it as a clean CSV data file.


<a name="workflow"></a>

## Workflow

The project follows three essential steps - `Inspection`, `Cleaning` and `Verifying` - in order to make it easy to keep track of changes and better structure the clean data set.

Before you begin, start by importing the table and the necessary libraries. Ready? Let's go!

### Step 1 - `INSPECTION`

In the first step, we need to collect the data we will be cleaning and examine it for potential anomalies.

To begin we need to:

#### 1.1 Collect the data

We need to read the csv file into a pandas dataframe

- pd.read_csv

#### 1.2 Take a look at the shape and features of the DataFrame 

The following methods print information about the DataFrame including: the dimensionality, the index dtype and column dtypes, non-null values and memory usage.

- sharks.shape
- sharks.info
- sharks.head

#### 1.3 Check for NaN values across all columns in the table

A quick way of isolating all the null values per column is using .isnull() and adding all the results per column:

- sharks.isnull().sum()

To get a clear picture of the NA per column, you can use a function that returns a new dataframe including the total number of NA values and the percentage of NA values in each column

- percent_NA(data)

### Step 2 - `CLEANING`

After getting a better understanding of the data set, we can begin organising it and make it more understandable.

#### 2.1 Column Names

Using a function, it is possible to quickly remove all dots, whites spaces and aplies lower case.

- def clean_col(data)

#### 2.2 Drop Columns

Depending on the focus of the analysis, there might be columns which are not so relevant. Using the .drop() command we are able to reduce the size of our table and narrow our results.

- sharks = sharks.drop(to_drop, axis=1) #this updates our DF and deletes all the unecessary columns

#### 2.3 Check for `Incorrect` and `Inconsistent` values in the table

The value_counts() function is used to get a Series containing counts of unique values. The resulting object will be in descending order so the first element is the most frequently-occurring element. Excludes NA values by default.

- column_check = sharks[i].value_counts()

It is used a FOR loop to get an initial idea of the issues with the results. To get into more detail and structure the next steps with each column it is recommended to use `sharks[<column_name>].value_counts()` individually.


#### 2.4 Deep Cleaning Time

At this point, since the issues with the DF have been identified, it is now time to start tackling each one individually and update the results in our DF.

- **date**: different lenghts and types of date formats
- **year**: different lengths (<4 digits) and value 0
- **type**: inconsistent with Provoked/Unprovoked
- **country**: inconsistent with name of the country
- **activity**: unexpected large strings instead of categories
- **sex**: unexpected values besides M/F
- **age**: unexpected values besides 2 or max 3 digits
- **fatal**: inconsistent values with boolean logic (Y/N)


#### 2.4.1 Collecting data from DATE to analyse attacks per month:

1 - Create a new column MONTH using DATE and fill with NaN if month doesn't exist
2 - Change column order so MONTH shows up next to DATE
3 - Drop NaN values and clean the rows with issues

#### 2.4.2 Clean the column SEX to analyse distribution of attacks per gender:

1 - Define a function that will take all the values and check if they are 'M' or 'F', otherwise replace them as NaN
2 - Use .apply() to update all values in SEX

#### 2.4.3 Clean the column **AGE** to analyse **distribution of attacks per age**:

1 - Define a function that will take all the values and replace them as 0 if they are not integers
2 - Include a condition that will replace the existing AGE ranges for NaN values
2 - Due to the amount of NaN values generated, it is recommended to create a new DF and conduct the analysis separately

#### 2.4.4 Clean the column **FATAL** to analyse **fatality of the attacks**:

1 - Define function will take all the values and check if they are 'Y'or 'N', otherwise replace them as NaN
2 - Use .apply() to update all values in FATAL

### Step 3 - `Verifying`

After having organised and cleaned the data set, the last step is to inspect the results to verify correctness. 

1 - Using the same method as in the beginning, check for shape, info and call a sample of the clean data set
2 - In case you identify anomalies with the clean dataset, go back to Step 2 and look for the source of the such issue
3 - After fixing the cause of the problem, export the clean dataset as a csv file


<a name="results"></a>

## Results

- Clean sharks data set 


## Deliverables

- `main.ipynb` with your commands and code you've used to clean the dataset
- `sharks_original.csv` containing the clean dataset
- `sharks_clean.csv` containing the clean dataset



