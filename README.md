# Heatmap 1.1
orig author: jjguy
modified by: chucknthem
This is a fork of chucknthem itself being a fork of of heatmap by jjguy. 
https://github.com/chucknthem/heatmap

## Description
heatmap is a python library for creating heatmaps.

Works with gps coordinates and generates point sets for retrieving correctly adjusted static maps from GoogleMaps.

See Also: http://code.google.com/p/gheat/

## Installation

Either clone this git repo or download the source. Then install it as a normal python package:

    python setup.py install

## Modifications to the original:
 1. New and faster heatmap generating algorithm.
 2. Fixed an issue with points at the border of the heatmap being clipped.
 3. Allows generating a time sequenced kml file for visualising heatmaps over time.

### Generating a heat map for static googlemaps.

    hm = heatmap.Heatmap() 
    hm.plot(
      pointsets, 
      outputfile, 
      opacity=128, 
      size=(2048 ?, 2048 ?),
      scheme="classic") 

Most parameters are the same as the heatmap() function described below. The only difference is the 'pointset' parameter which is defined as follows:

    pointset = [(begin, end, [lat, lng]), (begin, end, [lat, lng]), ...]

This will generate  n = len(pointset) .png-files.

## Original documentation from http://jjguy.com/heatmap/

  heatmap() has only two required parameters:

    A list of two-element tuples
    The filename to save the resulting image
    There are several optional parameters, with reasonable defaults:
       |  heatmap(self, points, fout, dotsize=150, opacity=128, size=(1024, 1024), scheme='classic')
       |      points  -> an iteratable list of tuples, where the contents are the
       |                 x,y coordinates to plot. e.g., [(1, 1), (2, 2), (3, 3)]
       |      fout    -> output file for the PNG
       |      dotsize -> the size of a single coordinate in the output image in
       |                 pixels, default is 150px.  Tweak this parameter to adjust
       |                 the resulting heatmap.
       |      opacity -> the strength of a single coordiniate in the output image.
       |                 Tweak this parameter to adjust the resulting heatmap.
       |      size    -> tuple with the width, height in pixels of the output PNG
       |      scheme  -> Name of color scheme to use to color the output image.
       |                 Use schemes() to get list.  (images are in source distro)

## Examples from jjguy's website:

### Make a random heatmap:


    import heatmap
    import random

    if __name__ == "__main__":    
        pts = []
        for x in range(400):
            pts.append((random.random(), random.random() ))

        print "Processing %d points..." % len(pts)

        hm = heatmap.Heatmap()
        hm.heatmap(pts, "classic.png")

### Creating a heatmap for static googlemaps:

    import heatmap
    import random

    hm = heatmap.Heatmap()
    pts = [(random.uniform(-77.012, -77.050), random.uniform(38.888, 38.910)) for x in range(100)]
    hm.heatmap(pts, "classic.png")
    hm.saveKML("data.kml")


The original readme is below:
=============================================

Build heatmaps in python.  Requires the Python Imaging Library.

Minimal example in example.py.  Full readme at http://jjguy.com/heatmap/

