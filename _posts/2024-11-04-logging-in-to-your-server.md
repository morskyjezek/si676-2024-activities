---
layout: post
title:  "Logging In to Your Server"
date:   2024-11-04
categories: guides servers omekas cpanel ssh
---

This page describes how to log in to your LAMP servers.
UMSI has provided each of you with your own server, which is
already configured with a LINUX operarating system, the Apache web server software,
and the capacity to work with PHP files and SQL databases.
As you work to get your servers running Omeka S, you need to get the software files,
add them to your server, and configure them to run on your server.

But before you do all of that, you will need to log in to your server!
There are three main ways that you can interact with your server:

1. **cPanel.** This is a browser-based "control panel" interface.
To access cPanel, navigate to your server's URL and append `:2083`,
which directs the browser to port 2083. There, you will have the option
to log in with the admin username and password for your server.
You can read the [cPanel documentation here](https://docs.cpanel.net/), though it's probably not necessary for our purposes.
2. **SSH.** This is a terminal interface that allows you to interact with your server.
The interface is a bash environment, so you should be able to run shell commands and most regular navigation and file system commands.
Note that this is a restricted environment for security purposes, so it is possible that you may not be able to run all shell commands; and in some cases you may be prompted to enter your username or password to confirm permissions.
3. **Filezilla.** This is a GUI client that is helpful for moving files to your server.
All of its functions could probably also be accomplished using _SFTP_, which is
a terminal-based protocol. But this file manager is used in some digital collections environments
and provides all of the functions you will need (without learning additional commands). If you prefer graphical over text interfaces, this is for you! :-)

## Find Your Server

Each student in the class has a server provided by UMSI.
Your server can be accessed at a URL formulated with the following pattern,
where `YOUR-UNIQNAME` is substituted with your actual uniqname:

`http://YOUR-UNIQNAME.si676.si.umich.edu/`

So, if my uniqname was `umsifan`, my server URL would be: `http://umsifan.si676.si.umich.edu/`.

To log in you will need a username and password. Your username is your uniqname. Your password is your UMID (an 8-digit number with no spaces).

When you navigate to your server's URL with a browser, you should see something like this:

![Blank server page]({{ site.url }}/assets/blank-server-page.jpg "Screenshot of blank LAMP server viewed by web browser"){:style="border: 1px solid black;"}

## Logging in to cPanel

Log in to cPanel at your server using port 2083.

1. Open a web browser and use the following template for your URL: `https://YOUR-UNIQNAME.si676.si.umich.edu`
2. At this page, you should see the unconfigured server page (basically, like a listing of files available there.
3. To access the server, you can use the cPanel tools. To do this, access the above url with port 2083. To do this, append a colon (`:`) to the end of the URL and the number `2083`. For example, if your uniqname was `umsifan`, you would use the following URL to access cPanel: `https://umsifan.si676.si.umich.edu:2083`.
4. The page that opens will prompt you for your login credentials. **Your username is your uniqname. Your password is your 8-digit UMID number.** So, if `umsifan`'s UMID was 12345678, their password would be `12345678`.
5. When you log in, you should see a screen that looks something like the screenshot below. Notice: at the right, you will see your user information, the name of the domain that connects to your server, the IP address, the path to your home directory (that will be where to add files when we access the server using terminal), and some other information about the setup of cPanel. See below for a screenshot:

![cPanel login via port 2083]({{ site.url }}/assets/cpanel-login-port2083.jpg "Screenshot of cPanel login page at port 2083"){:style="border: 1px solid black;"}

## SSH via the Terminal

To log in with the SSH (Secure SHell), open the client that you use for command shell (e.g., Terminal, GitBash, or other). The command to access your server is `ssh` (secure shell).
To use this command, use the following syntax:

```bash
ssh user@domain.com
```

For `umsifan`, the command would look like this:

```bash
ssh umsifan@umsifan.si676.si.umich.edu
```

When you run the command, you will be prompted for your password.
This is your UMID. The login screen should look something like this:

![ssh login via terminal]({{ site.url }}/assets/.jpg "Screenshot of cPanel login page at port 2083"){:style="border: 1px solid black;"}


When you type the password, you will not see the response,
which can make it difficult to know if you have typed the right information.
But type carefully, then press enter. If your login is successful, you'll see a page something like this:

**SSH Notes:** 

* If you incorrectly enter your password more than three times, the server will be inaccessible for 10 minutes
* 

## FileZilla for File Management (FTP)