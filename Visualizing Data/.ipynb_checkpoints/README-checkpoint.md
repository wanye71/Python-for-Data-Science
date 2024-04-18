# Python for Data Science - Visualizing Data


## Table of Contents

1. [Small multiples with ggplot](#basic-charts-in-ggplot)
2. [Small multiples with ggplot](#small-multiples-with-ggplot)
3. [Small multiples with ggplot + seabord](#small-multiples-with-ggplot--seabord)
4. [Finish your plots](#finish-your-plots)

### Basic charts in ggplot
```python
#!pip install --upgrade ggplot

# Yo, yo, yo! Get ready to dive into the world of data visualization like a boss!

# First things first, we're setting the stage for some epic visualizations by importing our weapons of choice.
# We're bringing in the 'matplotlib' library and telling it to work its magic inline, right here in our coding playground.
# It's like summoning a magician to perform tricks right before our eyes!
%matplotlib inline

# But wait, there's more! We're not stopping there. We're taking it up a notch with the 'ggplot' library.
# This bad boy is like the Picasso of data visualization, turning our data into beautiful masterpieces.
# We're importing all its powers with a single line of code, ready to unleash its full potential.
from ggplot import *  # Time to paint with all the colors of the data rainbow!

# And last but not least, we're enlisting the help of our trusty sidekicks, 'pandas' and 'numpy'.
# These dynamic duos are like the Batman and Robin of the coding world, always ready to swoop in and save the day.
import pandas as pd  # Our data wrangling wizard, turning messy datasets into clean, organized treasures.
import numpy as np  # The silent powerhouse, crunching numbers behind the scenes like a ninja in the shadows.


# Alright, hold onto your hats, folks, 'cause we're about to take a peek at the shiny world of diamonds!

# First things first, let's set the stage. Our diamond dataset comes from the 'ggplot' library, a treasure trove of data goodies.
# It's like stumbling upon a hidden cave filled with diamonds, just waiting to be discovered.
# The 'diamonds' dataset is one of the gems in this collection, containing a wealth of information about these precious stones.
# Think of it as our ticket to a dazzling journey through the world of data visualization.


# Now that we've got our hands on this sparkling dataset, let's dive right in and see what it's all about.
# We're summoning the power of the 'head' function to get a sneak peek at the first few rows of our diamond dataset.
# It's like flipping through the pages of a treasure map, getting a taste of the riches that lie ahead.
diamonds.head()  # Let's shine a light on these diamonds and see what sparkles we uncover!


# Alright, hold onto your hats, folks, 'cause we're about to take a dive into the sparkling world of diamonds!

# First things first, let's set the stage. Our diamond dataset comes from the 'ggplot' library, a treasure trove of data goodies.
# It's like stumbling upon a hidden cave filled with diamonds, just waiting to be discovered.
# The 'diamonds' dataset is one of the gems in this collection, containing a wealth of information about these precious stones.
# Think of it as our ticket to a dazzling journey through the world of data visualization.

# Now that we've got our hands on this sparkling dataset, let's dive right in and see what it's all about.
# We're summoning the power of the 'tail' function to take a peek at the last few rows of our diamond dataset.
# It's like exploring the depths of an ocean, searching for hidden treasures waiting to be discovered.
diamonds.tail()  # Let's see what secrets lie at the bottom of this diamond mine!


# Alright, buckle up, fam, 'cause we're about to size up this diamond dataset like pros!

# First things first, let's get a sense of how big our dataset is. We're calling on the 'len' function to count the number of rows in our diamond dataset.
# It's like sizing up the loot after a successful heist, getting a feel for the magnitude of our treasure haul.
data_size = len(diamonds)  # Time to see just how many diamonds are sparkling in our dataset!

# And there you have it! With a single line of code, we've uncovered the size of our diamond dataset.
# It's like measuring the depth of a treasure chest, revealing the vast riches that lie within.
data_size  # Let's see just how big this diamond mine really is!

# Alright, fam, buckle up for a visual extravaganza! We're about to plot some serious bling!

# First things first, we're summoning the mighty 'qplot' function to create a quick plot of our diamond dataset.
# We're setting the 'price' column as the x-axis, so get ready for a rollercoaster ride through the price spectrum!
# It's like charting the rise and fall of stock prices, except we're dealing with the value of diamonds.
qplot(x='price', data=diamonds)  # Time to see just how much sparkle we can pack into a single plot!

# Alright, fam, it's time to shake things up with a bar chart showdown! Get ready to see some serious bling in action!

# First things first, we're summoning the mighty 'qplot' function to create a quick plot of our diamond dataset.
# This time, we're setting the 'cut' column as the x-axis and the 'price' column as the y-axis.
# It's like throwing a diamond-themed party and inviting all the different cuts to show off their price tags!
# And since we're dealing with bars, it's gonna be a showdown of epic proportions!
qplot(x='cut', y='price', data=diamonds, geom='bar')  # Get ready to witness the clash of the diamond cuts!


qplot(x='price',y='carat', data=diamonds, geom='line')

# Yo, check it!

# We're bringing in the 'warnings' library to keep things in check. We ain't playin' around when it comes to keepin' our code clean!
# It's like having a bouncer at the door, makin' sure only the VIPs get in.

import warnings  # Time to put those warning signs on notice!

# And here's where the magic happens: we're tellin' Python to ignore any UserWarnings that come our way.
# Ain't nobody got time for distractions when we're on a mission!
# It's like flickin' away annoying bugs that try to mess with our flow.

warnings.filterwarnings("ignore", category=UserWarning)  # Consider those UserWarnings officially on mute! We're keepin' it smooth and steady.


# Aight, squad, get ready for a visual feast with a side of urban flair! We're about to turn up the heat on this plot!

# We're summoning the mighty 'qplot' function to whip up a quick plot of our diamond dataset.
# This time, we're setting the 'price' column as the x-axis and the 'carat' column as the y-axis.
# But wait, there's more! We're adding a touch of chaos with the 'jitter' geometry, spreading those points like confetti at a party!
# And to make things pop, we're coloring each point based on the 'cut' of the diamond, adding a splash of flavor to our plot!
qplot(x='price', y='carat', data=diamonds, geom='jitter', color='cut') # Get ready to see diamonds shine in technicolor!


# Yo, check it out!

# We're diving deep into the world of data visualization with the 'ggplot' library. It's like a paintbrush in the hands of a master artist!
# We're summoning the 'diamonds' dataset to the stage, ready to unleash its secrets with style.

ggplot(diamonds, aes(x='price', color='clarity')) + \  
    geom_density()  # Get ready to ride the data waves with a density plot!
```

### Small multiples with ggplot + seabord
```python
# Aight, let's kick things off in style!

# We're summoning the 'ggplot' library to the stage. Get ready for some serious data magic!
from ggplot import *

# But wait, there's more! We're bringing in some backup dancers with 'seaborn' and 'matplotlib.pyplot'.
# It's like assembling the dream team of data visualization, ready to take the world by storm!
import seaborn as sns  # Time to add some spice to our plots!
import matplotlib.pyplot as plt  # Get ready to paint the town red with stunning visualizations!

# And don't forget our trusty sidekicks, 'pandas' and 'numpy'. These bad boys are the backbone of our data adventures.
import pandas as pd  # Our data wrangling wizard, turning messy datasets into organized treasures.
import numpy as np  # The silent powerhouse, crunching numbers behind the scenes like a ninja in the shadows.

# Last but not least, we're settin' the stage for some inline magic with '%matplotlib inline'.
# It's like having a front-row seat to the data spectacle, right here in our coding playground!

# Get ready to witness the magic of data visualization come to life!
%matplotlib inline  


# Aight, let's cook up some visual goodness real quick!

# We're summoning the mighty 'qplot' function to whip up a quick plot of our diamond dataset.
# This bad boy is like a magic wand, turning our data into visual gold in the blink of an eye!

qplot(x='price', data=diamonds)  # Get ready to witness the sparkle of diamond prices in all their glory!


# Alright, fam, it's time to level up our plot game with some Facets (trellis) action!

# We're summoning the mighty 'qplot' function to whip up a quick plot of our diamond dataset.
# But hold onto your hats 'cause we're takin' it up a notch with the 'facet_wrap' command.
# It's like splittin' our plot into multiple mini-plots, each one tellin' its own story!

qplot(x='price', data=diamonds) + facet_wrap(x='clarity', y='cut')  # Get ready to dive deep into the world of diamond clarity and cut!


# Yo, check it out, we're takin' this plot to the next level with some grid organization!

# We're summoning the mighty 'qplot' function to whip up a quick plot of our diamond dataset.
# But hold onto your hats 'cause we're steppin' up our game with the 'facet_grid' command.
# It's like layin' out our plots in a neat grid, each one fit snug as a diamond in a ring!

qplot(x='price', data=diamonds) + facet_grid(x='clarity', y='cut')  # Get ready to explore the diamond world in an organized grid!


# Yo, yo, yo! Time to check out Anscombe's Quartet, a legendary dataset in the world of statistics!

# We're summoning the 'pd' library to the stage, ready to unleash its data-wrangling powers.
# It's like calling in the big guns to handle our data with finesse!

import pandas as pd  # Get ready to dive deep into the world of Anscombe's Quartet!

# Now, let's load up the dataset. We're using the 'read_csv' function to read in the CSV file.
# And with a flick of the wrist, we're setting the header and index columns to make sense of the data.
# It's like cracking open a treasure chest and unveiling the hidden gems inside!

aq = pd.read_csv('../anscombes-quartet-hier.csv', header=[0,1], index_col=[0])  # Get ready to unravel the mysteries of Anscombe's Quartet!


# Aight, let's crunch some numbers and break down Anscombe's Quartet like bosses!

# First up, we're summoning the 'mean' function to calculate the mean of each column in our dataset.
# It's like finding the average vibe of each quartet, giving us a taste of the overall rhythm!

aq.mean()  # Get ready to groove to the mean beat of Anscombe's Quartet!

# Now, we're dialing it up a notch with the 'var' function to calculate the variance of each column.
# It's like measuring the spread of vibes within each quartet, revealing the diversity of their sound!

aq.var()  # Get ready to vibe with the variance of Anscombe's Quartet!


# Aight, let's dive into the groove of Anscombe's Quartet with a fresh dataset!

# We're summoning the 'pd' library to the stage, ready to unleash its data-wrangling powers.
# It's like calling in the big guns to handle our data with finesse!

import pandas as pd  # Get ready to vibe with Anscombe's Quartet!

# Now, let's load up the dataset. We're using the 'read_csv' function to read in the CSV file.
# And with a flick of the wrist, we're setting the header and index columns to make sense of the data.
# It's like tuning in to the rhythm of Anscombe's Quartet, ready to groove to its beats!

df = pd.read_csv('../anscombes-quartet.csv', header=0, index_col=0)  # Get ready to unravel the mysteries of Anscombe's Quartet!


# Aight, let's set the stage for a FacetGrid showdown with Anscombe's Quartet!

# We're summoning the 'sns' library to the stage, ready to unleash its plotting powers.
# It's like calling in the artist to paint a masterpiece with our data!

import seaborn as sns  # Get ready to vibe with Anscombe's Quartet!

# Now, let's create the FacetGrid. We're setting the 'hue' to differentiate groups and arranging the subplots in 2 columns.
# It's like setting up the stage for a concert, with each subplot ready to jam to its own beat!

g = sns.FacetGrid(df, hue="group", col='group')  # Get ready for a grid of grooves with Anscombe's Quartet!

# Now, we're mapping the scatterplot function to each subplot.
# It's like setting up the instruments for each band to rock out on stage!

g.map(sns.scatterplot, "x", "y")  # Get ready to vibe with scatterplots of Anscombe's Quartet!

# And last but not least, we're setting the plotting context to add some extra flavor to our plot.
# It's like setting the mood lighting for the concert, creating the perfect ambiance for the vibe!

sns.plotting_context();  # Get ready to immerse yourself in the vibe of Anscombe's Quartet!

```

### Styling plots in ggplot
```python

```

### Finish your plots
```python

```


