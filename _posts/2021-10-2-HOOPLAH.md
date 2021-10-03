---
layout: post
title: HOOPLAH
---


In this blog post, we will explore how to visual data using python.\
We will need to import numpy pandas and pyplot from matplotlib.\
\
The pandas package is great for summarizing, manipulating, visualizing and working with data in a table. It will take our data into a dataframe that should make calling needed data much simpler. I'm hoping you are already familiar with it but I'll explain the necessary functions for create visualizations.\
\
The pyplot package offers many different ways to visualize data including, standard plots, scatterplots, boxplots and more.


```python
import pandas as pd
from matplotlib import pyplot as plt
```

We are going to work with the Palmer Penguins data set. We are going to directly read it into a pandas dataframe.\
If you would like to learn more about the data set just follow the url used below.


```python
url = "https://raw.githubusercontent.com/PhilChodrow/PIC16B/master/datasets/palmer_penguins.csv"
penguins = pd.read_csv(url)
```

Let's familiarize ourselves a bit with the data by giving it a look.


```python
penguins
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>studyName</th>
      <th>Sample Number</th>
      <th>Species</th>
      <th>Region</th>
      <th>Island</th>
      <th>Stage</th>
      <th>Individual ID</th>
      <th>Clutch Completion</th>
      <th>Date Egg</th>
      <th>Culmen Length (mm)</th>
      <th>Culmen Depth (mm)</th>
      <th>Flipper Length (mm)</th>
      <th>Body Mass (g)</th>
      <th>Sex</th>
      <th>Delta 15 N (o/oo)</th>
      <th>Delta 13 C (o/oo)</th>
      <th>Comments</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>PAL0708</td>
      <td>1</td>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>Anvers</td>
      <td>Torgersen</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N1A1</td>
      <td>Yes</td>
      <td>11/11/07</td>
      <td>39.1</td>
      <td>18.7</td>
      <td>181.0</td>
      <td>3750.0</td>
      <td>MALE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Not enough blood for isotopes.</td>
    </tr>
    <tr>
      <th>1</th>
      <td>PAL0708</td>
      <td>2</td>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>Anvers</td>
      <td>Torgersen</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N1A2</td>
      <td>Yes</td>
      <td>11/11/07</td>
      <td>39.5</td>
      <td>17.4</td>
      <td>186.0</td>
      <td>3800.0</td>
      <td>FEMALE</td>
      <td>8.94956</td>
      <td>-24.69454</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PAL0708</td>
      <td>3</td>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>Anvers</td>
      <td>Torgersen</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N2A1</td>
      <td>Yes</td>
      <td>11/16/07</td>
      <td>40.3</td>
      <td>18.0</td>
      <td>195.0</td>
      <td>3250.0</td>
      <td>FEMALE</td>
      <td>8.36821</td>
      <td>-25.33302</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>PAL0708</td>
      <td>4</td>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>Anvers</td>
      <td>Torgersen</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N2A2</td>
      <td>Yes</td>
      <td>11/16/07</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Adult not sampled.</td>
    </tr>
    <tr>
      <th>4</th>
      <td>PAL0708</td>
      <td>5</td>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>Anvers</td>
      <td>Torgersen</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N3A1</td>
      <td>Yes</td>
      <td>11/16/07</td>
      <td>36.7</td>
      <td>19.3</td>
      <td>193.0</td>
      <td>3450.0</td>
      <td>FEMALE</td>
      <td>8.76651</td>
      <td>-25.32426</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>339</th>
      <td>PAL0910</td>
      <td>120</td>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>Anvers</td>
      <td>Biscoe</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N38A2</td>
      <td>No</td>
      <td>12/1/09</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>340</th>
      <td>PAL0910</td>
      <td>121</td>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>Anvers</td>
      <td>Biscoe</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N39A1</td>
      <td>Yes</td>
      <td>11/22/09</td>
      <td>46.8</td>
      <td>14.3</td>
      <td>215.0</td>
      <td>4850.0</td>
      <td>FEMALE</td>
      <td>8.41151</td>
      <td>-26.13832</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>341</th>
      <td>PAL0910</td>
      <td>122</td>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>Anvers</td>
      <td>Biscoe</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N39A2</td>
      <td>Yes</td>
      <td>11/22/09</td>
      <td>50.4</td>
      <td>15.7</td>
      <td>222.0</td>
      <td>5750.0</td>
      <td>MALE</td>
      <td>8.30166</td>
      <td>-26.04117</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>342</th>
      <td>PAL0910</td>
      <td>123</td>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>Anvers</td>
      <td>Biscoe</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N43A1</td>
      <td>Yes</td>
      <td>11/22/09</td>
      <td>45.2</td>
      <td>14.8</td>
      <td>212.0</td>
      <td>5200.0</td>
      <td>FEMALE</td>
      <td>8.24246</td>
      <td>-26.11969</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>343</th>
      <td>PAL0910</td>
      <td>124</td>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>Anvers</td>
      <td>Biscoe</td>
      <td>Adult, 1 Egg Stage</td>
      <td>N43A2</td>
      <td>Yes</td>
      <td>11/22/09</td>
      <td>49.9</td>
      <td>16.1</td>
      <td>213.0</td>
      <td>5400.0</td>
      <td>MALE</td>
      <td>8.36390</td>
      <td>-26.15531</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>344 rows × 17 columns</p>
</div>



Good stuff.\
Now let's take a look at how we could call a single column of our data.


```python
# we simply take at look at the name of the column, then make the following call
# penguins[["column name"]]
# For example, say I wanted to only see the Species column of my data frame then
# I'd run the following line
penguins[["Species"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>339</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
    </tr>
    <tr>
      <th>340</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
    </tr>
    <tr>
      <th>341</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
    </tr>
    <tr>
      <th>342</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
    </tr>
    <tr>
      <th>343</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
    </tr>
  </tbody>
</table>
<p>344 rows × 1 columns</p>
</div>




```python
# We can call multiple columns at the same time
# for example, say I want to call the "Species" and "Culmen Length (mm)" columns
penguins[["Species", "Culmen Length (mm)"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Species</th>
      <th>Culmen Length (mm)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>39.1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>39.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>40.3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adelie Penguin (Pygoscelis adeliae)</td>
      <td>36.7</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>339</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>340</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>46.8</td>
    </tr>
    <tr>
      <th>341</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>50.4</td>
    </tr>
    <tr>
      <th>342</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>45.2</td>
    </tr>
    <tr>
      <th>343</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>49.9</td>
    </tr>
  </tbody>
</table>
<p>344 rows × 2 columns</p>
</div>




```python
# Hopefully you're familiar with the concept of masks
# If not here is an example of utilizing masks to call specific subsets
# of our data frame
mask = penguins["Culmen Length (mm)"] > 54
penguins[["Species","Culmen Length (mm)"]][mask]
# As you can see below, the above two lines of code will display a dataframe
# with two columns, "Species" and "Culmen Length (mm)" which will only include
# the penguins whose culmen lengths are greater than 54 mm.
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Species</th>
      <th>Culmen Length (mm)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>169</th>
      <td>Chinstrap penguin (Pygoscelis antarctica)</td>
      <td>58.0</td>
    </tr>
    <tr>
      <th>183</th>
      <td>Chinstrap penguin (Pygoscelis antarctica)</td>
      <td>54.2</td>
    </tr>
    <tr>
      <th>215</th>
      <td>Chinstrap penguin (Pygoscelis antarctica)</td>
      <td>55.8</td>
    </tr>
    <tr>
      <th>253</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>59.6</td>
    </tr>
    <tr>
      <th>283</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>54.3</td>
    </tr>
    <tr>
      <th>321</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>55.9</td>
    </tr>
    <tr>
      <th>335</th>
      <td>Gentoo penguin (Pygoscelis papua)</td>
      <td>55.1</td>
    </tr>
  </tbody>
</table>
</div>



Okay, we can start visualizing our data using pyplots.\
We'll start with a simple boxplot.


```python
# To get started we need call the function plt.subplots(1).
# This function will create a single figure and a single axes
# So we will need two variable to hold this infomation
fig,ax = plt.subplots(1)

# Now we can easily create a boxplot of any of the numerical columns of our data
# Let's visualize the Body Mass (g) of the penguins in a boxplot as an example
# Unfortunately though, there is some invalid data in our penguins data frame
# We can using masking to ignore that data though!
mask = penguins["Body Mass (g)"].isna() == False
# The function .isna() returns True if an entry is NaN
# since we are only interested in entries that are not NaN, we want the entries
# which isna() will return False.

# Now we can make a box plot of the body mass of the penguins
ax.boxplot(penguins["Body Mass (g)"][mask])
# We use the .boxplot function on ax which is the axes we defined before.
```




    {'whiskers': [<matplotlib.lines.Line2D at 0x2145cb09c88>,
      <matplotlib.lines.Line2D at 0x2145e598448>],
     'caps': [<matplotlib.lines.Line2D at 0x2145cb099c8>,
      <matplotlib.lines.Line2D at 0x2145cb09a88>],
     'boxes': [<matplotlib.lines.Line2D at 0x2145c735848>],
     'medians': [<matplotlib.lines.Line2D at 0x2145cb09088>],
     'fliers': [<matplotlib.lines.Line2D at 0x2145cf4c108>],
     'means': []}




    
![png](output_11_1.png)
    


Neat! Except this figure is incomplete.\
It needs a little bit of love, perhaps a bit of care. I'd recommend doing so tenderly.\
It is missing some key elements to actually be useful.\
Let's explore that now.


```python
# We need a label for the y axis and maybe a title so that
# the figure can be interpreted.
# This is easily added using the .set function on our axes variable,
# We can even do it all in one line!
# Let's also remove the x axis since it serves no purpose for this plot
ax.set(ylabel = "Body Mass (g)", title = "Palmer Penguins", xticks = [])
# run the command fig to display the plot again
fig
```




    
![png](output_13_0.png)
    



Now that we have a complete figure. Let's expand on this and create something more complex.\
Say, we wanted to visualize the differences that may exist among each species of penguin.\
For instance I want to quickly have a visualizing of how each species differ when it comes to a certain attribute.\
Let's write a function that can handle this.\
The function will take as input a specific attribute and output a convenient visualization.


```python
# Before we start to write the function let's clean the data just a little bit.
# We're just gonna change the "Species" column by just shortening the names
# of the penguin species

penguins["Species"] = penguins["Species"].str.split().str.get(0)
```


```python
# We're going to use boxplots again.
# The function can be easily adapted to instead use histograms or even violin plots
# just replace .boplot with .hist or .violinplot

# This line will just change the font size of the labels and title of the plots.
plt.rcParams.update({'font.size': 15})

def penguin_boxplot(attribute):
    '''
    Creates 3 violin plots on a single row.
    There will be one violin plot for each species. The plots will share the same
    y-axis and will be displaying the distribution of the given attribute of each
    species
    '''
    # As before we will use plt.subplots command but this time we will specify
    # more inputs. We want our figure to have 3 plots all displayed on a single
    # row and we want them to share the same y-axis.
    # Also we will adjust the size of the figure by passing a tuple of integers
    fig, ax = plt.subplots(1,3,sharey = True, figsize = (14,6))
    # If you were to inspect ax, it is now a numpy array of length 3
    
    # We're going to give a title to the whole figure
    fig.suptitle("Boxplot of "+attribute+" for each species", fontsize=25)
    
    # We'll define a set of all the penguin species and iterate over it.
    species_set = set(penguins["Species"])
    # A mask to exclude any invalid data
    nan_mask = penguins[attribute].isna() == False
    
    ax[0].set(ylabel = attribute)
    # variable to help interate over each ax                   
    j = 0
    
    # This for loop will handle the plotting in much the same way as we did
    # in the example above, except this time we have more than one ax
    # We will plot one figure at a time
    for species in species_set:
        spec_mask = penguins["Species"] == species
        ax[j].boxplot(penguins[spec_mask & nan_mask][attribute])
        ax[j].set(title = species)
        ax[j].set_xticks([])
        j = j +1
    # This is a helpful function to tidy up the figure automatically
    fig.tight_layout()
```


```python
penguin_boxplot("Body Mass (g)")
```


    
![png](output_17_0.png)
    


One last task.\
We're going to create a scatter plot. I think it's different enough to warrant walking through it quickly.\
Our scatter plot will assign a different color for each species.\
We'll of course need a legend this time so that it can be read.


```python
# Let's make a scatter with flipper length on the x-axis and 
# body mass on the y-axis.

fig,ax = plt.subplots(1,figsize = (9,7))
flip_len = "Flipper Length (mm)"
BM = "Body Mass (g)"
ax.set(xlabel = flip_len,
      ylabel = BM,
      title = "Scatter plot of body mass and flipper length by species")
# Similarly to before, we will define a set consisting of the penguin species
species_set = set(penguins["Species"])
# We also will need to exclude invalid data in our data set
# We're gonna make a new data frame with only the columns we need
# Using the .dropna() function will remove any invalid data
penguin_scatter = penguins[["Species",flip_len,BM]].dropna()
# This loop will populate our plot, one species at a time
for species in species_set:
    spec_mask = penguin_scatter["Species"]==species
    # We define two variables, x and y, to hold the relevant information
    x = penguin_scatter[spec_mask][flip_len]
    y = penguin_scatter[spec_mask][BM]
    
    # Using ax.scatter, we can populate our figure with the correct data
    # Each species will be in a different color and we'll define the legend
    # at the same time
    # We are also going to set the opacity of each data point by setting
    # a value for alpha as follows
    ax.scatter(x,y,alpha = .4,label = species)

ax.legend()    
fig.tight_layout()
```


    
![png](output_19_0.png)
    

