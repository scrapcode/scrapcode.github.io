---
title: Exposé / Mission Control on Xubuntu (XFCE)
layout: post
date: 2015-04-08 01:30:00
---

I'm not extremely into bells and whistles when it comes to desktop
effects, which is why I use XFCE in the first place. However, one of 
the main reasons that I can be so much more productive on my Macbook 
is because of the Exposé feature that allowed me to drag my cursor into 
a certain corner and display all of my current app windows on one screen 
and making them available for rapid selection.

So I did a little searching and ran into
[skippy-xd](https://github.com/richardgv/skippy-xd). In ubuntu,
installation was as simple as

    sudo apt-add-repository ppa:landronimirc/skippy-xd-daily
    sudo apt-get update
    sudo apt-get install skippy-xd

While digging around I've also seen some discussion about a bug in
skippy-xd that doesn't display minimized windows. Here's a fix:

    sudo apt-get install xdotool
    wget https://raw.github.com/hotice/webupd8/master/skippy-xd-fix -O
    /tmp/skippy-xd-fix
    sudo install /tmp/skippy-xd-fix /usr/local/bin/

## Activating skippy-xd via a "hot corner"

skippy-xd provides us with the ability to show all of the windows. You
can apply that to a hotkey through the XFCE's settings, or you can apply
it to execute when your mouse hits a corner using
[brightside](http://packages.ubuntu.com/precise/gnome/brightside).
Install brightside using apt:

    sudo apt-get install brightside

Brightside wont install a menu launcher, so open it manually from the
terminal using

    brightside-properties
