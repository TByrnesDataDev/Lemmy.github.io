---
layout: post
title: Model.stl Creation
---

An example of the .stl model is here.
Now the steps for creating a .stl object are a little trickier, but that are based off what was done to produce the html version. 
<script src="https://embed.github.com/view/3d/TierynnB/TierynnB.github.io/master/images/model.stl">{newline}</script>

<!-- more -->

<h2>Create .STL Model</h2>
Requirements: install Blender. its open source modelling/animation software which will be used to combine the three .stl files into a single 3d object.

<h3>Step 1. </h3>
Go back to the QGIS project you created, and open the QGIS2three.js plugin. There is a dropdown at the top of the popup, select 'Export'. Press Finish.

<h3>Step 2. </h3>
It will open up a page that looks like this:

select .stl (ASCII). I don't know the difference between these types, but this exercise may work with some(or all) of the others.

<h3> Step 3. </h3>

There are now have 3 .stl files, and a PNG. I'm stil figuring out how to use the png and attach it to the model, so for now ignore it. 
open Blender and import the three .st file. 

Selecting all three together, or doing it one a time, join them all together with the option 'object->join'.

<h3> Step 4. </h3>
Export the combined object as an .stl object.

<h3> Step 5. </h3>
To display this object on a github page as I have it here, put it somewhere in your repository. Then add a script tag like this one to your markdown.

```
<script src="https://embed.github.com/view/3d/<username>/<repo>/<ref>/<path_to_file>">{newline}</script>
```
