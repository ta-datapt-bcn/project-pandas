

The original .csv file was obtained from Kaggle's Global Shark Attack Incidents dataset. After downloading it was imported with pandas (pd.read_csv).

Before beggining with the manipulation I thought wich variables I would like to work with, afterwards.

The manipulation of the dataframe included: elimination of columns with redundant or useless information, renaming of columns, reordering of columns, deletion of rows with ancient cases (with poor information), deletion of duplicated rows and changing values 'yes' or 'not' from a column to 1 and 0.

Some parameters were studied from the cleaner dataframe, such as countries with more number of cases, the percentage of unprovoked attacks in the 2 countries with higher number of cases or the activities more susceptible of suffering a shark attack and the percentage of those attacks that are fatal.

Finally, the cleaner dataframe was exported as a csv file (tidy_shark_dataset.csv).