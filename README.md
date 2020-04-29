# IIEC_RISE-FINAL-DOCKER-PROJECT
# INTRODUCTION:
Docker is one of the revolutionary technologies based on the containerization technology created by Solomon Hykes officially released on 7th March 2013.
It is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and deploy it as one package. By doing so, thanks to the container, the developer can rest assured that the application will run on any other Linux machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code.
Docker is designed to benefit both developers and system administrators, making it a part of many DevOps (developers + operations) toolchains. For developers, it means that they can focus on writing code without worrying about the system that it will ultimately be running on. It also allows them to get a head start by using one of thousands of programs already designed to run in a Docker container as a part of their application. For operations staff, Docker gives flexibility and potentially reduces the number of systems needed because of its small footprint and lower overhead.
# PROJECT DESCRIPTION:
This is the final Docker project made with Docker Compose based on Red hat Linux-8 operating system as host. My project uses “Infrastructure as a Code” i.e. “Docker Compose” to launch a full working Joomla setup in one go.
# PORT NO. USED IN THE PROJECT- 8080:80

# COMMANDS TO RUN THE PROJECT:
1. To go to the workspace: Run "cd /myjoomplacompose/"
2. To launch the setup: Run "docker-compose up"
3. To terminate or stop the setup: Run"docker-compose stop"
4. To access the .YAML file: Go to "cd/myjoomlacompose/" then run "vim docker-compose.yml"

# What is Joomla?
https://www.joomla.org/
https://www.joomla.org/about-joomla.html
Joomla is a free and open-source content management system (CMS) for publishing web content. It is built on a model–view–controller web application framework that can be used independently of the CMS. Joomla is written in PHP, uses object-oriented programming (OOP) techniques and software design patterns, stores data in a MySQL, MS SQL, or PostgreSQL database, and includes features such as page caching, RSS feeds, printable versions of pages, news flashes, blogs, search, and support for language internationalization.
Joomla is written in PHP, uses object-oriented programming techniques (since version 1.5) and software design patterns, stores data in a MySQL, MS SQL (since version 2.5), or PostgreSQL (since version 3.0) database, and includes features such as page caching, RSS feeds, printable versions of pages, news flashes, blogs, search, and support for language internationalization.
Over 8,000 free and commercial extensions are available from the official Joomla Extensions Directory, and more are available from other sources. As of 2019, it was estimated to be the fourth most used content management system on the Internet, after WordPress and Drupal.
# To access Joomla Documentation:
Go to https://docs.joomla.org/Main_Page
# About Joomla Image:
joomla:<version>-alpine
This image is based on the popular Alpine Linux project, available in the alpine official image. Alpine Linux is much smaller than most distribution base images (~5MB), and thus leads to much slimmer images in general.

This variant is highly recommended when final image size being as small as possible is desired. The main caveat to note is that it does use musl libc instead of glibc and friends, so certain software might run into issues depending on the depth of their libc requirements. However, most software doesn't have an issue with this, so this variant is usually a very safe choice. See this Hacker News comment thread for more discussion of the issues that might arise and some pro/con comparisons of using Alpine-based images.

To minimize image size, it's uncommon for additional related tools (such as git or bash) to be included in Alpine-based images. Using this image as a base, add the things you need in your own Dockerfile (see the alpine image description for examples of how to install packages if you are unfamiliar).

# HOW TO USE JOOMLA IMAGE:
The following environment variables are also honored for configuring your Joomla instance:

-e JOOMLA_DB_HOST=... (defaults to the IP and port of the linked mysql container)
-e JOOMLA_DB_USER=... (defaults to "root")
-e JOOMLA_DB_PASSWORD=... (defaults to the value of the MYSQL_ROOT_PASSWORD environment variable from the linked mysql container)
-e JOOMLA_DB_NAME=... (defaults to "joomla")
If the JOOMLA_DB_NAME specified does not already exist on the given MySQL server, it will be created automatically upon startup of the joomla container, provided that the JOOMLA_DB_USER specified has the necessary permissions to create it.

If you'd like to be able to access the instance from the host without the container's IP, standard port mappings can be used:

$ docker run --name some-joomla --link some-mysql:mysql -p 8080:80 -d joomla
Then, access it via http://localhost:8080 or http://host-ip:8080 in a browser.

If you'd like to use an external database instead of a linked mysql container, specify the hostname and port with JOOMLA_DB_HOST along with the password in JOOMLA_DB_PASSWORD and the username in JOOMLA_DB_USER (if it is something other than root):

$ docker run --name some-joomla -e JOOMLA_DB_HOST=10.1.2.3:3306 \
    -e JOOMLA_DB_USER=... -e JOOMLA_DB_PASSWORD=... -d joomla

# INITIAL SETUP REQUIREMENTS:
Following are the steps to setup Docker in your host Red hat Linux system:
# Pre-requisites:
1.	First of all, configure your “yum” with your custom repo which allow you to install docker in your host system.
2.	Install Docker Community Edition with the command “yum install docker-ce –nobest”. This will install Docker in your base Red Hat system.
3.	Install Docker Compose by running this command:
“curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose”
4.	Now, run “chmod +x /usr/local/bin/docker-compose” to get the “docker-compose” command.
# Pulling docker images from Docker Hub:
1.	Pulling MySQL Image: 
Use “docker pull mysql:5.7” command to install MySQL in your system. This will create MySQL database in your system to host Joomla Web App Environment in your base Red Hat system.
2.	Pulling Joomla Image:
Use “docker pull joomla:latest” command to install Joomla in your system. This will install Joomla in your base Red hat system.

# CREATING THE ENTIRE INFRASTRUCTURE:
1.	First of all with “mkdir”, create a directory with any name, for example: “mkdir/myjoomlacompose” where we create our workspace to store our .yaml file.
2.	Now go to the directory (cd /myjoomlacompose) and create .yaml file with the command “vim docker-compose.yml”
3.	Write the yaml code to lunch your entire Joomla setup in one go.
4.	Save the .yml file and exit with (: wq) command.
5.	Now, go to your workspace directory by (cd /myjoomlacompose) command.
6.	Run “docker-compose up” to launch your entire setup.
7.	Your Joomla web environment is now successfully created hosted on your base Red Hat system. Go to http://192.168.43.87:8080 to check you Joomla Set up.
8.	To Stop the service run “docker-compose stop”.

# INSTALLING JOOMLA:
﻿Installing Joomla! for the first time is very easy. Joomla!’s built-in web installer makes setting up your new site a breeze.
# Requirements
# Hosting Requirements
Before we start installing Joomla!, there are a couple prerequisites that need to be met to install Joomla! 3.x successfully. These apply whether you have a dedicated server, a shared hosting plan server, or are installing a copy on a local computer for testing or development.

You’ll need to meet the following requirements to install and use Joomla!

# References
# Recommended PHP.ini Settings
There are some PHP settings that need to be sufficient for Joomla to install. The settings are usually in a "php.ini" or "user.ini". Talk to your host about how to change theses settings if it is possible to do so. If working on a localhost e.g. with XAMPP, you should not be restricted by these settings and VPS or dedicated hosting should also not be as restrictive.

The values for PHP.ini below are suggested values only.

memory_limit - Minimum: 64M Recommended: 128M or better
upload_max_filesize - Minimum: 20M
post_max_size - Minimum: 20M
max_execution_time: Recommended: 30
Prepare for Install
You will need to complete two tasks before you can install Joomla! on your server. First, you will need to download the Joomla! package files. Next, you will need to have a database for Joomla! use.

# Downloading and Uploading Joomla! Package Files
Download the current release of Joomla! 3.x
Move the downloaded Joomla! installation package to the server. Use a FTP Client to transfer the Joomla! 3.x files to your server. There are several available for use, here is a detailed list of FTP Clients. Please make sure you are using a FTP client's official release.
Hint - This can be accomplished by simply moving the downloaded package to your server, then unpacking it. Or you can unpack the files on your local computer, then move the Joomla installation over to your server. Either way, the Joomla installation needs to be unpacked in the root of your site.
The "root" of your site is the public folder where all web page files are stored so that a user can view the site examples include public_html and htdocs. What your Host uses depends on them.

# Your Server's "root" Folder
Normally you upload your web files to the root folder. This is typically named "public_html" but other variations include "htdocs" and this depends on what your host has the set up on the server. For Joomla purposes, you can load the files directly into "public_html" or a sub-folder within it.

# Stop hand nuvola.svg.pngWarning!
If you unpack the files on your own computer, then copy them to your server, be sure to move only the folders and files contained INSIDE the Joomla! package. If you unpack the folders and files into a folder, for example called, Joomla and then upload that folder, your site will have to be accessed at yoursitename.com/Joomla instead of yoursitename.com.


# Database for Joomla! Installation
If you need to create a database, please read "Create a database for use with Joomla!" first or skip to step #2.
You will need to note basic database information needed when the actual Joomla! installation is started.
Location of database, localhost? Or a specific host's server such as dbserver1.yourhost.com?
The database name
The database user's name
The database user's password
# Start Install
# Main Configuration
With the above requirements met, a database created and the required Joomla! files in place, you are ready to install Joomla!. Start the Joomla! web installer by opening your favorite browser and browsing to the site's domain name. On host installation you will use http://www.yoursitename.com. If your are installing Joomla! locally, you will use http://localhost/<path to Joomla files>, and you should see the installation screen.

J30 Installation screen page 1.png
Joomla! will try to identify the Select Language field automatically from your browser's language. You can change this if needed.

Fill in the following information.

Site Name: the name of your website — this can be changed at any point later in the Site Global Configuration page.
Description: enter a description of the website. This is a global fallback meta description used on every page which will be used by search engines. Generally, a maximum of 20 to 25 words is optimal. Again, this can be changed on the Site Global Configuration page at any time. For more on metadata, see Global Metadata Settings and Entering search engine meta-data.
Admin Email Address: the admin email address. Enter a valid email in case you forget your password. This is the email address where you'll receive a link to change the admin password.
Admin Username: Joomla! uses a default "admin" as the username for the Super User. You can leave it as is, change it now (which a good Security measure) or use My Profile in the Administration interface to change it later.
Admin Password: remember that super user has maximum control of the site (frontend & backend), so try to use a difficult password. Use My Profile in the Administration interface to change it later. Confirm the password in the Confirm Admin Password box.
Site Offline: click the Yes or No box. Yes - this means when installation is complete, your Joomla! website will display the 'Site is offline' message when you browse to yoursitename.com to view the home page. No - this means the site is live when you browse to yoursitename.com to view the home page. You can use the Site Global Configuration in the Administration interface to change the Offline status at any time.
When everything on the first page is completed, click the next button to proceed:
# Database Configuration
# Configuration Settings
You will need to enter the information about the database you will use for Joomla! now. It was suggested to write this information down under "Prepare for Install" tab. You may also read or review Creating a Database for Joomla!.
For simplification, these intructions are a reference to installing with a MySQLi database. The instructions on the installation page are self explanatory, but here they are again:

Database Type: MySQLi is the common database used
Hostname Where is your database located? Common is localhost, but some hosts use a specific database server such as dbserver1.yourhost.com
Username: the username used to connect to the database
Password: the password for the database's username
Database Name: the name of the database
Table Prefix: one is generated automatically, but you can change it. For example, jos3_ can be used. Just don't forget to put the underscore character (_) at the end of the prefix.
Old Database Process: should the installer backup or delete existing tables during the installation of new tables? Click, Yes or No to select the choice.
All these choices can be edited on the Site Global Configuration page, under Server options after the installation is completed. Note, you will break your installation if you change these settings after installation unless you have a complete copy of the current database being used by the Joomla! installation. Common uses would be to update the username and password of the database or to complete a move of an existing installation to a new host with different parameters.

When all the information has been filled in, click the next button to proceed:
# Finalise
It is now time to finalise the Joomla! installation. The last page of the web browser installation contains all the information about the installation. This includes the options(at the top) for installing sample data and the installation's configurations(at the bottom).
# Install Sample Data and Email Configurations
The first options are for automatically installing sample content to the website and emailing the configuration settings.
If you are new to Joomla! it would be beneficial to install some sample data to see how Joomla! works. You can at this time choose to have the configuration settings emailed to you. If the Email Configuration choice is selected, the Email Password choice will appear. The email password is off by default for security. You can choose to have the password included, just click Yes.

Time to check the configurations of your install and the environment of the installation.

# Configuration Check
# Checking Your Configurations
If everything is in order, you will see the install at the top of the overview page. If not, this is the place to check and see what may be causing an issue.
The section is broken into 4 groups:
Main Configuration: all the website specific information, such as the website name, description, admin username, etc.
Database Configuration: contains the information about the database Joomla! will use.
Pre-Installation Check: these requirements must all be shown as Yes, otherwise you will not be able to install Joomla! With the exception of the PHP Version, the rest are usually controlled in the php.ini. You may need assistance from your host in correcting these settings or checking to see if it is possible to adjust them.
Typical PHP settings that might cause the install to fail and may need adjusting include the following with suggested values: (1) memory_limit (64M), (2)max_execution_time (30), (3) post_max_size (30M), (4) upload_max_filesize (30M). For more information, see PHP configuration file file.
Recommended Settings: these are settings are recommended in your PHP configuration, but will not prevent Joomla! from being installed. You can refer to the above instructions on how they may be changed.
If everything is correct and all checks are passed, you may now click the Install button in the top right corner of the Overview page. This will start the actual installation process.

After you click the Install button, you should see a progress bar with additional information of the installation. Once the installation completes, you should see the success page!

# Finishing Up
# Success and Finishing Up the Installation
Congratulations! Joomla! 3 is now installed. If you want to start using Joomla! right way without installing extra languages there is one last step to complete the installation. You must delete the Installation Folder. Click on Remove Installation folder and a success message will appear. Now you can navigate to the Administrator log in by clicking Administrator or go right to your site by clicking Site.





