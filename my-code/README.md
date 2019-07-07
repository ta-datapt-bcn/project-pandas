
# Process of Wrangling Data

## Importing Libraries and CSV

When libraries pandas and numpy are imported, it pass to load CSV into Jupyter notebook.

First of all, an error for 'ut8' encoding has showed. It is suspicious because most of files are ut8-compliant nowadays. Afterwards a search, some possibles encoding stardards, could be used. The first try was __ISO-8859-1__, wich was decode this CSV succesfully.


## Getting Overview Info
With .info method an overview info was gotten. This identified Unnamed 22 & 23 as junk columns.

## Functions
Two functions were created:
 __pshape(df)__ shows shape of passed dataframe and shape of original loaded dataframe to compare.

__printr(df,list_cols,num_rows)__ prints n rows of each column to compare data. 


## Validating and Arranging Columns
* Nulls at columns 22 and 23
* Fill nulls in 'href formula' with good values
* Determining columns with duplicated values (date,year,pdf,href)
* Drop of descartable columns, bring very poor info (Case Number 1 & 2, Unnamed 22 & 23, original order)


## Refurbishing
* Rename of 'href formula' to 'href pdf', it is clearer.
* Indexing with Case Number 

## Save new CSV
The new csv file was saved with __'shark_attack.csv'__ file