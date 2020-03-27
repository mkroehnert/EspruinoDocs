<!--- Copyright (c) 2020 Gordon Williams, Pur3 Ltd. See the file LICENSE for copying permission. -->
Bangle.js Troubleshooting
=========================

<span style="color:red">:warning: **Please view the correctly rendered version of this page at https://www.espruino.com/Troubleshooting+Bangle.js. Links, lists, videos, search, and other features will not work correctly when viewed on GitHub** :warning:</span>

* KEYWORDS: Troubleshooting,Trouble,Problems,Help,Broken,Not Working

What follows is a quick list of potential problems and solutions. If your problem isn't covered here, please post in the [Bangle.js Forum](http://forum.espruino.com/microcosms/1424/).

Please also check out the [Bluetooth specific troubleshooting page](http://www.espruino.com/Troubleshooting+BLE)

* APPEND_TOC

### I can't upload apps, and the IDE just says `-> Terminal` when connected

On Firmwares shipped on KickStarter Bangle.js there was a bug. Please leave `Debug Info` set to `Hide` (the default) in Bangle.js's `Settings`, then update to the latest Bootloader version using https://banglejs.com/apps (which will allow everything to work even with `Debug Info` set to `Show`).


### My Bangle.js no longer boots to the clock

This may be because the JS bootloader has been overwritten, which can
be done if you use `Save to Flash` to write code in the IDE.

* Go to https://banglejs.com/apps
* Click `About -> Install default apps` which will erase everything and return Bangle.js to default (or try installing just `Bootloader` from library)


### I can't get a GPS fix / GPS doesn't seem to be working

When you get the Bangle (or after it has run out of battery and been recharged) the GPS is in a 'fresh' state. It has no idea of the time or where it is in the world. It can take 5-10 minutes with a GPS app running **outside** or on a windowsill in order to get a fix. After having got an initial fix the GPS will be significantly faster at getting a fix next time.

**Why?** Phones and internet-connected GPS devices use AGPS (A=Assisted). They use the time and rough location info from mobile phone masts to help them get a fix much faster. Since Bangle.js doesn't have that info it's working from first principles and it can take a while to get a lock (just like any other standalone GPS device).