---
layout: post
title: Model (html and .stl) Creation
---

This post will show hot to create html pages for your maps that let the viewer twist and turn the model. This is a pretty cool tool to view maps or areas with interesting topology or elevation. 

<h1> html creation </h1>

An example of the HTML model is here.
<h2>Step 1.</h2>
Download the QGIS2three.js plugin in QGIS (I used version 2.18.17, please check if this plugin exists for your version).

<h2>Step 2. </h2>
Make your map, preferably with some cool elevataion and colour scheme. If lost, refer to one of my other posts (to be added) or google how. it Doesnt really matter when outputting this HTML, as it will still work, but the value of the plugin won't really come across with a flat map that you can zoom in on. 

At least use a basemap such as OpenStreetMap.

<h2> Step 3. </h2>
go to the GQIS plugin you've just installed 'QGISthree2.js'. Theres not that many options that will prevent you outputting a html, but if you have added additional vector features to your map, these can be useful.
Name the file you're exporting and press 'Finish'.

<h2> Step 4. </h2>
find the file and open it! it should give you something like this.

An example of the .stl model is here.
Now the steps for creating a .stl object are a little trickier, but that are based off what was done to produce the html version. 

<h1> .stl creation </h1>
requirements: install Blender. its animation software. this will be used to combine the three .stl files into a single 3d object.

<h2>Step 1. </h2>
go back to the QGIS project you created, and got the the QGIS2three.js plugin. There is a ddropdown at the top of the popup, select 'Export'. Press Finish.

<h2>Step 2. </h2>
It should open up a page that looks like this:

select .stl (ASCII). I don't know the difference between these different types, but this exercise may work with some(or all) of the others.
<h2> Step 3. </h2>

you now have 3 .stl files, and a png. I'm stil figuring out how to use the png and attach it to the model, so for now ignore it. 
open Blender and import the three .st file. 

selecting all three together, or doing it one a time, join them all together with the option 'object->join'.

<h2> Step 4. </h2>
Export the combined object as an .stl object.

<h2> Step 5. </h2>
To display this object on a github page as I have it here, put it somewhere in your repository. Then add a script tag like this one to your markdown.

` 
<script src="https://embed.github.com/view/3d/<username>/<repo>/<ref>/<path_to_file>">{newline}</script>
`
