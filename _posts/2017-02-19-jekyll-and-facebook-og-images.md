---
layout: post
title: Jekyll and Facebook OG Images
description: "Make sure you setup your Posts with the OG Protocol so your links will show your cool images!"
modified: 2017-02-19
tags: [jekyll, facebook, Open Graph]
image: jekyll-and-facebook-og-images.jpg
---
![Jekyll and Facebook OG images]({{  site.baseurl | prepend: site.url }}/images/jekyll-and-facebook-og-images.jpg)

This might be very basic stuff but I figured it out and wanted to share it. For me it was not so basic or clear. I did a lot of Googling and could not find the answer. Usually that means it is super simple and no one needs to look up the answer. Except, well, for me.<!--more-->

So you have your cool [Jekyll](https://jekyllrb.com/) driven, static website blog up and running on GitHub Pages (*a really useful free resource*). And you have written a super cool blog post you want to share with the world! However, when you go to post a link on Facebook the main image of the post doesn’t show, what do you do?

## Every [Jekyll](https://jekyllrb.com/) setup is different, this is what I did.

Facebook uses the ***[Open Graph protocol](http://ogp.me/)*** (***OG***) which enables any web page to become a rich object in a social graph. This is used on Facebook to allow any web page to have the same functionality as any other object on Facebook.

I added this code to the head.html file that is located in the “***_includes***” folder of my Jekyll setup. This is the Open Graph stuff Facebook uses!

	{% raw %}
	<meta property="og:locale" content="en_US">
	<meta property="og:type" content="article">
	<meta property="og:title" content="{% if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}">
	<meta property="og:description" content="{% if page.description %}{{ page.description }}{% else %}{{ site.description }}{% endif %}">
	<meta property="og:url" content="{{ site.url }}{{ page.url }}">
	<meta property="og:site_name" content="{{ site.title }}">
	<meta property="og:image" content="{{ site.url }}/images/{{ page.image }}">

	<meta property="og:image:width" content="637" />
	<meta property="og:image:height" content="403" />
	{% endraw %}

The important part of all that code is the parts about calling the image (***property=“og:image”***) and setting the size. Facebook likes to have a specific size set.

### The liquid markup for calling an image is:

	{% raw %}
	<meta property="og:image" content="{{ site.url }}/images/{{ page.image }}">
	{% endraw %}

You have now set up the OG tags in the “*head*” but where is it getting the images from? Well you set the image in the [YAML front matter](https://jekyllrb.com/docs/frontmatter/) of the post. As you know all Jekyll posts use the [YAML](http://www.yaml.org/) (YAML Ain't Markup Language). [YAML](http://www.yaml.org/) is a human friendly data serialization standard for all programming languages.

### Here is an example of setting an image in the ***[YAML Front Matter](https://jekyllrb.com/docs/frontmatter/)***:

	{% raw %}
	---
	layout: post
	title: 3 Reasons to Switch from WordPress to Jekyll
	description: "These are the 3 reasons I switched away from WordPress and to using Jekyll a static website builder."
	modified: 2017-02-18
	tags: [jekyll, wordpress]
	image: 3-reasons-to-switch-from-wordpress-to-jekyll.jpg
	---
	{% endraw %}

By adding the “**image:***” to the Front Matter you have told Jekyll what image is associated with this post. 

And that is about it! You have included in every Page and Post an og:image tag. And you have declared in every Post’s YAML Front Matter what image goes with that Post. Now Facebook has all the data it needs to display your super cool Post along with its Wicked Catchy image.

