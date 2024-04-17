<center><h1>Python for Data Science</h1></center>

## Table of Contents

1. [Working with JSON data](#working-with-json-data)
2. [Working with CSV files](#working-with-csv-files)
3. [Working with Parquet files](#working-with-parquet-files)
4. [Read data from GitHub API](#read-data-from-github-api)

### Working with JSON data
```python
# Ah, the magic spell to summon JSON from the depths of the digital realm!
import json

# Yo, check it! Picture this: you got this fat scroll, like one ancient manuscript, but it ain't parchment and ink, it's all digital, stored up in the heart of the computer.
# So, you crack open this scroll using Python magic, just one slick line of code.
# We call this line `open('../MonthySalesByCategory.json')`. This line, it's like the key to the vault. It opens the door to the JSON world, letting us take a peek inside.

# Now, peep the `with` keyword? That's like the bouncer at the club, making sure we don't cause no trouble, closing the door behind us when we're done.
# Inside the `with` block, we got the `json.load(json_data)` line. That's where the real magic happens, fam!
# It reads the JSON data, like cracking a secret code, and transforms it into a Python dictionary. Mind-blowing, right?
# So now, we got the loot in our hands, ready to uncover the riches it holds!

# Open up the JSON file like it's the key to a hidden treasure
with open('../MonthySalesByCategory.json') as json_data:
    # Read the JSON data and convert it into a Python dictionary
    d = json.load(json_data)

# Yo, check this out! We just got our hands on some prime loot. It's like stumbling upon a hidden treasure in the concrete jungle!
# Peep this line: `from pprint import pprint as pp`. It's like calling up a tech-savvy sidekick to help us decode the secrets of the stash.
# And when we drop `pp(d)`? It's like activating a superpower, unveiling the hidden gems of the dictionary in all their glory.

# So, get ready to feast your eyes on the urban dictionary! Hit enter and brace yourself for the magic show!
from pprint import pprint as pp
pp(d)

# Okay, check it out, we're gonna peep into this JSON data and see what's poppin'. Let's roll!
print(d.keys())  # This prints out the keys of the JSON dictionary. We're looking for the main categories, ya dig?

# Yo, we 'bout to dive into this JSON data, so buckle up!
for a in d['contents']:  # We be loopin' through the 'contents' section of the JSON dictionary.
    print(a.keys())  # This here prints out the keys of each element in the 'contents' section. Let's see what's poppin'!

# Yo, we're cruising through these JSON vibes with a for loop, hitting up each 'monthlySales' section within the 'contents'.
for a in d['contents']:  # Rolling through every element in the 'contents' area.
    for b in a['monthlySales']:  # Now, we're zooming into each 'monthlySales' data nugget within.
        print(b.keys())  # Peeking inside to see the keys of each 'monthlySales' treasure chest!


# Ah, check this out! We're diving deep into the JSON ocean, using a slick Python loop to navigate through the keys and values.
for key, value in d.items():  # Looping through each key-value pair in our JSON dictionary.
    print(key + ': ', pp(value))  # Printing out the key along with its corresponding value, all neatly packed!


# Yo, we're diving into the 'contents' of our JSON dictionary, using a double loop to surf through the data waves!
for a in d['contents']:  # Looping through each item in the 'contents' list.
    for key, value in a.items():  # Now we're cruising through each key-value pair in the current item.
        print(key + ': ', value)  # Riding the waves, printing out the key along with its corresponding value!


# Alright, we're plunging into the 'contents' of our JSON dictionary, taking a deep dive into the 'monthlySales' data!
for a in d['contents']:  # Looping through each item in the 'contents' list.
    for b in a['monthlySales']:  # Now we're navigating through each 'monthlySales' entry in the current item.
        for key, value in b.items():  # As we descend further, we're exploring each key-value pair in the 'monthlySales'.
            print(key + ": ", value)  # With every wave, we're printing out the key along with its corresponding value!

```

### Working with CSV files
```python
# Alright, we're kicking off the code with an import statement for the CSV module. 
# This module's like the DJ at a party, spinning those CSV files into data we can groove with. 
# Get ready to drop some beats and wrangle some data, because we're about to make magic happen!
import csv

# Alright, check it out, we're starting off with an empty list here.
# This bad boy is gonna hold all our monthly sales data. 
# We're talking stacks on stacks of dollar signs, but for now, it's just a lonely pair of square brackets.
MonthlySales = []

# Alright, we're diving into some file handling action here.
# We're cracking open a CSV file named "MonthlySales.csv" located one directory up from where this script is chilling.
# The 'r' mode indicates we're opening this bad boy for reading purposes only.
with open('../MonthlySales.csv', 'r') as f:
    # Now, here's where the real magic happens.
    # We're creating a reader object using csv.DictReader(f).
    # This slick operator is gonna help us parse through the CSV file like a pro, turning each row into a dictionary where the keys are the column names.
    reader = csv.DictReader(f)
    
    # Now, hold onto your hats, 'cause here comes the loop!
    # We're looping through each row in our CSV file using for row in reader.
    for row in reader:
        # And what are we doing with each row?
        # We're stuffing it right into our MonthlySales list with MonthlySales.append(row).
        # So, every time this loop runs, we're snagging a row from our CSV and shoving it into our MonthlySales list.
        # It's like adding more ingredients to the pot, cooking up a feast of sales data!
        MonthlySales.append(row)

# Alright, we're about to embark on a journey through our MonthlySales data.
# Get ready to buckle up 'cause we're gonna loop through each item in MonthlySales.
# And what's this "a" all about? Well, it's just our ride, cruising through the sales data, one row at a time.
for a in MonthlySales:
    # Hold onto your hats 'cause things are about to get printed!
    # We're printing out each row of our MonthlySales data like a boss.
    print(a)

import itertools

# Alright, hold onto your hats 'cause we're diving into another loop through our MonthlySales data.
# With the power of "pooh," we're ready to rock and roll!
for a in MonthlySales:
    # Get ready for some key insights!
    # We're printing out the keys of each dictionary in our MonthlySales data.
    # It's like peeking into the treasure chest to see what goodies we've got.
    print(a.keys())

# Oh, snap! We're diving into the depths of our MonthlySales data once again with the power of "pooh"!
for a in MonthlySales:
    # Hold onto your hats 'cause we're about to break it down!
    # We're cruising through each dictionary in our MonthlySales data, extracting both the key and value.
    # It's like we're detectives, unraveling the mysteries hidden in our sales records.
    for key, value in a.items():
        # Get ready for some revelations!
        # We're printing out the key-value pairs of each dictionary in our MonthlySales data.
        # It's like shining a spotlight on each clue, revealing the secrets within.
        print(key + ": ", value)
    
    # Whoa, pause for dramatic effect!
    # We're adding a little breathing room with a newline character '\n'.
    # Gotta keep things neat and tidy, like giving our data some space to shine.
    print('\n')
```

### Working with Parquet files
```python
# Oh, we're stepping up our game with some serious firepower!
# We're importing PyArrow's Parquet module like a boss.
import pyarrow.parquet as pq

# We're diving into the world of Parquet files with PyArrow!
# Hold onto your seats 'cause we're about to read in some serious data.

# So, what's the deal with pq.read_table()?
# Well, it's like opening up a treasure chest full of data!
# This function reads in a Parquet file and returns a Table object.
# Think of it as unpacking all the juicy information stored in our MonthlyProductSales.parquet file.

# Now, what in the world is a Parquet file?
# Picture this: Parquet files are like the superheroes of data storage.
# They're super efficient, compact, and lightning-fast when it comes to handling big data.
# Parquet files organize data in a columnar format, making them perfect for analytics and processing massive datasets.
# It's like having your data neatly stacked and labeled, ready to be sliced and diced for analysis.
# So when we say we're reading in a Parquet file, we're tapping into a goldmine of structured data!
table = pq.read_table('../MonthlyProductSales.parquet')

# Brace yourselves, 'cause we're about to unleash the power of PyArrow's Table object!
# Hold onto your hats as we convert our table into a dictionary.

# Alright, what's the scoop with table_dict = dict(table.to_pydict())?
# We're taking our table, loaded with all that juicy data, and transforming it into a dictionary.
# It's like taking a high-tech blueprint and translating it into a language we can all understand.
# Each column becomes a key, and its corresponding values are like the hidden treasures waiting to be discovered.
table_dict = dict(table.to_pydict())

# Brace yourselves, 'cause we're about to unleash the power of our table dictionary!
# This baby is packed with all the juicy data we've been working with.

# Alright, what's the deal with table_dict?
# Well, it's like having a treasure map to all the riches in our dataset.
# We've transformed our table into a dictionary, making it super easy to navigate and access specific data points.
# Each key holds the name of a column, while its corresponding value is a list containing all the data in that column.
# It's like having the keys to the kingdom, ready to unlock insights and discoveries!
table_dict

# Alright, buckle up 'cause we're about to dive into our treasure trove of data!
# We're gearing up to explore the items in our table dictionary.

# So, what's the scoop with items = table_dict.items()?
# We're turning our dictionary into a collection of key-value pairs.
# It's like organizing all our loot into neat little packages, ready for inspection.

# Now, what's inside 'items'?
# 'items' holds a view of all the key-value pairs in our dictionary.
# Each pair represents a column name (key) and its corresponding data (value).
# It's like having a backstage pass to all the juicy details of our dataset!
items = table_dict.items()
items

# Alright, picture this: our code is like a cozy house, and we're about to explore its nooks and crannies.
# We're gearing up to uncover the keys to different rooms in our humble abode.

# So, what's the deal with keys = [item[0] for item in items]?
# It's like we're wandering through each room of our house, peeking at the labels on the doors.
# With each room we visit, we jot down the room number (index 0) in our trusty notebook.
# It's like creating a master keyring that'll help us unlock all the doors in our house!

# Now, what's inside 'keys'?
# 'keys' holds a list containing all the room numbers, or in this case, column names, of our house.
# Each name is like a label on a door, telling us what we can expect to find inside.
# It's like having a blueprint of our house, guiding us through its many rooms and secrets!
keys = [item[0] for item in items]
keys

# Welcome to our cozy coding home! Get ready to explore the values stored within.

# Ah, the magic is at work!
# We're about to dive into our house of data and uncover the treasures hidden within.

# So, what's the deal with values = [item[1] for item in items]?
# It's like we're rummaging through the belongings in each room of our house.
# With each room we explore, we pick out the valuable items (index 1) and add them to our collection.
# It's like discovering hidden gems in every corner of our home!

# Now, what's inside 'values'?
# 'values' holds a list containing all the valuable items we've collected from our house of data.
# Each item is like a precious artifact, revealing insights and stories waiting to be told.
# It's like curating a museum exhibition, showcasing the richness and diversity of our data home!
values = [item[1] for item in items]
values

# Step into our coding sanctuary, where we're about to rearrange the furniture of our data.

# Alright, what's the deal with pivoted_values = zip(*values)?
# Imagine we're rearranging the layout of our rooms, shifting sofas and tables around.
# This line is like taking all the items in our rooms and giving them a new layout.
# It's like changing the setup in our living room to create a more open and inviting space.

# Now, what's inside 'pivoted_values'?
# 'pivoted_values' holds the transformed version of our data, much like rearranging our home.
# Each row is now a column, and each column is now a row, creating a fresh perspective.
# It's like moving furniture to see how different arrangements change the vibe of our home.
pivoted_values = zip(*values)
pivoted_values

# Step into our coding sanctuary, where we're about to rearrange the furniture of our data.

# Alright, what's the deal with pivoted_values = zip(*values)?
# Imagine we're rearranging the layout of our rooms, shifting sofas and tables around.
# Here, the zip() function is like our interior design assistant, helping us rearrange our data effortlessly.
# By using the * operator, we're unpacking our values list, effectively passing each row as a separate argument to the zip() function.
# It's like gathering all the furniture from each room and putting it in a neat stack, ready for the makeover.

# Now, what's inside 'pivoted_values'?
# 'pivoted_values' holds the transformed version of our data, much like rearranging our home.
# Each tuple in pivoted_values represents a new arrangement of our data, with elements from the same position in each row now grouped together.
# It's like redecorating our living room to create a fresh new vibe, where every piece of furniture has its place.
pivoted_values = zip(*values)
pivoted_values

# Step into our coding sanctuary, where we're about to whip up something special with our data.

# Ah, the magic is happening once again!
# We're diving into our transformed data and crafting a whole new masterpiece.

# So, what's the deal with table_dictionary_array = []?
# It's like setting up a brand new storage space in our home, ready to hold our freshly brewed creations.
# We're preparing an empty array to store dictionaries, each representing a unique record.

# Now, what's happening in the loop?
# We're like master chefs, working our magic on each record from our pivoted values.
# For each record, we're creating a new dictionary by zipping together the keys and values.
# It's like mixing together the perfect ingredients to create a delicious dish!

# Each dictionary we create represents a record in our dataset, with keys mapping to column names and values representing the data.
# It's like crafting individual pieces of art, each telling its own story within our data masterpiece.
table_dictionary_array = []
for record in pivoted_values:
    table_dictionary_array.append(dict(zip(keys, record)))

# Step into our coding sanctuary, where we're about to explore the records in our data masterpiece.

# Ah, the magic is happening once again!
# Imagine our array of table dictionaries as a cozy neighborhood full of unique homes.

# Now, let's unpack this for loop like we're taking a leisurely stroll through the neighborhood:
# We're like curious homeowners, stepping out of our front door to wander through the streets.
# For each record (or house) in our array of table dictionaries (our neighborhood),
# We're gently knocking on the door and inviting ourselves in to explore.

# Inside each home (record), we're greeted with warmth and familiarity.
# We take a tour, examining every room and corner, admiring the decor (data) and the memories it holds.

# As we step back out onto the street, we carry with us a deeper understanding of our neighborhood,
# enriched by the unique stories and experiences of each home (record) we've visited.

# It's like taking a leisurely stroll through our cozy neighborhood, where every home has its own charm and story to tell.
for record in table_dictionary_array:
    print(record)
```

### Read data from GitHub API
```python

```
