---
layout: post
date: "2016-06-07T01:17:24+05:30"
title: "GNOME Online Accounts: Extending the ownCloud Provider"
categories: ["GNOME", "GSoC"]
---

GNOME Online Accounts (GOA) has had support for ownCloud since quite some time. As a part of my project, I've been extending the ownCloud provider to add support for the Music feature.

![GOA ownCloud](https://i.imgur.com/6MXnHA2.png)

ownCloud provides a neat [music app](https://github.com/owncloud/music) which allows users to access their music collection, while at the same time, it provides application developers with a rich [API](https://github.com/ampache/ampache/wiki/XML-API). The Ampache API rightly supports authentication and requires a password to be generated which is distinct from the user's ownCloud credentials.

![ownCloud Music Generate Password](https://i.imgur.com/KGPp3cg.png)

While one can manually generate a password for the Ampache API via ownCloud's settings, we decided it would be better to automatically generate the password when the user sets up the ownCloud account on GOA for the first time, and store it along with the ownCloud credentials in the Keyring. This meant extending ownCloud's music app to provide some endpoints for password generation (to be covered in detail in another post).

Since ownCloud's music app isn't a part of ownCloud core, there were a few special cases that needed attention:

* If the music app isn't enabled on ownCloud's end, the music feature is disabled.
* In case the music app is disabled after the the password has been generated, [EnsureCredentials](https://developer.gnome.org/goa/stable/gdbus-org.gnome.OnlineAccounts.Account.html#gdbus-method-org-gnome-OnlineAccounts-Account.EnsureCredentials) would return failure.
* A new method, RetryFeature will be available on the [Account Interface](https://developer.gnome.org/goa/stable/gdbus-org.gnome.OnlineAccounts.Account.html) which would allow the user to enable Music feature at a later time, in case ownCloud's music app was not available initially.

The code for the above mentioned features is [being reviewed](https://bugzilla.gnome.org/show_bug.cgi?id=753415) and should hopefully be merged soon :)

## What's next?

Now that GOA supports storing the Ampache API credentials, we can retrieve and use them for the implementation of a [grilo plugin](https://bugzilla.gnome.org/show_bug.cgi?id=676366). The Lua-factory plugin allows writing Grilo sources in LUA and I've recently extended it to support password based GOA accounts. In the coming week, I plan to work on the lua plugin for ownCloud/Ampache.
