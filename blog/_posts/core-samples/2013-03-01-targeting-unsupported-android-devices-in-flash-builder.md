---
title: 'Targeting &#8220;Unsupported&#8221; Android Devices in Flash Builder 4.5+'
author: Spencer
layout: post
permalink: /targeting-unsupported-android-devices-in-flash-builder/
categories:
  - Uncategorized
tags:
  - Android
  - Flash Builder
---
So you are wanting to test your cool AS3 or MXML app that you made in Adobe Flash Builder on a shinny new Android tablet. One problem, when you run “On Device” your nice phone or tablet doesn’t show up, just the comforting “flash builder could not find a connected device”. Fear not, here is the solution that I have tested on the Transformer Prime, Nexus 7, and Nexus 10.

(**Update (Especially Nexus 7): **You computer may have “old drivers” setup for you device if you have plugged it in before doing steps 1 & 2. To correct this issue:  
\- go to [Device Manager][1], under “Other Devices” you’ll see “Nexus” with the yellow exclamation mark, Right Click>Upate Drivers>Let me choose>Let me pick form device drivers on my computer.  
\-Scroll down to “SAMSUNG Android Phone” (Again, the Galaxy Nexus drivers should be installed already, if not, find them), and choose the driver for “Android ADB Interface”
[Source][2])

1.  **Download the [Android SDK][3]**  

2.  **Install SDK tools**  
    a. Extract that zip somewhere  
    b. run the SDK Manager  
    c. select “Android SDK Platform-Tools” and “Google USB Driver”(at the bottom)  
    d. then click “Install Packages…” to update the platform tools.  

3. **Go to the Flash Builder install directory (ex C:/Program Files/Adobe/Adobe Flash Builder/) with Windows Explorer**  

4. **Go into the sdks\4.6.0\lib\android folder, you should have a bin folder.**  
(You might have an older version of the AIR sdk, so it might be 4.5.0 or 4.5.1, don’t worry about that)  

5. **Create a copy of the bin folder** (just ctrl C then ctrl V the folder) **so you have a backup**  

6. **Now go into the /bin directory**  
You should see the following files:
![png;base64ce2c4bd846e7c950][4]

7. **Replace the following files in the lib/android/bin** folder by copying them from your {android-skd folder}/sdk/platform-tools folder (the one your extracted in step #2):  
    - aapt.exe
    - adb.exe
    - AdbWinApi.dll
    - AdbWinUsbApi.dll  
(**Update:** If you are unable to override these files because of adb “running elsewhere”, force end adb from your Task Manager/Activity Manager.)

8. **Test the updated version** of the bridge by Shift Right Clicking in an empty space on the window with the bin folder open, then run:  
    *adb devices*  
You should see an entry under “List of devices attached”  
![png;base64615abec019a5731f][5]  
If it doesn’t list your device, you may not have the right driver installed or developer mode turned on.

9. (Only if you are running FB 4.7)  
Repeat steps 5-7 for *C:\Program Files\Adobe\Adobe Flash Builder 4.7 (64 Bit)\eclipse\plugins*

If this doesn’t work, you can contact me on twitter [@soberstadt][6] or drop a comment.

What devices are you trying to debug on? Let me know in the comments!

   [1]: http://windows.microsoft.com/en-us/windows-vista/open-device-manager (Opening Device Manager)
   [2]: http://stackoverflow.com/questions/11533228/not-seeing-nexus7-in-eclipses-android-devices (Not seeing Nexus 7 - StackOverflow)
   [3]: http://developer.android.com/sdk/index.html (Android SDK)
   [4]: /blog/wp-content/uploads/2013/03/pngbase64ce2c4bd846e7c9501.png
   [5]: /blog/wp-content/uploads/2013/03/pngbase64615abec019a5731f.png
   [6]: http://twitter.com/soberstadt
