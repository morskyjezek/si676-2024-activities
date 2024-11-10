---
layout: post
title:  "Omeka S Install Guide"
date:   2024-11-10
categories: guides omeka
---

This page describes how to set up Omeka S on your servers.

## Installing Omeka S Manually

This is a multi-step process. For full disclosure, know that it is unlikely you would have to install a tool like this in this way (a more likely scenario is that a program has a helper install tool; see the section below "[Install Omeka S with Softaculous](#softaculous)"). That said, installing thai way helps you to understand the overall architecture of the LAMP server, how to interact with the different elements (in this step, particularly the file system - LINUX - and databases - MySQL). The server is handling the HTTP requests and tasks that display the cPanel interface (so you are also interacting via the Apache element), and any of the interactions between the platform components are likely communicating to the databases via PHP, but for the moment you won’t need to worry about those elements.

The manual install process has a few main steps:
1. Get the server ready.
  - Set up a place the program can “live” in the file structure.
  - Set up a database and database user agents.  
2. Get the files for the application ready:
  - Download the Omeka S files (in .ZIP) from the Omeka server at https://omeka.org/s/download/. 
  - Unzip the files locally and prep them (this is mostly the addition of your database user information).  
3. Put the files on the server. This is mostly transferring the Omeka S program files to your server.
4. Configure the web application. This is relatively basic and involves creating an initial login for the Omeka S platform (explained below).

The process explained in detail below is also [outlined in the Omeka S User Manual](https://omeka.org/s/docs/user-manual/install/), but the details of the steps are not described. Here are those steps described as they should be carried out on your LAMP server:

### Configure Your Server

Main steps include:

* Create a directory for the Omeka files in your server’s folder called: `public_html`
* Create a new database in the SQL server
* Create a new database user and password
* Assign that user to the new database

#### Create a Directory for Omeka S on Your Server

There are various ways that you can do this. You can use the file manager tool within cPanel, you can use ssh and mkdir, or you can create a new directory using FileZilla. **Whatever option you choose, make sure that the directory is located in the server’s `public_html` directory.** Keep in mind that the folder name you choose will shape the URLs for your repository, so choose something descriptive but also simple, like `omeka` or `omekas`.

In the above example, if your username was `umsifan` and your directory was `omekas`, your site’s URI would look like this: 

```
http://umsifan.projectst.si.umich.edu/omekas/
```

#### Create a New SQL Database on Your Server

There are various ways to do this, but for ease of use (and also because this is not a class about SQL), I suggest using the interactive Databases tool within cPanel.

To do this, click on “MySQL Databases” under “Databases” in cPanel. In the databases tool, you will complete the form for “Create New Database,” which is where you should type the name of the database that you want, then click on “Create Database.” The name you choose will be appended to your username after an underscore, and in a sense is like a namespace, providing a unique alias for your database even though there are likely thousands of database tables out there named omeka. It will look something like this, if you wanted to create a new database named `jajohnst_new_omeka_db`:

![Creating a new database for your Omeka S install]({{ site.url }}/assets/omeka-newdbs.jpg "Creating a new database for your Omeka S install"){:style="border: 1px solid black;"}

#### Create a database User Agent (username and password)

Scrolling down in the databases tool, create a username and password combination. You won’t need to use this frequently, but you will need to enter the pair in your .ini file, so make note of the username and password that you create. You are essentially creating credentials for a local “user agent,” which will interact with the databases on behalf of Omeka S. If you want to randomly generate a password, use the “Password Generator” button or try an online tool like [https://www.avast.com/en-us/random-password-generator#mac](https://www.avast.com/en-us/random-password-generator#mac). Remember when you create the password, write it down or copy it to a safe place before proceeding. You will need to reuse it later.

![Creating a new user agent for your database]({{ site.url }}/assets/omekas-db_user.jpg "Creating a new user agent for your database"){:style="border: 1px solid black;"}

#### Assign the user to the database

Finally, assign the user to the database. This makes use of the “Add User to Database” section of the database tools. Here, select the user you created, then select the database, and click “Add.” In the screen that follows, select all of the permissions (you want this user to be able to do all the things with the databases that Omeka S will need!):

![Adding user to the database]({{ site.url }}/assets/omekas-assignuserdb.jpg "Adding user to the database"){:style="border: 1px solid black;"}

### Download Omeka S

Download the entire package of files for Omeka S from the Omeka website at: [https://omeka.org/s/download/](https://omeka.org/s/download/). This should arrive in a zip format. Unzip the files and take a look. It is interesting to look around the files and get an idea of how they are structured.

Notice, for example, there are a lot of `.php` files but not many `.html` files. Why do you think that is?

### Prepare Omeka S files locally

After you’ve looked around, **find the file `database.ini` in the folder `config`**. This file contains the information that allows the Omeka files to talk to the SQL database. It has to have a user, a password, a database name, and a host name. This information will be used by the PHP files in Omeka to write new information to the database, create, read, update, delete, or whatever else it may need to do to access information in the database.

You can open this file as a plain text file using VSCode, or any other text editor. When you open the file, it should look like this:

![Configure the database connection]({{ site.url }}/assets/omekas-assignuserdb.jpg "Configure the database connection"){:style="border: 1px solid black;"}

Enter the information from the database that you previously created on the server. This will vary based on the names that you chose, the host name should always be “localhost”. Thus, the information should look something like this, if your user was `omekas_db123`:

```
user     = "omekas_db123"
password = "secret123"
dbname   = "omekas_db123"
host     = "localhost"
```

Once you have the information entered, **make sure you save the file**.

### Transfer Omeka S files to your server

Once the file is saved, use FileZilla to transfer all of the files and the directory tree to the server in the destination directory that you created in the first server setup step. In the case of your first install, that was suggested to be `omeka` or `omekas`.

After the file transfer process is complete, you should be able to navigate in the browser to your server’s URL, and then add the name of the Omeka S directory at the end to display the Omeka S interface. It will look something like this:

![Install Omeka S - first user]({{ site.url }}/assets/omekas-firstuser.jpg "Install Omeka S - first user"){:style="border: 1px solid black;"}

### Configure Omeka S

If you are seeing a page like the one above, then your Omeka S instance should be ready to go. The final steps are to configure Omeka S by creating a first user and setting a few fundamental properties for your install of Omeka S. Do this by filling in the form and clicking the “Submit” button at the bottom of the page.

## Install Omeka S with Softaculous {#softaculous}

Many hosted server configurations provide a tool called Softaculous. Softaculous is a software tool that will take care of the installation of many different types of open-source web systems, like Wordpress, MediaWiki, Drupal, and other systems. It basically configures the LAMP stack for these platforms by installing all of the controller files (usually PHP, but may be another controller language), initializing the necessary databases to store data (MySQL), and connecting these to the web server (Apache).

This tools provides a more "point and click" or "one-click install" process. For the purposes of getting more familiar and comfortable with your servers, we do not have access to Softaculous. But know that if you ever find yourself in the position of installing a Web-based service like this, you will probably have access to other tools that simplify the install process.

## Resources

* [Related slide deck illustrating the login process][related-slide-deck]
* [Guide to logging in to your server]({% link _posts/2024-11-04-logging-in-to-your-server.md %})

[related-slide-deck]: TBD