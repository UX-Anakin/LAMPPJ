# Matplotlib
Matplotlib is a data visulization module,Matplotlib is capable of creating most kinds of charts, like line graphs, scatter plots, bar charts, pie charts, stack plot, 3D graphs, and geographic map graphs.
```
import matplotlib.pyplot as plt
plt.plot([1,2,3], [5,7,4]) # pyplot to plot some coordinates.This means,we have 3 coordinates accodring to these lists: 1,5, 2,7 and 3,4.
# The plt.plot will draw this plot in the background,after graphing everything we intend to 
plt.show()
# window is a matplotlib window,which allows us to see our graph, as well as interact with it and navigate it.
```

**Home Button**: Will help you once you have begun navigating your chart.
**Forward/Back buttons**: You can click these to move back to the previous point you were at, or forward again.
**Pan Axis** : This cross-looking button allows you to click it, and then click and drag your graph around.
**Zoom**: The zoom button lets you click on it, then click and drag a square that you would like to zoom into specifically.Zooming in will require a left click and drag. You can alternatively zoom out with a right click and drag.
**Configure Subplots**: This button allows you to configure various spacing options with your figure and plot.Each of those blue bars is a slider, which allows you to adjust the padding.Some of these wont do anything right now.The wspace and hspace correspond to when you have multiple subplots,and this will act like "spacing" or "padding" between them.
**Save Figure**: This button will allow you to save your figure in various forms.

### Legends, Titles, and Labels with Matplotlib
```
import matplotlib.pyplot as plt
x = [1,2,3]
y = [5,7,4]

x2 = [1,2,3]
y2 = [10,14,12]

plt.plot(x,y, label='First Line')
plt.plot(x2,y2, label='Second Line')

# plt.xlabel, plt.ylabel 
plt.xlabel('Plot Number')
plt.ylabel('Important var')

plt.title('Interesting Graph\nCheck it out')
plt.legend()
plt.show()
```
### Bar Charts and Histograms with Matplotlib
```
import matplotlib.pyplot as plt
plt.bar([1,3,5,7,9],[5,2,7,8,2], label="Example One", color='b') # creates the bar chart for us.
plt.bar([2,4,6,8,10],[8,6,2,5,6], label="Example two", color='g')
plt.legend()
plt.xlabel('bar number')
plt.ylabel('bar height')
plt.title('Epic Graph\nAnother Line! Whoa')
plt.show()
```
The plt.bar creates the bar chart for us.
```
import matplotlib.pyplot as plt
population_ages = [22,55,62,45,21,22,34,42,42,4,99,102,110,120,121,122,130,111,115,112,80,75,65,54,44,43,42,48]
bins = [0,10,20,30,40,50,60,70,80,90,100,110,120,130]
plt.hist(population_ages, bins, histtype='bar', rwidth=0.8)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Interesting Graph\nCheck it out')
plt.legend()
plt.show()
```
For plt.hist, you first put in all of the values,then you specify into what "bins" or containers you will place the data into.In our case,we are plotting a bunch of ages,and we want to display them in terms of increments of 10 years.we give the bars a width of 0.8, but you can choose something else if you want to make the bars thicker, or thinner.

### Scatter Plots with Matplotlib
Cover scatter plots! The idea of scatter plots is usually to compare two variables, or three if you are plotting in 3 diemnsions, looking for correlation or groups.
```
import matplotlib.pyplot as plt
x = [1,2,3,4,5,6,7,8]
y = [5,2,4,2,1,4,5,2]
plt.scatter(x,y, label='skitscat', color='k', s=25, marker="o")
plt.xlabel('x')
plt.ylabel('y')
plt.title('Interesting Graph\nCheck it out')
plt.legend()
plt.show()
```
The plt.scatter allows us to not only plot on x and y, but it also lets us decide on the color,size,and type of marker we use.There are a bunch of marker options,see the [Matplotlib Marker Documentation](http://matplotlib.org/api/markers_api.html)for all of your choices.

### Stack Plots with Matplotlib
stack plots, the idea of stack plots is to show "parts to the whole" over time. A stack plot is basically like a pie-chart, only over time.
```
'''
Let's consider a situation where we have 24 hours in a day,and we'd like to see how we're spending our time.We'll divide our activities into:Sleeping,eating,working,and playing.
We're going to assume that we're trakcing this over the course of 5 days,so our starting data will look like:
'''
import matplotlib.pyplot as plt

days = [1,2,3,4,5]

sleeping = [7,8,6,11,7]
eating =   [2,3,4,3,2]
working =  [7,8,7,2,2]
playing =  [8,5,7,8,13]

plt.plot([],[],color='m', label='Sleeping', linewidth=5)
plt.plot([],[],color='c', label='Eating', linewidth=5)
plt.plot([],[],color='r', label='Working', linewidth=5)
plt.plot([],[],color='k', label='Playing', linewidth=5)

'''
"x" axis will consist of the days variable,Then,our consituents for the days are held in their respective activities
'''
plt.stackplot(days, sleeping, eating, working, playing, colors=['m','c','r','k'])

plt.xlabel('x')
plt.ylabel('y')
plt.title('Interesting Graph\nCheck it out')
plt.show()
```

### Pie Charts with Matplotlib
Pie charts are a lot like the stack plots, only they are for a certain point in time.Typically, a Pie Chart is sued to show parts to the whole, and often a % share.Luckily for us, Matplotlib handles the sizes of the slices and eveything, we just feed it the numbers.
```
import matplotlib.pyplot as plt

slices = [7,2,2,13]
activities = ['sleeping','eating','working','playing']
cols = ['c','m','r','b']

plt.pie(slices,
        labels=activities,
        colors=cols,
        startangle=90,
        shadow= True,
        explode=(0,0.1,0,0),
        autopct='%1.1f%%')

plt.title('Interesting Graph\nCheck it out')
plt.show()
```
Within the plt.pie, we specify the "slices",which are the relevant sizes for each part.Then,we specify the color list for the corresponding slices.Next, we can optionally specify the "Start angle" for the graph.Next, we can optionally add a shadow to the plot for a bit of character, and then we can even use "explode" to pull out a slice a bit.
Finally, we do autopct to optionaly overlay the percentages on the graph itself.

