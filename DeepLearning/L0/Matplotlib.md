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
