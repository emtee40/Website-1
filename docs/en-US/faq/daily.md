# daily use-faq
 [[toc]]

 ## After clicking freeze, the corresponding application can not be found on the desktop
 - Yes.  Under normal circumstances, it will disappear without special treatment, but don’t worry, the corresponding application will reappear after thawing, and the relevant data will not be lost under normal conditions.
 -How can I easily open the corresponding application?  In the application list of `self-freeze freezeyou`, create a desktop freeze-thaw startup shortcut of the corresponding application (it is recommended to create it before freezing).

 ## Some apps cannot be unfreezed
 -Some applications are disabled (frozen) by the system (including system applications), and currently cannot be unfrozen in the root-free mode.
 -If you don't need to freeze in root mode, you need to choose __hide/unhide__ mode to unfreeze when using __self-freezefreezeyou__ in __root mode__.

 ## Why are there three icons on the desktop
 -The current new version has only one icon displayed by default.
 -Some users reported that the early version of the icon was a bit scary at night, so an icon was added later, and a circular icon for android 7.0 from the early version was separated into a single column, and finally three icons appeared spectacular.  But don't worry, these three icons can be switched on and off in `More Settings`, and even all can be turned off-use the dial pad to start (requires dial-up software support, native android default support).

 ## I accidentally turned off all three icons on the desktop, and my desktop does not support password startup freezeyou
 -Aha, don’t worry, enter `System Settings`, and then find `Freezeyou` in `Applications`. Is the familiar `Clear Data` eaten by `Manage Space`?  That's right, click on `Manage Space`, everything you are familiar with will come back!

 ## After one-key lock screen can only be unlocked by password
 -Yes, on **some** devices (especially devices that rely on Google services to unlock the face or fingerprint), for security reasons, the system is mandatory to lock the screen through the device manager  Under the prohibition of face, fingerprint, and smartlock ([Google official explanation here](https://issuetracker.google.com/issues/37010802#comment110)).
 -Starting from the `5.2` version, using one-key lock screen on ROOT devices can no longer affect Smartlock.

 ## Why is there a small logo in the lower right corner of the shortcut on the desktop, can it be removed?
 -Starting from Android 8.0, Android will add the icon of the source application in the lower right corner of the shortcut created by the application by default.
 -Since FreezeYou version 5.3, you can find one-key freeze, one-key thaw, and one-key lock screen in the added widgets (widgets) of the desktop. There is no logo in the lower right corner.
 -Since FreezeYou version 7.2, you can add desktop widgets (widgets), find the FreezeYou group, and select Freeze/Unfreeze to start widgets. There is no icon in the lower right corner. After creation, it is equivalent to creating desktop shortcuts.

 ## What is the dot on the right in the application list
 -Light gray means that the application is not frozen. If it is a theme color (such as blue), it means that the corresponding application has been frozen.

 ## One-click freeze after lock screen does not seem to take effect
 -Is the function of "one key freeze after lock screen" enabled in `More Settings`?
 -Is there no whitelist for the background service of `FreezeYou` in the system or related management software?
 -It is recommended to use the trigger `When the screen is turned off` in the `Trigger task` in the `Schedule task` to achieve a similar effect.

 ## Leaving the freeze seems to be invalid eh
 -Is the function of `Leave Freeze` enabled in `More Settings`?
 -Is the accessibility function of `FreezeYou` enabled in the system settings?
 -Is there no whitelist for the background service of `FreezeYou` in the system or related management software?

 ## The app icon seems to be transparent
 -This problem has occurred on some devices with Android 8.0 and 8.1.  How to avoid it?  Do not update or overwrite the corresponding application when the application is frozen to avoid it.

 ## The icon of the application has become an Android robot
 -This problem has occurred on some devices with Android 8.0 and 8.1.  How to avoid it?  Do not update or overwrite the corresponding application when the application is frozen to avoid it.

 ## What is the difference between **thawed start** and **freezed start**
 -`Unfreeze start` in `click function` is to start after thawing (will not freeze), while `freeze start` is a derivative function of `automatic freeze and thaw`, it will prompt when thawing or directly start the corresponding application  program.

 ## Desktop One-click freeze One-click defrost shortcuts sometimes have no effect
 -Some device systems have extremely strict restrictions on applications. Under normal circumstances, the problem disappears after enabling the battery optimization for `FreezeYou` and allowing self-starting.

 ## Cannot create desktop shortcut in FreezeYou
 -Do you allow `FreezeYou` to create shortcuts in the permissions?
 -You can try to use the `Freeze/Unfreeze/Start` desktop widget of `FreezeYou` to achieve the same effect.

 ## App clone and dual opening seem to be out of use
 -After enabling ROOT-free, some devices may not work normally with the application clone that comes with the system. If this happens, you can use other third-party clone software instead. There is currently no known better solution, if any  For better solutions, please contact us.

 ## I turned on the cache application icon but the list loading is still very slow
 -It needs to be written to the cache for the first load after it is turned on, which may take a long time.
 -If the subsequent loading time is still long, please pay attention to whether the Cache data of `FreezeYou` is cleared. The icon cache is stored in the Cache data. If it is cleared, it needs to be regenerated.
 -If the cache data is not cleared, and it is not the first time to load, it is likely that the small file reading efficiency of your device is low, and the reading cannot be completed quickly, resulting in slow loading.  This is not a big problem, just wait a little longer.

 ## In addition to displaying the main interface as a line-by-line list, is there anything else?
 -Go to `More settings`-`Appearance`-`Home page layout`, change, support list (default), grid.

 ## Can I follow the dark mode of the system to automatically adjust the daily color scheme I set to dark
 -Go to `More settings`-`Appearance`, check the `Allow automatic switch to dark mode following the system`.

 ## I want to remove the quick freeze notification of a specific application in the notification bar, but I can’t cross it
 -Go to `More Settings`-`Notification Bar`-Select the corresponding application in the `Manage Freeze/Unfreeze Quick Notifications` and remove the notification.
 -In this case, you usually select `More settings`-`Notification bar`-The option of `No sliding to remove` in `Freeze and unfreeze`, if you don’t need it, you can just close the shortcut for the notification bar created next time.  Can be removed by sliding.

 ## I (don't) want FreezeYou to appear in the recent apps list
 -Go to `More Settings`-`General`, and adjust whether the `Display in the recent task list` is enabled or not.

 ## Can you avoid freezing apps that have notifications in the notification bar?
 -Go to `More settings`-`Freeze and unfreeze`, tick `Avoid freezing apps with notifications`.

 ## Can it be avoided to freeze applications that are being used in the foreground?
 -Go to `More settings`-`Freeze and unfreeze`, check the `Avoid freezing foreground applications`.

 ## How to manage my choice
 -Go to `More settings`-`Manage space`-`Manage my preferences`, click on the desired selection to manage it.

 ## How to uninstall?
 -`More settings`-`Dangerous zone`-`Uninstall` to uninstall.  If ROOT-free is enabled, you may need to click `Remove ROOT-free` to remove permissions before uninstalling.

 ## More Faq
 * [FAQ](../faq/)

 ## Need More Help
 -[Join QQ Group(704086494)](https://jq.qq.com/?_wv=1027&k=5RJffet)
