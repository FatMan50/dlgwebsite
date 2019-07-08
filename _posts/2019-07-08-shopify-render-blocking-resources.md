---
layout: post
title: Fix Render Blocking Resources in Shopify
description: "Render Blocking Resources can slow down a Shopify site, learn how to find what resources is slowing the site down and how to keep it from doing that."
tags: [technology, e-commerce]
image: Fix-render-blocking-resources-in-shopify.jpg
---

![Using Jekyll to drive an e-commerce website]({{  site.baseurl | prepend: site.url }}/images/Fix-render-blocking-resources-in-shopify.jpg)

Render blocking resources have been an issue with Shopify websites. When testing a site’s speed using the Chrome feature called Lighthouse you can pinpoint what resources are causing you issues.<!--more-->

<div>
<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed//uNperuWO8s4' frameborder='0' allowfullscreen></iframe></div>
</div>

Go to Chrome and the website you want to test. Then click View in the top left of the screen and in the drop-down choose Developer and then Developer Tools. The window that opens gives you lots of tools to use.

Choose the Audit tab from Developer Tools. There you can run an audit of the page in either the mobile or desktop environment. After the test has run you will get some very helpful information.

Specifically we are looking at the Performance section. Look for the Render Blocking Resources row and click it. It will open a drop-down that will show you specifically what resources are slowing down the page. It will also give you the amount of time that is being used to run these resources.

After you have identified a specific resource that is slowing the page, go to the admin side of your Shopify. Then go to the Online Store and click on Themes. There you want to click the Action button on the theme you wish to work on. Always test your changes on an off-line theme before making changes to the active theme.

Under Actions choose Edit Code. On the left is a column showing the different parts of the theme, Layout, Templates, Sections, Snippets, etc. On the top is the Layout, in there click on the theme.liquid file.

## Disable Render Blocking Resources

Look for the resource, JavaScript file, CSS file, or include, that the Lighthouse speed test indicated as slowing the page down. In many cases the resource isn’t needed on the specific page you are testing, like the home page for example.

If you are using a specific LightBox function, for example, but it is only being used on the Product pages, you do not need to load those resources on every page. What you would do is create a “If” statement around the resource, so it will only load in the pages that need it.

All you need to do is add this line of code just before the resource:

{% raw %}
`{% if template contains 'product' %}`
{% endraw %}

And then just after the resource add the end statement:
{% raw %}
` {% endif %} `
{% endraw %}

This example will load the resource only on the Product pages.

## Test & Tune

To make sure the resource you are controlling does not mess up your site, you need to test it. Once you are sure you are controlling the resource correctly you can make the changes to the active theme.

If you need to have the resource applied to more than one page you would add this before the resource:

{% raw %}
` {% if template == 'product' or template == 'cart' %}  `
{% endraw %}

In this example the resource would be loaded on every Product page as well as the Cart. And of course it would need to be followed up by the “endif” statement.

Shopify Themes and APP’s add lots of resources in the Theme.liquid file. Not all are required by every page of your site. This is done for simplicity sake. APP developers and theme developers are trying to make things as simple as possible for themselves. Which is fine.

But as owners and managers you need to get the best performance out of your Shopify site as possible. By using the “if” statement you can limit what gets loaded on each page, and by doing so, reduce the render blocking resources that are slowing your Shopify site down.
