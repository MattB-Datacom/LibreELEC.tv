# LibreELEC

This repository holds a custom fork of LibreELEC. It tracks the official LibreELEC releases, but with the following modifications.

* A fix to detect incorrectly tagged 23.976fps content to avoid refresh rate changes after the video has started playing. 
* OpenSSL replaced with LibreSSL

The fix for 23.976fps content is primarily to aid the playback of Anime which is typically released with invalid scale and rate values. Without this change, playback will initially default to 60fps, and a few seconds later switch the display to 23.976fps once the actual frame rate has been correctly worked out. This causes playback to be interrupted for a few seconds in a very ugly way. It's the files themselves that are at fault, and my fix is a dirty hack, but I preferred to just make LibreELEC just deal with it rather than to have to apply a patch to every faulty MKV I see.

LibreELEC also switched back to use OpenSSL [some time ago](https://github.com/LibreELEC/LibreELEC.tv/pull/1312) due to LibreSSL refusing to validate certificates with a post-2038 expiry date on 32-bit Linux systems. Personally I agree with the LibreSSL maintainers that [this behaviour is correct](https://github.com/libressl-portable/portable/issues/207), I prefer LibreSSL for security reasons, and my player is 64-bit anyway, hence I've stuck with LibreSSL here. So expect these builds will likely run into certificate problems if you make a 32-bit build. Just so you're aware, this difference will also likely make 3rd-party add-ons built for the official LibreELEC builds incompatible with any version built from these sources.

Unless you want/need these specific changes then you're better off sticking to the official LibreELEC repository [here](https://github.com/LibreELEC/LibreELEC.tv). Please do not raise issues or bug reports with the LibreELEC developers for any problems you find in this fork.

I am not associated with the LibreELEC project in any way. If you with to donate to support the project, I'd suggest you donate directly to them. Details below.

**About LibreELEC**

LibreELEC is a 'Just enough OS' Linux distribution for running the award-winning [Kodi](http://kodi.tv) software on popular mediacentre hardware. LibreELEC is a conservative fork of the popular [OpenELEC](http://openelec.tv) project with a stronger focus on pre-release testing and post-release change management. Further information on the project can be found on the [LibreELEC website](https://libreelec.tv).

**Donations**

Contributions towards current project funding goals can be sent via PayPal to donations@libreelec.tv

**License**

LibreELEC original code is released under [GPLv2](http://www.gnu.org/licenses/gpl-2.0.html).

**Copyright**

As LibreELEC includes code from many upstream projects it includes many copyright owners. LibreELEC makes NO claim of copyright on any upstream code. However all original LibreELEC authored code is copyright LibreELEC.tv. For a complete copyright list please checkout the source code to examine license headers. Unless expressly stated otherwise all code submitted to the LibreELEC project (in any form) is licensed under [GPLv2](http://www.gnu.org/licenses/gpl-2.0.html) and copyright is donated to LibreELEC.tv. This approach allows the project to stay manageable in the long term by giving us freedom to maintain the code as part of the whole without the management overhead of preserving contact with every submitter, e.g. GPLv3. You are absolutely free to retain copyright. To retain copyright simply add a copyright header to each submitted code page. If you submit code that is not your own work it is your responsibility to place a header stating the copyright.
