# Python for Data Science

## Table of Contents

1. [Read data with Pandas](#read-data-with-pandas)
2. [Inspect DataFrames with Pandas](#working-with-csv-files)
3. [Aggregate data with Pandas](#aggregate-data-with-pandas)
4. [Export data with Pandas](#export-data-with-pandas)

### Read data with Pandas
```python
# Step into our cozy coding haven, where each line of code wraps us in a comforting embrace.

# Ah, the 'import pandas as pd' line ushers in the mighty pandas library, like opening the door to a trusted friend.
# It's as if we're welcoming an esteemed guest into our cozy home, ready to embark on a data-driven adventure.

# This line of code imports the pandas library and aliases it as pd.
# It's like inviting a trusted friend into our coding sanctuary, someone who's got our back when it comes to handling data.
import pandas as pd


# Now, with the 'df = pd.read_csv('../MonthlySales.csv')' line, we embark on a journey through the data realms.
# It's like opening a treasure chest filled with precious information, ready to be explored and analyzed.

# This line of code reads a CSV file named 'MonthlySales.csv' and stores its contents in a DataFrame called df.
# It's like discovering a treasure chest full of valuable data, waiting to be uncovered and analyzed.
df = pd.read_csv('../MonthlySales.csv')


# Ah, the 'df' variable holds the key to our data treasure.
# It's like a map guiding us through the vast expanse of our data landscape, ready to reveal its secrets.

# This 'df' variable represents a DataFrame that contains our data treasure.
# It's like possessing a map that guides us through the vast expanse of our data landscape, revealing its secrets and insights.
df


# Yo, we 'bout to dive deep into the data game, so we bringin' in the JSON crew.
# It's like hittin' up the data wizards to put some magic on our files, you dig?

# This 'import json' line brings in the JSON crew, allowing us to work with JSON data.
# It's like calling in the data wizards to work their magic on our files and unlock their secrets.

import json

# Check it, we're bringin' in the JSON normalization squad straight outta the pandas block.
# It's like havin' the data SWAT team on speed dial, ready to handle any format like pros.

# This 'from pandas import json_normalize' line imports the json_normalize function from the pandas library.
# It's like having the data SWAT team on standby, ready to normalize our JSON data into a structured format.

from pandas import json_normalize

# A'ight, we crack open the JSON file and load it up.
# It's like poppin' the lock on the front door to our data crib and lettin' the numbers flow in for a chill session.

# This 'with open('../MonthlySalesByCategory.json') as json_data' line opens the JSON file for reading.
# It's like unlocking the front door to our data crib and welcoming the numbers inside for a chill session.
with open('../MonthlySalesByCategory.json') as json_data:
    # This 'd = json.load(json_data)' line loads the JSON data from the file into a variable called 'd'.
    # It's like inviting the numbers inside our data crib, ready to be analyzed and explored.
    d = json.load(json_data)


# A'ight, we 'bout to lay down some serious data moves, so we callin' up the JSON normalization squad.
# It's like bringin' in the heavy hitters to unpack our data stash, you feel me?

# This 'json_normalize' function call normalizes our JSON data into a structured DataFrame.
# It's like bringing in the heavy hitters to unpack and organize our data stash, making it ready for analysis.
# The parameters specify the structure of the JSON data, with 'monthlySales' being the nested key to normalize,
# and ['category', 'region'] indicating additional keys to include as columns in the DataFrame.
df = json_normalize(d['contents'], 'monthlySales', ['category', 'region'])

# Check it, now we got our data all nice and normalized, ready to rock and roll.
# It's like havin' a fresh set of blueprints for our data mansion, laid out and ready to build.

# This line displays the DataFrame 'df', showing the normalized data.
# It's like admiring the fresh set of blueprints for our data mansion, envisioning the insights and discoveries that lie ahead.
df


# A'ight, we 'bout to bring some data flavor into our crib, so we callin' up the parquet pandas.
# It's like invitin' a squad of data architects to design the blueprint for our data mansion.

# This 'import pyarrow.parquet as pq' line brings in the parquet pandas library under the alias 'pq'.
# It's like inviting a squad of data architects to our data mansion, ready to design the blueprint in Parquet format.
import pyarrow.parquet as pq


# Yo, we bringin' in the data masterpiece straight into our crib.
# It's like havin' the blueprint for our data mansion delivered right to our doorstep.

# This 'pq.read_table' function call reads a Parquet file and returns a Table object.
# It's like having the blueprint for our data mansion delivered right to our doorstep,
# ready for us to explore and analyze.
table = pq.read_table('../MonthlyProductSales.parquet')


# Yo, we ain't just stoppin' at the blueprint, we turnin' it into a livable space right in our crib.
# It's like takin' them data blueprints and buildin' our data mansion from the ground up.

# This 'table.to_pandas()' function call converts the Parquet Table object into a pandas DataFrame.
# It's like turning the data blueprints into a livable space in our data mansion,
# allowing us to explore and analyze the data more comfortably.
table.to_pandas()


#!pip install html5lib

# Yo, listen up! If you ain't got html5lib installed, you better go get it.
# Just hit up the pip and drop that install command like it's hot, you know what I'm sayin'?

# Check it, we 'bout to raid the data vault straight from a HTML site.
# It's like sneakin' into the backdoor of our data mansion and grabbin' all them state abbreviations.

# This line of code reads HTML content from the specified URL and parses it to extract tabular data.
# pd.read_html() is a pandas function specifically designed to scrape HTML tables and return them as a list of DataFrames.
# The URL provided leads to a Wikipedia page listing U.S. state abbreviations, so we're scraping that data.
# If you don't have the html5lib library installed, you might encounter issues with parsing the HTML content.
df = pd.read_html('https://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations')


# Yo, check it! We're grabbin' the juicy part of our data stash, straight outta the HTML grab.
# It's like sifting through the treasure chest in our data mansion and snaggin' the golden nuggets.

# This line of code selects the first element (index 0) from the list of DataFrames obtained from reading the HTML page.
# When we read HTML using pd.read_html(), it returns a list of DataFrames, each representing a table found on the page.
# We're specifically interested in the first table, which contains the states and their abbreviations.
df_usa = df[0]


# Alright, let's get down to business and clean up our data crib.

# This line of code drops the first 11 rows from our DataFrame df_usa.
# It's like sweeping away the clutter at the entrance of our data mansion, getting rid of any unnecessary information.
# These rows typically contain header information or introductory text that we don't need for our analysis.
df_usa_cleaned = df_usa.drop(df_usa.index[range(0, 11)])

# Now, we drop columns 10 to 14 (inclusive) from our DataFrame df_usa_cleaned.
# It's like renovating our data mansion's kitchen, getting rid of outdated appliances and unnecessary clutter.
# These columns likely contain additional information that we don't need for our analysis, so we're removing them.
final_df = df_usa_cleaned.drop(df_usa_cleaned.columns[10:15], axis=1)


# Time to give our columns some proper names and organize our data mansion.

# This line of code renames the columns in our DataFrame final_df.
# It's like labeling the rooms in our data mansion, making it easier to navigate and understand.
# Each column is assigned a new name based on its position in the DataFrame.
final_df.rename(columns={
    0: 'Region Name',
    1: 'Region Status',
    2: 'ISO',
    3: 'ANSI_Letter',
    4: 'ANSI_Code',
    5: 'USPS',
    6: 'USCG',
    7: 'GPO',
    8: 'AP',
    9: 'Other Abbreviations'
}, inplace=True)


# Time to reset the index of our rows and get things back in order.

# This line of code resets the index of the rows in our DataFrame final_df.
# It's like reorganizing the rooms in our data mansion, ensuring everything is in its proper place.
# By setting drop=True, we're dropping the current index and replacing it with a new sequential index.
final_df_reset = final_df.reset_index(drop=True)

```

### Inspect DataFrames with Pandas
```python
# Alright, let's bring in the pandas library and get this data party started!

# This 'import pandas as pd' line imports the pandas library and aliases it as 'pd'.
# It's like sending out invitations to our data party and welcoming pandas as our honored guest.
import pandas as pd


# Now, let's get to the real deal! We're loading up our CSV file 'MonthlyProductSales2.csv'
# and dumping its juicy contents right into a DataFrame called df.
# It's like cracking open a treasure chest packed with data gold and pouring it into our data crib.

# This line of code uses the 'pd.read_csv()' function from the pandas library to read a CSV file
# and create a DataFrame. The DataFrame is assigned to the variable 'df'. It's like unlocking
# a treasure chest full of valuable data and pouring its contents into our data crib.
df = pd.read_csv('../MonthlyProductSales2.csv')


# Yo, peep this! The 'df' DataFrame holds all our dope data from the CSV file 'MonthlyProductSales2.csv'.
# It's like takin' another look at our data crib, checkin' out the treasures we've already scooped up.
df


# Alright, fam, let's get a glimpse of the first few rows in our DataFrame.

# This line of code uses the 'head()' method on our DataFrame 'df' to display the first 10 rows.
# It's like peeking through the front window of our data crib to see who's chillin' inside.
df.head(n=10)


# show last 10 rows
df.tail(n=10)

# Alright, fam, here's the deal. We're diving deep into our data game with this slice.

# This line of code uses the 'tail()' method on our DataFrame 'df' to retrieve the last 10 rows.
# The 'tail()' method is like taking a peek at the end of our data crib, seeing what's up in the final stretch.
# The 'n=10' argument specifies that we want to fetch the last 10 rows specifically.
df.tail(n=10)


# Yo, check it out! Time to hit up the 'info()' function for our DataFrame 'df'.

# This function is like callin' in the data squad to give us the lowdown on our crib.
# It spills all the tea on our data, from its size and shape to the data types rollin' in.
df.info()


# Yo, check it! We're about to dive into the world of series with this slice.

# First up, we're selecting the 'Product Name' column from our DataFrame 'df' and assigning it to the series 's'.
# It's like grabbing a specific stack of records from our data crib and tossing them into a new container.
s = df['Product Name']

# Next, we're using the 'value_counts()' method on the series 's' to tally up the frequency of each value.
# This method is like running a headcount on each item in our series, so we know how many of each we've got.
# The 'dropna=False' argument ensures that missing values are also counted.
s.value_counts(dropna=False)
```

### Aggregate data with Pandas
```python

```

### Export data with Pandas
```python

```