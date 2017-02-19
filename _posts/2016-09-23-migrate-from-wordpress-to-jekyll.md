---
layout: post
title: "Migrating from WordPress to Jekyll"
description: Do you want to migrate from WordPress to Jekyll, well there are a few things to think about first and I hope I can help you make the migrating smooth.
date: 2016-09-23 01:57:32 -0500
tags: [help, jekyll]
permalinks: /migrate-from-wordpress-to-jekyl/
image: migrate-from-wordpress-to-jekyll.jpg
---

![moving from WordPress to Jekyll]({{ site.baseurl | prepend: site.url }}/assets/images/migrate-from-wordpress-to-jekyll.jpg)

So, you want to migrate from [WordPress](http://wordpress.org) to [Jekyll](https://jekyllrb.com). It can be easy or a huge pain in the ass. Well, when it comes to dealing with Jekyll it is never apple pie simple. But every time you use it you do learn something. I find learning as you go to be more important than just a simple point-and-click experience.<!--more-->

If you want to migrate from WordPress to [Jekyll](https://jekyllrb.com) and you want to bring in all your old Posts and Pages, this is what you need to do. You need to get your WordPress database, install it on a local MySQL database, then migrate it from that database to Jekyll. Simple, there you go, thank you for reading this post! Bye!

I wish it was that simple. I use [GoDaddy](http://godaddy.com) for hosting and they have cPanel which is good. Log into whatever control panel you have, go to the **phpMyAdmin**. When in **phpMyAdmin** find your database, click on it and click the “*Export*” tab.

![cPanel in phpMyAdmin]({{ site.baseurl | prepend: site.url }}/assets/images/cPanel-and-phpMyAdmin.jpg)
*cPanel locate phpMyAmin*

The Export screen is super simple. Just leave all the settings alone and click the Go button. It will download the database as an SQL file.

![Export your data]({{ site.baseurl | prepend: site.url }}/assets/images/export-your-wordpress-database.jpg)
*Export your data*

You should install [MAMP](https://mamp.info), it will run on a Windows, Linux or Mac system, I use a Mac. Once [MAMP](https://mamp.info) is installed and running, you want to go to phpMyAdmin and create a database. Once it is created, click the “Import” tab. Click the “**Choose File**” button then navigate to the SQL file you downloaded from you hosting account.

![create a database in phpmyadmimn]({{ site.baseurl | prepend: site.url }}/assets/images/create-a-new-database.jpg)
*Create a Database*

![import the wordpress data]({{ site.baseurl | prepend: site.url }}/assets/images/import-wordpress-data.jpg)
*Import the WordPress data*

## Migrate from WordPress – Now for Jekyll
I am assuming you have [Jekyll](https://jekyllrb.com) installed and you have created a new [Jekyll](https://jekyllrb.com) project. After that is done you should have a folder that looks something like this:

![default Jekyll folder]({{ site.baseurl | prepend: site.url }}/assets/images/default-jekyll-project-folder.jpg)

The default Jekyll website looks like this:

![Migrating from WordPress - Jekyll default website]({{ site.baseurl | prepend: site.url }}/assets/images/default-jekyl-website.jpg)


The default theme that [Jekyll](https://jekyllrb.com) uses (at the time this was written) is called Minima. I found it helpful to [download the Minima theme](https://github.com/jekyll/minima) so you have the default files to deal with.

![minima-folder-files]({{ site.baseurl | prepend: site.url }}/assets/images/minima-folder-files.jpg)

Now it is time to import the data from your local [WordPress](http://wordpress.org) database. This can be tricky and you can run into some problems. I have done this before without any issues. Then when I try and do it a week later I have nothing but issues. It is important to stay calm and work the problem and not get frustrated.

For example, this last time I had to add the following to the Gemfile. I didn’t have to do this the last time.

`gem "sequel"`

and:

`gem "unidecode"`

![migrating from WordPress to Jekyll]({{ site.baseurl | prepend: site.url }}/assets/images/gemfile-and-added-gems.jpg)

I also ran into a problem with the [Jekyll](https://jekyllrb.com) import. I had to install it using this:

`$ gem install jekyll-import`

That’s not the end either. I had to install the following in order to get Ruby to connect to the database.

`gem install mysql2`

Connecting to the database was another issue. If you are using MAMP the “*Path*” is very specific and something I struggled with. The Path you want to use it:

1
/Applications/MAMP/tmp/mysql/mysql.sock
The import code you enter in the command line is posted on the Jekyll website in the migration section. Below is what I used, remember you will need to put in your own database name, user, and password. This is the code I used:

```
$ ruby -rubygems -e 'require "jekyll-import";
    JekyllImport::Importers::WordPress.run({
      "dbname"   => "group-1",
      "user"     => "root",
      "password" => "root",
      "host"     => "localhost",
      "socket"   => "/Applications/MAMP/tmp/mysql/mysql.sock",
      "table_prefix"   => "wp_",
      "site_prefix"    => "",
      "clean_entities" => true,
      "comments"       => true,
      "categories"     => true,
      "tags"           => true,
      "more_excerpt"   => true,
      "more_anchor"    => true,
      "extension"      => "html",
      "status"         => ["publish"]
    })'
```    
### Migration is not 100% Perfect
Hopefully if you migrate from [WordPress](http://wordpress.org) it will go smoothly. I said before, if you get errors work them. Copy and paste them in Google, read what other people did to fix the issues. It is not that difficult to figure out, I did and so can you.

The result will be a horrible looking website. But that is what you get when you migrate from [WordPress](http://wordpress.org). This is what my site looked like after the migration.

![migrate from WordPress website-after-wordpress-migration]({{ site.baseurl | prepend: site.url }}/assets/images/website-after-wordpress-migration.jpg)

This does require a lot of clean-up and moving of images. But it does a lot of the heavy lifting up front. It might look messy but it gives you a jumping off point. You now have all the content from your [WordPress](http://wordpress.org) site in [Jekyll](https://jekyllrb.com).

I just want to remind people that I am still learning. I do not know all the tricks. I am just putting this out there for people like me. I believe that it is important to share your knowledge and help other people. Everyday in my journey of learning I am thankful for the countless people out there that are willing to share what they know. I hope this helps someone.

