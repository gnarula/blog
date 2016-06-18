---
layout: post
date: "2016-06-18T15:17:24+05:30"
title: "Grilo Plugins: ownCloud source"
categories: ["GNOME", "GSoC"]
---

This week concluded weeks 3-4 of my [GSoC project](https://wiki.gnome.org/Outreach/SummerOfCode/2016/Projects/GauravNarula_MusicOwnCloud) on adding ownCloud support to GNOME Music. Carrying on from my previous post, after adding support for ownCloud Music in GOA, I've been working on implementing a grilo plugin for the same.

To a task that seemed fairly straightforward with ownCloud Music's implementation of the Ampache API, it suffered a bit of a roadblock since the app didn't support the Album Artist ID3 tag ([TPE2](http://help.mp3tag.de/main_tags.html)). This was crucial since the grilo plugin would be used by gnome-music at a later stage which uses the tag quite often.

There seems to be a bit of an ambiguity around the usage of the Album Artist tag. After digging around a bit, Michael Koby's [article](https://mkoby.com/2007/02/18/artist-versus-album-artist/) on the topic makes it pretty clear. Adding support for the tag in ownCloud music required changing the schema and rewriting a fair bit of the queries. On the frontend of ownCloud's music app, the albums will now be grouped by Album Artists instead of Track Artists which makes finding albums easier at one place in case they have tracks by different artists. The code for the above changes is being reviewed and can be accessed at [GitHub](https://github.com/owncloud/music/pull/503).

![Grouping Albums by Album Artist](http://i.imgur.com/i6cmW0R.png)

Moving on, I was excited to write the [grilo plugin](https://bugzilla.gnome.org/show_bug.cgi?id=676366) in LUA. While I didn't have much experience with the language, it didn't feel strange at all perhaps because of my familiarity with Python. Kudos to [Tyler Neylon's](https://www.youtube.com/watch?v=5uhHkeVpcgo) screencast on working with the C API and the LUA stack in particular, which immensely helped me in writing some wrapper methods in C.

![grilo-test-api showing the ownCloud source in action](http://i.imgur.com/ly5I0md.png)

Shout out to [Bastien Nocera](http://www.hadess.net/) and [Victor Toso](http://www.victortoso.com) who helped me all along during the development of the plugin and the required wrapper methods :) Next up, working on queries and moving over to the gnome-music side of things!
