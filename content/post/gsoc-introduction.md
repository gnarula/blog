+++
date = "2016-05-18T16:27:48+05:30"
title = "GSoC 2016 Introduction"
categories = ["GNOME", "GSoC"]
+++

Hi everyone! My name's Gaurav Narula and I'm a third year undergrad student at [BITS Pilani K.K. Birla Goa Campus](http://www.bits-pilani.ac.in/Goa/). I'm pursuing a double major in Economics and Computer Science.

I've been using GNOME since a long time - the first instance I recall is when I got a Live CD of Ubuntu 6.10 via ShipIt. GNOME's evolved a lot since then and has still remained my go to DE over all these years. I started with GTK+ development rather recently, with some contributions to [gnome-mpv](https://github.com/gnome-mpv/gnome-mpv), a GTK+ frontend for the MPV Media Player around October 2015.

A few months later, I stumbled upon [GNOME Music](https://wiki.gnome.org/Apps/Music) while searching for a new music player and it soon became my default music player. I then decided to become more involved with the project. I dived into its source and tried to fix some small bugs around February with assistance from [Felipe Borges](https://wiki.gnome.org/FelipeBorges), [Victor Toso](https://wiki.gnome.org/VictorToso) and [Carlos Garnacho](https://wiki.gnome.org/CarlosGarnacho) all along.

Coming to my project, GNOME Music currently only allows access to one's local music collection. Over the past few years, GNOME apps have integrated well with [ownCloud](https://owncloud.org/) to sync and retrieve files stored remotely and Music shouldn't be an exception to the same :) The goal of the project is to allow playing and searching ones music collection over ownCloud. ownCloud's [music app](https://github.com/owncloud/music) exposes an Ampache API which will be used to develop a Grilo Plugin to allow remote media discovery in Music. Victor's work in [GSoC 2013](https://wiki.gnome.org/Outreach/SummerOfCode/2013/Projects/VictorToso_LuaGriloPlugins) would allow writing the plugin in LUA and will be of great help to quickly get things working. Recent changes in ownCloud's music App with help from [Moris Jobke](http://morrisjobke.de/) have set the stage and I can't wait to begin work!

I'm fortunate to have Felipe Borges (GNOME) and [Lukas Reschke](https://statuscode.ch/) (ownCloud) as my mentors along with many other people from both the organisations who've helped me all along. Looking forward to an exciting summer ahead! Stay tuned for more updates :)
