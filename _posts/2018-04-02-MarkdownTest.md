---
layout: post
title: Markdonw example
---

I stumbled upon QGIS as a way to visualize and analyze spatial information. As an initial example, I tought 
i'd create a gif of Hurricane Harvey's movement over a few days. the steps were followed in the tutorial [here](http://www.geodose.com/2017/08/creating-hurricane-harvey-track-path-time-lapse-radar.html) by Geodose. 

![Hurricane Katrina gif](/images/file.gif)

Clearly I needed to zoom in closer to the affected area, but you get the point. What isnt so clear is how to export and convert your fancy time lapse into a gif or video. 

If you're using linux, i think this capability is built in. however for windows users, when you export your time lapse, it will export each individual frame into the given folder.

[frames](/images/Frames.PNG)

To convert these frames into the prefered video/gif format, I used FFMPEG. pretty easy to download, good documentation, and heaps of stack-overflow Q&A's. 

Step 1. Download and install FFMPEG. 

Step 2. open the command line and navigate to where the frames are saved. in this case it is 'HurricanFrames'. 

This command will convert the images straight into a gif.
```
ffmpeg -framerate 5 -i frame%03d.png out.gif
```

The below command will convert all thos frames into a video file. 

```
\HurricaneFrames>ffmpeg -framerate 5 -i frame%03d.png video.avi
```
The framerate determines frames/second, so this will cause each frame to appear for 1/5 of a second. 

one this video is created, it is converted into a pallete of colours
```
ffmpeg -i video.avi -vf palettegen=max_colors=12 palette.png
```
Which is used to convert the video into a gif. The paraeters pased when creating the pallete will determine the size and quality of the gif.
```
ffmpeg -y -i video.avi -i palette.png -filter_complex paletteuse -r 10 -s 320x480 file.gif
```