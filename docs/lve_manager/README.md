<div class="notranslate">

# User interface (LVE Manager)

</div>

<span class="notranslate">LVE Manager</span> is a plugin for most popular control panels including cPanel, Plesk, DirectAdmin and ISPmanager (InterWorx coming soon). It allows you to control and monitor limits, and set limits on per package bases.

<span class="notranslate">LVE Manager</span> is installed by default on most servers. If it is missing you can always install it by running:

<div class="notranslate">

```
$ yum install lvemanager
```
</div>

<div class="notranslate">

## CloudLinux installation wizard

#### Overview

<span class="notranslate">CloudLinux Installation Wizard </span> allows you to easily install and set up CloudLinux OS components on your server with cPanel, Plesk or DirectAdmin.

#### Set up

As you have CloudLinux OS installed, navigate to <span class="notranslate"> CloudLinux LVE Manager </span> in your control panel. CloudLinux Installation Wizard starts automatically if <span class="notranslate"> `lvemanager` </span> package is installed for the first time (not updated).

![](/images/installationwizardmain_zoom70.png)

To start setting up your CloudLinux OS, click <span class="notranslate">_Start Wizard_</span>, otherwise click <span class="notranslate">_Skip Wizard_</span>, and you will be redirected to the <span class="notranslate"> LVE Manager Dashboard</span>.

:::tip Note
Installation statuses of all components are duplicated inside their corresponding boxes on the <span class="notranslate">Dashboard</span>. All <span class="notranslate">Wizard</span> actions are available there as well. <span class="notranslate">Dashboard</span> will be automatically updated as soon as the installation process finishes.
:::

![](/images/wizard-dashboard_zoom60.png)

The next step is selecting required components to be installed.
![](/images/installationwizardstep1_zoom70.png)

Click <span class="notranslate"> _Finish_and Install_ </span> to complete installation or click <span class="notranslate">_Skip Wizard_</span> to go back to the <span class="notranslate"> Dashboard</span>.

You can find a complete description of the CloudLinux components below.

#### CloudLinux components

<div class="notranslate">

#### **CageFS**

</div>

A virtualized per-user file system encapsulates each customer into a ‘cage’ preventing them from seeing each other files and viewing sensitive information (e.g., system files)

![](/images/wizardcagefs_zoom90.png)

Toggle the sliders to enable CageFS by default for new and/or existing users. 

:::tip Note
CageFS is a requirement for PHP Selector operation.
:::

<div class="notranslate">

#### **LSAPI**

</div>

It is the fastest and most reliable way to serve PHP pages for Apache web-servers, a drop-in replacement for SuPHP, FCGID, RUID2, and ITK.

![](/images/wizard_lsapi_zoom90.png)

LSAPI requires CRIU to operate and we also recommend you to use mod_suexec. You can find details in our [documentation](/cloudlinux_os_components/#apache-mod-lsapi-pro).

<div class="notranslate">

#### **MySQL Governor**

</div>

Monitors MySQL usage to throttle abusers, preventing server overload and improving overall performance.

![](/images/wizard_mysqlgovernor_zoom90.png)

:::tip Note
<span class="notranslate">MySQL Governor</span> can be automatically installed only with cPanel/WHM and DirectAdmin - use CLI instructions available [here](/command-line_tools/#mysql-governor) in all other cases.
:::

We recommend you to create a full database backup before the <span class="notranslate"> MySQL Governor </span> installation.

<div class="notranslate">

#### **Node.js Selector**

</div>

Allows end users to create Node.js applications and select the specific version of Node.js and other parameters.

![](/images/wizard_node.jsselector_zoom90.png)

Here you can choose versions to be installed and the version to be used as default.

<div class="notranslate">

#### **Ruby Selector**

</div>

Allows end users to select the specific version of <span class="notranslate"> Ruby</span> they need. 
![](/images/wizard_ruby_selector_zoom90.png)

Here you can choose <span class="notranslate">Ruby</span> versions to be installed.

<div class="notranslate">

#### **Python Selector**

</div>

Allows end users to select the default version of <span class="notranslate">Python</span> and set the required versions for installation.

![](/images/wizard_python_selector_zoom90.png) 


Here you can choose <span class="notranslate">Python</span> versions to be installed.

#### **PHP Selector**

Allows end users to select the specific version of PHP they need, with over 120 PHP extensions to choose from.

![](/images/wizard_php_selector_zoom90.png)

Go to <span class="notranslate">LVE Manager</span> settings to set up <span class="notranslate"> PHP Selector</span> options and parameters. Read more in the [PHP Selector documentation](/cloudlinux_os_components/#installation-and-update-4). 

:::tip Note
CageFS should be enabled for PHP Selector to operate.
:::

When the components to be installed are selected and configured, and installation is started, you will be redirected to the <span class="notranslate">LVE Manager | Dashboard</span>.

#### Installation process and possible errors

Installation status is displayed throughout the process in the <span class="notranslate">Dashboard</span>. Click <span class="notranslate">_Installing_</span> to show modules installation state.

![](/images/wizard_installation_status_zoom70.png)

All installed modules are displayed on the <span class="notranslate"> Dashboard</span>.
When installation is completed successfully, you will see the following status.

![](/images/wizardsuccess_zoom90.png)

If you decide to remove failed module or a module to be installed by clicking the (X) button, a confirmation dialog will appear.

After confirming the action, the module will disappear from the list.

![](/images/wizardinstallremove_zoom90.png)

If module installation fails, the Installing button changes to <span class="notranslate">_Warning_</span> and the module indicator will turn red.

![](/images/wizard_warning_zoom70.png)


* Click ![](/images/wizard_download_btn.png) to download the error log.
* Click ![](/images/wizard_try_again_btn.png) to try to install a module again.
* Click ![](/images/wizard_close_btn.png) to remove a specific module from the installation queue. The module will be displayed on the <span class="notranslate">Dashboard</span> but will not be installed.

If module auto-installation fails, you will see that the module indicator turns yellow.

![](/images/wizardautoinstallationfails_zoom80.png)

In this case, you can download a log for details and try to install the module again.

#### **Wizard fatal error**

In case of a fatal error, you will see the following warning.

![](/images/wizardbroken_zoom70.png)


* Click ![](/images/wizard_download_btn.png) to download the error log.
* Click ![](/images/wizard_try_again_btn.png) to try to install module(s) again.
* Click ![](/images/wizard_close_btn.png) to cancel installation. The canceled modules will be removed from the installation process.

You can contact our support team for further assistance anytime by [submitting a ticket in our helpdesk system](https://cloudlinux.zendesk.com/hc/requests/new).

## Dashboard

</div>

:::tip Note
Available starting from LVE Manager Beta version 4.0-26.8
:::

CloudLinux dashboard provides a quick overview of statistics and all administrative information for server administrators.

Go to <span class="notranslate">LVE Manager | Dashboard</span>.

![](/images/dashboard_zoom70.png)

The <span class="notranslate">Cloudlinux Dashboard</span> provides the following information:

* <span class="notranslate">End Users hitting limits</span> — number of users reaching their limit in any kind of resource. Data is within the last 24 hours.
* <span class="notranslate">Resellers hitting limits</span> —  number of enrolled Resellers that are reaching their limit in any kind of resource. Data is within the last 24 hours.
* <span class="notranslate">[Node.js Selector](/lve_manager/#node-js-selector-2)</span> block displays the following data:
  * <span class="notranslate">Node.js Selector</span> status (<span class="notranslate">Enabled/Disabled/Not installed</span>) —  displays a current status of the <span class="notranslate">Node.js Selector</span>.
  
    * To manage <span class="notranslate">Node.js Selector</span>, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Options | Node.js Selector</span>.

    * Click _Install_ to install <span class="notranslate">Node.js Selector</span>, you will be redirected to <span class="notranslate">LVE Manager | Options | Node.js.Selector</span>.
  * Default version — the current default version of Node.js set in your system. Click <span class="notranslate">_Manage_</span> to change the default version account wide.
  * <span class="notranslate">Applications</span> —  number of installed/all applications for the account.
* <span class="notranslate">Ruby Selector</span> block displays the following data:
  * <span class="notranslate">Ruby Selector</span> status (<span class="notranslate">Enabled/Disabled/Not installed</span>) — displays a current status of the Ruby Selector.

    * To manage <span class="notranslate">Ruby Selector</span>, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Options | Ruby Selector</span>.

    * Click <span class="notranslate">_Install_</span> to install <span class="notranslate">Ruby Selector</span>, you will be redirected to <span class="notranslate">LVE Manager | Options | Ruby Selector</span>.

  * <span class="notranslate">Applications</span> — number of installed/all applications for the account.
* <span class="notranslate">[PHP Selector](/lve_manager/#php-selector-2)</span> block displays the following data:
  * <span class="notranslate">Default version</span> — the default version of PHP binaries.
  Click <span class="notranslate">_Manage_</span> to change the default version, enable or disable <span class="notranslate">PHP Selector</span>, change the list of supported versions, and choose default modules. You will be redirected to <span class="notranslate">LVE Manager | PHP Selector</span>.
* <span class="notranslate">[Python Selector](/lve_manager/#python-selector-2)</span> block displays the following data:
  * <span class="notranslate">Python Selector</span> status (<span class="notranslate">Enabled/Disabled/Not installed</span> — displays a current status of the Python Selector.
  
    * To manage <span class="notranslate">Python Selector</span>, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Options | Python Selector</span>.

    * Click <span class="notranslate">_Install_</span> to install <span class="notranslate">Python Selector</span>, you will be redirected to <span class="notranslate">LVE Manager | Options | Python Selector</span>.
  * <span class="notranslate">Applications</span> —  number of installed/all applications for the account.
* [Reseller Limits](/lve_manager/#reseller-limits) block displays the following data:
  * <span class="notranslate">Reseller Limits</span> status (<span class="notranslate">Enabled/Disabled</span>). To manage <span class="notranslate">Reseller Limits</span>, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Users</span> tab.
  * Reseller’s accounts with Reseller Limits/all —  the number of Reseller accounts with Reseller Limits enabled versus the total number of Reseller accounts.
  * Reseller’s End Users with enabled Reseller Limits/all — the number of end users with Reseller Limits enabled versus all End Users that belong to all resellers.
* <span class="notranslate">[MySQL Governor](/cloudlinux_os_components/#mysql-governor)</span> block displays the following data:
  * <span class="notranslate">MySQL Governor</span> status (<span class="notranslate">Enabled/Disabled/Not installed</span>). To manage <span class="notranslate">MySQL Governor</span>, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Options | MySQL Governor Mode of Operation</span>. Click <span class="notranslate">_Install_</span> to install <span class="notranslate">MySQL Governor</span>.
  * <span class="notranslate">[Mode](/cloudlinux_os_components/#modes-of-operation)</span> — displays the <span class="notranslate">MySQL Governor</span> mode of operation. Click <span class="notranslate">_Manage_</span> to change the mode.
    * <span class="notranslate">Single</span> — single LVE is used for all customers that go over their DB limits (deprecated).
    * <span class="notranslate">Off</span> — monitor Only, no DB query limits are applied.
    * <span class="notranslate">All</span> — all queries are run inside user's LVE.
    * <span class="notranslate">Abusers</span> — only queries that go over DB limits are executed inside that user's LVE (this is the default mode).
  * <span class="notranslate">Database version</span> —  displays a current version of <span class="notranslate">MySQL/MariaDB/Percona</span> server installed in the system.
* [CageFS](/cloudlinux_os_components/#cagefs) block displays the following data:
  * <span class="notranslate">CageFS</span> status (<span class="notranslate">Enabled/Disabled/Not installed</span>). To manage CageFS, click <span class="notranslate">_Manage_</span>. You will be redirected to <span class="notranslate">LVE Manager | Options | CageFS</span>. Click <span class="notranslate">_Install_</span> to install CageFS.
  * <span class="notranslate">Mode</span> displays the current CageFS mode of operation.
  * <span class="notranslate">End users</span> — displays the number of users with CageFS enabled/all.
* [ModLSAPI](/cloudlinux_os_components/#apache-mod-lsapi-pro) block displays the following data:
  * Mod_lsapi status (<span class="notranslate">Enabled/Disabled/Not installed</span>). Click <span class="notranslate">_Install_</span> to install Mod_lsapi.
  * Module version displays the running version of Mod_lsapi.
  * [Criu_status](/cloudlinux_os_components/#criu-support) displays the status of lsapi_criu:
    * <span class="notranslate">Running</span> —  means that lsapi_criu is working.
    * <span class="notranslate">Stopped</span> —  means that lsapi_criu is not working.
  * <span class="notranslate">Total Domains</span> displays the total number of domains with Mod_lsapi configured as PHP handler.
  * <span class="notranslate">Criu_version</span> displays the running version of lsapi_criu.
  * LSAPI with connection pool.

:::tip Note
* If statistics for server is absent for any reasons, you can update it by pressing the <span class="notranslate">_Refresh_</span> button. This process can last from 10 seconds to one hour depending on your server's performance, number of users and applications.
* If statistics collection is turned off it is not displayed. If you wish to get daily statistics for your server, please turn it on by adding <span class="notranslate">`cl_statistics_enabled=1`</span> parameter to the <span class="notranslate">`/etc/sysconfig/cloudlinux`</span> file.
* Data for the Dashboard is collected once per day. If you want to update data manually, press <span class="notranslate">_Refresh_</span>. This process can last from 10 seconds to one hour depending on your server's performance, number of users and applications.
:::


## LVE Manager

<span class="notranslate">cPanel LVE Manager</span> administrator interface allows monitoring and managing limits for hosts end users, managing packages and monitoring statistics.

Administrator credentials allow controlling limits for host users.

![](/images/lvemanagermainmenu_zoom80.png)

Log in as administrator to get access to the following functionality:

* <span class="notranslate">Current usage</span> tab - allows monitoring users resource usage at the moment;
* <span class="notranslate">Users</span> tab with the list of all users allows viewing and managing all the users limits;
* <span class="notranslate">Statistics</span> tab displays the statistics of resource usage for proper timeframe or proper users;
* <span class="notranslate">Options</span> tab - allows setting LVE Faults email notifications for users;
* <span class="notranslate">Packages</span> allows managing packages limits;
* <span class="notranslate">PHP Selector</span> tab.
* ImunifyAV allows to get access to a brand new malware scanner installed with LVE Manager. Click ImunifyAV on the main menu to go to ImunifyAV interface and use the next-generation, automated security solution that automatically scans the file system for malware injection and quarantines infected files.

For more details, please go to the [ImunifyAV documentation](https://docs.imunifyav.com/).

:::tip Note
Available starting from LVE Manager Beta version 4.0-26.8.
:::

<div class="notranslate">

### Current usage

</div>

Choose <span class="notranslate">_Current usage_</span> tab to monitor users resource usage at the moment displayed in the table.

<span class="notranslate">Current usage</span> table provides the information on the usage of <span class="notranslate"> Speed, memory, IO, IOPS, Number of Processes</span>, and <span class="notranslate"> Entry Processes</span>.

<span class="notranslate"> Resource usage </span> values are being refreshed every 10 seconds which is set in <span class="notranslate">_Auto-refresh_</span> field. You can refresh the table manually by clicking <span class="notranslate">_Refresh now_</span> or you can freeze the values by clicking pause button. Usage values will not change until the next manual refresh.

Tick <span class="notranslate">_Hide MySQL usage_</span> checkbox to hide the information on MySQL usage.

To expand the list of users click on the number above and in the dropdown choose the number of user to be displayed on the page.

![](/images/man_01_zoom73.png)

<div class="notranslate">

### Users

</div>

Choose <span class="notranslate"> Users</span> tab to view the list of all users of the system and manage their limits.

Click <span class="notranslate">_Filter by_</span> to apply filters. The following filters available in the dropdown:

* <span class="notranslate"> Username</span>
* <span class="notranslate"> Domain</span>
* <span class="notranslate"> LVE ID</span>

![](/images/man_02_zoom79.png)

Actions column – click on a pencil icon in <span class="notranslate"> Actions</span> column to edit a proper user limits.

Set proper LVE values:
* <span class="notranslate">SPEED</span>
* <span class="notranslate">PMEM</span>
* <span class="notranslate">VMEM</span>
* <span class="notranslate">EP</span>
* <span class="notranslate">IO</span>
* <span class="notranslate">IOPS</span>
* <span class="notranslate">NPROC</span>
* <span class="notranslate">INODES</span>

![](/images/man_03_zoom86.png)
![](/images/man_04_zoom86.png)

Click <span class="notranslate"> _Save_ </span> to apply changes or <span class="notranslate"> _Cancel_ </span> to close the window.

<div class="notranslate">

### Statistics

</div>

Choose <span class="notranslate">Statistics</span> tab to view hosts users resource usage statistics.

The following parameters are displayed in the statistics table:

* <span class="notranslate"> CPU </span> usage per user;
* <span class="notranslate"> PMEM </span> usage per user;
* <span class="notranslate"> VMEM </span> usage per user;
* <span class="notranslate"> IO </span> (in Kb/sec per user).

<span class="notranslate"> Statistics </span> table can be filtered by:

* <span class="notranslate"> Timeframe </span> - to view the statistics for a proper period;
* <span class="notranslate"> Limit ID </span> - to view a proper limit type usage only;
* <span class="notranslate"> Top LVEs </span> - to view top used limits only;
* <span class="notranslate"> LVE approaching limit </span> - to view the limits that are approaching maximum allocated value;
* <span class="notranslate"> Fault LVE </span> - the limits that have reached the maximum value.

![](/images/man_05_zoom92.png)

<div class="notranslate">

### Options

</div>

An administrator can set email notifications for users and resellers in cases of limits faults.

Choose <span class="notranslate">_Options_</span> tab to manage <span class="notranslate">LVE Faults</span> email notifications.

In <span class="notranslate">_LVE Faults_</span> email notifications section check proper checkboxes to set the required type of notification:

* <span class="notranslate">Notify me on users faults</span> - to receive notifications on users LVE faults;
* <span class="notranslate">Notify customers</span> - to allow hosts users receiving notifications on their LVE faults;
* <span class="notranslate">Notify me when I hit my limits</span> - to receive notifications on LVE faults.

In <span class="notranslate">_Faults to include_</span> section check proper checkboxes to include proper limits to the notifications:

* <span class="notranslate"> SPEED </span> - include speed limit fault to the notification;
* <span class="notranslate"> IO </span> - include <span class="notranslate"> I/O </span> limit fault info to the notification;
* <span class="notranslate"> IOPS </span> - include <span class="notranslate"> IOPS </span> limit fault info to the notification;
* <span class="notranslate"> Memory </span> - include <span class="notranslate"> Memory </span> limit fault info to the notification;
* <span class="notranslate"> Concurrent connections </span> - include <span class="notranslate"> concurrent connections </span> limit fault info to the notification.

In <span class="notranslate">_Minimum number of Faults to notify_</span> section enter proper number of faults required for the notification to be sent for:

* <span class="notranslate">Me</span> - for an administrator;
* <span class="notranslate">User</span> - for a User;

Set the frequency of email notifications sending in <span class="notranslate"> Notify me every.. hours/days</span> section.

Click <span class="notranslate">_Save_</span> to apply changes.

![](/images/lveman_08.jpg)
![](/images/lveman_09.jpg)

<div class="notranslate">

### Packages

</div>

<span class="notranslate"> Packages</span> tab allows setting the limits for as many users as you need by editing packages of proper limits. Each account belonging to a proper package adheres to those limits.

Choose <span class="notranslate">_Packages_</span> tab to view and modify:

* limits for hosts user’s packages (Created by Admin);
* limits for reseller’s packages (Created by Admin).

![](/images/man_06_zoom82.png)

To modify package limits click on a pencil icon in <span class="notranslate">Action</span> column in a proper package row. The following limits for this package are available for setting:

* <span class="notranslate"> SPEED</span> in percent (%);
* <span class="notranslate"> Virtual memory (VMEM)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> Physical memory (PMEM)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> Concurrent connections (EP)</span>;
* <span class="notranslate"> Number of processes (NPROC)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> IOPS</span> limits;
* <span class="notranslate"> I/O limits (IO)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> INODES soft</span>;
* <span class="notranslate"> INODES hard</span>.

When limits are set click <span class="notranslate">_Save_</span> to apply changes or <span class="notranslate">_Cancel_</span> to close the window.

<div class="notranslate">

### PHP Selector

</div>

<span class="notranslate"> Selector</span> tab allows controlling <span class="notranslate">PHP Selector</span> settings.

In <span class="notranslate">_Selector is_</span> section choose <span class="notranslate">`Enabled`</span> or <span class="notranslate">`Disabled`</span> from the dropdown list to enable or disable <span class="notranslate">PHP Selector</span>.

In <span class="notranslate">_Default PHP version_</span> choose a proper PHP version or <span class="notranslate"> Native</span> from dropdown list to apply.

In <span class="notranslate">_Supported versions_</span> choose required PHP versions to support.

Choose default modules from the list for a proper PHP version or for native.

![](/images/lveman_092.jpg)
![](/images/lveman_093.jpg)


### Python Selector

#### Hoster

Hoster interface allows to enable and disable Python Selector and manage individual Python versions.

Go to <span class="notranslate">LVE Manager → Options Tab → Python Selector</span>.

A list of installed Python versions is displayed. There are several columns in the list.
* <span class="notranslate">Version</span> — displays Python version.
* <span class="notranslate">Path</span> — Python package location.
* <span class="notranslate">Applications</span> — number of applications that use this Python version. Click on an application number to go to the list of applications.
* <span class="notranslate">Enabled</span> — displays if particular Python version is enabled.
* <span class="notranslate">Actions</span> — allows to install, delete, and make default a particular Python version.

To display all changes immediately click <span class="notranslate">_Refresh_</span>.

![](/images/PythonGeneral.png) 

#### How to enable/disable Python Selector

To enable Python Selector move a slider to <span class="notranslate">_Enable_</span> and complete the action by clicking <span class="notranslate">_Agree_</span> or click <span class="notranslate">_Cancel_</span> to close the popup.
To disable Python Selector move a slider back to <span class="notranslate">_Disable_</span>.

:::tip Note
If you disable Python, all users won't be able to manage their applications
:::

![](/images/PythonEnableDisable.png)

::: tip Note
Python Selector icon in end user interface is absent when Python is disabled.
:::

![](/images/PythonEndUserIcon.png)

#### How to manage Python Selector 

In the list of installed Python versions you can enable and disable, install and delete, and set a particular Python version as a default.
 
#### **Enable and disable particular Python version**
 
To enable particular Python version do the following:

* Move a disabled slider in the <span class="notranslate">Enabled</span> column for a particular Python version.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to save changes or <span class="notranslate">_Cancel_</span> to close popup.

![](/images/PythonEnabled.png)

To disable particular Python version do the following:

* Move an enabled slider in the <span class="notranslate">Enabled</span> column for a particular Python version.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to save changes or <span class="notranslate">_Cancel_</span> to close popup.
 
#### **Install and delete particular Python version**
 
To install particular Python version do the following:

* Click <span class="notranslate">_Install_</span> button in the Actions column for a particular Python version.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to save changes or <span class="notranslate">_Cancel_</span> to close popup.
 
To delete particular Python version do the following:

* Click <span class="notranslate">_Bin_</span> icon in the <span class="notranslate">Actions</span> column for a particular Python version.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to start uninstalling process. Or close popup without changes by clicking <span class="notranslate">_Cancel_</span> button.

:::tip Note
It is impossible:
* to remove default Python version
* to remove version with applications
* to install or remove version if another installation/uninstalling process is running
:::

![](/images/PythonInstall.png)

#### **Make a particular Python version as a default**

To make a particular Python version as a default do the following:

* Click <span class="notranslate">_Double-Tick_</span> icon in the Actions column for a particular Python version.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to save changes or <span class="notranslate">_Cancel_</span> to close popup.
 
:::tip Note
It is impossible to make default disabled version
:::

![](/images/PythonChangeDefaultVersion.png)

#### **Applications column**
 
To view and operate with the list of domains with Python versions click a number in the <span class="notranslate">_Applications_</span> column for a particular Python version. A section with a list of Domains for particular Python version will be displayed.

![](/images/PythonDomains.png)

Domains are displayed by three. To load more domains click <span class="notranslate">_Load More_</span> button.
 
To change Python version for a particular application do the following:

* Click <span class="notranslate">_Double-Arrow_</span> icon in the <span class="notranslate">_Actions_</span> column in a particular application row. A confirmation popup will be displayed.
* In the popup choose Python version from a dropdown.
* Click <span class="notranslate">_Change_</span> to confirm the action or <span class="notranslate">_Cancel_</span> to close the popup.
* To refresh state of applications in current version you can click <span class="notranslate">_Refresh_</span>.
 
:::tip Note
All packages of the application(s) will be re-installed.
:::

#### End User

:::tip Note
Python Selector icon in end user interface is absent when Python is disabled
:::

![](/images/PythonEndUserIcon.png)

End User interface allows end users to setup and manage Python for their web applications.

Go to <span class="notranslate">cPanel → Software Section → Setup Python App</span>.
 
Web Applications page is displayed.

![](/images/PythonEUWebApp.png)

There are several columns in the list:

* <span class="notranslate">App URI</span> — application URI including the domain.
* <span class="notranslate">App Root Directory</span> — application root directory relative to user's home.
* <span class="notranslate">Status — started/stopped</span> — displays if an application is running or not and version of the application.
* <span class="notranslate">Actions</span> — allows to migrate, start, restart, stop, edit, and remove a particular application.

#### How to manage an application

#### **Create application**

1. Click <span class="notranslate">_Create Application_</span> to create an application. The Create Application tab opens.

    ![](/images/PythonCreateApp.png)

2. Specify the following:
    * <span class="notranslate">Python version</span> — select from the dropdown (required);
    * <span class="notranslate">Application root</span> — physical address to your application on a server that corresponds with its URI (required);
    * <span class="notranslate">Application URL</span> —  HTTP/HTTPS link to your application (optional);
    * <span class="notranslate">Application startup file</span> — the file where WSGI callable object is located. It is required for application to run. Default is <span class="notranslate">`passenger_wsgi.py`</span>;
    * Application Entry point — WSGI callable object for your application (optional). Default is <span class="notranslate">`application`</span>;
3. Optionally, add environment variable. To do so, click <span class="notranslate">_Add Variable_</span> and specify variable name and value, then click the <span class="notranslate">_Done_</span> or <span class="notranslate">_Cancel_</span> to close an adding form.

To delete or edit environment variable, click <span class="notranslate">_Bin_</span> or <span class="notranslate">_Pencil_</span> for the required variable.

![](/images/PythonEnvVar.png)

**Start application**
 
To start a stopped application do the following:

* Click <span class="notranslate">_Start_</span> in the <span class="notranslate">_Actions_</span> column in a stopped application row.
* When an action is completed a <span class="notranslate">_Start_</span> changes to <span class="notranslate">_Stop_</span>.
 
**Stop application**
 
To stop a started application do the following:

* Click <span class="notranslate">_Stop_</span> icon in the <span class="notranslate">_Actions_</span> column in a started application row.
* When an action is completed a <span class="notranslate">_Stop_</span> changes to <span class="notranslate">_Start_</span>.

![](/images/PythonStartStopApp.png)

**Restart application**
 
To restart a started application do the following:

* Click <span class="notranslate">_Restart_</span> in the <span class="notranslate">_Actions_</span> column in a started application row. A current row is blocked and when a process is completed it will be unblocked.
 
**Remove application**
 
To remove application do the following:

* Click <span class="notranslate">_Bin_</span> in the <span class="notranslate">_Actions_</span> column in a particular application row.
* In the confirmation popup click <span class="notranslate">_Agree_</span> to start removing or <span class="notranslate">_Cancel_</span> to close the popup.
* When an action is completed an application will be removed from the <span class="notranslate">_Web Applications_</span> table and a confirmation popup will be displayed.

![](/images/PythonRestartRemove.png)

**Edit application**
 
To edit application do the following:

* Click the <span class="notranslate">_Pencil_</span> in the <span class="notranslate">_Actions_</span> column in a particular application row. A particular application tab opens.

![](/images/PythonEditApp.png)

The following actions are available:

* Restart application — click <span class="notranslate">_Restart_</span>.
* Stop application — click <span class="notranslate">_Stop App_</span>.
* Remove application — click <span class="notranslate">_Destroy_</span> and confirm the action in a popup.
* Change Python version — choose Python version from a dropdown.
* Change Application root — specify in a field a physical address to the application on a server that corresponds with its URI.
* Change Application URL — specify in a field an HTTP/HTTPS link to the application.
* Open Application URL — click the <span class="notranslate">_Open_</span>.
* Change Application startup file — specify as <span class="notranslate">`NAME.py`</span> file.
* Change Application Entry point — specify WSGI callable object for your application.
* Run pip install command — click <span class="notranslate">_Run pip install_</span> to install the package(s) described in the configuration file.
* Add Configuration files — click <span class="notranslate">_Add_</span> and specify all required information.
* Edit available configuration file — click <span class="notranslate">_Edit_</span>, the file opens in a new popup.
* Remove available configuration file from the list — click <span class="notranslate">_Remove_</span> and confirm the action or click <span class="notranslate">_Cancel_</span> to close the popup.
* Add Environment variables — click <span class="notranslate">_Add Variable_</span> and specify a name and a value.
  
Click <span class="notranslate">_Save_</span> to save all changes or <span class="notranslate">_Cancel_</span> to close the tab.

**Migrate application**

For details see [How to migrate an application to the new Python Selector](/cloudlinux_os_components/#how-to-migrate-an-application-to-the-new-python-selector)


### Node.js Selector

#### Hoster

Hoster interface allows to enable and disable Node.js, and manage individual Node.js versions.

Go to <span class="notranslate"> _LVE Manager → Options Tab → Node.js Section_ </span> . A list of installed Node.js versions is displayed. There are several columns in the list.

* <span class="notranslate"> Version </span> — displays Node.js version.
* <span class="notranslate"> Path </span> — Node.js package location.
* <span class="notranslate"> Applications </span> — number of applications that use this Node.js version. Click on a digit to go to the list of applications.
* <span class="notranslate"> Enabled </span> — displays if particular Node.js version is enabled.
* <span class="notranslate"> Actions </span> — allows to install, delete, and make default a particular Node.js version.

To display all changes immediately click <span class="notranslate"> _Refresh_ </span> link.

![](/images/nodejsgeneral_zoom70.png)

**How to enable/disable Node.js**

* To enable Node.js move the slider to <span class="notranslate"> _Enable_ </span> .
* To disable Node.js move the slider back to <span class="notranslate"> _Disable_ </span> . 

::: tip Note
If you disable Node.js, its version for all your applications will not be changed, but you can not add a new application to this version.
:::

![](/images/nodejsslider_zoom70.png)

::: tip Note
<span class="notranslate">Node.js Selector</span> icon in end user interface is absent when Node.js is disabled.
:::

![](/images/nodejsselectorlogo_zoom70.png)

**How to manage Node.js**

The list of installed Node.js versions allows to enable and disable, install and delete, and set a particular Node.js version as a default.

**Enable and disable particular Node.js version**

To enable particular Node.js version do the following:
* Move a disabled slider in the <span class="notranslate"> _Enabled_ </span> column for a particular Node.js version.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to save changes or <span class="notranslate"> _Cancel_ </span> to close pop-up.

![](/images/nodejsenable_zoom70.png)

To disable particular Node.js version do the following:
* Move an enabled slider in the <span class="notranslate"> _Enabled_ </span> column for a particular Node.js version.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to save changes or <span class="notranslate"> _Cancel_ </span> to close pop-up.

**Install and delete particular Node.js version**

To install particular Node.js version do the following:
* Click <span class="notranslate"> _Install_ </span> button in the <span class="notranslate"> _Actions_ </span> column for a particular Node.js version.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to save changes or <span class="notranslate"> _Cancel_ </span> to close pop-up.

To delete particular Node.js version do the following:
* Click <span class="notranslate"> _Bin_ </span> icon in the <span class="notranslate"> _Actions_ </span> column for a particular Node.js version.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to start uninstall process.
* Or just close a pop-up without any changes.

**Note that it is impossible**:  
* to remove default Node.js version;
* to remove version with applications;
* to install or remove version if another installation/uninstall process is running.

![](/images/nodejsconfirmation_zoom70.png)

**Make a particular Node.js version as a default**

To make a particular Node.js version as a default do the following:
* Click <span class="notranslate"> _Double-Tick_ </span> icon in the <span class="notranslate"> _Actions_ </span> column for a particular Node.js version.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to save changes or <span class="notranslate"> _Cancel_ </span> to close pop-up.

::: tip Note
It is impossible to make a disabled version default.
:::


![](/images/nodejsmakedefault_zoom70.png)

**Applications column**

To view and operate with the list of domains with Node.js versions click on a number in the <span class="notranslate"> _Applications_ </span> column for a particular Node.js version. A section with a list of Domains for particular Node.js version will be displayed.

![](/images/nodejsselectordomains_zoom70.png)

Domains are displayed by three. To load more domains click on <span class="notranslate"> _Load More_ </span> button.


To change Node.js version for a particular application do the following:
* Click <span class="notranslate"> _Double-Arrow_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a particular application row. A confirmation pop-up will be displayed.
* In the pop-up choose Node.js version from a drop-down.
* Click <span class="notranslate"> _Change_ </span> to confirm the action or <span class="notranslate"> _Cancel_ </span> to close the pop-up.
* To refresh state of applications in current version you can click <span class="notranslate"> _Refresh_ </span> link. 

:::tip Note
All packages of the application(s) will be re-installed.
:::

#### End User

:::tip Note
<span class="notranslate"> Node.js Selector </span> icon in end user interface is absent when Node.js is disabled.
:::

![](/images/nodejslogoenduser_zoom70.png)

End User interface allows end users to setup and manage Node.js for their web applications.  
Go to <span class="notranslate"> _cPanel → Software Section → Select Node.js Version_ </span> .

<span class="notranslate"> _Web Applications_ </span> page is displayed.

![](/images/nodejsusermain_zoom70.png)

There are several columns in the list.
* <span class="notranslate"> App URI </span> — application URI including the domain.
* <span class="notranslate"> App Root Directory </span> —  application root directory relative to user's home.
* <span class="notranslate"> Mode </span> — can be production or development.
* <span class="notranslate"> Status </span> — started/stopped — displays if an application is running or not and version of application.
* <span class="notranslate"> Actions </span> — allows to start, restart, stop, edit, and remove a particular application.

**How to manage application**

**Start application**

To start a stopped application do the following:
* Click <span class="notranslate"> _Start_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a stopped application row.
* When an action is completed a <span class="notranslate"> _Start_ </span> icon changes to <span class="notranslate"> _Stop_ </span> icon.

**Stop application**

To stop a started application do the following:
* Click <span class="notranslate"> _Stop_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a started application row.
* When an action is completed a <span class="notranslate"> _Stop_ </span> icon changes to <span class="notranslate"> _Start_ </span> icon.

![](/images/nodejsuseruistartstop_zoom70.png)

**Restart application**

To restart started application do the following:
* Click <span class="notranslate"> _Restart_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a started application row. A current row is blocked and when a process is completed it will be unblocked.

**Remove application**

To remove application do the following:
* Click <span class="notranslate"> _Bin_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a particular application row.
* In the confirmation pop-up click <span class="notranslate"> _Agree_ </span> to start removing or <span class="notranslate"> _Cancel_ </span> to close pop-up.
* When an action is completed an application will be removed from the <span class="notranslate"> _Web Applications_ </span> table and a confirmation pop-up will be displayed.

![](/images/nodejsuseruirestartremove_zoom70.png)

**Edit application**

To edit application do the following:
* Click <span class="notranslate"> _Pencil_ </span> icon in the <span class="notranslate"> _Actions_ </span> column in a particular application row. A particular application tab opens.

![](/images/nodejseditapp_zoom70.png)

The following actions are available:
* Restart application — click <span class="notranslate"> _Restart_ </span> button.
* Stop Node.js — click <span class="notranslate"> _Stop Node.js_ </span> button.
* Run JavaScript script — click <span class="notranslate"> _Run JS Script_ </span> button to run a command specified in the <span class="notranslate"> Scripts </span> section of the <span class="notranslate"> package.json </span> file. Specify the name of the script to run plus any parameters then click <span class="notranslate"> Ok </span> .
* Remove application — click <span class="notranslate"> _Delete_ </span> button and confirm the action in a pop-up.
* Change Node.js version — choose Node.js version from a drop-down.
* Change Application mode — choose application mode from a drop-down. Available modes are <span class="notranslate"> _Production_ </span> and <span class="notranslate"> _Development_ </span> .
* Specify Application root — specify in a field a physical address to the application on a server that corresponds with its URI.
* Specify Application URL — specify in a field an HTTP/HTTPS link to the application.
* Specify Application startup file — specify as <span class="notranslate"> NAME.js file </span> .
* Run <span class="notranslate"> npm install command </span> — click <span class="notranslate"> _Run npm install_ </span> button to install the package(s) described in the <span class="notranslate"> package.json </span> file.
* Add Environment variables — click <span class="notranslate"> _Add Variable_ </span> and specify a name and a value.

**Application error log**

Since <span class="notranslate"> alt-mod-passenger </span> version 5.3.7-3 we have included support for the PassengerAppLogFile directive.
<div class="notranslate">

``` 
Syntax: PassengerAppLogFile path
Default: PassengerAppLogFile path-to-passenger-log-file
Context: virtual host, htaccess
```
</div>
 
By default, <span class="notranslate"> Passenger </span> log messages are all written to the Passenger log file. With this option, you can have the app specific messages logged to a different file in addition. In <span class="notranslate"> alt-mod-passenger </span>, you can use it in the context of a virtual host or in the htaccess file.

See also [Node.js Selector CLI tools](/command-line_tools/#node-js-selector).

### Reseller limits

#### Hoster interface

Hoster interface allows to monitor and manage limits for hosters’ end users, resellers and resellers’ end users, and also manage packages and monitor statistics.

Hoster credentials allow to control limits for hosters’ end users and resellers. To control reseller end user limits Hoster has to log in as Reseller.

Log in as Hoster to get access to the following functionality.

* <span class="notranslate">[Current Usage](/lve_manager/#current-usage-2)</span> tab allows to monitor users and resellers resource usage at the moment.
* <span class="notranslate">[Users](/lve_manager/#users-2)</span> tab with the list of all users and resellers allows viewing and managing all the users and resellers limits.
* <span class="notranslate">[Statistics](/lve_manager/#statistics-2)</span> tab displays the statistics of resource usage for particular timeframe or particular user.
* <span class="notranslate">[Options](/lve_manager/#options-2)</span> tab allows to set LVE faults email notifications for hoster, users, and resellers.
* <span class="notranslate">[Packages](/lve_manager/#packages-2)</span> tab allows to manage resellers packages limits;
* <span class="notranslate">[Selector](/lve_manager/#selector)</span> tab allows to control <span class="notranslate">PHP Selector</span> settings.

<div class="notranslate">

#### Current Usage

</div>

Choose <span class="notranslate">Current Usage</span> tab to monitor users, resellers and resellers’ end users resource usage at the moment displayed in the table.

<span class="notranslate">Current Usage</span> table provides information on usage of the following:
* <span class="notranslate"> SPEED (All</span> and MySQL)
* <span class="notranslate"> memory (MEM)</span>
* data throughput (<span class="notranslate">IO) (All</span> and MySQL)
* read/write operations per second (<span class="notranslate">IOPS</span>)
* number of processes (<span class="notranslate">PNO</span>)
* entry processes (<span class="notranslate">EP</span>)

Resource usage values are being refreshed every 10 seconds by default which is set in <span class="notranslate">_Auto-refresh_</span> field. You can set <span class="notranslate">_Auto-refresh time_</span> by choosing a value from the drop-down.

You can refresh the table manually by clicking <span class="notranslate">_Refresh now_</span> or you can freeze the values by clicking <span class="notranslate">_pause_</span>. Usage values will not change until the next manual refresh. To unfreeze click <span class="notranslate">_unpause_</span>. The countdown will continue.

Tick <span class="notranslate">_Hide MySQL usage_</span> to hide the information on MySQL usage.

The list of users can be filtered by <span class="notranslate">_Username_</span> and <span class="notranslate">_Domain_</span>.

Hoster can **view** all types of users:
* <span class="notranslate">End users</span>
* <span class="notranslate">Resellers</span>
* <span class="notranslate">Reseller’s end users</span>
* <span class="notranslate">Reseller’s end users (no Reseller limit)</span>.

But hoster can only **manage**:
* <span class="notranslate">End users</span>
* <span class="notranslate">Resellers</span>
* <span class="notranslate">Reseller’s end users (no Reseller limit)</span>

To manage Reseller’s end users hoster should login as a reseller.

In the drop-down <span class="notranslate">_Show top_</span> you can choose the number of user to be displayed on the page.

![](/images/currentusagetabhoster_zoom60.png)

<div class="notranslate">

#### Users

</div>

Choose <span class="notranslate">_Users_</span> tab to view the list of all users and manage their limits.

To filter the list by user type click <span class="notranslate">_Manage_</span> and in the drop-down choose:

* <span class="notranslate">End users</span> - to manage hosts end users only.
* <span class="notranslate">Resellers</span> - to manage resellers only.
* <span class="notranslate">Reseller’s end users</span> - to manage resellers’ end users only.
* <span class="notranslate">Reseller’s end users (no Reseller limits)</span> - to manage resellers’ end users that do not have limits specified by reseller (these limits are specified by the hoster).

To filter the list by <span class="notranslate">_Username_, _Domain_, _LveID_</span> click <span class="notranslate">_Filter by_</span> and choose the value in the drop-down.

:::tip Note
A hoster can view the list of resellers’ end users and their limits, but can not manage resellers’ end users limits (if those are set by reseller).
:::

A hoster can view the limits of all types of users and manage the limits for hosters’ end users and resellers’ end users (only those with Reseller Limits disabled).
* Tick <span class="notranslate">_Show users with CageFS enabled_</span> to show users with CageFS file system enabled.
* Tick <span class="notranslate">_Show only ignored users_</span> to show users with ignored <span class="notranslate">MySQL Governor</span>.

![](/images/userstabhoster_zoom70.png)

<div class="notrnslate">

#### Actions

</div>

Click pencil icon in <span class="notranslate">_Actions_</span> column to edit limits for a particular user. The following actions are available:

* Enable/disable <span class="notranslate">CageFS</span>
* <span class="notranslate">**Reset**</span> - to reset limits to default values
* Apply <span class="notranslate">**Do not limit**</span> to set the limits to unlimited;
* Setting the limits values:
  * <span class="notranslate"> SPEED </span>
  * <span class="notranslate"> SPEED MYSQL </span>
  * <span class="notranslate"> VMEM </span>
  * <span class="notranslate"> PMEM </span> 
  * <span class="notranslate"> IO </span>
  * <span class="notranslate"> MySQL IO </span>
  * <span class="notranslate"> IOPS </span>
  * <span class="notranslate"> EP </span>
  * <span class="notranslate"> NPROC </span>
  * <span class="notranslate"> INODES </span> (hard and soft) (for <span class="notranslate">end users</span> and <span class="notranslate">resellers’ end users (with no Reseller Limits)</span>, if a hoster has enabled <span class="notranslate">_Initial quotas_</span> in cPanel settings).

Click <span class="notranslate">_Save_</span> to save changes or <span class="notranslate">_Cancel_</span> to close the pop-up.

![](/images/actionshoster.png)

Click on <span class="notranslate">_History_</span> symbol to view the history of a particular user resource usage. Choose time frame to view the history for a particular time period.

![](/images/historyhoster.jpg)

<div class="notranslate">

#### Statistics

</div>

Choose <span class="notranslate">_Statistics_</span> tab to view end users, resellers and resellers’ end users limits usage statistics.

The following parameters can be displayed in the statistics table:

* <span class="notranslate"> SPEED </span> usage per user;
* <span class="notranslate"> IO </span> usage per user;
* <span class="notranslate"> EP </span> usage per user;
* <span class="notranslate"> VMEM </span> usage per user;
* <span class="notranslate"> PMEM </span> usage per user;
* <span class="notranslate"> NPROC </span> usage per user;
* <span class="notranslate"> IOPS </span> usage per user;
* <span class="notranslate"> MySQL </span> usage per user.

Click <span class="notranslate">_Show_</span> and select columns from the drop-down to set which parameters should be displayed in the table.

Statistics table can be filtered by:

* <span class="notranslate"> Timeframe </span> - to view the statistics for a particular period;
* <span class="notranslate"> Limit </span> - to view a particular limit type usage only;
* <span class="notranslate"> Top LVEs </span> - to view top used limits only;
* <span class="notranslate"> LVE approaching limit </span> - to view the limits that are approaching maximum provided value;
* <span class="notranslate"> Fault LVE </span> - the limits that have reached the maximum value.

Click <span class="notranslate">_Manage_</span> to choose type of users to be displayed - <span class="notranslate">End users, Resellers, Resellers’ end users</span> or <span class="notranslate">Resellers’ end users (no Reseller limit)</span> by ticking checkbox in the drop-down.

![](/images/statisticstabhoster_zoom70.png)

Click chart symbol in the <span class="notranslate">_View_</span> column to view the detailed resource usage history for a particular account. Use timeframe drop-down to view the history for a particular period of time.

![](/images/history_charts_zoom70.png)

<div class="notranslate">

#### Options

</div>

A hoster can set email notifications for panel administrator, reseller customer, and resellers’ customers in cases of limits faults. Choose <span class="notranslate">_Options_</span> tab to manage LVE Faults email notifications.

In <span class="notranslate">_LVE Faults Email Notifications_</span> section tick the required checkboxes to set a type of notification.

* <span class="notranslate"> _Notify Panel Administrator_ </span> - notify hoster when his end users have exceeded minimum number of faults set for particular limits.
* <span class="notranslate"> _Notify Reseller_ </span> - notify reseller when his end users have exceeded minimum number of faults set for particular limits.
* <span class="notranslate"> _Notify Customers_ </span> - notify hosters’ end users when they have exceeded limits.
* <span class="notranslate"> _Notify Reseller's customers_ </span> - notify resellers’ end users when they have exceeded limits.

![](/images/optionstabemailnotifhoster.png)

In <span class="notranslate">_Faults to include_</span> section tick the checkboxes to include required limits to the notifications.
Set the frequency of email notifications sending in <span class="notranslate">_Notify …. every.. days/hours/minutes/seconds_</span> section.

![](/images/optionshosterfaultstoinclude.png)

In <span class="notranslate">_Minimum number of Faults to notify_</span> section enter the number of faults required for the notification to be sent for <span class="notranslate">_Panel Admin & Reseller_</span> and <span class="notranslate">_User_</span>.

![](/images/optionstabhosterminimumftn.png)

* In <span class="notranslate">_Inodes limits_</span> section you can reset inode limits to default values and tick <span class="notranslate">_Show end-user inode usage_</span>.
* In <span class="notranslate">_User interface settings_</span> section tick the required checkboxes to apply user interface settings.
* In <span class="notranslate">_MySQL Governor settings_</span> section you can customize <span class="notranslate"> MySQL Governor</span>.

![](/images/optionstabhosterinodes.png)

<div class="notranslate">

#### Packages

</div>

<span class="notranslate">_Packages_</span> tab allows to set the limits for as many users as you need by editing packages of the limits. Each account belonging to a particular package adheres to those limits.

Choose <span class="notranslate">_Packages_</span> tab to view and modify:

* limits for user packages (created by hoster);
* limits for reseller packages (created by hoster);
* limits for resellers’ end users packages if reseller limits are not set for that reseller (hoster access allows identifying a particular reseller’s end user belonging to a particular reseller (created by reseller)).
  
![](/images/packageshostertab_zoom70.png)

To modify package limits click on a pencil symbol in <span class="notranslate">_Actions_</span> column in a particular package row. The following limits for this package are available for setting:

* <span class="notranslate"> SPEED</span> in percent (%);
* <span class="notranslate"> Virtual memory (VMEM)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> Physical memory (PMEM)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> I/O limits (IO)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> IOPS</span> limits;
* <span class="notranslate"> Concurrent connections (EP)</span>;
* <span class="notranslate"> Number of processes (NPROC)</span> (can be set as unlimited by setting 0);
* <span class="notranslate"> INODES (hard and soft)</span> (for end users and resellers’ end users (with no Reseller Limits), if a hoster has enabled <span class="notranslate">_Initial quotas_</span> in cPanel settings.)

When limits are set click <span class="notranslate">_Save_</span> to apply changes or <span class="notranslate">_Cancel_</span> to close the window.

<div class="notranslate">

#### Selector

</div>

<span class="notranslate">_Selector_</span> tab allows to control <span class="notranslate">PHP Selector</span> settings.

* In <span class="notranslate">_Selector is_</span> choose <span class="notranslate">_Enabled_</span> or <span class="notranslate">_Disabled_</span> from the drop-down to enable or disable <span class="notranslate">PHP Selector</span>.

* In <span class="notranslate">_Default PHP version_</span> choose PHP version or <span class="notranslate">_Native_</span> from the drop-down to apply.

* In <span class="notranslate">_Supported versions_</span> choose required PHP versions to support.

Choose default modules from the list for a particular version of PHP or for <span class="notranslate">native</span>.

![](/images/selector01_zoom70.png)

![](/images/selector02_zoom70.png)


#### Reseller Interface

Reseller interface is designed to manage limits for resellers’ end users, to monitor statistics and the history of resource usage and to modify reseller’s end user packages limits.

Log in under a particular reseller credentials to have access to the following functionality:

* <span class="notranslate">[Current Usage](/lve_manager/#current-usage-tab)</span> tab - allows to monitor resellers’ end users resource usage at the moment;
* <span class="notranslate"> [Historical Usage](/lve_manager/#historical-usage-tab)</span> tab - allows to control resellers’ end users resource usage history;
* <span class="notranslate"> [Users](/lve_manager/#users-tab)</span> tab with the list of all resellers’ end users allows to view and manage all the reseller’s end user limits;
* <span class="notranslate"> [Statistics](/lve_manager/#statistics-tab)</span> tab displays the statistics of resource usage for particular timeframe or particular reseller's end user;
* <span class="notranslate"> [Options](/lve_manager/#options-tab)</span> tab allows to set LVE Faults email notifications.
* <span class="notranslate"> [Packages](/lve_manager/#packages-tab)</span> tab allows to manage reseller’s end user packages limits.

Please note that reseller can manage all his end users via Reseller Interface. Reseller cannot manage <span class="notranslate"> INODE </span> or <span class="notranslate"> MYSQL </span> limits, neither his own nor for his users.

<div class="notranslate">

#### Current Usage tab

</div>

Current usage table provides the information on the usage of the following:
* <span class="notranslate"> SPEED (All)</span>
* <span class="notranslate">memory (MEM)</span>
* data throughput <span class="notranslate">(IO)(All)</span>
* read/write operations per second (<span class="notranslate">IOPS</span>)
* <span class="notranslate">number of processes (PNO)</span>
* <span class="notranslate">entry processes (EP)</span>

Resource usage data is being refreshed every 10 seconds which is set by default in <span class="notranslate">_Auto-refresh_</span> field. You can set <span class="notranslate">_Auto-refresh time_</span> by choosing the value from the drop-down.

You can refresh the table manually by clicking <span class="notranslate">_Refresh now_</span> or you can freeze the values by clicking <span class="notranslate">_pause_</span> button.

Usage values will not change until the next manual refresh. To unfreeze click on <span class="notranslate">_unpause_</span> button. The countdown will continue.

Reseller cannot manage <span class="notranslate">INODE</span> or MYSQL limits. Neither his own, nor for his users.

The bottom line star in the table displays the total reseller resource usage. It means, that all the usage of resellers’ end users and of his own is displayed as a summary for each parameter.


![](/images/currentusagetabresellerr_zoom70.png)

<div class="notranslate">

#### Historical Usage tab

</div>

Choose <span class="notranslate">_Historical Usage_</span> tab to view reseller and resellers’ end users resource usage history and faults. The list of users can be filtered by <span class="notranslate">_Timeframe_</span>.

When reseller’s end user reaches the limits set by hoster for the reseller, this will be displayed on the chart. 

:::tip Note
In this case reseller’s end user would not necessarily reaches his limits set by the reseller. These faults are not displayed on the chart.
:::

On the <span class="notranslate">_Historical Usage_</span> page the reseller is also able to see the list of <span class="notranslate">_Top 5 Reseller’s end users_</span> (based on resource usage, for the same period as charts/overall usage). Click <span class="notranslate">_History_</span> in the <span class="notranslate">_Actions_</span> column to view resource usage statistics for particular user.

Click <span class="notranslate">_LVE Statistics_</span> on the top of the <span class="notranslate">Top 5</span> list to go to the <span class="notranslate">_Statistics_</span> page to view or manage the rest of users.

![](/images/historicalusageresellertab_zoom70.png)

<div class="notranslate">

#### Users tab

</div>

Choose <span class="notranslate">_Users_</span> tab to view and manage the list of all resellers’ end users and resource usage limits provided for them. The following limits are available for the resellers’ end users:

* <span class="notranslate">SPEED</span>
* <span class="notranslate">PMEM</span>
* <span class="notranslate">IO</span>
* <span class="notranslate">IOPS</span>
* <span class="notranslate">EP</span>
* <span class="notranslate">NPROC</span>

You can filter the list by <span class="notranslate">_Username_, _Domain_, _LVE ID_.</span>

Tick <span class="notranslate">_Show only ignored users_</span> to display only users with <span class="notranslate">MySQL Governor</span> disabled.

![](/images/userstabreseller_zoom70.png)

<div class="notranslate">

#### Actions column

</div>

Click on a pencil icon in <span class="notranslate">_Actions_</span> column to edit limits for a particular user. The following actions are available:

* Click <span class="notranslate">Reset</span> to reset limits to default values.
* Click <span class="notranslate">Apply</span> for <span class="notranslate">Do not limit</span> to set unlimited resources to a user.
* Set values for <span class="notranslate"> PEED, PMEM, IO, IOPS, EP</span>, and NPROC and click <span class="notranslate">_Save_</span> to save changes or <span class="notranslate">_Cancel_</span> to close the window.

![](/images/userstabpopup_zoom70.png)

<div class="notranslate">

#### Statistics tab

</div>

Choose <span class="notranslate">_Statistics_</span> tab to view resource usage limits statistics.

<span class="notranslate">_Statistics_</span> table can be filtered by <span class="notranslate">_Timeframe_, _Limit_, _Top LVEs_, _LVE approaching limit_, _Fault LVE_</span>.

The following parameters are displayed:

* <span class="notranslate"> SPEED</span> per user;
* <span class="notranslate"> PMEM</span> usage per user;
* <span class="notranslate"> IO</span> usage per user;
* <span class="notranslate"> EP</span> usage per user;
* <span class="notranslate"> NPROC</span> usage per user;
* <span class="notranslate"> IOPS</span> usage per user.

![](/images/statisticstabreseller_zoom70.png)


Use <span class="notranslate">_Charts_</span> in the <span class="notranslate">_View_</span> column to view detailed resource usage charts for a particular period of time.

For example, 7 days period chart.

![](/images/sevendayschartresellers_zoom70.png)

<div class="notranslate">


#### Options tab

</div>

Choose <span class="notranslate">_Options_</span> tab to set user email notifications for resellers’ end users.

In <span class="notranslate">_LVE Faults email notifications_</span> section tick appropriate checkboxes to set the required type of notification.

![](/images/optionsresellernotify_zoom70.png)

* <span class="notranslate">_Notify me on users faults_</span> - notify reseller when his users have exceeded limits.
* <span class="notranslate">_Notify Customers_</span> - notify resellers’ end users when they have exceeded limits.
* <span class="notranslate">_Notify me when I hit my limits_</span> - notify reseller when overall resource usage limits are reached.

In <span class="notranslate">_Faults to include_</span> section tick checkboxes to include particular limits to email notifications.

![](/images/options02_zoom70.png)

In <span class="notranslate">_Minimum number of Faults to notify_</span> section enter the number of faults required for the notification to be sent for reseller and customer. You can also set the reseller notification frequency.

Set the frequency of sending the reseller email notifications in <span class="notranslate">_Notify Reseller Every ... days/hours/minutes/seconds_</span> section.

![](/images/options03_zoom70.png)

Click <span class="notranslate">_Save Changes_</span> to apply changes.

<div class="notranslate">

#### Packages tab

</div>

Choose <span class="notranslate">_Packages_</span> tab to view and modify limits for reseller’s packages.

![](/images/packagesreseller_zoom70.png)

Click pencil icon in a package row to set the following limits for a package:

* <span class="notranslate">SPEED</span> limit;
* <span class="notranslate">Physical memory (PMEM)</span> (can be set as unlimited by setting 0);
* <span class="notranslate">I/O</span> limits;
* <span class="notranslate">IOPS</span> limits;
* <span class="notranslate">Concurrent connections (EP)</span> limits.

When limits are set click <span class="notranslate">_Save_</span> to apply changes.


### LVE Manager options

When you need to change <span class="notranslate">LVE Manager</span> options in cPanel config file on big amount of servers, you don't have to edit file manually, therefore there is no need to login into cPanel on each server. Just go to WHM, choose CloudLinux and click <span class="notranslate">Options</span> - and you will be able to change settings from here.

<div class="notranslate">

```
root@toaster [~]# grep lve /var/cpanel/cpanel.config
```
</div>

| | |
|-|-|
|<span class="notranslate">`lve_hideextensions`</span>| Hides (when =1) range of php extensions for user in <span class="notranslate"> Select PHP </span> version.|
|<span class="notranslate">`lve_hideuserstat  `</span>| Hides (when =1) LVE statistics in <span class="notranslate"> cPanel Stats Bar (UI) </span> .|
|<span class="notranslate">`lve_showinodeusage`</span>| Displays (when =1) used inodes in cPanel (UI).|
|<span class="notranslate">`lve_hide_selector`</span>| Turns off <span class="notranslate">UI PHP Selector</span> (Select <span class="notranslate">PHP Version</span> option).|

### Server processes snapshots

In case when a CloudLinux user hits LVE limits, appropriate faults are generated and [lvestats](/deprecated/#lve-stats-0-x) package generates Server processes snapshot. Snapshot is a list of running applications and a list of running MySQL queries right after the faults happened.

Snapshots allow users to investigate the reason of account hitting its limits. Several snapshots are generated for each incident. An incident is a state when faults are generated in a close time period. The time period is configurable. By default, if faults are generated in 300 seconds time period, we consider them as a single incident.

The snapshot configuration options are available in

<div class="notranslate">

```
/etc/sysconfig/lvestats.config/SnapshotSaver.cfg
```
</div>

* <span class="notranslate">`period_between_incidents = 300`</span> by default, time in seconds
* <span class="notranslate">`snapshots_per_minute = 2`</span> by default, maximum number of snapshots per minute
* <span class="notranslate">`max_snapshots_per_incident = 10`</span> by default, maximum number of snapshots for an incident

To access <span class="notranslate">**Snapshots**</span> on Plesk you can use [lve-read-snapshot](/command-line_tools/#lve-read-snapshot) utility.

To access <span class="notranslate">**Snapshots**</span> on cPanel perform the following steps:

1. Go to cPanel | <span class="notranslate">CPU and Concurrent Connection Usage</span> in <span class="notranslate"> **paper_latern**</span> theme:

![](/images/snapshots.jpg)

2. Click the <span class="notranslate">**Snapshots**</span> in <span class="notranslate">**paper_latern**</span> theme:

![](/images/snapshots2.jpg)

3. Select a date:

![](/images/snapshots3.jpg)

4. Select an appropriate <span class="notranslate">**Snapshot**</span> in the combobox:

![](/images/snapshots4.jpg)
![](/images/snapshots5.jpg)


:::tip Note
The list of processes in a snapshot is close but not similar to the real processes list when faults were generated. It happens because of delay when the faults are happened and the snapshot is taken by the system.
:::


The list of MySQL queries is an output of a query:

<div class="notranslate">

```
SELECT command, time, info FROM information_schema.processlist

WHERE user = '%username';
```
</div>

### LVE plugins branding

:::tip Note
Requires <span class="notranslate">LVE Manager</span> 2.0-33+
:::

It is possible to apply branding to the LVE Plugins in cPanel end users’ interface. To brand the cPanel end users'  interface please do the following:

* Create a script that will patch <span class="notranslate">LVE Manager</span> files (with branding data, for example, image and logo) after every update of <span class="notranslate">`lvemanager rpm`</span> package;

* Locate this script in <span class="notranslate">`/usr/share/l.v.e-manager/branding_script`</span>;

* Make this script executable by running the command:

<div class="notranslate">

```
chmod a+x /usr/share/l.v.e-manager/branding_script
```
</div>

When done, the branding script will be executed while every update of <span class="notranslate">lvemanager</span> package and all branding changes will be applied in the end user’s interface.

:::tip Note
Modifying the <span class="notranslate">LVE Manager WHM</span> plugin (<span class="notranslate">`/usr/local/cpanel/whostmgr/docroot/cgi/CloudLinux.cgi`</span>) via <span class="notranslate">`branding_script`</span> is not allowed.
:::


### User message for PHP version

Since version 1.0-4 <span class="notranslate">LVE Manager</span> acquired a feature of adding user messages to PHP versions*. To add a message, you should create a file in <span class="notranslate">`/opt/alt/phpXX/name_modifier`</span> with a message that you want to be shown to a user.

For example, if you need to add the following message <span class="notranslate">`Don't use this PHP version`</span> to PHP version 4.4, you should create the following file:

<div class="notranslate">

```
/opt/alt/php44/name_modifier:

echo 'Don`t use this php version' > /opt/alt/php44/name_modifier
```
</div>

As a result, <span class="notranslate">LVE Manager</span> will automatically pick up this message and will show it in web-interface to administrator (see Figure 1.1 for cPanel, Figure 1.2 for DirectAdmin) and to user (see Figure 2.1 for cPanel, Figure 2.2 for DirectAdmin). You can add messages to other PHP versions this way as well.

![](/images/screen1.1lvemanfeature_zoom74.png)

_Figure 1.1_


![](/images/screen1.2lvemanfeature_zoom76.png)

_Figure 1.2_

![](/images/screen2.1lvemanfeature_zoom72.png)

_Figure 2.1_


![](/images/screen2.2lvemanfeature_zoom75.png)

_Figure 2.2_

:::tip Note
*For cPanel and DirectAdmin only.
:::


## inodes


:::tip Note
Supported on cPanel, Plesk, and DirectAdmin control panels
:::

<span class="notranslate"> LVE Manager inodes </span> limits extension allows setting <span class="notranslate"> inode </span> limits for the customers. An <span class="notranslate"> inode </span> is a data structure on a file system used to keep information about a file or a folder. The number of <span class="notranslate"> inodes </span> indicates the number of files and folders an account has. <span class="notranslate"> inodes </span> limits work on the level of <span class="notranslate"> disk quota </span> , and will be enabled on <span class="notranslate"> /home </span> partition only.

<span class="notranslate"> LVE Manager </span> allows to set <span class="notranslate"> soft </span> and <span class="notranslate"> hard IO </span> limit.

* <span class="notranslate"> Hard </span> limit prevents a user from writing data to disk.

* <span class="notranslate"> Soft </span> limit can be exceeded for a period of time. The grace period can be set using: <span class="notranslate"> edquota -t </span> .

* You can set <span class="notranslate"> inodes </span> limits using <span class="notranslate"> LVE Manager </span> , the same way you would set any other LVE Limits:

::: tip Note
We do not collect statistical information on the inodes like we do for other LVE limits.
:::

![](/images/inodes_zoom70.png)


The limits can be set on the level of individual account or package:

![](/images/inodespackages_zoom70.png)


Sometimes <span class="notranslate">disk quota</span> breaks, so do <span class="notranslate"> inodes </span> limits. You can reset them through the <span class="notranslate">_Options_</span> tab of <span class="notranslate">LVE Manager</span>:

![](/images/inodelimitsoptions_zoom70.png)

The same can be achieved using [cloudlinux-config](/command-line_tools/#cloudlinux-config) CLI utility

End users can monitor their inodes usage through cPanel only (not available on Plesk and DirectAdmin):

![](/images/inodescpanel.png)

End user can also see the usage inside resource usage menu.

#### cl-quota

<span class="notranslate">**cl-quota**</span> utility is designed to control <span class="notranslate">disk quotas</span> and provides:

* Setting user and package limits.

* Integration with panel packages.

* Limits synchronization.

* Automatic inheritance of panel limits to all appropriate users.

::: tip Note
cl-quota works only with inodes soft/hard limits (soft/hard file limits in setquota/repquota utilities terminology). Block limits are not controlled by cl-quota utility in any way, they are not taken into account and do not affect the data that they issue. That is why hereinafter it is the inode limits that are implied by the word “limits”.
:::

#### General provisions


<span class="notranslate"> cl-quota </span> utility never sets/reads limits directly in the system, it uses standard <span class="notranslate"> setquota/repquota </span> utilities included into the <span class="notranslate"> quota </span> package for this purpose.

<span class="notranslate"> cl-quota </span>  **will not work** in the following cases:

* <span class="notranslate"> setquota/repquota </span> are missing or working incorrectly;

* the <span class="notranslate"> quotas </span> are not configured in the system.

<span class="notranslate"> cl-quota </span> only **performs** the minimal diagnostics of <span class="notranslate"> quota </span> related errors:

* verifies the availability of <span class="notranslate"> setquota/repquota </span> utilities on the disk;

* verifies if <span class="notranslate"> quotas </span> are activated for a specified user (with a separate command), see below.

<span class="notranslate"> quota </span> package which contains the required <span class="notranslate"> setquota/repquota </span> utilities, is not included in <span class="notranslate"> lvemanager </span> package dependencies by default, and <span class="notranslate"> quotas </span> activation is a long process which sometimes depends on the panel used, therefore, all the steps on <span class="notranslate"> quotas </span> configuration and activation must be carried out by yourself, <span class="notranslate"> cl-quota </span> does not perform these actions.

Error messages sent back to the console are extremely rare, to receive error messages use the command:
<div class="notranslate">

```
# cat /var/log/messages | grep clquota
```
</div>

::: tip Note
You should not set soft limit higher than hard limit. cl-quota does not control it in any way, but in some cases, the system can ban such limits combination and they won’t be set or will be set in some other way.
:::

#### Setting limits and integration with panel packages


<span class="notranslate"> cl-quota </span> utility allows setting <span class="notranslate"> inodes </span> limits for users of the system.

<span class="notranslate"> cl-quota </span> integrates with the panels through a standard mechanism - [Integrating LVE Limits with Packages](/lve_manager/#detecting-and-working-with-cloudlinux) .

Panel users are such users whose UIDs are issued by the above panel integration mechanism. The list of panel packages and the information on the user's affiliation to a particular package is obtained from there as well.

When installing/reading the limits, the following peculiarities are applied:

1. When displaying <span class="notranslate"> quotas, cl-quota </span> displays information about the limits of all users - system and panel. No filter applied. The actual limit values are always displayed.

2. Limit value -1 for the packages (see below) is displayed as dash (-).

3. If <span class="notranslate"> cl-quota </span> is running under <span class="notranslate"> root </span> , it will display the limits returned by <span class="notranslate"> repquota </span> utility with no changes. If it is running under some other user, it will return data from a special cache file, see [Quotas cache and synchronization](/lve_manager/#caching-and-synchronizing-the-limits).

4. Limits setting only works for panel users, for all other users limits are not set (the command is ignored). The only exception - <span class="notranslate"> uid=0 </span> . The limits are never set for the <span class="notranslate"> root </span> user <span class="notranslate"> (uid=0) </span> , but they are stored in <span class="notranslate"> DB </span> file and are used by inheritance mechanism. See [Limits Inheritance](/lve_manager/#limits-inheritance).

5. <span class="notranslate"> Hard </span> and <span class="notranslate"> soft </span> limits are completely independent, <span class="notranslate"> сl-quota </span> does not apply any interdependencies to them. Setting only one of them (any) is acceptable, the other one will not change.

<span class="notranslate"> cl-quota </span> utility also supports package limits set/read. When setting package limits, they are set for all users of a particular package except for those whose limits are set individually. See also [Limits Inheritance](/lve_manager/#limits-inheritance).

If package name is <span class="notranslate"> "default" </span> , then setting limits command is ignored. If some limits are set for this package in <span class="notranslate"> DB </span> file, they will be displayed along with all the others, but will not be used. See also [Limits inheritance](/lve_manager/#limits-inheritance).

Any positive numbers are allowed as limit values. <span class="notranslate"> cl-quota </span> neither controls nor changes these values except the following cases:

negative values are taken modulo;

fractional values are converted to integers by discarding the fractional part;

if the transferred value can not be turned into a number (for example, 67wg76), it is completely ignored and the limit is not set at all.

Then these values are transmitted directly to <span class="notranslate"> setquota </span> system utility for the actual setting of the limits.

Thus <span class="notranslate"> cl-quota </span> has two limit values, which are processed in a special way:

* 0: Means inheritance of the limit from the package where the user is located, or from <span class="notranslate"> uid=0 </span> . See also [Limits inheritance](/lve_manager/#limits-inheritance) for more detailed information.

* -1: The real limits are set to 0, which means no limits, literally "unlimited". This is legit both for individual and for package limits. Limit value -1 is stored in the database as well as any other but is never displayed.

You can use the words <span class="notranslate"> “default” </span> and <span class="notranslate"> “unlimited” </span> instead of 0 and -1 respectively, they are fully interchangeable. See also [DB File](/lve_manager/#quotas-db-file) and [CLI Options](/lve_manager/#cli-options-examples).

Individual and package limits are always saved in DB file. Limits from there are used when synchronizing <span class="notranslate"> quotas </span> . Please find more details in [Limits Synchronization](/lve_manager/#caching-and-synchronizing-the-limits).

Also, find detailed information on DB file itself in [Quotas DB File](/lve_manager/#quotas-db-file) section.

Utility options are described in [CLI Options](/lve_manager/#cli-options-examples) section.

#### Limits inheritance


When setting package limits to the package users, the inheritance principle is applied. It means that:

* If no individual limit is set to a user, then he inherits the limits of the package he belongs to.

* If no limit is set to a package (=0), then the users inherit uid=0 limits.

Limits of the package named <span class="notranslate"> “default” </span> (if found in the <span class="notranslate"> DB </span> file) will always be ignored and all the users of this package will get <span class="notranslate"> uid=0 </span> limits.


#### Caching and synchronizing the limits


Any user of the system (including panel users) is always created with limits equal to 0. To assign him the limits of the corresponding package, the synchronization process is used.

During the synchronization, <span class="notranslate"> cl-quota </span> utility reads the database file and sets the limits from it to the users and packages specified therein.
This mode is designed to set the correct limits for the new users and to restore them for the existing ones. When recovering, the current limits are neither read nor analyzed.

Caching - is writing current limits to <span class="notranslate"> _/etc/container/cl-quotas.cache_ </span> file. If <span class="notranslate"> cl-quota </span> is not started from the <span class="notranslate"> root </span> for reading the current limits, then it returns data from this file.

When installing <span class="notranslate"> LVE Manager </span> package, a special <span class="notranslate"> cron job </span> is installed, which performs synchronization and caching ( <span class="notranslate"> cl-quota -YC </span> ) every 5 minutes. Therefore, the correct limits will be set for the user within 5 minutes from the moment of its creation.

Caching and synchronization can also be performed separately, see ["CLI Options"](/lve_manager/#cli-options-examples) section.

To disable this feature add to the config file _/etc/sysconfig/cloudlinux_ .


#### Quotas DB file


All <span class="notranslate"> cl-quota </span> limits settings are stored in along with the <span class="notranslate"> UID </span> or the name of the package the limit was set for.

When saving the limits to a file, the following rules are applied:

* If a limit value is non-integer or non-numeric, then the rules from <span class="notranslate"> "Setting limits and integrating with panel packages" </span> section are applied. The assigned value is saved to the file.

* Limits are always saved in pairs, no matter if only one limit was set or both. The pair looks as follows: <span class="notranslate"> soft_limit:hard_limit </span> .

* The values 0 and -1, when having a predetermined meaning, are saved as is without any transformations.

* The words <span class="notranslate"> “default” </span> and <span class="notranslate"> “unlimited” </span> are saved as 0 and -1 respectively.

* If both limits for a user/package were set as 0, then such user/package is not saved in the file, and if it was previously there - it will be removed. Therefore, if a user/package is not mentioned in the file, then all its limits are inherited. See [Limits Inheritance](/lve_manager/#limits-inheritance) section.

The lists of panel users, packages, and user-package correspondence are not saved anywhere, this information is always subtracted from the panel.

Example:
<div class="notranslate">

```
/etc/container/cl-quotas.dat
[users]
0 = 1000:2000
500 = -1:-1
958 = 0:20000
[packages]
pack1 = 5000:-1
```
</div>
It follows that:

* uid=0 limits are set to 1000:2000 - all users in the default package will obtain these limits.

* Both limits are set as unlimited for a user with uid=500, which means that its real limits will always be 0:0. The package limits do not affect this user.

* <span class="notranslate"> Soft </span> limit of the user with uid=958 is inherited (0 means inheritance), his <span class="notranslate"> hard </span> limit is set to 20000 and it will not depend on the package limits or uid=0 limits.

* Limits 5000:-1 are set for pack1 package, therefore its real limits are: <span class="notranslate"> soft_limit=5000 </span> and <span class="notranslate"> hard_limit=0 </span> (unlimited).

* The users of <span class="notranslate"> pack1 </span> package will get <span class="notranslate"> pack1 </span> limits (5000:-1), the users of all the rest of the packages will get the limits of uid=0 because no limits are set for them. Exceptions: uid=500 and 958. uid=500 has both limits set individually, and uid=958 inherits only <span class="notranslate"> soft </span> limits.

#### CLI options/examples


<span class="notranslate"> cl-quotа </span> utility has the following command line options:
<div class="notranslate">

```
-u | --user                  : specifies the user
-U | --user-id              : specifies the user ID
-S | --soft-limit            : sets the soft limit for a user. Pass 0 or 'default' to set package default limit. Pass -1 or 'unlimited' to cancel limit
-H | --hard-limit            : sets the hard limit for a user. Pass 0 or 'default' to set package default limit. Pass -1 or 'unlimited' to cancel limit
-V | --csv                  : returns data as comma separated values
-p | --package              : specifies a package to set or get limits
-P | --package-limits        : prints package limits
-a | --all-package-limits : prints all package limits (including packages without limits)
-Y | --sync                  : synchronizes packages and users limits with the database
-C | --cache-content        : cache quota data to a file the database
-F | --force                : save user quotas even when they are equal to defaults
       --check                : check if quotas is enabled/activated/suported; if disabled show diagnostic information; using with --user or --user-id options
```
</div>

<span class="notranslate"> **--user** </span> and <span class="notranslate"> **--user-id** </span> options are designed to specify user whose limits are required to be set or displayed. <span class="notranslate"> --user </span> specifies user name, <span class="notranslate"> --user-id - uid </span> . It is acceptable to specify one or another.

<span class="notranslate"> **--package** </span> - specifies package name.

<span class="notranslate"> **--soft-limit** ,  **--hard-limit** </span> - specify <span class="notranslate"> soft </span> and <span class="notranslate"> hard </span> limits values respectively. It is acceptable to use words <span class="notranslate"> “default” </span> or <span class="notranslate"> “unlimited” </span> as limit value.

<span class="notranslate"> **--csv** </span> - displays limits in <span class="notranslate"> csv </span> format (instead of data formatted in the table).

<span class="notranslate"> **--package-limits** </span> - displaying the limits of the packages created by the panel admin.

<span class="notranslate"> **--all-package-limits**   </span> - displaying the limits of all the packages, including the ones created by the resellers and packages with no users.

<span class="notranslate"> **--sync** </span> - synchronizes users <span class="notranslate"> quotas </span> and packages with the database.

<span class="notranslate"> **--cache-contents** </span> - performs <span class="notranslate"> quotas </span> caching.

<span class="notranslate"> **--force** </span> - saving user <span class="notranslate"> quotas </span> even if they are equal to the current.

<span class="notranslate"> **--check**   </span> - performs diagnostics for a specified user. Can be used only when a user is specified (along with <span class="notranslate"> --user / --user-id </span> ).

_Examples:_

1. Reading current user limits:

<div class="notranslate">

```
# cl-quota
# cl-quota --csv
```
</div>

2. Reading current package limits:

<div class="notranslate">

```
# cl-quota --package-limits
# cl-quota --all-package-limits
# cl-quota --package-limits --csv
# cl-quota --all-package-limits --csv
```
</div>

3. Specifying limits for a user:

<div class="notranslate">

```
# cl-quota --user-id=500 --soft-limit=0 --hard-limit=0
# cl-quota --user-id=500 --soft-limit=unlimited
# cl-quota --user-id=500 --soft-limit=0 --hard-limit=-1
# cl-quota --user-id=958 --hard-limit=20000 --soft-limit=0 --force
```
</div>

4. Specifying limits for a package:

<div class="notranslate">

```
# cl-quota --package pack1 --hard-limit=-1 --soft-limit=5000
# cl-quota --package pack1 --hard-limit=10000
# cl-quota --package pack1 --soft-limit=default
```
</div>

5. User diagnostics (with example output):

<div class="notranslate">

```
# cl-quota --user-id=500 --check
Quota disabled for user id 500 (home directory /home/cltest1); quotaon: Mountpoint (or device) / not found or has no quota enabled.
```
</div>

6. Synchronizing <span class="notranslate"> quotas with caching (executed in cron): </span>

<div class="notranslate">

```
# cl-quota -YC
```
</div>

## Control panel integration guide

Here you will find the instructions and common techniques used to integrate your software with CloudLinux.


### Detecting and working with CloudLinux


Detecting if system is running CloudLinux/CloudLinux kernel:


<div class="notranslate">

```
$ uname -r|grep lve 
```
</div>

If you get an output, it means the system is running CloudLinux kernel. CloudLinux kernels have lve in its name, like: <span class="notranslate"> 2.6.32-458.18.1.lve1.2.44.el6.x86_64 </span>

Alternatively you can check for the presence of <span class="notranslate">`/proc/lve/list`</span> file.

Check if CageFS is enabled (as <span class="notranslate"> root </span> ):

<div class="notranslate">

```
$ /usr/sbin/cagefsctl --cagefs-status
```
</div>

Check if CageFS is enabled for a particular user (as <span class="notranslate">`root`</span> ):

<div class="notranslate">

```
$ /usr/sbin/cagefsctl --user-status _USER_NAME_
```
</div>

Check if you are inside CageFS:

Check for the presence of <span class="notranslate">`/var/.cagefs/.cagefs.token`</span> file - if present, it means that you are inside CageFS.

### Displaying CPU, memory & IO limits


Most control panels choose to display CloudLinux usage & limits to end customers. To simplify that, we lve-stats exports a file that can be easily read and processed by a control panel to display the necessary information.

The information is located in the <span class="notranslate">/var/lve/info </span> file. This information is updated every 5 minutes, and contains default limits (first line), as well as usage and limits for all customers. If a customer is not present in the file, it means that customer is not active (no scripts were executed recently for the customer), and a customer has default limits (so you can display no usage, and default limits in the control panel for that customer.

The data is stored in a form of one line per customer, with coma separated values.

| | |
|-|-|
|0 | user id|
|1 | <span class="notranslate"> entry processes </span>|
|2 | <span class="notranslate"> entry processes </span> limit|
|3 | <span class="notranslate"> CPU </span>|
|4 | <span class="notranslate"> CPU </span> limit|
|5 | <span class="notranslate"> Virtual Memory </span>|
|6 | <span class="notranslate"> Virtual Memory </span> Limit|
|7 | Number of <span class="notranslate">  virtual memory </span> faults|
|8 | Number of <span class="notranslate"> entry processes </span> faults|
|9 | <span class="notranslate"> Physical Memory </span> Limit|
|10 | <span class="notranslate"> Physical Memory </span>|
|11 | Number of <span class="notranslate"> Physical memory </span> faults|
|12 | <span class="notranslate"> Number of processes </span> limit|
|13 | <span class="notranslate"> Number of processes </span>|
|14 | <span class="notranslate"> Number of processes </span> fault|
|15 | Reserved|
|16 | <span class="notranslate"> IO </span> Usage|
|17 | <span class="notranslate"> IO </span> Limit|

With LVE version 4 (CloudLinux lve0.x) only the first 9 parameters are available. You can check the the version by reading the first byte of <span class="notranslate">/proc/lve/list. </span>

In the version 6 all 15 parameters should be available.

There are only 2 LVE versions currently used in production. Future versions might add more fields, but will not alter order of existing fields.

Memory is defined in 4KB pages (so, 1024 would mean 1024 4KB pages, or 4MB).

<span class="notranslate"> IO </span> is defined as KB/s.

<span class="notranslate"> CPU </span> is defined as % of total number of cores on a server.

### cPanel LVE Extension

:::tip Note
<span class="notranslate">LVE Manager</span> 1.0-9.8+
:::

<span class="notranslate"> cPanel LVE Extension </span> allows to control LVE limits for packages via cPanel hosting packages control interface and via <span class="notranslate"> cPanel WHM API </span> . It simplifies integration with existing billing systems for cPanel (like WHMCS for example).

#### **Add Package Extension**

To add LVE Settings to standard cPanel package, go to <span class="notranslate">_Packages_</span> | <span class="notranslate">_Add a Package_</span>.

:::tip Note
You can find the information on how to add a package in official cPanel documentation on the link: [https://documentation.cpanel.net/display/ALD/Add+a+Package](https://documentation.cpanel.net/display/ALD/Add+a+Package)
:::

![](/images/lve-extension_01.jpg)


Tick <span class="notranslate">_LVE Settings_</span> in the bottom of the page to open <span class="notranslate">_LVE Settings_</span> form.

![](/images/lve-extension_02.jpg)

You can specify the following options:

:::tip Note
Your changes to <span class="notranslate">_LVE Settings_</span> will appear in the system after a little while.
:::

| | |
|-|-|
|<span class="notranslate">Speed Settings</span> | Maximum CPU usage for an account. Must be in the range 1 - 100 (but obligatory > 0 ) if old format is used; use `%` or <span class="notranslate">`Mhz\Ghz`</span> to set <span class="notranslate">`CPU`</span> limit as speed; Type <span class="notranslate">`DEFAULT`</span> to use default value.|
|<span class="notranslate"> Memory Settings </span> |`Pmem` - Maximum physical memory usage for an account. `Vmem` - Maximum virtual memory usage for an account. Must be a positive number. Postfix allowed only in `KGMT`. Type <span class="notranslate">`DEFAULT`</span> to use default value. Type `0` for unlimited resource.|
|<span class="notranslate"> Max entry proc Settings </span> | Maximum number of entry processes (concurrent connections) for an account. Must be a positive number. Type <span class="notranslate">`DEFAULT`</span> to use default value. Type `0` for unlimited resource.|
|<span class="notranslate"> Nproc Settings </span> | Maximum number of processes usage for an account. Must be a positive number. Type <span class="notranslate">`DEFAULT`</span> to use default value. Type `0` for unlimited resource.|
|<span class="notranslate"> IO Settings </span> | Maximum <span class="notranslate">I/O (input/output)</span> usage speed for an account. Is measured in <span class="notranslate">`Kb/s`</span>. Must be a positive number. Type <span class="notranslate">`DEFAULT`</span> to use default value. Type `0` for unlimited resource.|
|<span class="notranslate"> IOPS Settings </span> | Maximum <span class="notranslate">`IOPS`</span> (input/output operations per second) usage for an account. Must be a positive number. Type <span class="notranslate">`DEFAULT`</span> to use default value. Type `0` to unlimited resource.|

![](/images/lve-extension_03.jpg) 

Click <span class="notranslate">_Add_</span> to apply your changes.

#### **Edit Package Extensions**

You can edit limits in any convenient for you way - in <span class="notranslate">_Edit a Package_</span> section, in the  <span class="notranslate">LVE Manager </span> or even via WHM API.

<span class="notranslate">**Edit a Package**</span>

To edit package extensions, go to <span class="notranslate"> _Packages_</span> | <span class="notranslate">_Edit a Package_</span>. Choose a package from the <span class="notranslate">_Package_</span> list and click <span class="notranslate">_Edit_</span>.

![](/images/lve-extension_04.jpg)

<span class="notranslate">**LVE Manager**</span>

To edit package extensions, go to <span class="notranslate">LVE Manager</span> | <span class="notranslate">Server Configuration</span> | <span class="notranslate"> CloudLinux LVE Manager</span> | <span class="notranslate"> Packages</span> and click pencil (edit) icon.

![](/images/lve-extension_05.jpg)

<span class="notranslate">**WHM API**</span>

To learn how to work with package extensions limits using WHM API, please read the official cPanel documentation: [https://documentation.cpanel.net/display/SDK/Guide+to+Package+Extensions+-+Data+Behavior+and+Changes](https://documentation.cpanel.net/display/SDK/Guide+to+Package+Extensions+-+Data+Behavior+and+Changes)


### Package integration

**[lve-utils 1.4+]**

CloudLinux can automatically detect the most popular control panels, like cPanel - and allows to set different limits for users in different packages. It simplifies management as you don't have to choose between one limit that fits all your customers on the server, or individual limits for the customers.

If you have a custom made control panel, with your own 'package' implementation, you can still use CloudLinux framework to manage limits for your packages.

To do that, you would need:

Implement script that would map users to packages.

Configure lvectl to use your script.

**Implementing script**

A script can be written in any language, and it has to be executable.

It should accept the following arguments:

--list-all                        prints [userid package] pairs

Output should look like a list of space separate pairs of user Linux IDs and package names.

<div class="notranslate">

```
100 package1
101 package1
102 package2
103 package3
```
</div>

<span class="notranslate">--userid=id prints package for a user specified </span>

Output should contain package name, like:

<div class="notranslate">

```
package1
```
</div>

<span class="notranslate">--package="package"    prints users for a package specified. </span>

Output should look like a list of user Linux IDs.

<div class="notranslate">

```
100
101
```
</div>

<span class="notranslate">--list-packages prints the list of packages </span>

Output contains a list of names of packages, like:

<div class="notranslate">

```
package1
package2
package3
```
</div>

**Configuring lvectl to use your custom script**

Edit <span class="notranslate">/etc/sysconfig/cloudlinux </span> file.

Edit or modify parameter <span class="notranslate">`CUSTOM_GETPACKAGE_SCRIPT`</span>, and set it to point to your script, like: <span class="notranslate">`CUSTOM_GETPACKAGE_SCRIPT=/absolute/path/to/your/script`</span>


For the script example please check the following article: [https://cloudlinux.zendesk.com/hc/en-us/articles/115004529105-Integrating-LVE-limits-with-packages-for-unsupported-control-panels](https://cloudlinux.zendesk.com/hc/en-us/articles/115004529105-Integrating-LVE-limits-with-packages-for-unsupported-control-panels).