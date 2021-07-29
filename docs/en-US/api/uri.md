# Freeze and unfreeze the application via uri
 [[toc]]

 ## Authorization scope
 -Call up the **freeze/unfreeze/start** dialog box of **freezeyou** (for safety reasons, the first **freeze/unfreeze/start** specific operations must be done by the user independently).

 ## how to use

 ### Embed html
 #### Request Freeze/Unfreeze/Start [app package name]
 ``` html
 <a href="freezeyou://fuf/?pkgName=[app package name][&action=[action]]">request to freeze/thaw/start [app package name]</a>
 ```

 #### Request Freeze/Unfreeze/Start USIM Card Application
 ``` html
 <a href="freezeyou://fuf/?pkgName=com.android.stk">Request to freeze/unfreeze/start USIM card application</a>
 ```
 [Click here to try to freeze/unfreeze/start the USIM card application (com.android.stk)](freezeyou://fuf/?pkgName=com.android.stk)

 #### Request to freeze/unfreeze/start USIM card application <Badge text="8.3+" type="tip"/>
 ``` html
 <a href="freezeyou://fuf/?pkgName=com.android.stk&action=fuf">Request to freeze/unfreeze/start USIM card application</a>
 ```
 [Click here to try to freeze/unfreeze/start the USIM card application (com.android.stk)](freezeyou://fuf/?pkgName=com.android.stk&action=fuf)

 #### Request to unfreeze the USIM card application <Badge text="8.3+" type="tip"/>
 ``` html
 <a href="freezeyou://fuf/?pkgName=com.android.stk&action=unfreeze">Request to unfreeze the USIM card application</a>
 ```
 [Click here to try to unfreeze the USIM card application (com.android.stk)](freezeyou://fuf/?pkgName=com.android.stk&action=unfreeze)

 #### Request to freeze the USIM card application <Badge text="8.3+" type="tip"/>
 ``` html
 <a href="freezeyou://fuf/?pkgName=com.android.stk&action=freeze">Request to freeze the USIM card application</a>
 ```
 [Click here to try to freeze the USIM card application (com.android.stk)](freezeyou://fuf/?pkgName=com.android.stk&action=freeze)

 #### Request to unfreeze and start (if unfrozen, start directly) USIM card application <Badge text="8.3+" type="tip"/>
 ``` html
 <a href="freezeyou://fuf/?pkgName=com.android.stk&action=unFreezeAndRun">request to unfreeze and start (if it is unfrozen, start directly) USIM card application</a>
 ```
 [Click here to try to defrost and start (if it has been defrosted, start directly) USIM card application (com.android.stk)](freezeyou://fuf/?pkgName=com.android.stk&action=unFreezeAndRun)


 ### Application Room
 ``` java
 Uri webPage = Uri.parse("freezeyou://fuf/?pkgName=" + pkgName);
 Intent intent = new Intent(Intent.ACTION_VIEW, webPage);
 if (intent.resolveActivity(getPackageManager()) != null) {
    startActivity(intent);
 } else {
    Toast.makeText(MainActivity.this, "There is no program available. Have you installed FreezeYou 7.2 and above?", Toast.LENGTH_LONG).show();
 }
 ```

 ## Sample
 -[FreezeYouApiTest](https://github.com/FreezeYou/FreezeYouApiTest)

 ## Need Help
 * [Join QQ Group(704086494)](https://jq.qq.com/?_wv=1027&k=l356Aq75)
 -[Join QQ Group(838379270)](https://jq.qq.com/?_wv=1027&k=5vmxG1F)
