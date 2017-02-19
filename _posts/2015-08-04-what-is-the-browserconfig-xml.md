---
layout: post
title: "What is the browserconfig.xml"
date: 2015-08-04 14:58:24 -0400
mood: happy
tags: [help, windows]
permalink: /what-is-the-browserconfig-dot-xml/
---

![What is the browserconfig]({{ site.baseurl | prepend: site.url }}/assets/images/browser-config-file.jpg)



If you are looking through your error logs and see that you are missing a browserconfig.xml and you have no idea what this is, you are not alone. It is a [Windows](http://www.microsoft.com "Windows") things and it is easily fixable.


First of all what the heck is it. Browser configuration files *also known as browserconfig* is used to define things like tile backgrounds, badge updates, and tile notifications. Browser configuration files let you set these images using external XML files rather than metadata within the HTML markup of a webpage.
<!--more-->

What we are talking about are these areas, tiles of the newer **Windows OS**.

![Windows 10 tiles]({{ site.baseurl | prepend: site.url }}/assets/images/Windows-8-Live-Tiles.jpg)

You can set a tile on **Windows 8** and above to be a link to a website. When that is done the website can control what color or image will fill that tile. In order to do that you need to add a few files to your root folder.

![Browser config items]({{ site.baseurl | prepend: site.url }}/assets/images/Browser-Config-items.png)

If you are like me and you are running a [WordPress](https://wordpress.org "WordPress") website you just add those files to your server in the same place your .htaccess file is.

The best way (*easiest way*) to get these files is to use the [Internet Explorer site tile builder](http://www.buildmypinnedsite.com). Before you do, you will need a few things. First decide on a default color. They have a color picker available so you can pick one on the fly if you like. Then you will need an image, a logo or photo that will be used on the desktop tile to represent your website.

They will ask for a URL to your RSS feed, if you have one. This is not required and can be skipped.
Then you can download your code. You will get a **ZIP** file with 6 files in it. I replaced the four(4) image files with my own. The [Site Tile builder](http://www.buildmypinnedsite.com "Site Tile builder") just stretches your photo to fit the 4 required image sizes. I used Photoshop to crop my images to the needed sizes, it looked better that way.

You also get a line of meta code to add to your head area of your website.

**Upload the files to your root folder and add the line of code to your head section of your website and you are done.**

You will no long get the error saying the browserconfig.xml doesn't exist and you will be a bit more friendly to **Windows** machines.
