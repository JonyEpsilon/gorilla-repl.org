---
layout: page
title: Plotting
---

This page is as close as currently exists to reference documentation for gorilla-plot. You might like to first look at
the [getting started](/start.html) page that has some more usage oriented information about the plot library.

## Plot functions

All of these functions are in the `gorilla-plot.core` namespace.

### list-plot

A function for plotting a list of data, used `(list-plot data & options)`. The data can be a sequence of y-values, in
which case the x-values will be assumed to run across the integers starting at zero, or a sequence of `[x y]` pairs.
Note that to plot multiple series on the same chart you should `compose` several list-plots (see below). The options
accepted are:

- `:joined` : whether the points should be shown as discrete circles, or a line joining the points. Default `false`.
- `:plot-size` : the width of the plot in pixels. Default 400. 
- `:aspect-ratio` : the ratio of the width to the height of the plot. Defaults to the golden ratio.
- `:colour` : the colour of the plot points/line. Can be anything a web-browser understands. Defaults to `"steelblue"`
if joined is `false` and `"#FF29D2"` if the plot is joined.
- `:color` : as above, for those who don't write British English.
- `:plot-range` : the range that the plot should display. Given as a pair of pairs of values `[[xmin xmax] [ymin ymax]]`.
Either pair of values can be replaced with `:all` to display the full range of the data i.e. `[[1 5] :all]`. Defaults to
`[:all :all]`.
- `:symbol-size` : the size of the symbols in mysterious units, when joined is `false`. Defaults to 70.  
- `:opacity` : the opacity of the plot points/line. Defaults to 1.

### plot

A function for plotting functions, used `(plot my-func [xmin xmax] & options)`. Takes the same options as `list-plot`, 
apart from `:joined` which is always effectively `true`. Also takes the additional option:

- `:plot-points` : determines how many points will be used to sample the function for plotting. Sampling is done with
uniform spacing over the plot range. Defaults to 100.

### bar-chart

A function for plotting categorical data, used `(bar-chart categories values & options)`, where categories is a list of
category labels and values are the values for those categories. Takes the following options, which have the same 
meaning as for `list-plot`, `:plot-size`, `:aspect-ratio`, `:colour`, `:color`, `:plot-range`, `:opacity`. Note that
bar-charts do not compose well with list-plots and plots, as their x-axis is categorical, not continuous. It's possible
that instead you can use `histogram`, which does compose with continuous-axes charts.

### histogram

Plots a histogram of the data, used `(histogram data & options)`. Data should be a list of numbers. Takes options
`:plot-range`, `:plot-size`, `:aspect-ratio`, `:colour`, `:color`, `:opacity` which have the same meaning as above,
plus:

- `:bins` : the number of bins to divide the data in to. Defaults to using the Sturges rule to calculate the number of
bins.
- `:normalize` : determines the scaling of the bar heights. Options are `:probability` which shows the probability of
landing in the bin, `:probability-density` which gives a histogram that approximates the PDF of the distribution, and
`:count` which gives the number of items landing in the bin. Defaults to `:count`.
- `:normalise` : a variant spelling of the above.
- `:fill-opacity` : the opacity of the filled portion of the histogram, below the line. Defaults to 0.4. 

### compose

Compose is used to show several plots on the same axes. It can be used to produce plots with multiple data series, or
to compare line/point plots with histograms. It is used `(compose & plots)` where plots are one or more of the values
returned by the above plotting functions. As noted above, bar-charts do not compose well with other plot types.