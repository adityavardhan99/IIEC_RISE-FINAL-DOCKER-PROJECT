# IIEC_RISE-FINAL-DOCKER-PROJECT
# INTRODUCTION:
Docker is one of the revolutionary technologies based on the containerization technology created by Solomon Hykes officially released on 7th March 2013.
It is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and deploy it as one package. By doing so, thanks to the container, the developer can rest assured that the application will run on any other Linux machine regardless of any customized settings that machine might have that could differ from the machine used for writing and testing the code.
Docker is designed to benefit both developers and system administrators, making it a part of many DevOps (developers + operations) toolchains. For developers, it means that they can focus on writing code without worrying about the system that it will ultimately be running on. It also allows them to get a head start by using one of thousands of programs already designed to run in a Docker container as a part of their application. For operations staff, Docker gives flexibility and potentially reduces the number of systems needed because of its small footprint and lower overhead.
# PROJECT DESCRIPTION:
This is the final Docker project made with Docker Compose based on Red hat Linux-8 operating system as host. My project uses “Infrastructure as a Code” i.e. “Docker Compose” to launch a full working Joomla setup in one go.
# PORT NO. USED IN THE PROJECT:
8080:80
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


