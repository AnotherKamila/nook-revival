# nook-revival
Reviving my 6-year-old Nook Classic: collecting materials from the now-dead NookDevs wiki and such

![nook with new launcher](n.jpg)

Thanks to
=========

NookDevs (no link, site is dead). Also, [The Wayback Machine](https://web.archive.org/web/) (as the NookDevs site is dead).

What's in here
==============

Various apps by NookDevs, plus some of my personal customizations.

Who is responsible if the Nook blows up or eats your children if you use this
=============================================================================

You.

(I also never checked the included files for backdoors. I don't really care if someone tries to attack my 6-year-old e-reader that I never connect to public WiFi via APKs that took me the whole evening to collect online. But *do* mind that by rooting the Nook you are giving root access via WiFi to anyone who cares to check.)

What are these things?
======================

As I have stuff in my head and nobody else uses this, I have been too lazy to document things properly. In the unexpected case that you do use this, please ask me to document whatever you need documented.

How to
======

Step 0: rooting the Nook
------------------------

See https://github.com/ruediste-zz/NookPDFViewer/wiki/Installation. This procedure may take quite a few tries, but in the end it worked for me.
The needed file (`ratc.bin`) is included in this repo under `rooting/`.

Apps
====

`apks` contains APKs by NookDevs that I found useful. The following is in there:

- ru.mynook.launcher: a customizable replacement for the original B&N home/launcher
- Home: replaces the original home with a version that does not get in the way of the new launcher, so that the system defaults to the new one
  - this must replace the original Home app -- install by `adb push Home.apk /system/app`
- nookLibrary: a better library
- trook: an awesome RSS reader / file browser / Calibre catalog browser (!!!)
- orion_viewer: better PDF viewer
- nookBrowser: an alternative web browser
- nooklet: container for apps written in HTML+JS :-)
- Music: stock old Android music app, with buttons moved to the touchscreen/arrow keys

Also see https://web.archive.org/web/20140109090359/http://nookdevs.com/Application_Directory.  
`orig-apks` collects all original APKs (from firmware 1.7)

Accessing your Calibre collection on the Nook wirelessly
========================================================

1. Run calibre-server somewhere:
   - you can launch it from the GUI on your laptop, but this is not very useful
   - you can run it on a server from the commandline:  
     `calibre-server --port=$PORT --username=$USERNAME --password=$PASSWORD --with-library=$LIBRARY`
   - you probably want to stick it behind a reverse proxy (I like NGINX), so that you can add HTTPS and use the standard port and such
2. install the Trook app
3. if you want two-click access, install a custom root feed with the correct address:
   I have included the default `root.xml` + extra first entry in `customizations/my feeds`; you need to edit your library's parameters and put it into a folder named `my feeds` in the root of the Nook.

   Edit *both* occurences of `https://$USERNAME:$PASSWORD@$HOST:$PORT/stanza`. If you don't use https, change that to http. Hint: Testing the URL in a browser is easier than on device. (You should see an RSS feed if it works.)

   Note: [Let's Encrypt](https://letsencrypt.org/) HTTPS certificates don't work with Trook (too old for that). Coming up with a solution is a WIP. See http://wiki.cacert.org/FAQ/ImportRootCertAndroidPreICS .

My customizations
=================

`customizations` contains

- icons for the launcher that I use
- a new root feed for Trook, including an entry where you should write your Calibre server's address

Just stick any of the subfolders into the root of your Nook to apply it.

Virus detected?
===============

That's expected -- see [#1](https://github.com/AnotherKamila/nook-revival/issues/1#issuecomment-503560472) for more details.

License
=======

This repository only collects third-party files for convenience. Everything
is licensed by the original authors. These files are licensed under various
open-source licenses, such as Apache 2.0. If you want to build on anything in
this repository, you must find the original licenses.
([The Wayback Machine](https://web.archive.org/web/) may be of use.)

My contributions (if any) are licensed under the MIT license.
