---
layout: post
title: "Reset the Permalinks using MySQL"
description: What do you do when you can’t access the admin side of Wordpress and you need to reset the Permalinks to get the site working again?
date: 2016-04-20 18:45:41 -0400
permalink: /reset-permalinks-using-mysql/
tags: [help, mysql, wordpress]
image: reset-permalinks-using-mysql.jpg
---

![permalikns and how to reset them]({{ site.baseurl | prepend: site.url }}/assets/images/reset-permalinks-using-mysql.jpg)

What do you do when you can’t access the admin side of Wordpress and you need to reset the Permalinks to get the site working again? I had this happen to me the other day.<!--more-->

I was migrating a site to a new Hosting account. The original hosting had the WordPress installation in a sub folder. However on the new hosting account there was no sub folder. This caused a huge problem and WordPress was looking for resources in a folder that didn’t exist.

The site worked, kind of, okay, it was a mess. This was because the Permalink structure was looking for a sub folder that didn’t exist. There was no way to log into the admin area and update it. All I was getting was a **404** Page Not Found error when attempting to access the login page.

## Reset the Permalinks

If you have more than one WordPress website on your hosting account you’ll need to know the name of your database. You can find that by either using the File Manager in cPanel or a FTP client and getting a look at your WordPress files.

![WordPress config file]({{ site.baseurl | prepend: site.url }}/assets/images/the-wp-confog-file.jpg)

You need to open a file called “**wp-config.php**” with any text editor. You are looking for the line that says **/** The name of the database for WordPress */** right under that will be the name of the database. In this example the database name is **danapress**.

![TextMate]({{ site.baseurl | prepend: site.url }}/assets/images/wp-config-textmate.jpg)
Then go to your cPanel, look for the Databases section and click on the “**phpMyAdmin**” icon.

![cPanel]({{ site.baseurl | prepend: site.url }}/assets/images/cPanel-databases.jpg)

In the left column, look for the name of your database. Expand it and look for the table called “**wp-options**”. In that table you are looking for the “option_name” of “**siteurl**” and “**home**”. Buy editing these two rows in this table you can fix the Permalinks.

![phpMyAdmin]({{ siet.baseurl }}/assets/images/danapress-phpmyadmin.jpg)

In this example the sub folder is called “**wp**”. Once that is removed and the **siteurl** and the **home** match, the site should work properly again.
You should now be able to log into the admin side. I would suggest you then reset your Permalinks from there, just in case.
As always when working within the database be **VERY CAREFUL**. Having said that, it is very simple and straightforward to edit the database.