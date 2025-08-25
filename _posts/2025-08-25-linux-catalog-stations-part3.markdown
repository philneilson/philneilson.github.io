---
layout: post
title:  Library Catalog Kiosk Stations, Free with Linux (Part 3) - Install and Configure Utilities & Script
date:   2025-08-25
author: Phil Neilson
categories: [libraries, Linux]
image: /assets/images/posts/utility.jpg
---

Now that you have a fresh installation of Linux Mint on your catalog computer kiosk station, you're ready to set up the kiosk session to run in a browser automatically when the computer is booted. In this post, we'll be going through the installation and setup of a few utilities and scripts that will help us meet the requirements for the kiosk station outlined in part 1.

A note about these instructions. On Linux as in most computing, there are two ways to get something done: with the command line in a terminal, or with the graphical interface. Some things are easier to do one way than the other. Experienced Linux users and adminsitrators tend to prefer the command line because it's direct and to the point, and often you can accomplish tasks with a terse command that would take lots of clicking through menus or folders if you went the graphical route.  As a Linux hobbyist who is very much still learning, I have found that there are some things that are easier for me to accomplish with the command line, and some things that just make more sense to me when I use the graphical interface.  So in these instructions, I am going to use a mix based on what felt more comfortable for me.

### Step 1: Install Chromium Browser

Out of the box, Linux Mint 22.1 Cinnamon comes with Firefox preinstalled, and it would be a fine browser to use for this project.  But I ended up installing and using Chromium, which is readily available.

To install Chromium, first run a system update to make sure your system is up to date.  To do this, open up a terminal by pressing **ctrl** + **alt** + **T**.  Now enter the following command:
 
```
sudo apt update && sudo apt upgrade
```

After you hit enter, you'll be asked for your password.  This is because you used "sudo" (short for superuser do) at the beginning of your command to run the command as the administrator, which is necessary to modify systemwide software.

The first half of this command will refresh your package list, and the second half will automatically download and install any updated versions of the packages found, ensuring that your system is up to date.  It's always a good idea to run this command before installing new software.  After it runs, you'll have 
