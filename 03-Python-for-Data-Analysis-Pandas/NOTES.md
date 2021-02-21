# Pandas

## Series
Series - similar to numpy array - built on top of them
Can specify index (default is number 0...n-1)
Create labeled indexed series
pd.Series(data, index)
Can pass in list, numpy array, or dictionary as data (dictionary will use keys as index)
Can hold a variety of object types
Very fast lookup by index
Use syntax like dictionary to get value by index
Can do basic operations with series - match by keys and add, subtract, etc.

pd.Series(data, index)

## Data Frames
Main tool when working with Pandas, built off of Series
pd.DataFrame(data, indexes, columns)
Creates a matrix - similar to numpy matrix, indexes are rows mapped to the columns

### Data Frames Basics
Use bracket notation to grab values
df[ColumnVal] - returns column as a series
Can also use "dot" notation e.g. df.<colVal> - recommend using bracket
Can pass in a list of columns to get multiple ones (returns dataframe)
df[[col1, col2]]

Can add new columns
df[newCol] = df[col1] + df[col2] to create a new column with the result of adding col1 & col2
df.drop(col, axis=1) to remove a col (axis must be 1, default is axis = 0 which are the indexes/rows)
Also set inplace=True argument to actually update the dataframe - prevents accidental deletion - otherwise just returns new dataframe with deletion

Select rows with loc method
df.loc[label] - pass in row to return a series for that row
df.iloc[rowIndex] - pass in row index to get series for that row
df.loc[row1,col1] - return single value at row/column
df.loc[[row1, row2], [col1, col2]] - pass in lists of rows/cols to select subset

### Data Frames Part 2
Conditional Selection
df > 0 - will return dataframe with boolean values where condition is true/false
df[booldf] - will return new dataframe with values where booldf is true & NaN where false
e.g. df[df>0]

df[df[col]>0] to get a series where rows where condition is true
Grabs all rows across all columns even though col condition is only matching one column
Returns dataframe that can be used for further interrogration

Can do the following to conditionally filter and grab values of interest
df[df['W']>0]['X'] - grab column X with all rows where the value of column W > 0
df[cf['W']>0][['X', 'Y']] grab columns X & Y by passing in list of cols

Compound conditions
df[(df['W'] > 0) & (df['X'] > 1)] - have to use & for and 
Use | for or 

Index resetting
df.reset_index() - resets index back to default numeric index, creates column called "index" with old index values
By default does not happen inplace

Set a column with new index values (e.g. df['newCol'] = newValues)
df.set_index('newCol') - to reset index to new column but overwrites old index

### Data Frames Part 3
Multi Indexes & Index Hierarchy
List of tuples to build multiple index hierarchy
Use zip function to create all matching tuples for 2 lists (e.g. ['A', 'B', 'C'] & [1, 2, 3] creates [('A', 1), ('B', 2), ('C', 3)])
Use pd.MultiIndex.from_tuples to convert to create pandas index
Pass index to pd.DataFrame to create dataframe with multi-index DF

df.loc['G1'].loc['1'] to get inner nested index

Can name indexes
df.index.names = [name1, name2] - pass in list of names

df.loc['G2'].loc['2']['B'] to grab column value from nested index

Cross Section function
df.xs(1, level='indexName') - grabs inner index cross sectioned across all rows

## Missing Data
df.dropna - drops any row with any missing values (use axis to perform on columns, and inplace to perform on df in pace)
Can specify threshold - (thresh) integer value that requires that # of non-missing values before it is kept

df.fillna - specify value to fill in missing values 
Can fill with mean of column - e.g. df['A'].fillna(value=df['A'].mean())

## Group By
df.groupby(colName) - returns groupby object
df.groupby(colName).mean() - returns dataframe with numeric columns aggregated grouped by the column specified
Useful aggregate functions - count, sum, mean, min, max, etc.
describe method gives many stats (count, min, max, mean, std dev, quartiles, etc.) - add .transpose to format as columns instead of rows

## Merging, Joining, & Concatenating
How to combine data frames
concat method - pass lists of DFs to concatenate - just appends along axis (default axis is 0 or rows or 1 for columns) will set to NaN if index value is missing

merge to merging dataframes together based on a key column, similar to a "join" in sql - can use inner our outer type joins, on to specify key column (can be multiple key columns too)
pd.merge(left, right, how="inner", on="key")
how = inner, outer, right, or left

pd.join - combines dataframes based on index value - similar to merge but uses index value instead of arbitrary column

## Operations
Find unique values in a DF
All unique values in a column - use unique method df['col'].unique()
Find # of unique values - use generic len method or nunqiue 
df['col'].value_counts() - returns each unique value with # of times it appears

apply method - very powerful tool for pandas
allows you to apply a custom function or built in function
df['col'].apply(myFunc)
Can be lambda expression to
df['col'].apply(lambda x: x\*2)

df.columns or df.index to get information on columns & indexes

### Sorting & Ordering
df.sort_values(by, axis) 

df.isnull() - find null values in df

### Pivot Table
df.pivot_table(values, index, columns) 
Similar to Excel pviot table feature
values = actual values to put in table
index = rows/indexes to use - can be multi index
columns can be list too - will create columns out of values in the specified column(s)

## Data Input & Output
Read & write data from/to sources (e.g. CSV, Excel, HTML, SQL)
pd.read_csv('file')
Many read_ functions for different types
df.to_csv('file') - to write to a file - can set index=false so index is not included

Excel
pd.read_excel('file', 'sheet') - each sheet is a data frame, only supports values - no formulas, etc.

HTML
pd.read_html('url') - returns list of all table elements & convert each one into a df

SQL
Pandas are not the best way to read a SQL database - better to use RDBMS specific library instead of pandas
Use sqlalchemy to create an in-memory sql engine - e.g. using sqlite
