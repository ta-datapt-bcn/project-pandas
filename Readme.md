![IronHack Logo](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_d5c5793015fec3be28a63c4fa3dd4d55.png)

# *PANDAS CLEANING PROJECT* #
## by Hernán Sosa.

We are given a very untidy and messy dataset from Kaggle Datasets [Sharks Dataset](https://www.kaggle.com/teajay/global-shark-attacks/version/1). This dataset contains records on shark attacks over history. 
Our goal is to provide a consistent Dataset to properly show up **'Shark attack cases over time and place'**. In order to get useful information, we processed this dataset by following the next steps:

## 0. Setting up Workspace:

Since we've done some different processes along the project, we've also used different libraries:

- `import re`: Imports the *Regex* library. Useful for text manipulation.

- `import pandas as pd`: *Pandas* library. The core of our DataFrame structure.

- `import numpy as np`: *Numpy* lets us manipulate arrays, numeric operations and brings many other useful functions.

- `import datetime`: *Datetime* is needed in order to get a better date manipulation.

- `import random`: *Random* is used to generate random values in different approaches.

- `import seaborn as sns`: *Seaborn* is a library to generate prettier graphics.

- `import matplotlib.pyplot as plt`: *Matplotlib*, used for graphic creation. It's integration with *Pandas* makes it very useful.

- `%matplotlib inline`: Jupyter and *Matplotlib* need this code in order to get proper visualizations on the notebook.

- `from pandas.plotting import register_matplotlib_converters`: Future versions of *Pandas* wiil need this library in order to show plots correctly.

After that, we're importing our ``'sharks.csv'`` file and transform it to a DataFrame through ``pd.read_csv()``


## 1. Analyzing Dataset : ##

As we said, our Dataset is untidy. It contains the following columns:

           'Case Number', 'Date', 'Year', 'Type', 'Country', 'Area', 'Location',
           'Activity', 'Name', 'Sex ', 'Age', 'Injury', 'Fatal (Y/N)', 'Time',
           'Species ', 'Investigator or Source', 'pdf', 'href formula', 'href',
           'Case Number.1', 'Case Number.2', 'original order', 'Unnamed: 22',
           'Unnamed: 23'


Using our custom function `df_total_na(df)` we can see that our dataset has a total **19.15%** missing values overall.

Also, our function `column_nulls_percentage(df)` shows total percentage of missing values *per row*. Showing the ones with `Nan` over 40%:

            Age                       44.74
            Time                      53.62
            Species                   48.97
            Unnamed: 22               99.98
            Unnamed: 23               99.97
        
### 1.1 Erasing unuseful columns:

After a quick exploration using `df.info()`, `df.value_counts`, and `df.head()` we quickly realized that we don't need the following columns, so we're taking them out with `df.drop()`:

- `'Case Number'`, `'Case Number.1'`, `'Case Number.2'` provides IDs not useful for us, since we plan to have a DateTime index, and contains too many NA's.

- `'pdf'` contains unuseful name archives.

- `'Year'` contains duplicated data, also present in `'Dates'`, and contains 44.7% null values.

- `'Type'` contains unclear values for our study.

- `'href formula'`, `'href'` contains links leading to non-existing web pages.

Then, we proceed to clean the column names and `.lower()`them down, just for practical pruposes.

This is what's left:

        Index(['date', 'country', 'area', 'location', 'activity', 'name', 'sex', 'age',
        'injury', 'fatal', 'time', 'species ', 'source'])


## 2. Cleaning Dataset:

We'll treat columns one by one, since all of them should behave in a particular way.

- ###  2.1 Setting up a DateTime Index:


We can set the index of the DataFrame in order to have a proper way to study it, using the `'date'` column values:

            0    18-Sep-16
            1    18-Sep-16
            2    18-Sep-16
            3    17-Sep-16
            4    16-Sep-16
            5    15-Sep-16
        
This format is good for us, but not the `dtype`. So we'll just set all the column values to datetime objects, and set the non-readable values to `NaT`, using`pd.to_datetime()`.

This process sacrifices 857 values, **15% of our observations**. Analyzing the points, in the original `Series` we conclude that these values were not useful due its ambiguity.

Finally, we set the `df.index` to a this new DateTime series:

            df = df.set_index(df_time)
        
Additionally, with `df.index.rename('')` and `df.index.strftime('%B %d, %Y')` we set proper ways to visualize this data.


- ### 2.2 Location manipulation


On the format we've given, we can see 3 rows which can be converted to just one by joining them and manipulating its content: `'country'`, `'area'` and `'location'`.

We'll transform all the values of these columns with `capitalize()`, a custom function that takes every word of a string and `str.Title` it. Once we have this processed strings, we join them on a single one using the `zip()` function to concatenate rows in order.

With this values, we'll be able to tranform them into 'latitude' and 'altutide' coordinates to geolocalize them (coming soon)

- ### 2.3 'Age' column


We'll use Regex and `str.contains` to see how much of the values in 'age' have valid data points. We see that we have a total 3280 '1 or 2 digit' type observations:

            True     3280
            NaN      2681
            False      31
            
The age of the victims is really not important in our case study, but it's information that might be handy in some cases.
So, we'll process all the data points with `clean_2d_age(string)`, another custom function that takes a string containing numbers and converts it to a one or two digits integer using RegEx. Now we have a proper `dtype=int` column for this values.

- ### 2.4 'Fatal' column: Bool variables

In this column we should expect to have just two values, `yes` and `no`:

            N          4315
            Y          1552
            UNKNOWN      94
            nan          19
             N            8
            n             1
            F             1
            #VALUE!       1
            N             1
    
Not the expected output. For a better approach, we could use `True` and `False` so we'll use the custom function (using RegEx) `yn_to_tf(string)`.
This function analyzes a string using regex. If the string is Yes, return True. If it is No, return False. For invalid data, returns Nan.

            False    4440
            True     1552
            
- ### 2.5 'Sex' column: Categorical variables

Similarly to 'Fatal' column, `sex` should have only 3 observations: `male`, `female`, and `nan` (since Unknown it's not a valid value for our study)

We're making use of the function `mf_to_malefemale(string)`, which is a variation of the one that we used before.

After assigning the processed values to this column, we end up with 4837 `male` and 585 `female` values.
        

- ### 2.6 'Name' column: Assigning unwanted variables to Nan

The 'name' column it's a pretty messy one. We can't afford to process this values, since names are super irregular.
In this case, we'll make a list with the most frequent values using `names.value_counts()`, to find errors:

            male       367
            nan        145
            female     68
            boy        16
            boat       12

Because names should be unique values, finding repeated terms it's a practical way to find errors. We end up with a list `'errors'` using `names.value_counts().index.tolist()`.
With this list, we'll get the 12 most repeated values `errors[:12]`. This will be use on a function `delete_errors(name)` which will examine each name, and if it finds it on this list, will transforme it to `NaN`.

- ### 2.7 Deleting rows containing NaN values

For this excercice, we are not interested on having rows containing missing values. After all the processes we went on, we have enough data to make valuable insights and complete visualizations. So we'll simply make a new dataframe containing only rows with full observations, and save it as `clean.csv`. We'll also have to reassign the DateTime Index:

            df_clean = df.dropna(axis=0)
            df_clean.shape
            df_clean.index = pd.to_datetime(df_clean.index)
            df.to_csv('Data/clean.csv')

            (1419, 11)

# 3. Using the clean data

Now we've been throught de data wrangling, we can for example:

- ### 3.1 Plot

Using `plt.plot` we can make a simple graph containing all the shark attacks per year. For this matter, we'll have to `resample`our DateTime index to group and sum the observations per year:

             df_plot = df_clean.resample('Y').count()
             
Using the simple `Matplotlib` syntax, we show the nº of attacks per year, keeping in mind that we've erased nearly 70% of the data we originally had:

![plt.plot](https://github.com/H89Sosa/project-pandas/blob/master/imgs/plot.jpg?raw=true)

- ### 3.2 shark_attack() function

We wanted to make a function that takes a date as user input, or a random date as default, to print the following statement:

*'In `{date}`, a `{sex}` of age`{age}` named `{name}`, was `{activity}` in `{location}` when got `{injuries}`, he/she`{sex}` died/didn't die`{fatal}`, as pointed out by `{source}'`*

We would have to use the `df.iloc[]` accessor as the input and also use `np.random.randint()` to generate a random value for the Index.

This function would be funny to use because the user could enter a date of his own or simply show a random case.