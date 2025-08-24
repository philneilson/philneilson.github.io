---
layout: post
title:  Library Catalog Kiosk Stations, Free with Linux Mint (Part 1)
date:   2025-08-23 11:03:16 -0700
author: Phil Neilson
categories: [libraries, Linux]
image: /assets/images/posts/catalog.jpg
---

In the library where I work, we recently had to find a new solution for our catalog computer stations. For the past few years, we had been running our catalog on computers with the excellent open-source, **Linux-based [Porteus Kiosk](https://porteus-kiosk.org/index.html)**.

Prior to version 6.0.0, you could download Porteus, flash it to a USB, boot to the USB on your catalog computer and configure the settings you wanted, then install the image to the catalog computer's hard drive, all for free. There was an optional "automatic updates and support" option that you could pay for, but you could just not check that box and it would run for free. We had it running all our catalog stations.

With version 6.0.0 and forward, the "automatic updates and support" feature is mandatory; in other words, Porteus Kiosk is no longer free to use. One of our computers stopped booting correctly for some reason, and when I went to reinstall, I discovered this. (I actually tried installing a pre-6.0.0 version, but it wouldn't let me get through the startup process because it said that the version I was using, which was the latest version prior to 6.0.0 I could find, was no longer supported.) The pricing per year is not egregious, but if you have worked for municipal governments before, then you know that it can be hard to convince your purchasing department to pay for new and seemingly obscure things. I'm sure we could have made it work, and if you work in a library and are looking for a good catalog station solution, you should still definitely look at Porteus Kiosk.

---

### The Free Alternative

However, if you're like me and want to save yourself some red tape and/or stretch your budget a bit further, you can create a catalog kiosk station that functions very similarly to Porteus Kiosk, for free.

In this series of blog posts, I will share the process I went through to install **Linux Mint** on a catalog computer station and then added a few utilities and a custom script to make the computer function automatically as a kiosk station.

Here were the main requirements that I was after in my setup:

* The catalog station should boot straight into the library catalog homepage in a web browser upon hitting the computer's power button
* Likewise, the catalog station should shut down when the power button is pressed
* The catalog station should have the address and navbar removed to limit the computer to the use of the catalog and a few peripheral pages only
* For the same reason, the browser should be limited to a set of whitelisted URLs
* The catalog user should be able to still navigate or at least start over, despite the lack of a navbar
* If a catalog user leaves the catalog station on a page other than the homepage, the station will refresh back to the homepage after around 30 seconds of inactivity so the next user can start from the beginning

---

### Getting Started

I began this process with the very helpful tutorial video **[How to turn a LINUX MINT PC into a Web KIOSK](https://www.youtube.com/watch?v=XC0JonvTTOk)** and its **[Part 2](https://www.youtube.com/watch?v=Tp6QBJcXUIo)**, so thank you to TECHMIMIC for these excellent tutorials. However, after completing the instructions I still hadn't gotten some of the features I listed above (URL whitelist, the ability to navigate a bit or at least not get stuck, reset upon inactivity), so I kept going.  The rest of the instructions are pieced together from blog and forum posts (my usual way of learning Linux) and, eventually some AI help (not my usual way, but it was helpful).

These instructions are written by a librarian for other librarians, so they are by design not super technical and might overexplain things a bit. Also, there are certainly more elegant and lightweight ways to achieve all this (Porteus Kiosk is proof), but my hope is that this method will be replicable for a majority of those who give it a try.
