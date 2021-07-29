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

| Use           | Uri                                                       | Method        | Arg   | Extras    |
| ------------- | --------------------------------------------------------- |:-------------:|:-----:| --------- |
| Get current operating mode | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY")` | `QUERY_MODE` | Not applicable | Null Bundle |
| Get whether the app is frozen | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY")` | `QUERY_FREEZE_STATUS` | Not applicable | Bundle，key packageName Must contain the name of the application package being queried |
| Access is available**FreezeYou**Install the app<Badge text="9.2+" type="tip"/> | `Uri.parse("content://cf.playhi.freezeyou.export.QUERY)` | `QUERY_IF_CAN_INSTALL_APPLICATIONS_STATUS` | Not applicable | null Bundle |
| Perform defrosting application operations | `Uri.parse("content://cf.playhi.freezeyou.export.UNFREEZE")` | `MODE_AUTO`或`MODE_ROOT`或`MODE_MROOT` | Not applicable | Bundle，key packageName Must contain the name of the application package to be unfrozen |
| Perform freezing application operations | `Uri.parse("content://cf.playhi.freezeyou.export.FREEZE")` | `MODE_AUTO`或`MODE_ROOT`或`MODE_MROOT` | Not applicable | Bundle，key packageName Must contain the name of the frozen application package |


 ## Return data
___If the corresponding key value is `null`，Then check the request `Method` as well as `Extras` Is it `null`.___

| return value | Get current operating mode（key currentMode）| Get whether the app is frozen（key status）| Perform defrosting application operations（key result）| Perform freezing application operations（key result）| Get whether the app can be installed through self-freezing（key status) |
| ----- | ------------------------------- | ---------------------------- | --------------------------- | -------------------------- | ----------------------- |
| dpm | DPM（waived ROOT）model（ROOT Mode may be available） | Not applicable | Not applicable | Not applicable | Not applicable |
| root | ROOT model（DPM Mode is not available） | Not applicable | Not applicable | Not applicable | Not applicable |
| unavailable | DPM and ROOT None of the modes are available | Not applicable | Not applicable | Not applicable | Not applicable |
| -4 | Not applicable | Not applicable | ROOT Mode thawing failed | ROOT Mode freeze failed | Not applicable |
| -3 | Not applicable | Not applicable | DPM Mode thawing failed | DPM Mode freeze failed | Not applicable |
| -2 | Not applicable | Bundle middle packageName Key value null | Bundle middle packageName Key value null | Bundle middle packageName Key value null | Not applicable |
| -1 | Not applicable | (FreezeYou) internal error | (FreezeYou) internal error | (FreezeYou) internal error | Not applicable |
| 0 | Not applicable | Not frozen | Thawed successfully | Freeze successfully | Not applicable |
| 1 | Not applicable | ROOT Mode freeze | Not applicable |Not applicable | Not applicable |
| 2 | Not applicable | DPM Mode freeze | Not applicable | Not applicable | Not applicable |
| 3 | Not applicable | DPM + ROOT Dual mode freeze | Not applicable | Not applicable | Not applicable |
| 998 | Not applicable | No corresponding application found | No corresponding application found | No corresponding application found | Not applicable |
| 999 | Not applicable | Not applicable | Check that it is not frozen, no need to thaw | The inspection found that it is not thawed, no need to freeze | Not applicable |
| other | Not applicable | Not applicable | Not applicable | Not applicable | boolean\[\]{Estimation function is available, installation channel is available, have ROOT Authority, Have DPM permissions} |

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
