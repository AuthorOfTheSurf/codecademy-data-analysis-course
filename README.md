## Python Cheatsheet
### For the Codecademy 10-week Data Analysis Course

Here is the [matplotlib cheat-sheet](https://s3.amazonaws.com/codecademy-content/courses/matplotlib/data_vis_matplotlib_cheatsheet_v1_revisons.pdf) provided by the course

# Figure (area where one or more charts are plotted)
```py
# Define the "figure") by using the `figsize` parameter and giving it a tuple
# with width and height: `plt.figure(figsize=(x_width_inches, y_width_inches))
plt.figure(figsize=(10,8))
```

# Axes Object
```py
# You can get a reference to the Axis object via calling plt.subplot()
# This is a little unintuitive if you are only plotting one barchart
ax = plt.subplot()

# We have seen the axis object mainly used for its `set_` methods so far
# when creating a bar chart
ax.set_xticks(tick_indexes)
ax.set_xticklabels(drinks, rotation=-30)
```

# Chart title & labelling Axes
```py
plt.title('Final Exam Averages')
plt.ylabel('Test average')
plt.xlabel('Year')
```

# Saving a created figure 
```py
# This will destroy a file with the same name if one exists!!!
plt.savefig('my_bar_chart.png')
```

# Bar Charts
```py
# Plots y vs. x in a Bar Chart
plt.bar(x, y)

# range(len(sales)) is a nice trick to get x values to plot vs. your y values
sales =  [91, 76, 56, 66, 52, 27]
plt.bar(range(len(sales)), sales)

# Side-by-side Barcharts
# It turns out that the x values in a bar chart are used to state *where* to
# place the bars. This fact allows us to plot two sets of data next to each
# other by shifting one set, and maintaining nice spacing
#Paste the x_values code here
# China Data (blue bars)
n = 1   # This is our first dataset (out of 2)
t = 2   # Number of datasets
d = 6   # Number of sets of bars
w = 0.8 # Width of each bar
store1_x = [t*element + w*n for element
             in range(d)]
n = 2 # only change values that need changing
store2_x = [t*element + w*n for element
             in range(d)]
plt.bar(store1_x, sales1)
plt.bar(store2_x, sales2)

# You can plot a stacked bar chart by plotting the first set of data (bottom-most)
# then plotting a second set of data and specifying the first set with the
# `bottom` parameter
plt.bar(x_values, sales1,
        label="Location 1")
plt.bar(x_values, sales2,
        bottom=sales1,
        label="Location 2")
# The easiest way to add a legend to a bar chart is by using the `label` parameter,
# then calling plt.legend()
plt.legend()

# Add error bars to your bar chart using the `yerr` parameter to specify a same-length
# list of error values, and the `captize` parameter to draw horizontal lines at the
# terminal ends of the error bars
plt.bar(range(len(ounces_of_milk)), ounces_of_milk,
        yerr=error,
        capsize=5)
```

# Line Charts
```py
# List comprehensions can be used to creates lists that are based on lists
# The first part of a list comprehension is what you want the values to look like,
# the second part is where you refer to original list
y_lower = [i - 0.1 * i for i in revenue]
y_upper = [i + 0.1 * i for i in revenue]

# To display an area of uncertainty on a line chart, use the `plt.fill_between` method
# to plot the area of uncertainty in addition to the data line
plt.plot(months, revenue)
plt.fill_between(months, y_lower, y_upper, alpha=0.2)
```

# Pie Charts
```py
# Creating a pie chart is simple as pie!
# This is frequently paired with `plt.axis('equal')` to produce a perfect circle
plt.pie(payment_method_freqs)
plt.axis('equal')

# Add named and percentage labels using the `labels` and `autopct` parameters
# ".1f%" in the format string specifies that the percentage values should be
# displayed to one decimal-place accuracy and with a "%" sign.
plt.pie(payment_method_freqs,
        labels=payment_method_names,
        autopct='%0.1f%%')
# `plt.legend(...)` is used to display a legend on a pie chart
plt.legend(payment_method_names)
plt.axis('equal')
```

# Format Strings
```py
# Format string specify how numeric values should be displayed as text
ROUNDED_TO_NEAREST_INTEGER = "%d%%" # 10%
TWO_SIG_FIGS = "%0.2f%%"            # 2.36%
```

# Histograms
```py
# Create a histogram with `plt.hist(...)`, specify the number of bins with the
# `bins` parameter
plt.hist(sales_times, bins=20)

# You can plot multiple histograms on top of one another by calling `plt.hist`
# again. The `alpha` parameter can be used to adjust transparency to make
# comparison easier. If the two data sets have differing amounts of value, the
# `normed` parameter can be used to normalize the data and better-compare how
# the data sets are distributed
plt.hist(sales_times1, bins=20, alpha=0.4, normed=True)
plt.hist(sales_times2, bins=20, alpha=0.4, normed=True)
```

# List Comprehensions
```py
# List comprehensions can be used to transform one list into another without error
# by defining how the output list should look
temperatures = [-5, 29, 26, -7, 1, 18, 12, 31]
temperatures_adjusted = [temp + 20 for temp in temperatures]

# `zip` can be used to create a list of tuples, this list
zip([1, 2, 3], [4, 6, 8])
# yields [(1, 4), (2, 6), (3, 8)]... `(1, 4)` is a tuple with first value `1` and second value `2`

# Here is a simple example of adding similar-indexed values in two lists
[a + b for a,b in zip([1, 2, 3], [4, 6, 8])]
# yields [5, 8, 11]
```
