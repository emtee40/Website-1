# Freeze and unfreeze the application by startactivity
 [[toc]]

 ## Authorization scope
 -Get the list of frozen apps, freeze apps, and unfreeze apps.

 ## how to use

 ### Declare permissions
 -Need to declare permissions in `androidmanifest.xml` (apply on demand)

   -Get the list of frozen apps
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.GET_DISABLED_APPLICATIONS"/>
     ```

   -Perform defrost application
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.ENABLE_APPLICATIONS"/>
     ```

   -Freeze the application
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.DISABLE_APPLICATIONS"/>
     ```

 ## Sample
 -[FreezeYouApiTest](https://github.com/Playhi/FreezeYouApiTest)

 ## FAQ

 ### ActivityNotFoundException
 -The old version of FreezeYou is installed or FreezeYou is not installed

 ### SecurityException
 -Has the permission been declared in the **Manifest** (`freeze\unfreeze the application` also needs to be similar to requesting sensitive permissions **`requestPermissions`**

 ## Current Limitation
 -You need to install or update (overwrite installation) applications that use relevant permissions after installing **FreezeYou**, otherwise, an Exception may be reported (in the Android Google documentation, it is mentioned that it needs to be installed before request)

 ## Need Help
 * [Join QQ Group(704086494)](https://jq.qq.com/?_wv=1027&k=l356Aq75)
 * [Join QQ Group(838379270)](https://jq.qq.com/?_wv=1027&k=5vmxG1F)
