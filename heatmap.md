# Chart: Heatmap {#heatmap}

<!-- Chapter Banner -->
![](images/banners/banner_heatmap.png)


<!-- Under Construction Section
----------------------------------------------------------------------------- -->
![Under Construction](images/banners/banner_under_construction.png)
*This page is a work in progress. We appreciate any input you may have. If you would like to help improve this page, consider [contributing to our repo](contribute.html).*
<!-- ------------------------------------------------------------------------ -->

## Overview

This section covers how to make heatmaps.

## tl;dr

[Coming soon <i class="far fa-smile-beam"></i>](https://www.youtube.com/watch?v=7kdV8VmD76w){target="_blank"}

## Simple examples

Too complicated! [Simplify, man!](https://www.youtube.com/watch?v=PlsW2hd06R0){target="_blank"}

For these heat maps, we will use the `SpeedSki` dataset.

### Heat map of two-dimensional bin counts

Only two variables, `x` and `y` are needed for two-dimensional bin count heat maps. The third variable--i.e., the color--represents the bin count of points in the region it covers. Think of it as a two-dimensional histogram.

To create a heat map, simply substitute `geom_point()` with `geom_bin2d()`:

```r
library(ggplot2) # plotting 
library(GDAdata) # data (SpeedSki)

ggplot(SpeedSki, aes(Year, Speed)) + 
  geom_bin2d()
```

<img src="heatmap_files/figure-html/heat-map-default-1.png" width="672" />

### Modifications

You can change the color palette by specifying it explicitly in your chain of `ggplot` function calls. The bin width can be added inside the `geom_bin2d()` function call:

```r
library(viridis) # viridis color palette

# create plot
g1 <- ggplot(SpeedSki, aes(Year, Speed)) + 
  scale_fill_viridis() # modify color

# show plot
g1 + geom_bin2d(binwidth = c(5, 5)) # modify bin width
```

<img src="heatmap_files/figure-html/heat-map-color-bin-width-1.png" width="672" />

Here are some other examples:

```r
# larger bin width
g1 + geom_bin2d(binwidth = c(10, 10)) 
```

<img src="heatmap_files/figure-html/unnamed-chunk-1-1.png" width="672" />


```r
# hexagonal bins
g1 + geom_hex(binwidth = c(5, 5))
```

<img src="heatmap_files/figure-html/unnamed-chunk-2-1.png" width="672" />


```r
# hexagonal bins + scatterplot layer
g1 + geom_hex(binwidth = c(5, 5), alpha = .4) + 
  geom_point(size = 2, alpha = 0.8)
```

<img src="heatmap_files/figure-html/unnamed-chunk-3-1.png" width="672" />


```r
# hexagonal bins with custom color gradient/bin count
ggplot(SpeedSki, aes(Year, Speed)) + 
  scale_fill_gradient(low = "#cccccc", high = "#09005F") + # color
  geom_hex(bins = 10) # number of bins horizontally/vertically
```

<img src="heatmap_files/figure-html/unnamed-chunk-4-1.png" width="672" />

## Theory

Heat maps are like a combination of [scatterplots](scatter.html) and [histograms](histo.html): they allow you to compare different parameters while also seeing their relative distributions.

*   While heatmaps are visually striking, there are often better choices to get your point across. For more info, checkout this [DataCamp section on heatmaps and alternatives](https://campus.datacamp.com/courses/data-visualization-with-ggplot2-2/chapter-4-best-practices?ex=10){target="_blank"}.

## External resources
- [R Graph Gallery: Heatmaps](https://www.r-graph-gallery.com/heatmap/){target="_blank"}: Has examples of creating heatmaps with the `heatmap()` function.
- [How to make a simple heatmap in ggplot2](https://www.r-bloggers.com/how-to-make-a-simple-heatmap-in-ggplot2/){target="_blank"}: Create a heatmap with `geom_tile()`.













