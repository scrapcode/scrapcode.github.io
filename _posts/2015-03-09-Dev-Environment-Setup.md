---
title: Dev Environment Setup
layout: post
date: 2015-03-09 17:00:00
---

I recently installed a fresh copy of Xubuntu 14.04 LTS along side of
Windows 7 on my desktop. I find myself trying to recreate my
"development comfort zone" across many different platforms, VPS', etc.
for many different reasons that I wont get into. I wanted to document
what my typical development environment looks like, and what I generally
go through everytime when setting up a fresh box.

### Xubuntu 14.04 LTS

All of this was done in Xubuntu 14.04 LTS (Ubuntu using XFCE), so YMMV.

### Vim, cURL, Git

    sudo apt-get install vim curl git

Vim is my go-to editor. It can be a pain in the ass when you're bouncing
around on different machines because the configuration can be such a
hassle. To remedy this, I recommend keeping your `.vimrc` in a
repository on [GitHub](http://github.com), or using
[Janus](http://github.com/carlhuda/janus) which I do below.

cURL and Git are now only used a lot in my regular workflow, but they
are required to install much of the rest of my environment below so we
install them first.

### Ruby

    sudo apt-get install ruby-full

This gets mostly everything I need in regards to Ruby.

### [Janus](http://github.com/carlhuda/janus)

    cd ~/.vim && curl -Lo- https://bit.ly/janus-bootstrap | bash

Janus installs a lot of awesome plugins for Vim and organizes Vim
configuration in a pleasurable way. Checkout their GitHub page for more
information.

### Monokai colorscheme

    cd ~/.vim/janus/vim/colors && git clone https://github.com/sickill/vim-monokai.git

If you've ever used Sublime Text, you're familiar with this sexy
colorscheme.

<strong>Edit:</strong> I've since switched to a heavily modified version of Monokai called [wells-colors](https://github.com/wellsjo/wells-colorscheme.vim)

### Node.js and NPM

    curl -sL https://deb.nodesource.com/setup | sudo bash -

    sudo apt-get install -g nodejs

### Express.js

    sudo npm install -g- express express-generator

This installed Express.js and the Node.js Express-Generator so that we
can use commands such as "express my-website"

### Angular.js

    sudo npm install -g angular

### MongoDB

    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

    echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list

    sudo apt-get update

    sudo apt-get install -y mongodb-org

Run all of these commands seperately. Mongo is now accessible using

    sudo service mongod start
    sudo service mongod stop
    sudo service mongod restart

### RVM

    gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3

    \curl -sSL https://get.rvm.io | bash -s stable --ruby

### Rails

    gem install rails

### Java

Java might take a little more legwork via Google-fu. I would generally
recommend using OpenJDK and installing via their documentation, but
since I want to use Java 8, I installed it via the [source code
available from
Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html).

    sudo mkdir /usr/lib/jvm
    tar -zxvf jdk-1.8.0_40.tar.gz
    mv jdk-1.8.0_40 /usr/lib/jvm/jdk-1.8.0_40

After you install it to /usr/lib, export the path to your JAVA_HOME:

    export JAVA_HOME=/usr/lib/jvm/jdk-1.8.0_40

Then add that to your PATH:

    export PATH=$PATH:$JAVA_HOME

I recommend adding those settings to you .bash_profile, or in Ubuntu's
case, ~/.profile.

### GNU Screen

    sudo apt-get install screen

After you get disconnected from your ssh session a few times you'll
really come to appreciate the value of GNU Screen or Tmux, even if you
don't use it for their other amazing features. I mainly use screen to
switch between windows and save the session for picking up at another
time. I will post a short post later on the basics of GNU Screen if
there's any interest.

### IRSSI

    sudo apt-get install irssi
    mkdir ~/.irssi ~/.irssi/scripts
    cd ~/.irssi/scripts && wget http://wouter.coekaerts.be/irssi/scripts/nicklist.pl

IRSSI is by far my favorite IRC client in linux. When using IRSSI in GNU
screen, I also load the nicklist.pl script to show the online nicklist
to the right of the channel and bind '[' and ']' to scroll up and down
the list. `irc.freenode.net` still has a lot of very smart people
hanging around.


### Any suggestions?

I'm sure there is a lot I could improve on in the way that I do things,
and as I use this configuration I'll find better ways of doing things
and will update this document accordingly. I really needed to document
this for my own use since I'm always forgetting little things here and
there and wasting precious time searching for answers to my environment
setup problems rather than coding.

What would you do different?
