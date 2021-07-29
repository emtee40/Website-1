# scheduled task
 [[toc]]

 ## general task commands

 ### available commands

 * `okff`: One key freeze.
 * `okuf`: One key unfreeze.
 * `ff`: Freeze.
 * `uf`: Unfreeze.
 * `es`: enable a setting item <small>* (available from 6.2 version `wifi`; from 7.1 version available `cd` (cellular mobile data network); from 7.3 version available `bluetooth`)*</small>.
 * `ds`: Turn off a setting item <small>* (available from 6.2 version `wifi`; from 7.1 version available `cd` (cellular mobile data network); from 7.3 version available `bluetooth`)*</small>.
 * `st`: Show one toast.
 * `sn` <Badge text="8.6+" type="tip"/>: Show one notification.
 * `sp`: Open the specified application.
 * `su`: Open the specified application by URI.
 * `lg` <Badge text="7.2+" type="tip"/>: Print an ERROR level LOG, generally there is no need to use it.
 * `ls` <Badge text="8.7+" type="tip"/>: Lock screen.

 ### Additional Parameters(Optional)

 * `-d` <Badge text="7.2+" type="tip"/>: Delay execution, the unit is `seconds`.

 ### Internal Variables

 * `[ppkgn]` <Badge text="7.4+" type="tip"/>: The package name of the previous application.  Only the trigger can be used when leaving the application and when opening the application. You can use `st [ppkgn]` to understand the relevant content in related tasks before formal use to reduce the possibility of accidental freezing.
 * `[cpkgn]` <Badge text="7.4+" type="tip"/>: The current application package name.  The only trigger can be used when leaving the application, opening the application, thawing the application, and freezing the application. Before the official use, you can use `st [cpkgn]` to understand the related content and reduce the possibility of accidental freezing.

 ### Usage Example

 #### okff

 * `okff`: Execute one-key freeze immediately.

 #### okuf

 * `okuf`: Execute one-click defrosting immediately.
 * `okuf -d 10`: Delay for 10 seconds to perform one-key defrosting.

 #### ff

 * `ff com.tencent.mobileqq`: Freeze the application whose package name is `com.tencent.mobileqq` (QQ).
 * `ff com.tencent.mobileqq,@5oiR55qE5YiX6KGo`: Freeze the package named `com.tencent.mobileqq` (QQ) and `exist in my self-selected` application with the alias of 5oiR55qE5YiX6KGo.
 * `ff com.tencent.mobileqq,com.tencent.mm`: Freeze applications with package names `com.tencent.mobileqq` (QQ) and `com.tencent.mm` (WeChat).
 * `ff com.tencent.mobileqq,com.tencent.mm,com.taobao.taobao`: the frozen package names are `com.tencent.mobileqq` (QQ) and `com.tencent.mm` (WeChat) and `com  .taobao.taobao` (淘宝) application.
 * `ff -d 3600 com.tencent.mobileqq`: Delay 3600 seconds to freeze the application named `com.tencent.mobileqq` (QQ).

 #### uf

 * `uf com.tencent.mobileqq`: Unfreeze the application whose package name is `com.tencent.mobileqq` (QQ).
 * `uf com.tencent.mobileqq,com.tencent.mm`: Unfreeze applications with packages named `com.tencent.mobileqq` (QQ) and `com.tencent.mm` (WeChat).
 * `uf com.tencent.mobileqq,@5oiR55qE5YiX6KGo`: Unfreeze the package named `com.tencent.mobileqq` (QQ) and `exist in my self-selected` application with the alias of 5oiR55qE5YiX6KGo.
 * `uf com.tencent.mobileqq,com.tencent.mm,com.taobao.taobao`: the unfrozen package names are `com.tencent.mobileqq` (QQ) and `com.tencent.mm` (WeChat) and `com  .taobao.taobao` (淘宝) application.

 #### es

 * `es wifi`: Enable WiFi.
 * `es -d 20 wifi`: Delay for 20 seconds to enable WiFi.
 * `es wifi,cd`: enable WiFi and cellular mobile data network.
 * `es wifi;okuf;uf com.tencent.mobileqq`: enable WiFi, perform one-key defrost, and defrost the application whose package name is `com.tencent.mobileqq` (QQ).

 #### ds

 * `ds wifi`: Turn off WiFi.
 * `ds cd`: Turn off the cellular mobile data network.
 * `ds wifi;okff`: Turn off WiFi and perform one-key freeze.
 * `ds -d 15 wifi;okff`: Delay for 15 seconds to turn off WiFi and immediately perform one-key freeze.

 #### st

 * `st This is a prompt`: Display a Toast prompt with the content of `This is a prompt`.

 #### sn

 * `sn notification title, notification content`: display a notification in the notification bar.

 #### sp

 * `sp com.tencent.mobileqq`: Open QQ (package name is `com.tencent.mobileqq`).
 * `sp com.tencent.mobileqq,com.tencent.mm`: Open QQ and WeChat (package names are `com.tencent.mobileqq` and `com.tencent.mm`).

 #### su

 * `su [Uri]`: Try to open the specified Uri.  (Refer to: [each application URL Scheme](//www.urischeme.com))
 * `su alipayqr://platformapi/startapp?saId=20000056`: Open the Alipay payment code.

 #### lg

 * `lg 10086`: output an ERROR level LOG with the content of 10086.

 #### ls

 * `ls`: Lock the screen.

 ## Trigger additional parameters

 ### Use Preface

 * Some triggers do not need additional parameters (if they are filled in, they will be ignored).
 * Some triggers can fill in additional parameters (not required).
 * Some triggers must provide additional parameters that meet the conditions, otherwise they cannot be executed normally.

 ### Parameter requirements

 * `When opening the screen`: There are currently no additional parameters.
 * `When closing the screen`: There are currently no additional parameters.
 * `When opening the application`: *<small> `7.0 and earlier versions` </small>* Must attach `application package name`; *<small> `From 7.0` </small>* may attach `application package name`  , `My list`*<small>`(V9.2)`</small>*, if there is no additional, open any application and execute it.  *With the application package name attached, under normal circumstances, when opening the XX application, all delayed tasks that have been deployed but not yet executed when leaving the XX application will be cancelled.  *
 * `When leaving the application`: You can attach `application package name`, `my list` <small>*`(V9.2)`*</small>. If there is no attachment, leave any application to execute.  *With the application package name attached, under normal circumstances, when leaving the XX application, all delayed tasks that have been deployed but not yet executed when the XX application is opened will be cancelled.  *
 * `When unfreezing an application`: You can add an `application package name`. If there is no attachment, any application will be unfreezed and executed.
 * `When freezing the application`: You can attach the `application package name`, if there is no attachment, any application will be frozen and executed.

 ### Available parameters

 * `App package name`: For example, `com.tencent.mobileqq`.
 * `My list`: For example, `@5oiR55qE5YiX6KGo`.

 ### Use case

 * Select `When opening the application` and fill in the additional parameter `com.tencent.mobileqq`, then the preset `task` will be executed when running `QQ`.
 * Select `When opening the application` and fill in the additional parameters `com.tencent.mobileqq,com.tencent.mm`, then the preset `task` will be executed when running `QQ` or `WeChat`.
 * Select `When opening the application`, and fill in the additional parameters of `com.tencent.mobileqq,@5oiR55qE5YiX6KGo`, and the preset `tasks will be executed when running `QQ` or `applications in the list with alias 5oiR55qE5YiX6KGo`  `.
 * Select `When opening the application`, fill in the additional parameter of the `package name of the currently used desktop`, and the preset `task` will be executed when **return to the desktop**.
 * If you select `When leaving the application`, the additional parameters do not fill in any content, and the preset `task` will be executed when **leave any application**.

 ## FAQ
 * [FAQ](../faq/)
