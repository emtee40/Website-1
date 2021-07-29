# noroot-faq
 [[toc]]

 ## hint
 -If you want to enable root-free, but have not tried to enable root-free before coming here, it is recommended to go to [enable noroot](../guide/enable-mroot.html) first.

 ## adb server version doesn't match this client
 -**(Only for users of windows system)** Delete the adb file obtained after decompression and delete the larger one (approximately 2544kb), and try again?
 -Is there any PC mobile phone assistant software that occupies the relevant ports?  You can first exit the related assistant software (end its PC background, including derivative content).

 ## error: device unauthorized
 -Please click Confirm on the operated device to allow the operation.

 ## java.lang.IllegalStateException: ... there are already several accounts ... ("Trying to enable ROOT-free mode......")
 -Please check whether all the accounts in the account in your system settings have been deleted (you need to delete them all, you can manually add them back after the ROOT is not required) (the accounts that can't be deleted, you can try to delete them after disconnecting the network connection.  If it doesn’t work, you can try to back up the relevant application data first and then uninstall the relevant application, and then restore the backup after success.) If you don’t know which application’s account is not cleared, please click on `"Trying to enable ROOT-free mode..."`  At the top, look for `"Current device account information:"` In the `Accounts` group, check the item `type=`, the application package name after `=`, and then in the list of **FreezeYou**  Find the program corresponding to the package name to know which application the account comes from.
 -You can also try to restart to <b>safe mode</b> (after calling up the shutdown interface, long press the displayed "shutdown" button), and try to activate again.

 ## java.lang.IllegalStateException: ... there are already several users ... ("Trying to enable ROOT-free mode......")
 -Please check whether other users visible in your system settings have been deleted and the clone application has been closed (some clones are implemented using Android's own multi-user function, which will affect the enabling of ROOT-free), if it still fails,  You can try `adb shell pm remove-user [USER_ID]` <Badge text="This operation may cause the system's built-in clone function to not work properly" type="error"/>.

 ## java.lang.SecurityException: Neither user 2000 nor current process has android.permission.MANAGE\_DEVICE\_ADMINS
 -There is a `USB debugging (security setting)` under the `USB debugging`, which also needs to be turned on. If you are prompted to log in to your Xiaomi account, please avoid checking the synchronization option.  [MIUI announcement](https://www.miui.com/thread-5711795-1-1.html)

 ## So troublesome, is there something simpler
 -[Use AutumnBox to enable FreezeYou free ROOT mode](https://www.atmb.top/?from=freezeyou)

 ## After activation, can USB debugging be turned off?
 -Under normal circumstances, it is okay (currently, we have not received any failure or failure to turn off after being turned off). At the same time, for safety reasons, it is also recommended to `Turn off USB debugging` after activation.

 ## Can it be uninstalled after enabling?
 -It can be uninstalled, but you may need to go to `More Settings` → `Dangerous Zone` and click `Release Free ROOT`, and then uninstall normally.

 ## More Faq
 * [FAQ](../faq/)

 ## Need More Help
 -[Join QQ Group(704086494)](https://jq.qq.com/?_wv=1027&k=5RJffet)
