# Perform operations such as freezing, unfreezing and data query through the provider
 [[toc]]

 ## Version requirements
 -**Freezeyou** version is not less than **9.0**.
 -Some require a higher version (marked).

 ## Authorization scope
 -Get the current running mode of __自冻(freezeyou)__, get the list of frozen applications, and get whether the application can be installed through __自冻(freezeyou)__<badge text="9.2+" type="tip"/>  , Perform freezing application operations and unfreeze application operations.

 ## how to use

 ### Declare permissions
 -Need to declare permissions in `androidmanifest.xml` (apply on demand)
   -Get the current running mode of __自冻(freezeyou)__:
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.QUERY_STATUS" />
     ```
   -Get whether the app is frozen:
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.QUERY_STATUS" />
     ```
   -Perform defrosting application operations:
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.ENABLE_APPLICATIONS" />
     ```
   -Perform freezing application operations:
     ``` xml
     <uses-permission android:name="cf.playhi.freezeyou.permission.DISABLE_APPLICATIONS" />
     ```

 ### Code example
 -Get the current operating mode:
   ``` java
   Bundle resultBundle = getContentResolver().call(
       Uri.parse("content://cf.playhi.freezeyou.export.QUERY"),
       "QUERY_MODE", null, new Bundle()
   );
   String currentMode = resultBundle.getString("currentMode", "Failed");
   ```

 -Get whether the app is frozen:
   ``` java
   Bundle willBeSend = new Bundle();
   willBeSend.putString("packageName", packageName);
   Bundle resultBundle = getContentResolver().call(
       Uri.parse("content://cf.playhi.freezeyou.export.QUERY"),
       "QUERY_FREEZE_STATUS", null, willBeSend
   );
   int resultStatusCode = resultBundle.getInt("status", 123456);
   ```

 -Perform defrosting application operations:
   ``` java
   Bundle willBeSend = new Bundle();
   willBeSend.putString("packageName", pkgName);
   Bundle resultBundle = getContentResolver().call(
       Uri.parse("content://cf.playhi.freezeyou.export.UNFREEZE"),
       "MODE_AUTO", null, willBeSend
   );
   int resultCode = resultBundle.getInt("result", 123456);
   ```

 -Perform freezing application operations:
   ``` java
   Bundle willBeSend = new Bundle();
   willBeSend.putString("packageName", pkgName);
   Bundle resultBundle = getContentResolver().call(
       Uri.parse("content://cf.playhi.freezeyou.export.FREEZE"),
       "MODE_AUTO", null, willBeSend
   );
   int resultCode = resultBundle.getInt("result", 123456);
   ```

 ## Parameter requirements

 | Use | Uri | Method | Arg | Extras |
 | ------------- | -----------------------------------  ---------------------- |:-------------:|:-----:| ---  ------ |
 | Get the current running mode | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY")` | `QUERY_MODE` | Not applicable | Empty Bundle |
 | Get whether the application is frozen | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY")` | `QUERY_FREEZE_STATUS` | Not applicable | Bundle, the key packageName must contain the name of the queried application package |
 | Get whether the application can be installed through **self-freezing**<Badge text="9.2+" type="tip"/> | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY)`  | `QUERY_IF_CAN_INSTALL_APPLICATIONS_STATUS` | Not Applicable | Empty Bundle |
 | Perform unfreezing application operations | `Uri.parse("content://cf.playhi.freezeyou.export.UNFREEZE")` | `MODE_AUTO` or `MODE_ROOT` or `MODE_MROOT` | Not applicable | Bundle, key packageName must contain  The name of the unfrozen application package |
 | Perform freezing application operations | `Uri.parse("content://cf.playhi.freezeyou.export.FREEZE")` | `MODE_AUTO` or `MODE_ROOT` or `MODE_MROOT` | Not applicable | Bundle, key packageName must contain  Frozen application package name |


 ## Return data
 ___If the corresponding key value is `null`, check whether the `Method` and `Extras` in the request are `null`.  ___

 | Return value | Get the current running mode (key currentMode) | Get whether the application is frozen (key status) | Perform an unfreeze application operation (key result) | Perform a frozen application operation (key result) | Get whether the application can be installed through self-freezing (  Key status) |
 | ----- | ------------------------------- | -----------  ----------------- | --------------------------- | ----  ---------------------- | ----------------------- |
 | dpm | DPM (ROOT free) mode (ROOT mode may be available) | Not Applicable | Not Applicable | Not Applicable | Not Applicable |
 | root | ROOT mode (DPM mode is not available) | Not Applicable | Not Applicable | Not Applicable | Not Applicable |
 | unavailable | DPM and ROOT modes are not available | Not applicable | Not applicable | Not applicable | Not applicable |
 | -4 | Not Applicable | Not Applicable | ROOT Mode Defrosting Failed | ROOT Mode Freezing Failed | Not Applicable |
 | -3 | Not Applicable | Not Applicable | DPM Mode Defrosting Failed | DPM Mode Freezing Failed | Not Applicable |
 | -2 | Not Applicable | The packageName key value in the Bundle is null | The packageName key value in the Bundle is null | The packageName key value in the Bundle is null | Not applicable |
 | -1 | Not applicable | FreezeYou internal error | FreezeYou internal error | FreezeYou internal error | Not applicable |
 | 0 | Not Applicable | Not Frozen | Successfully Thawed | Successfully Frozen | Not Applicable |
 | 1 | Not Applicable | ROOT Mode Freeze | Not Applicable | Not Applicable | Not Applicable |
 | 2 | Not Applicable | DPM Mode Freeze | Not Applicable | Not Applicable | Not Applicable |
 | 3 | Not Applicable | DPM + ROOT Dual Mode Freeze | Not Applicable | Not Applicable | Not Applicable |
 | 998 | Not applicable | Corresponding application not found | Corresponding application not found | Corresponding application not found | Not applicable |
 | 999 | Not Applicable | Not Applicable | Check that it is not frozen, no need to defrost | Check that it is not thawed, no need to freeze | Not applicable |
 | Others | Not Applicable | Not Applicable | Not Applicable | Not Applicable | boolean\[\]{Estimation function is available, installation channel is available, ROOT permission, DPM permission} |

 ## Sample
 -[FreezeYouApiTest](https://github.com/Playhi/FreezeYouApiTest)

 ## FAQ
 ### SecurityException
   -Has the permission been declared in the **Manifest** (`freeze\unfreeze the application` also needs to be similar to requesting sensitive permissions **`requestPermissions`**).

 ## Current Limitation
 -You need to install or update (overwrite installation) applications that use relevant permissions after installing **self-freezing FreezeYou**, otherwise, an Exception may be reported (it is mentioned in the Android Google documentation that it needs to be installed before request).

 ## Need Help
 * [Join QQ Group(704086494)](https://jq.qq.com/?_wv=1027&k=l356Aq75)
 -[Join QQ Group(838379270)](https://jq.qq.com/?_wv=1027&k=5vmxG1F)
