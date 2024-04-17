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

```

### Read data from GitHub API
```python

```
