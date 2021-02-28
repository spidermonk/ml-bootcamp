Matplotlib

Most popular plotting library for python - similar to MatLab
Works well with pandas & numpy arrays
matplotlib.org -> gallery

import mapplotlib.pyplot as plt
%matplotlib inline or plt.show() to see plots inline (jupyter vs other pyton environments)

Create plots from numply arrays
function vs object oriented methods

plt.plot(x, y) -> x & y are numpy arrays
Can add other arguments for plot style - e.g. colors and line styles (same syntax as MatLib)

plt.xlabel('mylabel') - add X label (or ylabel or title)

Can create multi plots on the same canvas
plt.subplot(numRows, numCols, plotNum)
plt.plt(x, y, 'r')
1 - first command sets subplot to work on
plt.subplot(numRows, numCols, plotNum+1)
plt.plt(y, x, 'b') -> 'b' is for blue line

Object Oriented Method
fig = plt.figure() -> creates blank canvas
axes = fig.add_axes([left, bottom, height, width]) - % of canvas to use
axes.plot(x, y)
axes.set_xlabel, etc.
Add multiple axes to add subplots (e.g. axes1 = fig.add_axes)

fig, axes = plt.subplots(nrows, ncols) - creates figure with 2 columns - calling add_axes for us
axes.plots(x,y)
axes will be an array if subplots
axes[0].plot(x, y)

plt.tight_layout() -> fixes overlapping plots

Figure Size & DPI
fig = plt.figure(figsize=(width, height), dpi=300) -> dimensions are in inches

fig.savefig('filename.png') -> saves to format of extension, can specify dpi too

Legends
axes.legend() - can specify optional loc to set location of legend using code or tuple - 0 is best
add label to plot calls
axes.plot(x, y, 'Label')
axes.plot(y, x, 'Label 2')

Color
axes.plot(x, y, color)
Basic color names
RGB hex codes

linewidth (or lw) - float
alpha - for transparency
linestyle (or ls) = (codes) - '--' or '-.' or 'steps'
marker='o' - for diff marker symbols, 'o' for dots
markersize
markerfacecolor
markeredgecolor
markeredgewidth

Axes & Plot Range
axes_set_xlim([lbound, ubound])

Special plot types
Use Seaborn but matplotlib supports
plt.scatter or plt.hist or plt.box

Tutorial: http://www.lora.fr/~rougier/teaching/matplotlib
