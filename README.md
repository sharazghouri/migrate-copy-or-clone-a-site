# Migrate, Copy, Or Clone A Site

## How to move your site from one server to another.

## Prerequisite Skills

*   Basic cPanel/Plesk knowledge
*   Familiarity with FTP Client

## Objectives

*   Preparing students for the hassle free site migration.

## Teacher Notes

*   Show all of the steps on the live server rather than " MAMP, XAMPP, WAMP " since it is needed to use FTP client and handle the database.

## Hands-on Walkthrough

### First Things First You Need the Old Site’s Database

[![](https://make.wordpress.org/training/files/2016/04/First_Things_First_You_Need_the_Old_Site_s_Database.png)](https://make.wordpress.org/training/files/2016/04/First_Things_First_You_Need_the_Old_Site_s_Database.png) To export your old site’s WordPress database you need to head into the PHPMyAdmin section of your hosting provider. Every hosting provider different when it comes to how you can get to your PHPMyAdmin section, so I won’t be covering that here. Google “Hostname PHPMyAdmin” and hopefully you can find some documentation. Once you are logged into PHPMyAdmin, you should see something that resembles the screenshot above (older versions of PHPMyAdmin might look slightly different but the principles here are the same) <span style="font-weight: 400">You will need to select the correct database to export. If you do not know the database name you will need to figure that out from your wp-config.php file on your old WordPress website. (See screenshot below)</span>

### Finding Your Database Name

[![](https://make.wordpress.org/training/files/2016/04/Finding-Your-Database-Name.jpg)](https://make.wordpress.org/training/files/2016/04/Finding-Your-Database-Name.jpg) Search for the line that looks like define(‘DB_name, ‘YOURDATABASENAMEISHERE’); That second value is your database name. [![](https://make.wordpress.org/training/files/2016/04/PHP-My-Admin-Export.png)](https://make.wordpress.org/training/files/2016/04/PHP-My-Admin-Export.png) Once you know the Database name drill into the database in phpMyadmin by clicking on its name on the left-hand side. You will then see the above view. These are all the tables containing all of the data on your old WordPress site. Go ahead and click export at the top and save it as an SQL file.

### Setup and Install WordPress for the new site

Setup the clean WordPress site on your new server, download your wp-content folder from an old one and upload your old wp-content folder into the new one. The wp-content folder has your old sites themes, plugins, uploads etc. [![](https://make.wordpress.org/training/files/2016/04/Setup_and_Install_WordPress_for_the_new_site.png)](https://make.wordpress.org/training/files/2016/04/Setup_and_Install_WordPress_for_the_new_site.png)

### Find and Replace in old site’s database

This step can be skipped if you are migrating the site “ If the URL is staying the same but you are just changing the server or hosting provider “ Since you already saved your old database in SQL format on your computer the next step is updating the URL in the database from an old one to a new one. What you want to do is open up your MySQL export file ( a .sql file) with a text editor. Use Notepad++ on Windows or TextWrangler on Mac (It doesn’t matter too much what you use as long as it has found and replaces functionality) Make a copy of the .sql file before making any changes, just in case you screw the pooch. Now, Find and replace all instances of your old URL. So find www.oldsite.com and replace with www.newsite.com in that open text document. Make sure you are replacing the www.oldsite.com with the location of that fresh WordPress install you just set up. [![](https://make.wordpress.org/training/files/2016/04/Find_and_Replace_in_old_site_s_database.png)](https://make.wordpress.org/training/files/2016/04/Find_and_Replace_in_old_site_s_database.png) If you mess up on this step, don’t worry you have that backup remember? Also, you can quickly do a find and replace of the incorrect values in the database you are editing. The one thing that can be messed up is your admin if you try changing without www. What could happen is that your admin e-mail is admin@oldurl.com and if you update URL without www. , you will update WordPress admin e-mail as well.

### Clear out the new WordPress installs Database and Import the old

By now you should have edited the old MySQL database and updated the URLs to fit the new destination site, installed a brand spanking new version of WordPress for the new site and uploaded the entire wp-content folder from the old WordPress site. On the new site hosting provider, go ahead and log into phpMyAdmin just like in the first step (do this for your new site and make sure you are in the new database, it should have a different name than the earlier exported database) Open up the new MySQL DB by clicking into it (just like before). You should see something similar to the screenshot above. Now check all tables and click drop. It will ask you to confirm the drop, go ahead and do that. [![](https://make.wordpress.org/training/files/2016/04/Drop.png)](https://make.wordpress.org/training/files/2016/04/Drop.png) After dropping the database, import the one that you edit before. Please note that some servers are not allowing large database upload, so you might consider creating a .zip of it before upload.

### Editing wp-config.php

When you are done make sure that the database prefix is the same in wp-config.php and inside your PHP MyAdmin. If that is not the case, just simply edit the line i.e: `$table_prefix = 'wp_'; // Only numbers, letters, and underscores please! $table_prefix = 'y77_'; // Only numbers, letters, and underscores please!` Your website should be cloned correctly and it should look like an exact clone of the source one. Don’t forget that the different PHP and MySQL versions could cause issues in the proper functioning of the new website but mostly in the case when the versions are lower on a destination than on the source server. There are also a lot of plugins and SaaS that can help in making this job easier.

*   WordPress Duplicator
*   WordPress Move
*   BackupBuddy
*   WP Migrate DB Pro
*   myEASYbackup
*   UpdraftPlus
*   WP Clone by WP Academy
*   All-in-One WP Migration
*   ManageWP
