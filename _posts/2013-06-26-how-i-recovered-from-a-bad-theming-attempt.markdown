---
last_modified_at: '2017-04-10 05:14 -0700'
author: Gautham Yerroju
comments: true
date: 2017-04-10 05:14 -0700
layout: post
link: >-
  https://gtmstechblog.wordpress.com/2013/06/27/how-i-recovered-from-a-bad-theming-attempt/
slug: how-i-recovered-from-a-bad-theming-attempt
title: How I recovered from a bad theming attempt
wordpress_id: 190
categories:
  - Customization
  - Theming
tags:
  - theming
  - commandline tool
published: true
---

If you've ever set out to apply some of the gorgeous themes for Windows available at Deviantart, I'm sure you have come across UX theme Patcher. It allows you to apply unsigned themes on Windows (almost practically every good theme out there). [deviantART](http://browse.deviantart.com/customization/skins/windows7/visualstyle/ "Visual Styles for Windows 7 at deviantART") and many other websites have some amazing themes but they can’t be used, because they are not digitally signed by Microsoft. Another reason is that some of these themes modify/replace some system files (explorerframe.dll, shell32.dll, explorer.dll) to theme elements like the back/forward buttons in Windows Explorer, the start button, etc.

Since these themes provide modified system files, we need to make backups of the originals. There are tools to manage themes by changing the system files automatically, and [Theme Manager](http://bickelk.deviantart.com/art/Theme-Manager-Windows-7-176165228 "Theme Manager for WIndows 7 by bicklec at deviantART") is my favourite. I was using it to set a theme, but something must’ve gone wrong. explorer.exe got corrupted somehow and it was not starting on boot. And I had no backup of the original. If Theme Manager made a backup somewhere, I couldn’t find it.

I restarted the PC and hit F8 during boot to bring up the extended boot menu. I thought I’d find “Startup Repair” there, but I was wrong. All I got were a bunch of Safe Modes and a few other options. Luckily, my decision to have an Ubuntu dual boot proved helpful. I booted into Ubuntu and got online for solutions. I kept seeing a command: “sfc /scannow” all over the forums. That command basically check the integrity of all the system files (by verifying their checksums, presumably) and if it finds any corrupt files, it replaces those with the original file stored in the repository (C:\Windows\winsxs).

I booted back into Windows, but there was no explorer again. I logged into my user, hit Ctrl+Alt+Del, and got to task manager. Tried File > Run > explorer without luck (obviously, since explorer was corrupt). I started cmd.exe and ran “sfc /scannow” but alas, I had to have admin privileges to run that command! And I couldn’t, for the life of me, figure out how to start a cmd prompt with admin privileges. All the posts on the internet were describing the GUI way (from the start menu), but I didn’t have a start menu without explorer. Then I somehow found **[this blog post](http://jpassing.com/2007/12/08/launch-elevated-processes-from-the-command-line/)** about a nice utility written in C called elevate. With the help of that utility, I was able to start an elevated cmd prompt, run the “sfc /scannow” command, and reboot into a working Windows session, and all was well again.

So, in summary:

  * Always make a backup of all the files that you will change when you theme.
  * [Theme Manager](http://bickelk.deviantart.com/art/Theme-Manager-Windows-7-176165228 "Theme Manager for WIndows 7 by bicklec at deviantART") is a great tool for managing Windows themes.
  * Should something go wrong, run “sfc /scannow” with “[elevate.exe](http://jpassing.com/2007/12/08/launch-elevated-processes-from-the-command-line/)”

Have fun theming!
