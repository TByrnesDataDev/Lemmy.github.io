---
layout: post
title: Building Brisbane Elevations' from a Point Cloud
---

IT is extremely handy to have accurate heights for buildings when building 3 dimensional models of urban and suburban areas. It is unfortunate that not all areas have them readily available, or they may be behind a paywall. This post describes how you can use LIDAR values, or a point cloud, to approximate building heights.

This post just focusses on the buildings, but a future post will try to make the model a bit better with respect to roads and the satellite imagery of the area. 

<!-- more -->


<h3>Step 1. LIDAR Point Data</h3>

I retrieved the LIDAR Point dataset from http://elevation.fsdf.org.au/ , a organisation which provides Elevation and Depth spatial data for Australia. If you're not in Australia, try USGS Earth Explorer, Open Topography or your governments data portal. 

<< insert image of data seection from ELVIS>>

 Inner Brisbane City, approximately the area above, came to ~60Mb. A larger area could easily balloon to a few Gbs, so keep that in mind if you have internet or computing constraints.

#if possible, also retrieve the DEM layer for the same area. This can be useful as a 'basemap' of sorts, especially if the LIDAR is being used purely to estimate building heights as I've done here.

<h3>Step 2. Merge the LIDAR files </h3>
In my case these LIDARA images came in many separate zip files. Fortunately QGIS has a tool for merging point files called <a href = "https://rapidlasso.com/2013/09/29/how-to-install-lastools-toolbox-in-qgis/.">LAStools</a>.

Open QGIS and open the Processing Toolbox.

THis opens a sidebar which includes 'Tools for LiDAR data'. Under which there is the optin 'lasmerge' and 'las2dem'. These are the tools we're using to merge the point clouds and then convert them into raster layers. 

lasmerge allows for additional custom commands which we will use to select and merge the point files. This lets us merge more than 9 files at a time.

```
'-unique -i C:\Users\tbyrn\Desktop\GQIS Projects\Brisbane Building Elevations\Data\extracted\Brisbane*.laz'
```

Once the laz files are merged, convert it into a DEM layer with las2dem.

Now you have a raster layer in qgis which gives a very accurate picture of all the objects in the area and their heights

<h3> Step 3. </h3>
An issue I faced in this process is the CRS was incorrect, and the DEM layer was located near Monacco, instead of Brisbane, Australia. 

I used the georeferencer plugin with a basemap (OSM) to transform the raster to the correct location. If you need to do this, make sure you select different locations, making use of clearly defined landmarks such as bridges, skyscrapers and landmarks. Pay attention to any objects which are located along the edges of the raster, so it aligns correctly. 

<h3> Step 4. </h3>
From your basemap (probably OSM), extract the building polygons. 
//filter by building image here

I also tried to extract bridges and vegetation, so the birdges were rendered at the correct heights. It doesnt look good in the final 3d model if the buildings are rendered at the correct height, yet the roads stay the same height as the terrain, including the rivers.

<h3> Step 5. </h3>
Now you have the building polygons and a raster which has their heights. 

For a buildings height, we will find the MAJORITY height of the polygon. The polygons may include areas outside the actual building edge or it may have sections which read incredibly high (antennas?). Finding the most common height will give a more accurate height as opposed to getting the average or a median value.

Go to RASTER->Zonal Statistics and use MAJORITY for the method.

<h3> Step 6. Model </h3>
Now the polygons have heights according to the Point Cloud data. Using the qgisthree.js plugin, we can easily turn this into a nice html visualisation. 

<h3> Conclusion </h3>

The need for building heights is fairly specific, but the ability to use and consume point clouds is defintely useful. Hopefully this has helped you gain familiarity with some QGIS options and tools.
```
<script src="https://embed.github.com/view/3d/<username>/<repo>/<ref>/<path_to_file>">{newline}</script>
```
