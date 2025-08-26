---
layout: post
title:  Library Catalog Kiosk Stations, Free with Linux (Part 3) - Install and Configure Utilities & Script
date:   2025-08-25
author: Phil Neilson
categories: [libraries, Linux]
image: /assets/images/posts/utility.jpg
---

Now that you have a fresh installation of Linux Mint on your catalog computer kiosk station, you're ready to configure the kiosk session to run in a browser automatically when the computer is booted. In this post, we'll be going through the installation and setup of a few utilities and scripts that will help us meet the requirements for the kiosk station outlined in part 1.

A note about these instructions. On Linux (as in most computing) there are two ways to get something done: with the command line in a terminal, or with the graphical interface. Some things are easier to do one way than the other. Experienced Linux users and adminsitrators tend to prefer the command line because often you can accomplish tasks with a terse command that would take lots of clicking through menus or folders if you went the graphical route.  As a Linux hobbyist who is very much still learning, I have found that there are some things that are easier for me to accomplish with the command line, and some things that just make more sense to me when I use the graphical interface.  So in these instructions, I am going to use a mix based on what felt more comfortable for me.

### Step 1: Install Chromium Browser

Out of the box, Linux Mint 22.1 Cinnamon comes with Firefox preinstalled, and it would be a fine browser to use for this project.  But I ended up installing and using Chromium, which is readily available.

To install Chromium, first run a system update to make sure your system is up to date.  To do this, open up a terminal by pressing **ctrl** + **alt** + **T**.  Now enter the following command:
 
```
sudo apt update && sudo apt upgrade
```

After you hit enter, you'll be asked for your password.  This is because you used "sudo" (short for superuser do) at the beginning of your command to run the command as the administrator, which is necessary to modify systemwide software.  

The first half of this command will refresh your package list, and the second half will automatically download and install any updated versions of the packages found, ensuring that your system is up to date.  It's always a good idea to run this command before installing new software.

Once the update is complete you can proceed with installing Chromium.  For this step, I used the graphical interface.  Click on the main menu icon in the lower left hand corner of the screen and select "Software Center" (if you don't see it, you can search for it with the menu's built-in search bar).  

![image of Linux Mint software center](/assets/images/posts/software-center.jpg "Linux Mint's Software Center")

Once the software center opens, search for Chromium in the search bar.  Once you've found it, select it and click **Install**.  If you get an error message telling you that it isn't able to install Chromium, open up a terminal and run the update command again, then reopen the Sotware Center and try again.

### Step 2: Install Additional Packages

Besides Chromium, you will need to install a few additional utilities that will give your kiosk the funcitonalities we're looking for.  Most browsers, including Chromium, have a built-in kiosk mode that will force full screen, but for a truly locked down public kiosk, there are a few features that we'll need to add to it.

Open a terminal again by pressing **ctrl** + **alt** + **T** and then enter the following command:

```
sudo apt update
```

Enter your password and hit "enter". Once the update finishes, enter this command:

```
sudo apt install squid xprintidle xdotool xbindkeys 
```

This command will install the following programs:

* **squid** is a proxy server that will stand between our browser and the regular web.  We will use squid to set a list of whitelisted URLs that it will allow the user to access, while denying all other URL requests.
* **xpintidle** is a tool that measures how long it has been since the last user input.  We will use this to tell the computer to refresh back to the home screen if the catalog station sits idle so that each user can start from the beginning rather than from wherever the last user left it.
* **xdotool** is a tool that allows you to simulate mouse and keyboard movements.  We need this to work with xprintidle to make the refresh script work.  Essentially, if the computer sits idle and hits the refresh point, after the refresh xdotool will make a tiny movement of the mouse to reset the xprintidle counter.  Otherwise, your script would just continually be refreshing without waiting for the defined idle period.
* **xbindkeys** is a tool that allows you to define custom keyboard commands.  We will be using this tool to create a "start over" button for the user so that they can get back to the start of the catalog even without the browser's navigation bar.


