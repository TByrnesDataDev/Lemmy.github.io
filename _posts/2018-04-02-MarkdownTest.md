---
layout: post
title: Markdonw example
---

I stumbled upon QGIS as a way to visualize and analyze spatial information. As an initial example, I tought 
i'd create a gif of Hurricane Harvey's movement over a few days. the steps were followed in the tutorial [here](http://www.geodose.com/2017/08/creating-hurricane-harvey-track-path-time-lapse-radar.html) by Geodose. 

![Hurricane Katrina gif](/images/file.gif)

Clearly I needed to zoom in closer to the affected area, but you get the point. What isnt so clear is how to export and convert your fancy time lapse into a gif or video. 

If you're using linux, i think this capability is built in. however for windows users, when you export your time lapse, it will export each individual frame into the given folder. ( attach picture of frames in folder ) .

To convert these frames into the prefered video/gif format, I used FFMPEG. pretty easy to download, good documentation, and heaps of stack-overflow Q&A's. 

