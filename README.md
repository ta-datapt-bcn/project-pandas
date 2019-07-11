![IronHack Logo](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_d5c5793015fec3be28a63c4fa3dd4d55.png)

# Guided Project: Demonstration of Data Cleaning and Manipulation with Pandas
### Dani Eiroa

## Process
### Importing
- Downloaded dataset and renamed it to shark_attack_messy.csv
- Imported libraries
- Loaded dataset
### Exploring the original dataframe
- Explored dataframe using .info, .shape and .head() to get a general overview of the contents
- Got the proportion of null values per column to get an idea of very empty columns.
- Tried to check similarly named columns to see the differences amongst them.
#### General impressions:Case_Number
- Two empty columns, which seem useless (unnamed)
- 2 int variables - Rest of variables are mainly text
- href_formula and href seem pretty similar
- Case_Number, Case_Number.1 and Case_Number.2 seem pretty similar
    - Check the cases where there are differences between the values of those columns
- Age is type object (string)
- Dates and hours are also strings
- Very heterogeneous values for injuries and data, mainly for the former
### Cleaning and Manipulation
- Renamed columns
- Cleaned case numbers using the most suitable content for the non-equal columns and dropped case number 1 and number 2 columns
- Cleaned href columns using the most suitable content for the non-equal columns
- Changed 'age' type to numeric. Some of the strings did not contain only numberes (i.e. '60s'). Decided to drop those using the parameter errors = 'coerce', so NaN was set instead of the number.
- Changed 'year' type to numeric
- Changed 'original order' type to numeric
- Changed 'date' type to datetime
- Made a new column combining 'date' and 'time' and changed type to datetime
- Due to the heterogeneity of the 'injuries' column I decided to make a bag of words to facilitate posterior analysis of that column.
### Exporting
- Exported clean dataframe as 'shark_attack_clean_dani.csv'
- Exported 'injuries' bag of words as 'injury_bow.csv'


## Results and conclusions
- Started with a 5992x24 dataframe and ended up with a 5922x19 dataframe. Still significantly big to extract conclusions but way cleaner and easier to analyze at the expense of loosing some date and time information (turned to NaN when passing .to_datetime function).
- **'investigator_or_source'** could use some cleaning. I think maybe trying to separate source and date, maybe using regex.
- Bearing in mind the content of the **'species'** column, I don't think it is really useful. Would like to find a way to sort it out.
- I think the very old entries are not very reliable and may not contribute significantly to posterior analysis, but I finally decided to leave them in the df.


## Obstacles found and lessons learnt
- First time importing the dataset using pd.DataFrame the dataframe (df) turned out to be very messy. Fixed it by changing the 'encoding' parameter of the function.
- Initially tried to explore the df using profile.report() but it took a lot of time and every time I run it the names of the columns changed slightly (i.e. Sex to Sex_).
- I tried insistently to change 'time' type to date time, but I found no way to get only the time. The closest I got was to set the date to today's date by default and the time to the original time that wasin the column. Finally I combined 'date' and 'time' columns in a new column 'date_time' and passed .to_datetime()