# Command-line tools (CLI)

The list of the commands (CLI) you can use to manage CloudLinux OS components.

* [CageFS](/command-line_tools/#cagefs)
* [LVE-stats 2](/command-line_tools/#lve-stats-2)
* [MySQL Governor](/command-line_tools/#mysql-governor)
* [PHP Selector](/command-line_tools/#php-selector)
* [Python Selector](/command-line_tools/#python-selector)
* [Ruby Selector](/command-line_tools/#ruby-selector)
* [Node.js Selector](/command-line_tools/#node-js-selector)
* [Apache mod_lsapi PRO](/command-line_tools/#apache-mod-lsapi-pro)
* [Other CLI tools](/command-line_tools/#other-cli-tools)

## CageFS

`cagefsctl` is used to manage CageFS. It allows initializing and updating CageFS, as well as enabling/disabling CageFS for individual users.

Use the following syntax to manage CageFS:
<span class="notranslate">`/usr/sbin/cagefsctl [OPTIONS]`</span>


Options:

| | | |
|-|-|-|
|-i | <span class="notranslate"> --init </span> |initialize CageFS (create CageFS if it does not exist)|
|-r | <span class="notranslate"> --reinit </span> |reinitialize CageFS (make backup and recreate CageFS)|
|-u | <span class="notranslate"> --update </span> |update files in CageFS (add new and modified files to CageFS, remove unneeded files)|
|-f | <span class="notranslate"> --force </span> |recreate CageFS (do not make backup, overwrite existing files)|
|-d | <span class="notranslate"> --dont-clean </span> |do not delete any files from skeleton (use with <span class="notranslate"> --update </span> option)|
|-k | <span class="notranslate"> --hardlink </span> |use hardlinks if possible|
| | <span class="notranslate"> --create-mp </span> |Creates _/etc/cagefs/cagefs.mp_ file|
| | <span class="notranslate"> --mount-skel </span> |mount CageFS skeleton directory|
| | <span class="notranslate"> --unmount-skel </span> |unmount CageFS skeleton directory|
| | <span class="notranslate"> --remove-all </span> |disable CageFS, remove templates and _/var/cagefs_ directory|
| | <span class="notranslate"> --sanity-check </span> |perform basic self-diagnistics of common cagefs-related issues (mostly useful for support)|
| | <span class="notranslate"> --addrpm </span> |add rpm-packages in CageFS (run <span class="notranslate"> `cagefsctl --update` </span> in order to apply changes)|
| | <span class="notranslate"> --delrpm </span> |remove rpm-packages from CageFS (run <span class="notranslate"> `cagefsctl --update` </span> in order to apply changes)|
| | <span class="notranslate"> --list-rpm </span> |list rpm-packages that are installed in CageFS|
|-e | <span class="notranslate"> --enter </span> |enter into user's CageFS as root|
| | <span class="notranslate"> --update-list </span> |update specified files only (paths are read from stdin)|
| | <span class="notranslate"> --update-etc </span> |update _/etc_ directory of all or specified users|
| | <span class="notranslate"> --set-update-period </span> |set min period of update of CageFS in days (default = 1 day)|
| | <span class="notranslate"> --force-update </span> |force update of CageFS (ignore period of update)|
| | <span class="notranslate"> --force-update-etc </span> |force update of _/etc_ directories for users in CageFS|
| | <span class="notranslate"> --reconfigure-cagefs </span> |configure CageFS integration with other software (control panels, database servers, etc)|

Use the following syntax to manage users:    
<span class="notranslate"> `/usr/sbin/cagefsctl [OPTIONS] username [more usernames]` </span>

Options:

| | | |
|-|-|-|
|-m | <span class="notranslate"> --remount </span> |remount specified user(s)|
|-M | <span class="notranslate"> --remount-all </span> |remount CageFS skeleton directory and all users (use this each time you have changed _cagefs.mp_ file|
|-w | <span class="notranslate"> --unmount </span> |unmount specified user(s)|
|____ | <span class="notranslate"> --unmount-dir </span> |unmount specified dir for all users|
|-W | <span class="notranslate"> --unmount-all </span> |unmount CageFS skeleton directory and all users|
|-l | <span class="notranslate"> --list </span> |list users that entered in CageFS|
| | <span class="notranslate"> --list-logged-in </span> |list users that entered in CageFS via SSH|
| | <span class="notranslate"> --enable </span> |enable CageFS for the user|
| | <span class="notranslate"> --disable </span> |disable CageFS for the user|
| | <span class="notranslate"> --enable-all </span> |enable all users, except specified in _/etc/cagefs/users.disabled_|
| | <span class="notranslate"> --disable-all </span> |disable all users, except specified in _/etc/cagefs/users.enabled_|
| | <span class="notranslate"> --display-user-mode </span> |display the current mode ( <span class="notranslate"> "Enable All" </span> or <span class="notranslate"> "Disable All" </span> )|
| | <span class="notranslate"> --toggle-mode </span> |toggle mode saving current lists of users (lists of enabled and disabled users remain unchanged)|
| | <span class="notranslate"> --list-enabled </span> |list enabled users|
| | <span class="notranslate"> --list-disabled </span> |list disabled users|
| | <span class="notranslate"> --user-status </span> |print status of specified user (enabled or disabled)|
| | <span class="notranslate"> --getprefix </span> |display prefix for user|

<span class="notranslate"> PHP Selector </span> related options:
 
| | |
|-|-|
| <span class="notranslate"> --setup-cl-selector </span> | setup <span class="notranslate"> PHP Selector </span> or register new alt-php versions|
| <span class="notranslate"> --remove-cls-selector </span> |unregister alt-php versions, switch users to default php version when needed|
| <span class="notranslate"> --rebuild-alt-php-ini </span> |rebuild _alt_php.ini_ file for specified users (or all users if none specified)|
| <span class="notranslate"> --validate-alt-php-ini </span> |same as <span class="notranslate"> `--rebuild-alt-php-ini` </span> but also validates _alt_php.ini_ options|
| <span class="notranslate"> --cl-selector-reset-versions </span> |reset php version for specifed users to default (or all users if none specified)|
| <span class="notranslate"> --cl-selector-reset-modules </span> |reset php modules (extensions) for specific users to defaults (or all users if none specified)|
| <span class="notranslate"> --create-virt-mp </span> |create virtual mount points for the user|
| <span class="notranslate"> --create-virt-mp-all </span> |create virtual mount points for all users|
| <span class="notranslate"> --remount-virtmp </span> |create virtual mount points and remount user|
| <span class="notranslate"> --apply-global-php-ini </span> |use with 0, 1 or 2 arguments from the list: <span class="notranslate"> `error_log`, `date.timezone` </span> without arguments applies all global php options including the two above|

Common options:

| | | |
|-|-|-|
|___ | <span class="notranslate"> --disable-cagefs </span> |disable CageFS|
| | <span class="notranslate"> --cagefs-status </span> |print CageFS status: ( <span class="notranslate"> enabled </span> or <span class="notranslate"> disabled </span> )|
| | <span class="notranslate"> --set-min-uid </span> |Set min <span class="notranslate"> UID </span> |
| | <span class="notranslate"> --get-min-uid </span> |Display current MIN_UID setting|
| | <span class="notranslate"> --print-suids </span> |Print list of <span class="notranslate"> SUID </span> and SGID programs in skeleton|
| | <span class="notranslate"> --do-not-ask </span> |assume <span class="notranslate"> "yes" </span> in all queries (should be the first option in command)|
| | <span class="notranslate"> --clean-var-cagefs </span> |clean _/var/cagefs_ directory (remove data of non-existent users)|
| | <span class="notranslate"> --set-tmpwatch </span> |set `tmpwatch` command and parameters (save to _/etc/cagefs/cagefs.ini_ file)|
| | <span class="notranslate"> --tmpwatch </span> |execute tmpwatch (remove outdated files in tmp directories in CageFS for all users)|
| | <span class="notranslate"> --toggle-plugin </span> |disable/enable CageFS plugin|
|-v | <span class="notranslate"> --verbose </span> |verbose output|
| | <span class="notranslate"> --wait-lock </span> |wait for end of execution of other `cagefsctl` processes (when needed) before execution of the command|
|-h | <span class="notranslate"> --help </span> |this message|



#### Running command inside CageFS

::: tip Note
lve-wrappers 0.6-1+
:::

Sometimes you will need to execute a command as user inside CageFS.

If a user has shell enabled - you can simply use:
<div class="notranslate">

```
$ /bin/su - $USERNAME  -c "_command_"
```
</div>
Yet, if a user have they shell disabled, it wouldn't work. To solve this issue, we have added command:
<div class="notranslate">

```
$ /sbin/cagefs_enter_user $USERNAME "_command_"
```
</div>

If you disable CageFS for a user, then <span class="notranslate"> `cagefs_enter` </span> will be executed without <span class="notranslate"> `proxyexec` </span> .

You can forcibly disable <span class="notranslate"> `cagefs_enter` </span> start via <span class="notranslate"> `proxyexec` </span> for all users (regardless if CageFS is enabled or disabled) by specifying the parameter <span class="notranslate"> _cagefs_enter_proxied=0_ in _/etc/sysconfig/cloudlinux_ </span> .

<span class="notranslate"> _/bin/cagefs_enter.proxied_ </span> can be executed instead of <span class="notranslate"> _/bin/cagefs_enter_ </span> to enter CageFS without <span class="notranslate"> `proxyexec` </span> . Note that starting <span class="notranslate"> `cagefs_enter` </span> via <span class="notranslate"> `proxyexec` </span> is necessary to enable sending local notification messages to users with enabled CageFS. <span class="notranslate"> `cagefs_enter` </span> is executed via <span class="notranslate"> `proxyexec` </span> by default.


#### Sanity check


:::tip Note
CageFS 6.0-34+
:::

CageFS <span class="notranslate">`--sanity-check`</span> utility allows to check CageFS configuration consistency, so that an administrator can save the time investigating issues with CageFS and ensure that custom configuration is correct.

To start, run the command:
<div class="notranslate">

```
cagefsctl --sanity-check
```
</div>
At the moment 7 types of check are implemented:

1. _Check cagefs mount points exists_ - reads _cagefs.mp_ file and verifies if the directories specified in it really exist on the disk. To learn more, visit [Mount points](/cloudlinux_os_components/#mount-points) and [Split by username](/cloudlinux_os_components/#split-by-username)

2. _Check cagefs <span class="notranslate"> `users.enabled` </span> is a directory_ - ensures that if  <span class="notranslate"> _/etc/cagefs/users.enabled_ </span> exists, then it is a directory, not a file (if it is recognized as a file, then it would cause a breakdown).

3. _Check cagefs <span class="notranslate"> `users.disabled` </span> is a directory_ - ensures that if  <span class="notranslate"> _/etc/cagefs/users.disabled_ </span> exists, then it is a directory, not a file (if it is recognized as a file, then it would cause a breakdown).

4. _Check cagefs <span class="notranslate"> `disable.etcfs` </span> exists_ - checks if <span class="notranslate"> _/etc/cagefs/etc.safe/disable.etcfs_ </span> exists.

5. _Check cagefs users can enter cagefs_ - chooses two users in the system with enabled CageFS (the first and the second ones in the unsorted list) and tries to log in to CageFS under their credentials and see what happens. It runs <span class="notranslate"> `su -l "$USER" -s /bin/bash -c "whoami"` </span> and compares the output with the <span class="notranslate"> $USER </span> and <span class="notranslate"> su </span> command retcode estimation.

::: tip Note
If a login fails, it can be due to various reasons, that can only be determined in manual mode. The checker only gives the output of the command.
:::

6. _Check cagefs proxy commands configs are parsable_ - tries to load <span class="notranslate"> _/etc/cagefs/*.proxy.commands_ </span> files and parse them to check the syntax. In case of any parsing error the test will fail. To learn more, visit [Executing by proxy](/cloudlinux_os_components/#executing-by-proxy).

7. _Check cagefs virt.mp files syntax_ - reads all _/var/cagefs///virt.mp_ files (if any) and checks their syntax validity. At the moment there are only two checks of the syntax: the file is not empty if it exists, and the file is not starting with the sub directory definitions (with @). To learn more, visit [Per-user virtual mount points](/cloudlinux_os_components/#per-user-virtual-mount-points)

8. _Check MultiPHP system default PHP version_ – checks that MultiPHP system default PHP version is **NOT** Alt-PHP. That means <span class="notranslate"> PHP Selector </span> should work properly. If MultiPHP system default PHP version is Alt-PHP, <span class="notranslate"> PHP Selector </span> does not work and should be disabled. To learn more on how to disable <span class="notranslate"> PHP Selector, </span> visit [cPanel LVE Manager](/cloudlinux_os_components/#php-selector) 

Possible results of the checks:

* <span class="notranslate"> OK </span> - the check succeeded.

* <span class="notranslate"> FAILED </span> - the check revealed a problem.

* <span class="notranslate"> SKIPPED </span> - the check was skipped as it made no sense in such environment (e.g. wrong control panel) or can not be performed for some reason (e.g no users with enabled CageFS found). The actual result does not mean that a problem exists and can be considered as positive.

* <span class="notranslate"> INTERNAL_TEST_ERROR </span> - the check failed because of a problem inside the checker itself. Must be reported to the developers.

In case if at least one of the checks resulted neither <span class="notranslate"> OK </span> nor <span class="notranslate"> SKIPPED </span> then the checker will end with ret code >0.


#### CageFS quirks


Due to the nature of CageFS, some options will not work as before or will require some changes:

* lastlog will not work ( <span class="notranslate"> _/var/log/lastlog_ </span>).
* PHP will load php.ini from <span class="notranslate"> _/usr/selector/php.ini._ </span> That file is actually a link to the real _php.ini_ file from your system. So the same _php.ini_ will be loaded in the end.
* You have to run <span class="notranslate"> `cagefsctl --update` </span> any time you have modified _php.ini_, or you want to get new/updated software inside CageFS.
* CageFS installation changes <span class="notranslate"> `jailshell` </span> to regular bash on cPanel - [read why](https://cloudlinux.zendesk.com/hc/articles/115004517685-Why-CageFS-installation-changes-jailshell-to-regular-bash-on-cPanel-).

## LVE-stats 2

| | |
|-|-|
|<span class="notranslate"> `/usr/sbin/lveinfo` </span> |utility to display historical information about LVE usage.|
|<span class="notranslate"> `/usr/sbin/lvechart` </span> |creates a chart representing LVE usage for user.|
|<span class="notranslate"> `/usr/sbin/dbgovchart` </span> |creates a chart representing MySQL usage for user.|
|<span class="notranslate"> `/usr/sbin/lve-read-snapshot` </span> |displays information from system state (snapshots) for user.|
|<span class="notranslate"> `/usr/sbin/lve-create-db` </span> |creates/recreates database for <span class="notranslate">lve-stats</span>.|
|<span class="notranslate"> `/usr/sbin/cloudlinux-top` </span> |utility provides information about current MySQL and LVE usage of a running system in JSON format.|
|<span class="notranslate"> `/usr/sbin/cloudlinux-statistics` </span> |utility provides historical information about resource usage.|

<div class="notranslate">

#### lveinfo

</div>

:::tip Note
<span class="notranslate">lve-stats-2.2-2</span>
:::

**Usage**

<div class="notranslate">

```
lveinfo [-h] [-v] [--dbgov DBGOV] [-f YYYY-MM-DD[HH:MM]]

              [-t YYYY-MM-DD[HH:MM]] [--period PERIOD] [-u USER | --id ID]

              [-d] [-o ALIAS] [-b ALIAS [ALIAS ...]] [-p 0..100]

              [--by-fault ALIAS [ALIAS ...]] [-r FAULTS]

              [--style {user,admin}] [-l LIMIT] [-c [PATH] | -j]

              [--server_id SERVER_ID] [--servers-info]

              [--show-all | --show-columns COLUMN_NAME [COLUMN_NAME ...]]

              [--time-unit TIME_UNIT] [-m {v1,v2}]

              [--blank-value [BLANK_VALUE]]
```
</div>

<span class="notranslate">`lveinfo`</span> is an utility to display historical information about LVE usage.

**Optional arguments**

* <span class="notranslate"> `-h, --help` </span> – show this help message and exit
* <span class="notranslate"> `-v, --version` </span> – show program's version number and exit
* <span class="notranslate"> `--dbgov DBGOV` </span> – show <span class="notranslate"> MySql Governor</span> statistic
* <span class="notranslate"> `-u USER, --user USER` </span> – use username instead of <span class="notranslate"> LVE id</span>, and show only record for that user
* <span class="notranslate"> `--id ID` </span> – will display record only for that <span class="notranslate"> LVE id</span>
* <span class="notranslate"> `-d, --display-username` </span> – try to convert <span class="notranslate"> LVE id</span> into username when possible
* <span class="notranslate"> `-o ALIAS, --order-by ALIAS` </span> – orders results by one of the following:
  | | | |
  |-|-|-|
  |<span class="notranslate">ALIAS</span>|<span class="notranslate">ALIAS</span>|DESCRIPTION|
  |<span class="notranslate">`cpu_avg`</span>|<span class="notranslate">`aCPU`</span>|average CPU usage|
  |<span class="notranslate">`cpu_max`</span>|<span class="notranslate">`mCPU`</span>|max CPU usage|
  |<span class="notranslate">`total_cpu_faults`</span>|<span class="notranslate">`CPUf`</span>|total number of max CPU usage faults|
  |<span class="notranslate">`vmem_avg`</span>|<span class="notranslate">`aVMem`</span>|average virtual memory usage||<span class="notranslate">`vmem_max`</span>|<span class="notranslate">`mVMem`</span>|average virtual memory usage||<span class="notranslate">`total_vmem_faults`</span>|<span class="notranslate">`VMemF`</span>|total number of out of virtual memory faults|
  |<span class="notranslate">`mep_avg`</span>|<span class="notranslate">`aEP`</span>|average number of entry processes (concurrent connections)|
  |<span class="notranslate">`mep_max`</span>|<span class="notranslate">`mEP`</span>|max number of entry processes (concurrent connections)|
  |<span class="notranslate">`total_ep_faults`</span>|<span class="notranslate">`EPf`</span>|total number of max entry processes faults|
  |<span class="notranslate">`pmem_avg`</span>|<span class="notranslate">`aPMem`</span>|average physical memory usage (LVE version >= 6)|
  |<span class="notranslate">`pmem_max`</span>|<span class="notranslate">`mPMem`</span>|max physical memory usage (LVE version >= 6)|
  |<span class="notranslate">`nproc_avg`</span>|<span class="notranslate">`aNproc`</span>|average number of processes (LVE version >= 6)|
  |<span class="notranslate">`nproc_max`</span>|<span class="notranslate">`mNproc`</span>|max number of processes (LVE version >= 6)|
  |<span class="notranslate">`io_avg`</span>|<span class="notranslate">`aIO`</span>|average io usage (LVE version >= 6)|
  |<span class="notranslate">`io_max`</span>|<span class="notranslate">`mIO`</span>|max io usage (LVE version >= 6)|
  |<span class="notranslate">`total_pmem_faults`</span>|<span class="notranslate">`PMemF`</span>|total number of out of physical memory faults (LVE version >= 6)|
  |<span class="notranslate">`total_nproc_faults`</span>|<span class="notranslate">`NprocF`</span>|total number of max processes faults (LVE version >= 6)|
  |<span class="notranslate">`total_io_faults`</span>|<span class="notranslate">`IOf`</span>|total number of max io faults (LVE version >= 6)|
  |<span class="notranslate">`iops_avg`</span>|<span class="notranslate">`aIOPS`</span>|average io operations (LVE version >= 8)|
  |<span class="notranslate">`iops_max`</span>|<span class="notranslate">`mIOPS`</span>|max io operations (LVE version >= 8)|
  |<span class="notranslate">`total_iops_faults`</span>|<span class="notranslate">`IOPSf`</span>|total number of max io operations faults (LVE version >= 8)|
  |<span class="notranslate">`any_faults`</span>|<span class="notranslate">`anyF`</span>|total number of faults of all types|
* <span class="notranslate"> `-b ALIAS [ALIAS ...]` `--by-usage ALIAS [ALIAS ...]`</span> – show LVEs with usage (averaged) within 90 percent of the limit available values:

  | | | | |
  |-|-|-|-|
  |<span class="notranslate">ALIAS</span>|<span class="notranslate">ALIAS</span>|<span class="notranslate">ALIAS</span>|DESCRIPTION|
  |<span class="notranslate">`cpu_avg`</span>|<span class="notranslate">`cpu`</span>|<span class="notranslate">`aCPU`</span>|average CPU usage|
  |<span class="notranslate">`cpu_max`</span>|<span class="notranslate">`cpu_max`</span>|<span class="notranslate">`mCPU`</span>|max CPU usage|
  |<span class="notranslate">`vmem_avg`</span>|<span class="notranslate">`vmem`</span>|<span class="notranslate">`aVMem`</span>|average virtual memory usage|
  |<span class="notranslate">`vmem_max`</span>|<span class="notranslate">`vmem_max`</span>|<span class="notranslate">`mVMem`</span>|max virtual memory usage|
  |<span class="notranslate">`mep_avg`</span>|<span class="notranslate">`mep`</span>|<span class="notranslate">`aEP`</span>|average number of entry processes (concurrent connections)|
  |<span class="notranslate">`mep_max`</span>|<span class="notranslate">`mep_max`</span>|<span class="notranslate">`mEP`</span>|max number of entry processes (concurrent connections)|
  |<span class="notranslate">`pmem_avg`</span>|<span class="notranslate">`pmem`</span>|<span class="notranslate">`aPMem`</span>|average physical memory usage (LVE version >= 6)|
  |<span class="notranslate">`pmem_max`</span>|<span class="notranslate">`pmem_max`</span>|<span class="notranslate">`mPMem`</span>|max physical memory usage (LVE version >= 6)|
  |<span class="notranslate">`nproc_avg`</span>|<span class="notranslate">`nproc`</span>|<span class="notranslate">`aNproc`</span>|average number of processes (LVE version >= 6)|
  |<span class="notranslate">`nproc_max`</span>|<span class="notranslate">`nproc_max`</span>|<span class="notranslate">`mNproc`</span>|max number of processes (LVE version >= 6)|
  |<span class="notranslate">`io_avg`</span>|<span class="notranslate">`io`</span>|<span class="notranslate">`aIO`</span>|average io usage (LVE version >= 6)|
  |<span class="notranslate">`io_max`</span>|<span class="notranslate">`io_max`</span>|<span class="notranslate">`mIO`</span>|max io usage (LVE version >= 6)|
  |<span class="notranslate">`iops_avg`</span>|<span class="notranslate">`iops`</span>|<span class="notranslate">`aIOPS`</span>|average io operations (LVE version >= 8)|
  |<span class="notranslate">`iops_max`</span>|<span class="notranslate">`iops_max`</span>|<span class="notranslate">`mIOPS`</span>|max io operations (LVE version >= 8)|

* <span class="notranslate">`-p 0..100`, `--percentage 0..100`</span> – defines percentage for <span class="notranslate">`--by-usage`</span> option; default `90`
* <span class="notranslate"> `--style {user,admin}` </span> – deprecated, not used.
* <span class="notranslate"> `-l LIMIT`, `--limit LIMIT` </span> – max number of results to display, `10` by default, if `0` no limit
* <span class="notranslate"> `-c [PATH]`, `--csv [PATH]` </span> – save statistics in CSV format; `-` by default (output to screen)
* <span class="notranslate"> `-j`, `--json` </span> – display output in JSON format
* <span class="notranslate"> `--server_id SERVER_ID` </span> – used with central database for multiple servers, default <span class="notranslate">`localhost`</span>
* <span class="notranslate"> `--servers-info` </span> – show servers LVE versions
* <span class="notranslate"> `--show-all` </span> – full output (show all limits); brief output is default; equivalent <span class="notranslate">`--show-columns all`</span>
* <span class="notranslate"> `-show-columns COLUMN_NAME [COLUMN_NAME ...]` </span> – show only the listed columns; <span class="notranslate">`all`</span> for all supported columns
  
  | | |
  |-|-|
  |<span class="notranslate">COLUMN_NAME</span> |DESCRIPTION|
  |<span class="notranslate"> `From ` </span> |Show start period statistics|
  |<span class="notranslate"> `To  ` </span> |Show end period statistics|
  |<span class="notranslate"> `ID ` </span> |LVE Id or username|
  |<span class="notranslate"> `aCPU` </span> |Average <span class="notranslate"> CPU</span> usage|
  |<span class="notranslate"> `uCPU` </span> |The percentage of user-allocated resource <span class="notranslate">CPU</span>|
  |<span class="notranslate"> `mCPU` </span> |deprecated|
  |<span class="notranslate"> `lCPU` </span> |<span class="notranslate">CPU</span> limit|
  |<span class="notranslate">`CPUf`</span> |Out Of <span class="notranslate">CPU</span> usage Faults|
  |<span class="notranslate">`aEP`</span> | Average Entry Processes|
  |<span class="notranslate">`uEP` </span> |The percentage of user-allocated resource Entry processes|
  |<span class="notranslate">`mEP` </span> |deprecated|
  |<span class="notranslate">`lEP` </span> |maxEntryProc limit|
  |<span class="notranslate">`aVMem` </span> |Average Virtual Memory Usage|
  |<span class="notranslate">`uVMem ` </span> |The percentage of user-allocated resource Virtual Memory|
  |<span class="notranslate">`mVMem` </span> |deprecated|
  |<span class="notranslate">`lVMem` </span> |Virtual Memory Limit|
  |<span class="notranslate">`VMemF` </span> |Out Of Memory Faults|
  |<span class="notranslate">`EPf` </span> |Entry processes faults|
  |<span class="notranslate">`aPMem` </span> |Average Physical Memory Usage (LVE version >= 6)|
  |<span class="notranslate">`uPMem` </span> |The percentage of user-allocated resource Physical Memory (LVE version >= 6)|
  |<span class="notranslate">`mPMem` </span> |deprecated (LVE version >= 6)|
  |<span class="notranslate">`lPMem` </span> |Physical Memory Limit (LVE version >= 6)|
  |<span class="notranslate">`aNproc` </span> |Average Number of processes (LVE version >= 6)|
  |<span class="notranslate">`uNproc` </span> |The percentage of user-allocated resource Number of processes (LVE version >= 6)|
  |<span class="notranslate">`mNproc` </span> |deprecated (LVE version >= 6)|
  |<span class="notranslate">`lNproc` </span> |Limit of Number of processes (LVE version >= 6)|
  |<span class="notranslate">`PMemF` </span> |Out Of Physical Memory Faults (LVE version >= 6)|
  |<span class="notranslate">`NprocF` </span> |Number of processes faults (LVE version >= 6)|
  |<span class="notranslate">`aIO` </span> |Average <span class="notranslate">I/O</span> (LVE version >= 6)|
  |<span class="notranslate">`uIO` </span> |The percentage of user-allocated resource <span class="notranslate">I/O</span> (LVE version >= 6)|
  |<span class="notranslate">`mIO` </span> |deprecated (LVE version >= 6)|
  |<span class="notranslate">`lIO` </span> |<span class="notranslate">I/O</span> Limit (LVE version >= 6)|
  |<span class="notranslate">`IOf` </span> |Out Of <span class="notranslate">I/O</span> usage Faults (LVE version >= 6)|
  |<span class="notranslate">`aIOPS` </span> |Average <span class="notranslate">I/O</span> Operations (LVE version >= 8)|
  |<span class="notranslate">`mIOPS` </span> |deprecated (LVE version >= 8)|
  |<span class="notranslate">`uIOPS` </span> |The percentage of user-allocated resource <span class="notranslate">I/O</span> Operations (LVE version >= 8)|
  |<span class="notranslate">`lIOPS` </span> |<span class="notranslate">I/O</span> Operations Limit (LVE version >= 8) </span>|
  |<span class="notranslate">`IOPSf` </span> |Out Of <span class="notranslate">I/O</span> Operations Faults (LVE version >= 8)|

* <span class="notranslate"> `--time-unit TIME_UNIT` </span> – time step for grouping statistic in minutes; 1 min., by default; can use <span class="notranslate">`m\|h\|d`</span> suffixes; for example: `1h or 1h30m or 1d12h`
* <span class="notranslate"> `-m {v1,v2}`, `--compat {v1,v2}` </span> – `v1` - return old output mode; `v2` - new mode; default `v1`; you can change default in config
* <span class="notranslate"> `--blank-value [BLANK_VALUE]` </span> – Use to fill unsupported limits; default `-`
* <span class="notranslate"> `-f YYYY-MM-DD[ HH:MM]`,  `--from YYYY-MM-DD[ HH:MM]`</span> – run report from date and time in <span class="notranslate">`[YY]YY-MM-DD[ HH:MM]`</span> format; if not present last 10 minutes are assumed
* <span class="notranslate"> `-t YYYY-MM-DD[ HH:MM]`,  `--to YYYY-MM-DD[ HH:MM]`</span> – run report up to date and time in <span class="notranslate">`[YY]YY-MM-DD[ HH:MM]`</span> format; if not present, reports results up to now
* <span class="notranslate"> `--period PERIOD` </span> – time period; specify minutes with <span class="notranslate"> `m`, `h`</span> - hours, days with <span class="notranslate"> `d`</span>, and values: <span class="notranslate"> `today`, `yesterday`; `5m`</span> - last 5 minutes, `4h` - last four hours, `2d` - last 2 days, as well as <span class="notranslate"> `today`</span>
* <span class="notranslate"> `--by-fault ALIAS [ALIAS ...]` </span> – show LVEs which failed on max processes limit or memory limit
  
  | | | | |
  |-|-|-|-|
  |<span class="notranslate">ALIAS</span>|<span class="notranslate">ALIAS</span>|<span class="notranslate">ALIAS</span>|DESCRIPTION|
  |<span class="notranslate">`mcpu`</span>|<span class="notranslate">`cpu`</span>|<span class="notranslate">`CPUf`</span>|total number of max CPU usage faults|
  |<span class="notranslate">`mem`</span>|<span class="notranslate">`vmem`</span>|<span class="notranslate">`VMemF`</span>|total number of out of virtual memory faults|
  |<span class="notranslate">`mep`</span>|<span class="notranslate">`ep`</span>|<span class="notranslate">`EPf`</span>|total number of max entry processes faults|
  |<span class="notranslate">`pmem`</span>|<span class="notranslate">`pmem`</span>|<span class="notranslate">`PMemF`</span>|total number of out of physical memory faults (LVE version >= 6)|
  |<span class="notranslate">`nproc`</span>|<span class="notranslate">`nproc`</span>|<span class="notranslate">`NprocF`</span>|total number of max processes faults (LVE version >= 6)|
  |<span class="notranslate">`io`</span>|<span class="notranslate">`io`</span>|<span class="notranslate">`IOf`</span>|total number of max io faults (LVE version >= 6)|
  |<span class="notranslate">`iops`</span>|<span class="notranslate">`iops`</span>|<span class="notranslate">`IOPSf`</span>|total number of max io operations faults (LVE version >= 8)|
  |<span class="notranslate">`any_faults`</span>|<span class="notranslate">`any`</span>|<span class="notranslate">`anyF`</span>|total number of faults of all types|
* <span class="notranslate"> `-r FAULTS, --threshold FAULTS` </span>– in combination with <span class="notranslate">`--by-fault`</span>, shows only LVEs with number of faults above; default `1`
  
Prefixes <span class="notranslate">`Kb`, `Mb` </span> and <span class="notranslate">`Gb`</span> indicates powers of 1024.

:::tip Note
All <span class="notranslate">ALIAS</span> options are not case sensitive.
:::

<div class="notranslate">

#### lvechart

</div>

`/usr/sbin/lvechart` - creates a chart representing LVE usage for user.

**Usage**

<div class="notranslate">

```
/usr/sbin/lvechart [OPTIONS]
```
</div>

**Acceptable options**

| | |
|-|-|
|<span class="notranslate"> `--help ` </span> |This help screen|
|<span class="notranslate"> `--version` </span> |Version number|
|<span class="notranslate"> `--from` </span> |Run report from date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format (if not present, last 10 minutes are assumed)|
|<span class="notranslate"> `--to=` </span> |Run report up to date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format (if not present, reports results up to now)|
|<span class="notranslate"> `--period=` </span> |Time period: specify minutes with `m`, `h` - hours, days with `d`, and values: <span class="notranslate">`today`</span>, <span class="notranslate">`yesterday`</span>; `5m` - last 5 minutes, `4h` - last four hours, `2d` - last 2 days, as well as today|
|<span class="notranslate"> `--id= ` </span> |<span class="notranslate">`LVE id`</span> will display record only for that <span class="notranslate">LVE id</span>|
|<span class="notranslate"> `--user=` </span> |Use username instead of <span class="notranslate"> LVE id </span>, and show only record for that user|
|<span class="notranslate"> `--server= ` </span> |<span class="notranslate">`Server id`</span> will display record for that server, instead of default (current)|
|<span class="notranslate"> `--output= ` </span> |Filename to save chart as, if not present, output will be sent to STDOUT|
|<span class="notranslate"> `--show-all` </span> |Show all graphs (by default shows graphs for which limits are set)|
|<span class="notranslate"> `--style=` </span> |<span class="notranslate">`admin`, `user`</span> set chart style,  <span class="notranslate">CPU</span> limits are normalized to 100% in user’s style|
|<span class="notranslate"> `--format=` </span> |<span class="notranslate">`svg`, `png`</span> set chart output format|

<div class="notranslate">

#### dbgovchart

</div>


`/usr/sbin/dbgovchart` - creates a chart representing MySQL usage for user.`

**Usage**

<div class="notranslate">

```
/usr/sbin/dbgovchart [OPTIONS]
```
</div>

**Acceptable options**

| | |
|-|-|
|<span class="notranslate"> `--help ` </span> |This help screen|
|<span class="notranslate"> `--version` </span> |Version number|
|<span class="notranslate"> `--from=` </span> |Run report from date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format (if not present, last 10 minutes are assumed)|
|<span class="notranslate"> `--to=` </span> |Run report up to date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format (if not present, reports results up to now)|
|<span class="notranslate"> `--period=` </span> |Time period: specify minutes with `m`,  `h` - hours, days with `d`, and values: <span class="notranslate">`today`</span>, <span class="notranslate">`yesterday`</span>; `5m` - last 5 minutes, `4h` - last four hours, `2d` - last 2 days, as well as today`|
|<span class="notranslate"> `--user=` </span> |mysql username|
|<span class="notranslate"> `--output= ` </span> |Filename to save chart as, if not present, output will be sent to <span class="notranslate">STDOUT</span>|
|<span class="notranslate"> `--show-all` </span> |Show all graphs (by default shows graphs for which limits are set)|
|<span class="notranslate"> `--server=` </span> | <span class="notranslate"> `Server id`</span> will display record for that server, instead of default (current)|
|<span class="notranslate"> `--style=` </span> | <span class="notranslate">`admin`, `user`</span> set chart style,  <span class="notranslate">CPU</span> limits are normalized to 100% in user’s style|
|<span class="notranslate"> `--format=` </span> | <span class="notranslate">`svg`, `png`</span> set chart output format|

<div class="notranslate">

#### lve-read-snapshot

</div>

**Usage**

<div class="notranslate">

```
lve-read-snapshot [-h] [--version] [-f FROM [FROM ...]] [-t TO [TO ...]
                  [ -p PERIOD | --timestamp TIMESTAMP]
                  [-i ID | -u USER] [-l] [-o file] [-j] [--stats]
                  [--unit unit]
```
</div>

Reads LVE system state snapshots for <span class="notranslate">LVE/user</span>.

**Optional arguments**

* <span class="notranslate">`-h, --help`</span> – show this help message and exit
* <span class="notranslate">`--version`</span> – version number
* <span class="notranslate">`-f FROM [FROM ...]`, `--from FROM [FROM ...]`</span> – run report from date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format, if not present last 10 minutes are assumed (default: `2016-10-24 19:28`)
* <span class="notranslate">`-t TO [TO ...]`, `--to TO [TO ...]`</span> – run report up to date and time in <span class="notranslate">`YYYY-MM-DD HH:MM`</span> format, if not present, reports results up to now (default: `2016-10-24 19:38`)
* <span class="notranslate">`-p PERIOD`, `--period PERIOD`</span> – time period specify minutes with `m`, `h` - hours, days with `d`, and values: <span class="notranslate">`today`, `yesterday`</span>, `5m` - last 5 minutes, `4h` - last four hours, `2d` - last 2 days, as well as today (default: `10m`)
* <span class="notranslate">`--timestamp TIMESTAMP`</span> – time stamp in unix format for get one snapshot (default: <span class="notranslate">`None`</span>)
* <span class="notranslate">`-i ID, --id ID`</span> – LVE id to show records for (default: <span class="notranslate">`None`</span>)
* <span class="notranslate">`-u USER`, `--user USER`</span> – user account to show records for (default: <span class="notranslate">`None`</span>)
* <span class="notranslate">`-l`, `--list`</span> – show timestamp list only (default: <span class="notranslate"> `False`</span>)
* <span class="notranslate">`-o file`, `--output file`</span> – filename to save snaphots report to, if not present,output will be sent to <span class="notranslate">STDOUT</span> (default: <span class="notranslate">`None`</span>)
* <span class="notranslate">`-j`, `--json`</span> – output in json format (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--stats`</span> – output stats, instead of snapshots (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--unit unit`</span> – group stats by time unit. Example values `3h`, `24h`, `1d`, `1w`. Other possible value is <span class="notranslate">`auto`</span> for grouping by each incident (default: <span class="notranslate">`1d`</span>)
  
One of <span class="notranslate">`-u --user`</span> or <span class="notranslate">`-i --id`</span> should be specified.

<div class="notranslate">

#### lve-create-db

</div>

**Usage**

<div class="notranslate">

```
lve-create-db [-h] [--recreate] [--print-sql]
                   [--update-serverid-prompt] [--update-serverid-auto]
                   [--validate]
```
</div>

Creates a database for <span class="notranslate">lve-stats</span>.

**Optional arguments**

* <span class="notranslate">`-h`, `--help`</span> – show this help message and exit
* <span class="notranslate">`--recreate`</span> – drops and recreates database even if tables exists (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--print-sql`</span> – prints sql and exits, without creating db (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--update-serverid-prompt`</span> – update exist server ID or create new one (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--update-serverid-auto`</span> – update exist server ID with <span class="notranslate">uuid</span> (default: <span class="notranslate">`False`</span>)
* <span class="notranslate">`--validate`</span> – check the correctness of the database structure (default: <span class="notranslate">`False`</span>)

#### cloudlinux-top

Utility provides information about current MySQL and LVE usage of a running system in JSON format.

#### **Usage**

<div class="notranslate">

```
cloudlinux_top [-h] [-v] [-j] [--hide-mysql]
               [-u USERNAME | -r FOR_RESELLER] [-d DOMAIN] [-m MAX]
               [-o ORDER_BY]
```
</div>

**Optional arguments**

* <span class="notranslate"> `-h, --help` </span> – show this help message and exit
* <span class="notranslate"> `-v, --version`   </span> – show program version number and exit
* <span class="notranslate"> `-j, --json`   </span> – return data in JSON format
* <span class="notranslate"> `--hide-mysql`   </span> | `don't show MySQL related info
* <span class="notranslate"> `-u USERNAME`, `--username USERNAME` </span> – show data only for a specific user. Can be used to filter the output; returns users with username <span class="notranslate">`%USERNAME%`</span>
* <span class="notranslate"> `-r FOR_RESELLER`, `--for-reseller FOR_RESELLER` </span> – get information only about specified reseller and his users
* <span class="notranslate"> `-d DOMAIN`, `--domain DOMAIN` </span> – show data only for a specific domain. Can be used to filter the output; returns users with domain <span class="notranslate">`%DOMAIN%`</span>
* <span class="notranslate"> `-m MAX`, `--max MAX` </span> – show up to <span class="notranslate">`N`</span> records. If <span class="notranslate">`--max`</span> key is omitted. By default will show top 25 users
* <span class="notranslate"> `-o ORDER_BY`, `--order-by ORDER_BY` </span> – sort output by resource usage; available options: <span class="notranslate">`cpu`, `mysql_cpu`, `io`, `mysql_io`, `iops`, `ep`, `nproc`, `pmem`</span>

#### **Output format**

<div class="notranslate">

```
{
  "mySqlGov": "enabled",              # possible values: enabled, error
  "mySqlGovMode": "abusers",          # see “MySQL Governor > Modes Of Operation”
                                      # if MySQL Governor is not enabled, value is "none"
 
  "resellers": [                      # list of resellers (available only with
                                      # reseller limits feature)
      {
          "id": 1000020005,           # internal record id
          "limit": <lve_section>,     # current limits (last 5 seconds)
          "name": "reseller_name",    # reseller’s login in control panel
          "usage": <lve_section>      # current usage (last 5 seconds)
      }
  ],
  "result": "success",                # see the ‘errors handling’ section
  "timestamp": 1522858537.337549,
  "users": [
      {
          "domain": "domain.com",     # user’s primary domain (from control panel)
          "id": 20005,                # lve_id, same as user id in /etc/passwd file
          "limit": <lve_section>,     # limits for last 5 seconds
          "reseller": "reseler1",     # user’s reseller (from control panel)
          "usage": <lve_section>,     # usage for last 5 seconds
          "username": "user"          # username from /etc/passwd file or “N/A” if user
                                      # with such id does not exist
       }
   ]
 }
```
</div>

The structure<sup> *</sup> of <span class="notranslate">`<lve_section>`</span>:

<div class="notranslate">

```
{
"cpu": {
 "all": 50.0,      # CPU usage or limit (LVE only)
 "mysql": 0.0*     # CPU usage or limit (MySQL Governor only)
},
"ep": 1.0,           # number of entry processes
"io": {
 "all": 0.0,       # IO usage or limit (LVE only)
 "mysql": 0.0**     # IO usage or limit (MySQL Governor only)
},
"iops": 0.0,         # IO operations per second
"mem": 258048,       # memory usage or limit
"pno": 1.0           # number of processes
}
```
</div>


:::tip Note
* you can modify this structure using <span class="notranslate">`--show`</span> option, see [usage examples](/command-line_tools/#examples) for details.
* MySQL values are only present when <span class="notranslate">MySQL Governor</span> statistics is available and <span class="notranslate">`--hide-mysql`</span> options is not used.
:::

#### **Units of measurement**

For <span class="notranslate">`limits`</span> and <span class="notranslate">`usage`</span> sections we use the following units of measurement.

| | |
|-|-|
|**Value** | **Units of measurement**|
|<span class="notranslate"> cpu (lve and mysql) </span> | percentage of one <span class="notranslate"> CPU </span> core|
|<span class="notranslate"> io (lve and mysql) </span> | bytes per second|
|<span class="notranslate"> iops </span> | number of <span class="notranslate"> IO </span> operations per second|
|<span class="notranslate"> mem </span> | bytes|
|<span class="notranslate"> ep </span> | number of entry processes|
|<span class="notranslate"> pno </span> | number of processes|


#### **Errors handling**

The format of the error message is the same as in the other <span class="notranslate">`cloudlinux- *`</span> utilities. When everything is ok, the <span class="notranslate">`result`</span> value is <span class="notranslate">`success`</span>. Otherwise, it contains error message. In case of unexpected errors, the output will be as follows.

<div class="notranslate">

```
# cloudlinux-top --json 
{
  "context": {
      "error_text": "Very bad error"
  },
  "result": "An error occured: \"%(error_text)s\"",
  "timestamp": 1523871939.639394
}
```
</div>


#### **Examples**


* get 100 users ordered by <span class="notranslate"> CPU </span> usage

  <div class="notranslate">

  ```
  # cloudlinux-top --json --order-by cpu --max=100
  ```
  </div>

* get information about one user

  <div class="notranslate">

  ```
  # cloudlinux-top --json -u username
  ```
  </div>

* get information about reseller and his users

  <div class="notranslate">

  ```
  # cloudlinux-top --json --for-reseller=reseller_name
  ```
  </div>

* show only <span class="notranslate">IO</span> limits and usage

  <div class="notranslate">

  ```
  # cloudlinux-top --json --show=io
  ```
  </div>

<div class="notranslate">

#### cloudlinux-statistics

</div>

<span class="notranslate">cloudlinux-statistics</span> is a <span class="notranslate">CLI</span> utility that provides historical information about resource usage.

#### **Usage**

<div class="notranslate">

```
cloudlinux-statistics [-h] [-j] [-v] [--by-usage BY_USAGE]
                      [--percentage 0..100] [--by-fault BY_FAULT]
                      [--threshold THRESHOLD] [--server_id SERVER_ID]
                      [-f FROM] [-t TO] [--period PERIOD]
                      [--limit LIMIT]
                      [--show COLUMN_NAME [COLUMN_NAME ...]]
                      [-o ORDER_BY] [--id ID] [--time-unit TIME_UNIT]
                      [-r FOR_RESELLER]
```
</div>

**Optional arguments**

* <span class="notranslate"> `-h`, `--help` </span> – show this help message and exit
* <span class="notranslate"> `-j`, `--json` </span> – return data in JSON format
* <span class="notranslate"> `-v`, `--version` </span> – show program version number and exit
* <span class="notranslate"> `--server_id SERVER_ID`, `--server-id SERVER_ID` </span> – can be used with the central database for multiple servers; default `...`
* <span class="notranslate"> `--limit LIMIT` </span> – limit the number of results to display, `0` is unlimited
* <span class="notranslate"> `--show COLUMN_NAME [COLUMN_NAME ...]` </span> – show only listed columns; <span class="notranslate">`all`</span> for all supported columns (fields)
  | | |
  |-|-|
  |<span class="notranslate">Key</span>|Fields to show|
  |<span class="notranslate">`all`</span>|all available fields|
  |<span class="notranslate">`cpu`</span>|CPU field|
  |<span class="notranslate">`io`</span>|IO field|
  |<span class="notranslate">`iops`</span>|IOPS field|
  |<span class="notranslate">`ep`</span>|entry processes (concurrent connections) field|
  |<span class="notranslate">`nproc`</span>|number of processes field|
  |<span class="notranslate">`pmem`</span>|physical memory field|
  |<span class="notranslate">`vmem`</span>|virtual memory field|
  |<span class="notranslate">`mysql`</span>|`mysql_cpu` & `mysql_io` field|

* <span class="notranslate"> `-o ORDER_BY`, `--order-by ORDER_BY` </span> – order results by one of the following keys (fields):
  | | |
  |-|-|
  |FIELD|DESCRIPTION|
  |<span class="notranslate">`any_faults`</span>|total number of faults of all types|
  |<span class="notranslate">`cpu`</span>|average CPU usage`</span>|
  |<span class="notranslate">`mysql_cpu`</span>|average MySQL CPU usage`</span>|
  |<span class="notranslate">`io`</span>|average IO usage`</span>|
  |<span class="notranslate">`mysql_io`</span>|average MySQL IO usage`</span>|
  |<span class="notranslate">`iops`</span>|average IO operations; (LVE version >= 8)`</span>|
  |<span class="notranslate">`ep`</span>|average number of entry processes (concurrent connections)`</span>|
  |<span class="notranslate">`nproc`</span>|average number of processes`</span>|
  |<span class="notranslate">`pmem`</span>|average physical memory usage`</span>|
  |<span class="notranslate">`vmem`</span>|average virtual memory usage`</span>|
  |<span class="notranslate">`cpu_faults`</span>|total number of CPU usage faults`</span>|
  |<span class="notranslate">`io_faults`</span>|total number of max IO faults`</span>|
  |<span class="notranslate">`iops_fault`</span>|total number of max IO operations faults; (LVE version >= 8)`</span>|
  |<span class="notranslate">`ep_faults`</span>|total number of max entry processes faults`</span>|
  |<span class="notranslate">`nproc_faults`</span>|total number of max processes faults`</span>|
  |<span class="notranslate">`pmem_faults`</span>|total number of out of physical memory faults`</span>|
  |<span class="notranslate">`vmem_faults`</span>|total number of out of virtual memory faults`</span>|

* <span class="notranslate"> `-r FOR_RESELLER`, `--for-reseller FOR_RESELLER` </span> – show statistics only for given reseller and his users

Filter items by resource usage.

* <span class="notranslate"> `--by-usage BY_USAGE` </span> – show LVEs with usage (averaged) within 90 percent of the limit available values
  | | |
  |-|-|
  |FIELD|DESCRIPTION|
  |<span class="notranslate">`cpu`</span>|average CPU usage|
  |<span class="notranslate">`mysql_cpu`</span>|average MySQL CPU usage|
  |<span class="notranslate">`io`</span>|average IO usage|
  |<span class="notranslate">`mysql_io`</span>|average MySQL IO usage|
  |<span class="notranslate">`iops`</span>|average IO operations; (LVE version >= 8)|
  |<span class="notranslate">`ep`</span>|average number of entry processes (concurrent connections)|
  |<span class="notranslate">`nproc`</span>|average number of processes|
  |<span class="notranslate">`pmem`</span>|average physical memory usage|
  |<span class="notranslate">`vmem`</span>|average virtual memory usage|

* <span class="notranslate"> `-percentage 0..100` </span> – define percentage for <span class="notranslate">`--by-usage`</span> option; default `90`

Filter items by the number of faults.

* <span class="notranslate"> `--by-fault BY_FAULT` </span> – show only accounts that have some faults for the given limit
  | | |
  |-|-|
  |FIELD|DESCRIPTION|
  |<span class="notranslate">`any`</span>|faults of all types|
  |<span class="notranslate">`cpu`</span>|CPU usage faults|
  |<span class="notranslate">`io`</span>|max IO usage faults|
  |<span class="notranslate">`iops`</span>|max IO operations faults; (LVE version >= 8)|
  |<span class="notranslate">`ep`</span>|max entry processes faults|
  |<span class="notranslate">`nproc`</span>|max processes faults|
  |<span class="notranslate">`pmem`</span>|out of physical memory faults|
  |<span class="notranslate">`vmem`</span>|out of virtual memory faults|

* <span class="notranslate"> `--threshold THRESHOLD` </span> – in combination with <span class="notranslate">`--by-fault`</span> shows only accounts with the number of faults more than given; default `1`

Filter items by a time interval.

Allows to get information for the given period of time; you can either set <span class="notranslate">`--from`</span> and <span class="notranslate">`--to`</span> options, or just get information for the recent time period using <span class="notranslate">`--period option`.</span>

:::tip Note
<span class="notranslate">`--from`</span> and <span class="notranslate">`--to`</span> values are ignored when <span class="notranslate">`--period`</span> is set.
:::

* <span class="notranslate"> `-f FROM`, `--from FROM` </span> – run report from date and time in <span class="notranslate">`[YY]YY-MM-DD[ HH:MM]`</span> format; if not present, last 10 minutes are assumed
* <span class="notranslate"> `-t TO`, `--to TO` </span> – run report up to date and time in <span class="notranslate">`[YY]YY-MM-DD[ HH:MM]`</span> format; if not present, reports results up to now
* <span class="notranslate"> `--period PERIOD` </span> – time period; specify minutes with <span class="notranslate">`m`</span>, hours with <span class="notranslate">`h`</span>, days with <span class="notranslate">`d`</span>, and values: <span class="notranslate">`today`, `yesterday`</span>; `5m` - last 5 minutes, `4h` - last four hours, `2d` - last 2 days, and <span class="notranslate">`today`</span>

Get detailed statistics.

* <span class="notranslate"> `--id ID` </span> – get detailed statistics for database record with the given id
* <span class="notranslate"> `--time-unit TIME_UNIT` </span> – group statistics using the given time; 1 minute by default. For example: <span class="notranslate">`1h`</span> or <span class="notranslate">`1h30m`</span> or <span class="notranslate">`dynamic`</span>; available only in pair with <span class="notranslate">`--id`</span>


#### **Output format**

There are two different JSON formats used for **summary statistics** and **detailed statistics**.

**Summary statistics**

<div class="notranslate">

```
# cloudlinux-statistics --json
 {
 "resellers": [
   {
     "usage": <lve_section>,
     "faults": <lve_section>,
     "name": "reseller",
     "limits": <lve_section>,
     "id": 1000020005
   }
 ],
 "timestamp": 1522920637,
 "mySqlGov": "enabled",            # possible values: ”enabled”, “error”
 "result": "success",
 "users": [
   {
     "username": "username",
     "domain": "example.com",
     "reseller": "reseller",
     "limits": <lve_section>,
     "faults": <lve_section>,
     "usage": <lve_section>,
     "id": 20005
   }
 ]
 }
```
</div>

**Detailed statistics**

<div class="notranslate">

```
# cloudlinux-statistics --json --id=20001
 {
 "timestamp": 1523011550,
 "mySqlGov": "enabled",           # possible values: ”enabled”, “error”
 "result": "success",
 "user": [
   {
     "usage": <lve_section>,
     "faults": <lve_section>,
     "from": 1523011144,
     "limits": <lve_section>,
     "to": 1523011143
   },
 ...
   {
     "usage": <lve_section>,
     "faults": <lve_section>,
     "from": 1523011204,
     "limits": <lve_section>,
     "to": 1523011203
   }
 ]
 }
```
</div>

For both, **summary statistics** and **detailed statistics**, <span class="notranslate">`<lve_section>`</span> is the same and looks like following<sup> *</sup>.

<div class="notranslate">

```
{
   "ep": {
     "lve": 1        # number of entry processes
   },
   "vmem": {
     "lve": 2428928  # virtual memory usage or limit (deprecated)
   },
   "iops": {
     "lve": 0        # io operations per second
   },
   "io": {
     "lve": 0.0,     # io usage or limit (lve only)
     "mysql": 0.0**   # io usage or limit (mysql only)
   },
   "nproc": {
     "lve": 1        # number of processes in lve
   },
   "cpu": {
     "lve": 25.6,    # cpu usage (lve only)
     "mysql": 0.0*   # cpu usage (mysql governor only)
   },
   "pmem": {
     "lve": 360448   # physical memory usage or limit
   }
 }
```
</div>

:::tip Note
* you can specify only required fields using <span class="notranslate">`--show`</span> option;
* <span class="notranslate">`mysql`</span> fields are only available with <span class="notranslate"> [MySQL Governor](/cloudlinux_os_components/#installation-and-update-3)</span> installed.
:::

#### **Units of measurement**

For <span class="notranslate">`limits`</span> and <span class="notranslate">`usage`</span> sections we use the following units of measurement.

| | |
|-|-|
|Value|Units of measurement|
|<span class="notranslate">`cpu` (LVE and MySQL)</span> | percentage of one <span class="notranslate">CPU</span> core|
|<span class="notranslate">`io` (LVE and MySQL) </span> | bytes per second|
|<span class="notranslate">`iops`</span> | number of <span class="notranslate">IO</span> operations per second|
|<span class="notranslate">`pmem`</span> and <span class="notranslate">`vmem`</span> | bytes|
|<span class="notranslate">`ep`</span> | number of entry processes|
|<span class="notranslate">`nproc`</span> | number of processes in LVE|

#### **Errors handling**

The format of the error message is the same as in the other <span class="notranslate">`cloudlinux- *`</span> utilities. When everything is ok, the <span class="notranslate">`result`</span> value is <span class="notranslate">`success`</span>. Otherwise, it contains error message.

<div class="notranslate">

```
# cloudlinux-statistics --json 
{
  "context": {
      "error_text": "Very bad error"
  },
  "result": "An error occured: \"%(error_text)s\"",
  "timestamp": 1523871939.639394
}
```
</div>

#### **Examples**


* get top 10 users ordered by <span class="notranslate">CPU</span> usage for today

<div class="notranslate">

```
# cloudlinux-statistics --json --order-by=cpu --period=today --limit=10
```
</div>

* get users that hit <span class="notranslate">IO</span> limit more than 10 times for today

<div class="notranslate">

```
# cloudlinux-statistics --json --period=today --by-fault=io --threshold=10
```
</diV>

* get users that used more than 80% of <span class="notranslate">CPU</span> in last 24 hours

<div class="notranslate">

```
# cloudlinux-statistics --json --by-usage=cpu --percentage=80 --period=24h
```
</div>

* get information only about reseller and his users

<div class="notranslate">

```
# cloudlinux-statistics --json --for-reseller=reseller_name
```
</div>

* get information only about <span class="notranslate">CPU</span> and <span class="notranslate">IO</span> usage

<div class="notranslate">

```
# cloudlinux-statistics --json --show=cpu,io
```
</div>


## MySQL Governor

* <span class="notranslate">`dbtop`</span> monitors MySQL usage on per user bases.
* <span class="notranslate">`dbctl`</span> is a command line tool to manage <span class="notranslate">DB Governor</span> configuration.
* <span class="notranslate">`lveinfo --dbgov`</span> provides historical information about usage and customer restrictions. 
* <span class="notranslate">`dbgovchart`</span> generates charts for MySQL usage.


#### dbtop

Utility to monitor MySQL usage. Requires <span class="notranslate">`db_governor`</span> to be running. It shows usage for the current, mid and long intervals.

**Options:**

| | |
|-|-|
| <span class="notranslate"> -c </span> |show one time user list (no interactive mode) | 
| <span class="notranslate"> -r interval </span> |refresh interval for interactive mode (in seconds)|

**Control keys**

| | |
|-|-|
|<span class="notranslate"> z </span> |toggle color mode and two-color mode | 
|<span class="notranslate"> q </span> | <span class="notranslate"> F10, Ctrl-c </span> - quit program | 
|<span class="notranslate"> u </span> |sort table by username | 
|<span class="notranslate"> c </span> |sort table by cpu column | 
|<span class="notranslate"> r </span> |sort table by read column | 
|<span class="notranslate"> w </span> |sort table by write column | 
|<span class="notranslate"> l </span> |sort by restriction level | 
|<span class="notranslate"> t </span> |sort by time before restrictions will be lifted.|

Control keys, that sort table, displays into header of table bold and underlined symbol.
Sorted field will be highlighted by *.
<span class="notranslate"> CAUSE </span> field shows current stage, reason for restriction and number of seconds before restriction will be lifted:
Values of column ' <span class="notranslate"> CAUSE </span> ' - cause of restriction or freezing:
Possible stages:
* `-` <span class="notranslate"> OK </span>
* `1` - Restriction 1
* `2` - Restriction 2
* `3` - Restriction 3
* `4` - Restriction level 4

| | |
|-|-|
| <span class="notranslate"> c - current </span> |(current value of parameter)|
| <span class="notranslate"> s - short </span> |(average value of 5 last values of parameter)|
| <span class="notranslate"> m - middle </span> |(average value of 15 last values of parameter)|
| <span class="notranslate"> l - long </span> |(average value of 30 last values of parameter)|
| |and parameter which is cause of restriction|
| <span class="notranslate"> 1/s:busy_time/12 </span> | first level restricted account with short average restriction <span class="notranslate"> by busy_time </span> with 12 seconds left before re-enabled.|

**Display fields:**

* <span class="notranslate"> cpu </span> - number in %, shows <span class="notranslate"> cpu </span> usage by user
  * <span class="notranslate"> read </span> - number of bytes (kbytes, mbytes, gbytes) which user reads per second
  * <span class="notranslate"> write </span> - number of bytes (kbytes, mbytes, gbytes) write user reads per second


Accounts highlighted in _red_ color means that the account is restricted.  
Accounts highlighted in _blue_ color are in cool down period

Command line parameters of <span class="notranslate"> dbtop </span> utility:  
<span class="notranslate"> -r - dbtop </span> refresh period in seconds ( <span class="notranslate"> dbtop -r12 </span> )

#### dbctl


usage: <span class="notranslate"> dbctl command [parameter] [options] </span>

**Commands:**

| | |
|-|-|
| <span class="notranslate"> set </span> |set parameters for a <span class="notranslate"> db_governor </span> |
| <span class="notranslate"> list </span> |list users & their limits. It will list all users who had been active since <span class="notranslate"> Governor </span> restart,  as well as those for who explicit limits were set|
| <span class="notranslate"> list-restricted </span> |list restricted customers, with their limits, restriction reason, and time period they will still be restricted|
| <span class="notranslate"> ignore </span> |ignore particular user|
| <span class="notranslate"> watch </span> |start observing particular user again|
| <span class="notranslate"> delete </span> |remove limits for user/use defaults|
| <span class="notranslate"> restrict </span> |restrict user using lowest level (or if <span class="notranslate"> --level </span> specified, using the specified level)|
| <span class="notranslate"> unrestrict </span> |unrestrict username (configuration file remains unchanged)|
| <span class="notranslate"> unrestrict-all </span> |unrestrict all restricted users (configuration file remains unchanged)|
| <span class="notranslate"> --help </span> |show this message|
| <span class="notranslate"> --version </span> |version number|
| <span class="notranslate"> --lve-mode </span> |set <span class="notranslate"> DB Governor </span> mode of operation. Available values: <span class="notranslate"> off/abusers/all/single/on </span> |
| | <span class="notranslate"> off </span> - monitor only, don't throttle|
| | <span class="notranslate"> abusers </span> - when user reaches the limit, put user's queries into LVE for that user (experimental)|
| | <span class="notranslate"> all </span> - user's queries always run inside LVE for that user (experimental)|
| | <span class="notranslate"> single </span> - single LVE for all abusers.|
| | <span class="notranslate"> on </span> - same as <span class="notranslate"> single </span> (deprecated)|

**Parameters**

| | |
|-|-|
| <span class="notranslate"> default </span> |set default parameter|
| <span class="notranslate"> usrename </span> |set parameter for user|

**Options**

| | |
|-|-|
| <span class="notranslate"> --cpu=N </span> |limit <span class="notranslate"> CPU </span> (pct) usage|
| <span class="notranslate"> --read=N </span> |limit <span class="notranslate"> READ </span> (MB/s) usage|
| <span class="notranslate"> --write=N </span> |limit <span class="notranslate"> WRITE </span> (MB/s) usage|
| <span class="notranslate"> --level=N </span> |level (1,2,3 or 4) specified (deprecated) - this option is available only for period mode:|

<span class="notranslate"> <restrict_mode use="period"/> </span> (see [Configuration](/cloudlinux_os_components/#configuration-and-operation))

The default mode is " <span class="notranslate"> limit </span> " - when a user hits limits, the account will be marked as restricted and if the user does not hit the limit again during " <span class="notranslate"> unlimit=1m </span> " account will be unrestricted. This mode doesn't have any additional levels/penalties.  
<span class="notranslate"> <restrict_mode use="limit" unlimit="1m"/> </span>

Changing the <span class="notranslate"> "unlimit" </span> can be done only via the configuration file (see [Configuration](/cloudlinux_os_components/#configuration-and-operation)).

<span class="notranslate"> --slow=N: </span> limit time (in seconds) for long running <span class="notranslate"> SELECT </span> queries

Options for parameter <span class="notranslate">`list`</span>:

| | |
|-|-|
| `--kb` |show limits in Kbytes no pretty print|
| `--bb` |show limits in bytes no pretty print|
| `--mb` |show limits in Mbytes no pretty print|

Examples:
<div class="notranslate">

```
$ dbctl set test2 --cpu=150,100,70,50 --read=2048,1500,1000,800
```
</div>

sets individual limits for <span class="notranslate"> cpu (current, short, middle </span> period) and <span class="notranslate"> read (current, short, middle, long </span> periods) for user <span class="notranslate"> test2 </span>
<div class="notranslate">

```
$ dbctl set default --cpu=70,60,50,40
```
</div>

changes default <span class="notranslate"> cpu </span> limits.

All new limits will be applied immediately

To unrestrict user:
<div class="notranslate">

```
$ dbctl unrestrict username
```
</div>

To unrestrict all users:
<div class="notranslate">

```
$ dbctl unrestrict-all 
```
</div>

To restrict user:
<div class="notranslate">

```
$ dbctl restrict dbgov
```
</div>

To restrict user to level 2 restriction:
<div class="notranslate">

```
$ dbctl restrict dbgov --level=2
```
</div>

To make <span class="notranslate"> Governor </span> to ignore user:
<div class="notranslate">

```
$ dbctl ignore username
```
</div>

Delete user's limits, and use defaults instead:
<div class="notranslate">

```
$ dbctl delete username
```
</div>

Show limits as bytes:
<div class="notranslate">

```
$dbctl list --bb
```
</div>

#### lveinfo --dbgov


<span class="notranslate"> lveinfo </span> tool is a part of <span class="notranslate"> lve-stats </span> package. It was extended to collect historical information about MySQL usage.

<span class="notranslate"> $ lveinfo --dbgov --help </span>
<div class="notranslate">

```
Displays information about historical Db Governor usage
Usage: lveinfo [OPTIONS] 

-h --help              : this help run report from date and time in YYYY-MM-DD HH:MM format if not present last 10 mscreen
-v, --version          : version number
-f, --from=            : inutes are assumed
-t, --to=              : run report up to date and time in YYYY-MM-DD HH:MM format
      if not present, reports results up to now
	  --period=          : time period
      usage            : specify minutes with m,  h - hours, days with d, and values:
	  : today, yesterday; 5m - last 5 minutes, 4h -- last four hours,
	  : 2d - last 2 days, as well as today
-o, --order-by=        : orders results by one of the following:
      con              : average connections
      cpu              : average CPU usage
      read             : average READ usage
      write            : average WRITE usage
-u, --user=            : mysql username
-l, --limit=           : max number of results to display, 10 by default
-c, --csv              : display output in CSV format
-b, --format           : show only specific fields into output
      available values:
      ts               : timestamp records
      username         : user name
      con              : average connections
      cpu              : average CPU usage
      read             : average READ usage
      write            : average WRITE usage
      lcpu             : CPU limit
      lread            : READ limit
      lwrite           : WRITE limit
	  --show-all         : full output (show all limits); brief output is default 
	  
-o, --order-by=        : orders results by one of the following:
      ts               : timestamp records
      username         : user name
      max_sim_req      : max simultaneous requests
      sum_cpu          : average CPU usage
      sum_write        : average WRITE usage
      sum_read         : average READ usage
      num_of_rest      : number of restricts
      limit_cpu_end    : limit CPU on period end
      limit_read_end   : limit READ on period end
      limit_write_end  : limit WRITE on period end
	  --id=              : LVE id -- will display record only for that LVE id
	  -u, --user=            : Use username instead of LVE id, and show only record for that user
	  -l, --limit=           : max number of results to display, 10 by default
	  -c, --csv              : display output in CSV format
	  -b, --by-usage         : show LVEs with usage (averaged or max) within 90% percent of the limit
      available values:
      sum_cpu          : average CPU usage
      sum_write        : average WRITE usage
      sum_read         : average READ usage
      num_of_rest      : number of restricts
      limit_cpu_end    : limit CPU on period end
      limit_read_end   : limit READ on period end
      limit_write_end  : limit WRITE on period end
	  --show-all         : full output (show all limits); brief output is default 
	  
	  TS                     : timestamp records
	  USER                   : user name
	  CPU                    : average CPU usage
	  READ                   : average READ usage
	  WRITE                  : average WRITE usage
	  CON                    : average connections
	  lCPU                   : CPU limit
	  lREAD                  : READ limit
	  lWRITE                 : WRITE limit
	  RESTRICT               : C-cpu restrict, R- read restrict, W- write restrict
```
</div>

Example:
<div class="notranslate">

```
root@cpanel1 [~/ttttt]# lveinfo --dbgov --user=dbgov --period=1d --limit=10
TS                   USER   CPU     READ    WRITE   CON     lCPU    lREAD   lWRITE   RESTRICT  
2012-12-06 11:14:49  dbgov   9       0.0     0.0     1       90      1000    1000                
2012-12-06 11:13:49  dbgov   9       0.0     0.0     1       90      1000    1000                
2012-12-06 11:12:49  dbgov   9       0.0     0.0     1       90      1000    1000                
2012-12-06 11:11:49  dbgov   9       0.0     0.0     1       90      1000    1000                
2012-12-06 11:10:49  dbgov   9       0.0     0.0     1       90      1000    1000                
2012-12-06 11:09:49  dbgov   90      0.0     0.0     1       90      1000    1000     C          
2012-12-06 11:08:49  dbgov   0       0.0     0.0     0       400     1000    1000                
2012-12-06 11:07:49  dbgov   0       0.0     0.0     0       400     1000    1000                
2012-12-06 11:06:49  dbgov   0       0.0     0.0     0       400     1000    1000   
```
</div>

#### dbgovchart


<span class="notranslate"> dbgovchart </span> is analog of <span class="notranslate"> lvechart </span> tool to create charts representing customer's to MySQL usage

Usage: <span class="notranslate"> `/usr/sbin/dbgovchart [OPTIONS]` </span>

Acceptable options are:
<div class="notranslate">

```
--help      This help screen
--version   Version number
--from=     Run report from date and time in YYYY-MM-DD HH:MM format
            if not present last 10 minutes are assumed
--to=       Run report up to date and time in YYYY-MM-DD HH:MM format
            if not present, reports results up to now
--period=   Time period
            specify minutes with m,  h - hours, days with d, and values:
            today, yesterday
            5m - last 5 minutes, 4h - last four hours, 2d - last 2 days,
            as well as today
--user=     mysql username
--output=   Filename to save chart as, if not present, output will be sent to STDOUT
--show-all  Show all graphs (by default shows graphs for which limits are set)
```
</div>

Charts examples:

![](/images/1111_2.png)


## PHP Selector

| | |
|-|-|
|<span class="notranslate"> /usr/bin/alt-php-mysql-reconfigure.py </span> | Reconfigures <span class="notranslate"> alt-php </span> extensions to use correct MySQL library, based on the one installed in the system.|

#### selectorctl

<span class="notranslate">`selectorctl`</span> is a new tool that replaces <span class="notranslate">`cl-selector`</span> (which is deprecated and should not be used anymore) and <span class="notranslate">`piniset`</span>. It is available starting with **CageFS 5.1.3**.

All new features will be implemented as part of <span class="notranslate">`selectorctl`</span>.

**Common options**

| | |
|-|-|
|<span class="notranslate"> --interpreter (-i) </span> : | chooses the interpreter to work with. Currently only PHP is supported. If omitted, <span class="notranslate"> --interpreter=php </span> is implied.|
|<span class="notranslate"> --version (-v) </span> : | specifies alternatives version to work with|
|<span class="notranslate"> --user (-u) </span> : | specifies user to take action upon.|
|<span class="notranslate"> --show-native-version (-V) </span> : | prints the version of native interpreter|

**Global options**

The global options modify settings in <span class="notranslate"> /etc/cl.selector/defaults.cfg </span> file.

| | |
|-|-|
|<span class="notranslate"> --list (-l) </span> : | lists all available alternatives for an interpreter. For instance on server with Alt-PHP installed, it produces the following output. Columns are: short alternative version, full alternative version and path to php-cgi binary. |
| |<span class="notranslate"> $ selectorctl --list <br>5.2 5.2.17 /opt/alt/php52/usr/bin/php-cgi <br>5.3 5.3.28 /opt/alt/php53/usr/bin/php-cgi <br>5.4 5.4.23 /opt/alt/php54/usr/bin/php-cgi <br>5.5 5.5.7 /opt/alt/php55/usr/bin/php-cgi </span>|
|<span class="notranslate"> --summary (-S) </span> : | prints alternatives state summary. Output format: alternative version, state ('e' for 'enabled', '-' otherwise), chosen as default one or not ('d' for 'default', '-' otherwise). For example:| 
| |<span class="notranslate"> $ selectorctl --summary <br>5.2 e - <br>5.3 e - <br>5.4 e - <br>5.5 e - <br>native e d </span>|
| |if used with <span class="notranslate"> `--show-native-version` </span> displays version for native interpreter:|
| |<span class="notranslate"> $ selectorctl --summary --show-native-version <br>5.2 e - <br>5.3 e - <br>5.4 e - <br>5.5 e - <br>native(5.3) e d </span>|
|<span class="notranslate"> --current (-C) </span> : | prints currently globally selected default version (it is stored in <span class="notranslate"> _/etc/cl.selector/defaults.cfg_ </span> file):|
| |<span class="notranslate"> $ selectorctl --current <br>native native /usr/bin/php </span>|
| |If used with <span class="notranslate"> `--show-native-version` </span> , native interpreter version is displayed as well:|
| |<span class="notranslate"> --current --show-native-version <br>native(5.3) native(5.3.19) /usr/bin/php </span> |
|<span class="notranslate"> --set-current (-B): </span>  | sets specified version as globally default one (in <span class="notranslate"> _/etc/cl.selector/defaults.cfg_ </span> file). For example, to set current default version of PHP to 5.4, use:|
| |<span class="notranslate"> $ selectorctl --set-current=5.4 </span>|
|<span class="notranslate"> --disable-alternative (-N): </span> | adds <span class="notranslate"> state=disabled </span> option to alternative section. With it a corresponding alternative gets removed from user alternatives selection list. For instance to disable PHP 5.2, run:|
| |<span class="notranslate"> $ selectorctl --disable-alternative=5.2 </span>|
|<span class="notranslate"> --enable-alternative (-Y): </span> | Enables alternative version, removes <span class="notranslate"> state=disabled </span> option, if present, from alternative section. For example to enable PHP 5.2:|
| |<span class="notranslate"> $ selectorctl --enable-alternative=5.2 </span>|
|<span class="notranslate"> --enable-extensions (-E): </span> | enables extensions for particular PHP version by adding comma-separated list of extensions of modules for alternative in <span class="notranslate"> _/etc/cl.selector/defaults.cfg_ </span> . Requires <span class="notranslate"> --version </span> option. For example:|
| |<span class="notranslate"> $ selectorctl --enable-extensions=pdo,phar --version=5.2 </span>|
|<span class="notranslate"> --disable-extensions (-D): </span>  | removes extensions for a particular PHP version. Comma-separated list of extensions will be removed from <span class="notranslate"> /etc/cl.selector/defaults.cfg </span> . Requires <span class="notranslate"> --version </span> . Example:|
| |<span class="notranslate"> $ selectorctl --disable-extensions=pdo,phar --version=5.2 </span>|
|<span class="notranslate"> --replace-extensions (-R): </span> | replaces all extensions for particular PHP version to the list of comma separated extensions. Requires <span class="notranslate"> `--version`  option </span> . Example:|
| |<span class="notranslate"> $ selectorctl --replace-extensions=pdo,phar --version=5.2 </span>|
|<span class="notranslate"> --list-extensions (-G): </span> | lists extensions for an alternative for a particular version. Requires <span class="notranslate"> --version </span> . Example:|
| |<span class="notranslate"> $ selectorctl --list-extensions --version=5.3 <br>~ xml <br>- xmlreader <br>- xmlrpc <br>- xmlwriter <br>- xrange <br>+ xsl </span>|
| |Plus sign (+) stands for 'enabled', minus (–) for 'disabled', tilde (~) means compiled into interpreter. Enabled and disabled state relates to presence in <span class="notranslate"> _/etc/cl.selector/defaults.cfg_</span> file.|

**End user options**

All end user settings are contained in individual user's alt_php.ini files and controlled using selectorctl command.

| | |
|-|-|
|<span class="notranslate"> --user-summary (-s): </span>  | prints user alternatives state summary. Example:|
| |<span class="notranslate"> $ selectorctl --user-summary --user=user1 <br>5.2 e - - <br>5.3 e - - <br>5.4 e - - <br>5.5 e - - <br>native e d s </span>|
| |Columns are: alternative version, state ('e' for 'enabled', '-' otherwise), chosen as default one or not('d' for 'default', '-' otherwise), selected as user default one or not ('s' for 'selected', '-' otherwise). If used with <span class="notranslate"> `--show-native-version` </span> , version for native interpreter is shown in parenthesis:|
| |<span class="notranslate"> $ selectorctl --user-summary --user=user1 --show-native-version <br>5.2 e - - <br>5.3 e - - <br>5.4 e - - <br>5.5 e - - <br>native(5.3) e d s </span>|
| |<span class="notranslate"> `--user` </span> option is required. |
|<span class="notranslate"> --current (-c): </span> | prints currently globally selected default version (in <span class="notranslate"> _/etc/cl.selector/defaults.cfg_ </span> file):|
| |<span class="notranslate"> $ selectorctl --current <br>5.3 5.3.28 /opt/alt/php53/usr/bin/php-cgi </span>|  
| |If used with <span class="notranslate"> `--show-native-version` </span> to display native version:|
| |<span class="notranslate"> $ selectorctl --user-current --user=user1 <br>5.3 5.3.28 /opt/alt/php53/usr/bin/php-cgi </span>| 
| |<span class="notranslate"> `--user` </span> option is required.|
|<span class="notranslate"> --set-user-current (-b): </span> | sets specified version as the one to use for this end user:|
| |<span class="notranslate"> $ selectorctl --set-user-current=5.4 --user=user1 </span>|
| |changes user symlinks for the PHP interpreter to point to alternative 5.4.|
| |<span class="notranslate"> --user </span> option is required.|
|<span class="notranslate"> --enable-user-extensions (-e): </span> | Enables comma-separated list of extensions for the user user. Information is saved to <span class="notranslate"> _alt_php.ini_ </span> file. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --enable-user-extensions=pdo,phar --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --disable-user-extensions (-d): </span> | Disables extensions provided as comma-separated list. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --disable-user-extensions=pdo,phar --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --replace-user-extensions (-r): </span> | Replaces extensions with a provided comma-separated list of extensions Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options:|
| |<span class="notranslate"> $ selectorctl --replace-user-extensions=pdo,phar --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --reset-user-extensions (-t): </span> | Resets extensions for end user to default list of extensions as defined in <span class="notranslate"> default.cfg </span> . Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --reset-user-extensions --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --list-user-extensions (-g): </span> | lists enabled user extensions for an alternative. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --list-user-extensions --version=5.3 --user=user1 <br>xml <br>xmlreader <br>xmlrpc </span>|
| |if <span class="notranslate"> `--all` </span> option present, command will list all alternatives extensions marked enabled or disabled for given user. For example:|
| |<span class="notranslate"> $ selectorctl --list-user-extensions --version=5.3 --user=user1 --all <br>- xmlreader <br>- xmlrpc <br>- xmlwriter <br>- xrange <br>+ xsl </span>|
| |Plus sign (+) stands for 'enabled', minus (–) stands for 'disabled'. Enabled and disabled state relates to presence or absence of corresponding extensions in user <span class="notranslate"> _alt_php.ini_ </span> file.|
|<span class="notranslate"> --add-options (-k): </span> | adds options (as in <span class="notranslate"> _php.ini_ </span> ) to user <span class="notranslate"> _alt_php.ini_ </span> file. For example:|
| |<span class="notranslate"> $ selectorctl --add-options=log_errors:on,display_errors:on --version=5.2 --user=user1 </span>
| |adds <span class="notranslate"> `log_error` </span> and <span class="notranslate"> `display_errors` </span> options with values <span class="notranslate"> 'on' </span> to user <span class="notranslate"> _alt_php.ini_ </span> file overwriting default values for a user. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
|<span class="notranslate"> --replace-options (-m): </span> | replaces all options in user <span class="notranslate"> _alt_php.ini_ </span> file with specified ones. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --replace-options=log_errors:on,display_errors:on --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --delete-options (-x): </span> | removes custom options from user <span class="notranslate"> _alt_php.ini_ </span> file. Requires <span class="notranslate"> `--version` </span> and <span class="notranslate"> `--user` </span> options.|
| |<span class="notranslate"> $ selectorctl --delete-options=log_errors,display_errors --version=5.2 --user=user1 </span>|
|<span class="notranslate"> --print-options (-P): </span> | print options from <span class="notranslate"> _/etc/cl.selector/php.conf_ </span> file with default values or ones overwritten in user's <span class="notranslate"> _alt_php.ini_ </span> file.|
| |<span class="notranslate"> $ selectorctl --print-options --version=5.2 --user=user1 <br>TITLE:allow_url_fopen <br>DEFAULT:On <br>COMMENT:Allows PHP file functions to retrieve data from remote <br>locations over FTP or HTTP. This option is a great security risk, <br>thus do not turn it on without necessity. <br>TYPE:bool <br>... </span>|
| |Requires <span class="notranslate"> `--user`   </span> option. <span class="notranslate"> `--version` </span> option is optional. When <span class="notranslate"> `--version` </span> is omitted, options for current selected version will be printed. By default outputs as plain test. If <span class="notranslate"> `--json` ,  `--csv` ,  `--perl` </span> is specified, outputs data in corresponding format. For example, with <span class="notranslate"> `--perl` </span> option, the output is perl hash structure that can be evaluated. |
|<span class="notranslate"> --reset-options (-z): </span> | removes custom options from <span class="notranslate"> _alt_php.ini_ </span> files for ALL users and versions. Backup files in home folders are cleared.|
| |<span class="notranslate"> $ selectorctl --reset-options </span>|
| |The ranges of affected customers or versions can be narrowed with <span class="notranslate"> `--version` </span> or <span class="notranslate"> `--user`  options </span> :|
| |<span class="notranslate"> $ selectorctl --reset-options --user=user1,user2 --version=5.3,5.4 </span>|
|<span class="notranslate"> --list-users (-L): </span> | list users that use particular version of interpreter, specified with <span class="notranslate"> `--version` </span> option. For example, to see all users that use PHP version 5.3:|
| |<span class="notranslate"> $ selectorctl --list-users --version=5.3 </span>|
|<span class="notranslate"> --change-to-version (-T): </span> | changes all (or particular user) from one interpreter version to another.|
| |<span class="notranslate"> $ selectorctl --change-to-version=5.2 --version=5.3 </span>|

**Additional options**

| | |
|-|-|
|<span class="notranslate"> --base64 (-Q) </span> | Sometimes PHP options values can contain commas and other symbols that break command line formatting. In such a case convert a <span class="notranslate"> key:value </span> pair into <span class="notranslate"> base64 </span> and pass it as value for option-related arguments. For example, to add <span class="notranslate"> disable_functions=exec,popen,system </span> and <span class="notranslate"> display_errors=on </span> to user options, do the following:|
| |<span class="notranslate"> $ selectorctl --add-options=`echo disable_functions:exec,popen,system|base64 -w 0`,`echo display_errors:on|base64 -w 0` --version=5.2 --user=user1 --base64 </span>|
| |Option <span class="notranslate"> `-w 0`   </span> of <span class="notranslate"> base64 </span> executable stands for <span class="notranslate"> 'disable wrapping of lines' </span> . Without it <span class="notranslate"> base64 </span> output will break the command. |
|<span class="notranslate"> --quiet </span> | makes <span class="notranslate"> selectorctl </span> continue when it encounter option not found in <span class="notranslate"> _php.conf_ </span>. Without it <span class="notranslate"> selectorctl </span> exits with error.|


## Python Selector


### Old Python Selector


To create application run:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python --version=VERSION [--user=USER] [--print-summary] [--json] --create-webapp <FOLDER_NAME> <URI>
```
</div>

To delete application:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --destroy-webapp <FOLDER_NAME>
```
</div>

To change application folder name:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --relocate-webapp <FOLDER_NAME> <NEW_FOLDER_NAME>
```
</div>

To change application <span class="notranslate"> URI </span>:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=<python|ruby> [--user=USER] [--print-summary] [--json] --transit-webapp <FOLDER_NAME> <NEW_URI>
```
</div>

To change application interpreter version:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --set-user-current --version=<NEW VERSION> <FOLDER_NAME>
```
</div>

To set application <span class="notranslate"> WSGI </span> handler ( <span class="notranslate"> Python </span> only):

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --setup-wsgi=<file_path:callable> <FOLDER_NAME>
```
</div>

To install modules to application environment:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --enable-user-extensions=<module1[,module2...]> <FOLDER_NAME>
```
</div>

To remove modules from application environment:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --disable-user-extensions=<module1[,module2...]> <FOLDER_NAME>
```
</div>

To list modules installed in application environment:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--print-summary] [--json] --list-user-extensions <FOLDER_NAME>
```
</div>

To print applications summary for a user:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--json] --user-summary
```
</div>

To list available interpreters:

<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=python [--user=USER] [--json] --list
```
</div>

### New Python Selector

Below, there is a list of commands hoster and end user can run in a command line.

#### Hoster

:::tip Note
When running user command as root, please use <span class="notranslate">`--user`</span> option.
:::

* Get all Python-related information: default version, a list of supported versions, status of Python Selector, a list of users, their applications, etc:
  
    <div class="notranslate">

    ```
    cloudlinux-selector [get] [--json] --interpreter python
    ```
    </div>

    JSON output for <span class="notranslate">`get`</span> command:

<div class="notranslate">

```
{
  "selector_enabled": true | false, 
  "default_version": "2.7.15", 
  "result": "success", 
  "timestamp": 1508667174.220027,
  “cache_status”: “ready”,         //  or “updating” during automatic yum cache rebuild
  "available_versions": {   //  begin of  “versions”
      "2.7.15" : {   //   begin of version "2.7.15"
          "status": "enabled",  //  enabled, disabled, not_installed, installing, removing, locked
          “base_dir”: “/opt/alt/alt-python27”   //  empty when version is not installed
          “users”: {   //  begin of  “users”
              “user1”: {   //  begin of “user1”
	“homedir”: “/home/user1”,		
                 “applications”: {    //  begin of “applications”
                     “apps_dir/app1” : {   //   begin of application “apps_dir/app1”
                         “domain”: “cltest1.com”,
                         “app_uri”: “apps/my-app1”,
                         “startup_file” : “run.py”,
                         “entry_point” : “app”,
                         “app_status” : “started”,   // ‘started’ or ‘stopped’
                         “config_files” : [
                             “requirements.txt”,
                             “requirements-migration.txt”
                         ],
                         “env_vars” : {
                             “var1” : “value1”,
                             “var2” : “value2”
                         },
                     },   // end of application “apps_dir/app1”
                     “apps_dir/app2” : {    //   begin of application “apps_dir/app2”
                          << data for application “apps_dir/app2”  (same structure as for application “apps_dir/app1” above) >>
                     },   //  end of application “apps_dir/app2”
                 },   //  end of “applications”
              },   //  end of “user1”
              “user2”: {   //  begin of “user2”
                  << data for user “user2”  (same structure as for “user1” above) >>
              },   //  end of “user2”
          },   // end of “users”
        },    //  end of version “2.7.15”
      "8.21.5" : {   //   begin of version "3.3.7"
            << data for version "3.3.7"  (same structure as for version “2.7.15” above) >>
        },    //  end of version “3.3.7”
    },    //  end of “versions”
}   //   end of json
```
</div>

* Set default version, supported versions, and status of Python Selector:

    <div class="notranslate">

    ```
    cloudlinux-selector set [--json] --interpreter python (--selector-status <enabled,disabled> | --default-version <str> | --supported-versions <str>)
    ```
    </div>

#### *Examples*

1. Enable Python Selector:

    <div class="notranslate">

    ```
    cloudlinux-selector set --json --interpreter python --selector-status enabled
    ```
    </div>
2. Set default Python Selector version as 3.3:

    <div class="notranslate">
    
    ```
    cloudlinux-selector set --json --interpreter python --default-version 3.3
    ```
    </div>

3. Set supported Python Selector version as 3.3:

    <div class="notranslate">
    
    ```
    cloudlinux-selector set --json --interpreter python --supported-versions='{"2.7": false, "3.3": true}'
    ```
    </div>

4. Install a specific Python version:

    <div class="notranslate">
    
    ```
    cloudlinux-selector install-version --json --interpreter python --version 2.7
    ```
    </div>

5. Uninstall a specific Python version:

    <div class="notranslate">
    
    ```
    cloudlinux-selector uninstall-version --json --interpreter python --version 2.7
    ```
    </div>

6. Enable a specific Python version:

    <div class="notranslate">
    
    ```
    cloudlinux-selector enable-version --json --interpreter python --version 2.7
    ```
    </div>

7. Disable a specific Python version:

   <div class="notranslate">
   
    ```
    cloudlinux-selector disable-version --json --interpreter python --version 2.7
    ```
    </div>

* Change version for an application:
    * For a specific application:
        
        <div class="notranslate">
        
        ```
        cloudlinux-selector set [--json] --interpreter python --user <str> --app-root <str> --new-version <str>
        ```
        </div>

    * For all applications that use specific Python version:
        
        <div class="notranslate">
        
        ```
        cloudlinux-selector change-version-multiple --json --interpreter python --from-version <str> --new-version <str>
        ```
        </div>

    * For multiple applications:
        
        <div class="notranslate">
        
        ```
        cloudlinux-selector change-version-multiple --json --interpreter python --data  <pairs user:app-root as json> --new-version <str>
        ```
        </div>


#### *Examples*

1. Change version for a specific application:
    
    <div class="notranslate">

    ```
    cloudlinux-selector set --json --interpreter python --user user1 --app-root apps_dir/app1 --new-version 2.7
    ```
    </div>

2. Change version for all applications that use version 2.7.15 to version 3.3.5:
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector change-version-multiple --json --interpreter python --from-version 2.7 --new-version 3.3
    ```
    </div>

3. Change version of multiple application(s) and/or multiple users:
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector change-version-multiple --json --interpreter python --data <pairs user:app-root as json> --new-version <str>
    ```
    </div>

**Example**

<div class="notranslate">

```
cloudlinux-selector change-version-multiple --json --interpreter python --data [ {“user”: “user1”, “app_root”: “apps/app1”}, {“user”: “user2”, “app_root”: “apps/app1”} ]  --new-version 2.7
```
</div>

Common output for all <span class="notranslate">`set`</span> commands:

**in case of success:**

<div class="notranslate">

```
{
  "result": "success", 
  "timestamp": 1508666792.863358
}
```
</div>

**in case of error:**

<div class="notranslate">

```
{
  "result": "Some error message",
  "details" : "Traceback: ..." ,
  "context": {},
  "timestamp": 1508666792.863358
}
```
</div>

**in case of warning:**

<div class="notranslate">

```
{
  "result": "success",
  "warning" : "Some warning message" ,
  "context": {},
  "timestamp": 1508666792.863358
}
```
</div>

#### End user

:::tip Note
To start all users CLI commands use <span class="notranslate">`cagefs_enter`</span> command:

<div class="notranslate">

```
/bin/cagefs_enter.proxied /usr/sbin/cloudlinux-selector --json <other parameters>
```
</div>
:::

* Get config file for the user application:
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector read-config [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str> --config-file <name>
    ```
    </div>

    **JSON output:**

    <div class="notranslate">
    
    ```
    {
      	"result": "success", 
     "timestamp": 1508666792.863358
     	 “data”: “content of config file as Base64 encoded string”
    }
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector read-config --json --interpreter python  --user user1 --app-root app_dir/app1 --config-file requirements.txt
    ```
    </div>

* Save config file for user application:
  
    <div class="notranslate">
    
    ```
    cloudlinux-selector save-config [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str> --config-file <path> --content <content of config file as Base64 encoded string>
    ```
    </div>

    **JSON output** (the same as for all <span class="notranslate">`set`</span> commands):

    <div class="notranslate">
    
    ```
    {
      	"result": "success", 
    "timestamp": 1508666792.863358
    }
    ```
    </div>
    
    **Example:**
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector save-config --json --interpreter python  --user user1 --app-root app_dir/app1 --config-file requirements.txt  --content VGh1ICAyIE5vdiAxMDo0MzoxMiBFRFQgMjAxNwo=
    ```
    </div>

    :::tip Note
    An output for all commands below is like in Hoster’s CLI, but filtered out by username.
    :::

* Get a list of applications for a specific user:

    <div class="notranslate">
    
    ```
    cloudlinux-selector [get] [--json] --interpreter python  [--user <str> | --domain <str>]
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector get --json --interpreter python  --user user1
    ```
    </div>

* Create user application:

    <div class="notranslate">
    
    ```
    cloudlinux-selector create [--json] --interpreter python  [--user <str> | --domain <str>]  --app-root <str> --app-uri <str> [--version <str>]  [--startup-file <str>] [--entry-point <str>] [--env-vars <json string>]
    ```
    </div>

    **Example:**
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector create --json --interpreter python --app-root my_apps/app1 --domain xyz.com --app-uri apps/app1 --version 2.7 --startup-file run.py --entry-point app
    ```
    </div>

* Start, restart, stop, and destroy user application:
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector (start | restart | stop | destroy) [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str>
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector start --json --interpreter python --user user1 --app-root my_apps/app1
    ```
    </div>

* Change properties for an application:

    <div class="notranslate">
    
    ```
    cloudlinux-selector set [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str> [--app-mode <str>]  [--new-app-root <str>]  [--new-domain <str>]  [--new-app-uri <str>]  [--new-version <str>]  [--startup-file <str>] [--entry-point <str>] [--env-vars <json string>] [--config-files <str>]
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector set --json --interpreter python  --user user1 --app-root my_apps/app1 --app-mode production  --new-app-root new_apps/new_app1  --new-domain new.xyz.com --new-app-uri new_apps/app1  --new-version 8  --startup-file new_app.js --env-vars { “var1” : “value1”, “var2” : “value2” }  --config-files requirements.txt,reqs.txt
    ```
    </div>

* Run <span class="notranslate">`PIP install`</span> for user application:

    <div class="notranslate">
    
    ```
    cloudlinux-selector install-modules [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str> --requirements-file <path>
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector install-modules --json --interpreter python --user user1 --app-root my_apps/app --requirements-file requirements.txt
    ```
    </div>

* Optional: install or uninstall Python packages for user application:

    <div class="notranslate">
    
    ```
    cloudlinux-selector (install-modules|uninstall-modules) [--json] --interpreter python  [--user <str> | --domain <str>] --app-root <str> --modules <module1[,module2...]>
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector install-modules --json --interpreter python --user user1 --app-root my_apps/app --modules json-annotate,termcolor
    ```
    </div>

* Optional: run Python script in virtual environment of user application, arguments <span class="notranslate">`<args>`</span> are passed to the script:
    
    <div class="notranslate">
    
    ```
    cloudlinux-selector run-script [--json] --interpreter python  [--user <str | --domain <str>>] --app-root <str> --script-name <str> [-- <args>...]
    ```
    </div>

    **Example:**

    <div class="notranslate">
    
    ```
    cloudlinux-selector run-script --json --interpreter python --user user1 --app-root my_apps/app --script-name test_script -- --script_opt1 --script_opt2 script_arg1 script_arg2
    ```
    </div>

    **JSON output:**
    
    <div class="notranslate">

    ```
    {
      	"result": "success", 
     	"timestamp": 1508666792.863358
       	“data”: “script output as Base64 encoded string”
    }
    ```
    </div>


## Ruby Selector

To create application run:
<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=ruby --version=VERSION [--user=USER] [--print-summary] [--json] --create-webapp <FOLDER_NAME> <URI>
```
</div>
To delete application:
<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=ruby [--user=USER] [--print-summary] [--json] --destroy-webapp <FOLDER_NAME>
```
</div>
To change application folder name:
<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=ruby [--user=USER] [--print-summary] [--json] --relocate-webapp <FOLDER_NAME> <NEW_FOLDER_NAME>
```
</div>

To change application <span class="notranslate"> URI </span> :
<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=ruby [--user=USER] [--print-summary] [--json] --transit-webapp <FOLDER_NAME> <NEW_URI>
```
</div>

To change application interpreter version:
<div class="notranslate">

```
/usr/bin/selectorctl --interpreter=ruby [--user=USER] [--print-summary] [--json] --set-user-current --version=<NEW VERSION> <FOLDER_NAME>
```
</div>

To restart application:
<div class="notranslate">

```
selectorctl --interpreter ruby --user cltest1 --domain cltest1.com --restart-webapp testapp
```
</div>
To choose <span class="notranslate"> Ruby </span> version:
<div class="notranslate">

```
selectorctl --interpreter=ruby --user=$USER -v 2.0
```
</div>

## Node.js Selector

Below is a list of commands hoster and end user can run in a command line.

#### **Hoster**

Get information related to Node.js: default version, list of supported versions, status of <span class="notranslate"> Node.js Selector </span> , list of users, their applications, etc:
<div class="notranslate">

```
cloudlinux-selector [get] [--json] --interpreter nodejs
```
</div>

<span class="notranslate"> JSON </span> output for <span class="notranslate"> _get_ </span> command:
<div class="notranslate">

```
{  
"selector_enabled": true | false,   
"default_version": "6.11.3",   
"result": "success",   
"timestamp": 1508667174.220027  
"cache_status": "ready"         //  or “updating” during automatic yum cache rebuild  
"available_versions": {   //  begin of  “versions”
      "6.11.3" : {   //   begin of version "6.11.3"
		"name_modifier": "",
		"status": "enabled",  //  enabled, disabled, not_installed, installing, removing
		“base_dir”: “/opt/alt/alt-nodejs6”   //  empty when version is not installed
		“users”: {   //  begin of  “users”                      
			“user1”: {   //  begin of “user1”
				“homedir”: “/home/user1”,
				“applications”: {    //  begin of “applications”
					“apps_dir/app1” : {   //   begin of application “apps_dir/app1”
						“domain”: “cltest1.com”,
						“app_uri”: “apps/my-app1”,
						“app_mode” : “development”,
						“startup_file” : “app.js”,
						“app_status” : “started”,   // ‘started’ or ‘stopped’
						“config_files” : [
							“package.json”,
							“gruntfile.js”
						],
						“env_vars” : {
							“var1” : “value1”,
							“var2” : “value2”
						},
					},   // end of application “apps_dir/app1”
					“apps_dir/app2” : {    //   begin of application “apps_dir/app2”
						<< data for application “apps_dir/app2”  (same structure as for application “apps_dir/app1” above) >>
					},   //  end of application “apps_dir/app2”
				},   //  end of “applications”
			},   //  end of “user1”
			“user2”: {   //  begin of “user2”
				<< data for user “user2”  (same structure as for “user1” above) >>
			},   //  end of “user2”
		},   // end of “users”
	},    //  end of version “6.11.3”
	"8.21.5" : {   //   begin of version "8.21.5"
		<< data for version "8.21.5"  (same structure as for version “6.11.3” above) >>
	},    //  end of version “8.21.5”
},    //  end of “versions”}   //   end of json
```
</div>

Set default version, supported versions, and status of <span class="notranslate"> Node.js Selector </span> :
<div class="notranslate">

```
cloudlinux-selector set [--json] --interpreter nodejs (--selector-status <enabled,disabled> | --default-version <str> | --supported-versions <str>)
```
</div>

::: tip Note
<span class="notranslate"> Node.js Selector </span> is disabled by default. If an available Node.js version is not installed <span class="notranslate"> Node.js Selector </span> is always disabled and it is impossible to enable it.
:::

To set default Node.js version, please use the following command (note that required Node.js version should be enabled):
<div class="notranslate">

```
cloudlinux-selector set --json --interpreter=nodejs --default-version=<ver>
```
</div>

**Examples**:  
This command enables <span class="notranslate"> Node.js Selector </span> :

<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs --selector-status enabled
```
</div>

This command sets default Node.js version as 6:
<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs --default-version 6
```
</div>

This command sets supported Node.js version as 8:
<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs --supported-versions='{"6": false, "8": true}'
```
</div>

Install required Node.js version:
<div class="notranslate">

```
cloudlinux-selector install-version --json --interpreter nodejs --version 8
```
</div>

Uninstall required Node.js version:
<div class="notranslate">

```
cloudlinux-selector uninstall-version --json --interpreter nodejs --version 8
```
</div>

Enable required Node.js version:
<div class="notranslate">

```
cloudlinux-selector enable-version --json --interpreter nodejs --version 8
```
</div>

Disable required Node.js version (note that it is impossible to disable default Node.js version):
<div class="notranslate">

```
cloudlinux-selector disable-version --json --interpreter nodejs --version 8
```
</div>

Change version for application(s):
<div class="notranslate">

```
cloudlinux-selector set [--json] --interpreter nodejs ((--user <str> |  --domain <str>) --app-root <str> | --from-version <str>) --new-version <str>
```
</div>

**Examples** :  
This command changes version for the specific application:
<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs --user user1 --app-root apps_dir/app1 --new-version 8
```
</div>

Common output for all <span class="notranslate"> _set_ </span> commands:

**_in case of success_** :
<div class="notranslate">

```
{  "result": "success",   "timestamp": 1508666792.863358}
```
</div>

**_in case of error:_**
<div class="notranslate">

```
{  "result": "Some error message",  "details" : "Traceback: ..." ,  "context": {},  "timestamp": 1508666792.863358}
```
</div>

**_in case of warning:_**
<div class="notranslate">

```
{  "result": "success",  "warning" : "Some warning message" ,  "context": {},  "timestamp": 1508666792.863358}
```
</div>

To resolve issues related to <span class="notranslate"> _install-version/uninstall-version_ </span> commands (because they are running in the background) you may use this log file <span class="notranslate"> _/var/log/cl-nodejs-last-yum.log_ </span>
It contains full <span class="notranslate"> _yum_ </span> output from the <span class="notranslate"> **_latest_** </span> performed operation (install or uninstall) and it will be rewritten with each operation.

#### **End user**

::: danger
options --user and --domain are mutually exclusive now.
:::

Get config file for the user applications

<div class="notranslate">

```
cloudlinux-selector read-config [--json] --interpreter nodejs  [(--user <str> |  --domain <str>)] --app-root <str> --config-file <name>
```
</div>

JSON output:

<div class="notranslate">

```
{
    "result": "success",
	"timestamp": 1508666792.863358
	"data": "content of config file as Base64 encoded string"
}
```

</div>


**Example**:

This command gets config file for <span class="notranslate"> user1 </span> ’s application <span class="notranslate"> app1 </span> :

<div class="notranslate">

```
cloudlinux-selector read-config --json --interpreter nodejs  --user user1 --app-root app_dir/app1 --config-file package.json
```
</div>
Save config file for the user applications
<div class="notranslate">

```
cloudlinux-selector save-config [--json] --interpreter nodejs  [(--user <str> | --domain <str>)] --app-root <str> --config-file <path> --content <content of config file as Base64 encoded string>
```
</div>

<span class="notranslate"> JSON </span> output (the same as for all <span class="notranslate"> _set_ </span> commands):

<div class="notranslate">

```
{
          "result": "success",
		  "timestamp": 1508666792.863358
}
```
</div>

**Example**:  
This command saves config file for <span class="notranslate"> user1 </span> ’s application <span class="notranslate"> app1 </span> :

<div class="notranslate">

```
cloudlinux-selector save-config --json --interpreter nodejs  --user user1 --app-root app_dir/app1 --config-file package.json  --content                                         VGh1ICAyIE5vdiAxMDo0MzoxMiBFRFQgMjAxNwo=
```
</div>
Get a list of applications for the specific user
<div class="notranslate">

```
cloudlinux-selector [get] [--json] --interpreter nodejs  [(--user <str> |  --domain <str>)]
```
</div>

**Example**:  
This command gets a list of applications for the <span class="notranslate"> user1 </span> :

<div class="notranslate">

```
cloudlinux-selector get --json --interpreter nodejs  --user user1
```
</div>
Create user application

<div class="notranslate">

```
cloudlinux-selector create [--json] --interpreter nodejs [(--user <str> | --domain <str>)] --app-root <str> --app-uri <str> [--version <str>] [--app-mode <str>] [--startup-file <str>] [--env-vars <json string>]
```
</div>

**Example**:  
This command creates <span class="notranslate"> user1 </span> 's application for the domain <span class="notranslate"> xyz.com </span> :
<div class="notranslate">

```
cloudlinux-selector create --json --interpreter nodejs --user user1 --app-root my_apps/app1 --app-uri apps/app1
```
</div>
or
<div class="notranslate">

```
cloudlinux-selector create --json --interpreter nodejs --app-root my_apps/app1 --domain xyz.com --app-uri apps/app1
```
</div>
Start, restart, stop, and destroy user application
<div class="notranslate">

```
cloudlinux-selector (start | restart | stop | destroy) [--json] --interpreter nodejs  [(--user <str> | --domain <str>)] --app-root <str>
```
</div>

**Example**:
This command starts <span class="notranslate"> user1 </span> 's application:
<div class="notranslate">

```
cloudlinux-selector start --json --interpreter nodejs --user user1 --app-root my_apps/app1
```
</div>
Change properties for an application
<div class="notranslate">

```
cloudlinux-selector set [--json] --interpreter nodejs  [(--user <str> | --domain <str>)] --app-root <str> [--app-mode <str>] [--new-app-root <str>] [--new-domain <str>] [--new-app-uri <str>] [--new-version <str>] [--startup-file <str>] [--env-vars <json string>]
```
</div>

**Example 1**:
This command sets a production mode, new domain <span class="notranslate"> new.xyz.com </span> , new Node.js version 8, new <span class="notranslate"> URI </span> , new application <span class="notranslate"> root </span> directory and new startup file for <span class="notranslate"> user1 </span> application located on the domain <span class="notranslate"> xyz.com </span> :
<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs  --user user1 --app-root my_apps/app1 --mode production  --new-app-root new_apps/new_app1  --new-domain new.xyz.com --new-app-uri new_apps/app1  --new-version 8  --startup-file new_app.js --env-vars '{ "var1" : "value1", "var2" : "value2" }'
```
</div>

**Example 2**:

<div class="notranslate">

```
cloudlinux-selector set --json --interpreter nodejs  --domain xyz.com --app-root my_apps/app1 --mode production  --new-app-root new_apps/new_app1  --new-domain new.xyz.com --new-app-uri new_apps/app1  --new-version 8  --startup-file new_app.js --env-vars '{ "var1" : "value1", "var2" : "value2" }'
```
</div>

::: tip Note
When changing Node.js version all replies from web application to get request will be checked in Node.js Selector (before and after version changing). HTTP response codes and MIME type are comparing. So, make sure application is available via http(s) at least locally.
:::

Run <span class="notranslate"> _npm install_ </span> command for the user application
<div class="notranslate">

```
cloudlinux-selector install-modules [--json] --interpreter nodejs  [(--user <str> |  --domain <str>)] --app-root <str>
```
</div>

**Example**:
This command runs <span class="notranslate">`npm install`</span> for <span class="notranslate"> user1 </span> application:

<div class="notranslate">

```
cloudlinux-selector install-modules --json --interpreter nodejs --user user1 --app-root my_apps/app
```
</div>

::: tip Note
All replies from web application to get request will be checked in Node.js Selector (before and after modules installation). HTTP response codes and MIME type are comparing. So, make sure application is available via http(s) at least locally.
:::

Run a script from <span class="notranslate"> package.json </span> file of a user application, arguments <span class="notranslate"> _args_ </span> are passed to the script
<div class="notranslate">

```
cloudlinux-selector run-script [--json] --interpreter nodejs  [(--user <str> | --domain <str>)] --app-root <str> --script-name <str> [-- <args>...]
```
</div>

**Example**:
<div class="notranslate">

```
cloudlinux-selector run-script --json --interpreter nodejs --user user1 --app-root my_apps/app --script-name test_script -- --script_opt1 --script_opt2 script_arg1 script_arg2
```
</div>

<span class="notranslate"> JSON </span> output:

<div class="notranslate">

```
{
          "result": "success",
		  "timestamp": 1508666792.863358
		  "data": "script output as Base64 encoded string"
}
```
</div>

Activate virtual environment of NodeJS:
<div class="notranslate">

```
source <home_of_user>/nodevenv/<app_root>/<nodejs_version>/bin/activate
```
</div>

This command changes prompt to
**Example**:  
<div class="notranslate">

```
[newusr@192-168-245-108 ~]$ source /home/newusr/nodevenv/newapp4/newapp3/8/bin/activate
[newapp4/newapp3 (8)] [newusr@192-168-245-108 ~]$
```
</div>

After activation user can use <span class="notranslate">`npm`</span> and node from a virtual environment without full paths.

## Apache mod_lsapi PRO

switch_mod_lsapi is the command line tool used to manage mod_lsapi PRO.

It has the following syntax:

`/usr/bin/switch_mod_lsapi [OPTIONS]`

`[OPTIONS]`  can be the main and an additional (for usage together with any other main option).

**Main options**

| | |
|-|-|
|**Option** | **Description**|
|`--setup` | setup _mod_lsapi_ configurations for Apache, including PHP handlers setup; create native lsphp (if it doesn't exist) by doing: `cp /opt/alt/php56/usr/bin/lsphp /usr/local/bin/` <br> _* NOT supported for DirectAdmin_ |
|`--setup-light` | setup PHP handlers only<br> _* supported for cPanel EasyApache 4 only_|
|`--uninstall` | uninstall _mod_lsapi_ from Apache<br> _* supported for cPanel (EasyApache 3 and EasyApache 4), Plesk, and servers without control panel_|
|`--enable-domain` | enable _mod_lsapi_ for individual domain<br> _* supported for cPanel EasyApache 3 only_|
|`--disable-domain` | disable _mod_lsapi_ for individual domain<br> _* supported for cPanel EasyApache 3 only_|
|`--enable-global` | sets up _mod_lsapi_ as a default way to serve PHP, making it enabled for all domains. Once that mode is enabled, you cannot disable _mod_lsapi_ for an individual domain.<br> _* supported for cPanel only (EasyApache 3 and EasyApache 4)_|
|`--disable-global` | disable _mod_lsapi_ as a default way to serve PHP, disabling _mod_lsapi_ for all domains, including those selected earlier using<br> _--enable-domain_ _* supported for cPanel EasyApache 3 only_|
|`--build-native-lsphp` | build native _lsphp_ for cPanel EasyApache 3<br> _* supported for cPanel EasyApache 3 only_|
|`--build-native-lsphp-cust` | build native _lsphp_ for cPanel EasyApache 3 (with custom PHP source path)<br> _* supported for cPanel EasyApache 3 only_|
|`--check-php` | check PHP configuration<br> _* NOT supported for DirectAdmin_|
|`--stat` | return usage statistics in JSON format; the following statistics metrics are collected:<br> • control panel name;<br> • mod_lsapi version;<br> • liblsapi version;<br> • criu version and status;<br> • whether mod_lsapi is enabled;<br> • lsapi configuration options;<br> • number of domains, that use _mod_lsapi_, per each installed PHP version including those set in PHP Selector _(this metric is supported for cPanel EasyApache 4, Plesk and DirectAdmin)_ .|

**Additional options**

| | |
|-|-|
|**Option** | **Description**|
|`--verbose` | switch verbose level on|
|`--force` | switch force mode on|


The following table presents which `[OPTIONS]` are supported for various panels:

| |  |  |  |  |  |  | |
|-|--|--|--|--|--|--|-|
| | No Control Panel | cPanel EA3 | cPanel EA4 | DirectAdmin | Plesk | InterWorx | ISPManager|
|`setup` | + | + | + | custombuild | + | + | +|
|`setup-light` | - | - | + | - | - | - | -|
|`uninstall` | + | + | + | custombuild | + | + | +|
|`enable-domain` | - | + | - | - | - | - | -|
|`disable-domain` | - | + | - | - | - | - | -|
|`enable-global` | - | + | + | custombuild | - | - | -|
|`disable-global` | - | + | - | custombuild | - | - | -|
|`build-native-lsphp` | - | + | - | - | - | - | -|
|`build-native-lsphp-cust` | - | + | - | - | - | - | -|
|`check-php` | + | + | + | - | + | + | +|
|`verbose` | + | + | + | - | + | + | +|
|`force` | + | + | + | - | + | + | +|
|`stat` | + <br> _*without domain info_ | + <br> _*without domain info_ | + | + | + | + <br> _*without domain info_ | + <br> _*without domain info_|

## Other CLI tools


* [cldeploy](/command-line_tools/#cldeploy)
* [lvectl](/command-line_tools/#lvectl)
* [lveps](/command-line_tools/#lveps)
* [lvetop](/command-line_tools/#lvetop)
* [cldetect](/command-line_tools/#cldetect)
* [cldiag](/command-line_tools/#cldiag)
* [cloudlinux-config](/command-line_tools/#cloudlinux-config)


### cldeploy

<span class="notranslate">`sh cldeploy --help`</span>

Usage:

| | |
|--|--|
|<span class="notranslate">`-h, --help`</span>|Print this message|
|<span class="notranslate">`-k, --key &lt;key&gt;`</span>|Update your system to CloudLinux with activation key|
|<span class="notranslate">`-i, --byip`</span>|Update your system to CloudLinux and register by IP|
|<span class="notranslate">`-c, --uninstall`</span>|Convert CloudLinux back to CentOS|
|<span class="notranslate">`--serverurl`</span>|Use non-default registration server (default is `https://xmlrpc.cln.cloudlinux.com/XMLRPC`)|
|<span class="notranslate">`--components-only`</span>|Install control panel components only|
|<span class="notranslate">`--conversion-only`</span>|Do not install control panel components after converting|
|<span class="notranslate">`--hostinglimits`</span>|Install mod_hostinglimits rpm|
|<span class="notranslate">`--skip-kmod-check`</span>|Skip check for unsupported kmods|
|<span class="notranslate">`--skip-version-check`</span>|Do not check for script updates|
|<span class="notranslate">`--skip-registration`</span>|Don't register on CLN if already have access to CL repository|

The script will install the following to the server:

1. Register server with CLN.
2. Install CloudLinux kernel, lve libraries, lve-utils, lve-stats and pam_lve packages.
3. It will attempt to detect control panel and do the following actions:
*  _For cPanel & DirectAdmin_:
   * recompile Apache to install mod_hostinglimits;
   * install LVE Manager.

* _For Plesk, ISPManager & InterWorx_:
  * update httpd and install mod_hostinglimits;
  * install LVE Manager.

* To disable installation of LVE Manager and mod_hostinglimits, please use <span class="notranslate">`--conversion-only`</span> option.

* To disable installation of kernel & CLN registration, please use <span class="notranslate">`--components-only`</span> option.

* To install **mod_hostinglimits** only, use <span class="notranslate">`--hostinglimits`</span> option.

Examples:

<div class="notranslate">

```
$ cldeploy --key xx-xxxxxx           # convert RHEL/CentOS to CL by using activation key, install control panel components
$ cldeploy --byip --conversion-only  # convert RHEL/CentOS to CL by ip, don't install control panel components
$ cldeploy --components-only         # install control panel components on already converted system
$ cldeploy --hostinglimits           # update httpd and install mod_hostinglimits 
```
</div>


### lvectl

`lvectl` is the primary tool for LVE management. To use it, you have to have administrator access. lvectl is a part of lve-utils package.

**lvectl syntax**

**Usage**: <span class="notranslate">`lvectl command [veid] [options]`</span>

**Commands**

|  |  |
|--|--|
| <span class="notranslate"> `apply`   </span> |apply config settings to specified LVE|
| <span class="notranslate"> `apply all`   </span> |apply config settings to all the LVEs|
| <span class="notranslate"> `apply-many` </span> |to apply LVE limits to multiple distinct LVEs (uids of users are read from stdin)|
| <span class="notranslate"> `set`   </span> |set parameters for a LVE and/or create a LVE|
| <span class="notranslate"> `set-user`   </span> |set parameters for a LVE and/or create a LVE using username instead of ID|
| <span class="notranslate"> `list` </span> |list loaded LVEs|
| <span class="notranslate"> `list-user`   </span> |list loaded LVEs, display username instead of user id|
| <span class="notranslate"> `limits` </span> |show limits for loaded LVEs|
| <span class="notranslate"> `delete` </span> |delete LVE and set configuration for that LVE to defaults|
| <span class="notranslate"> `delete-user` </span> |delete LVE and set configuration for that user to defaults|
| <span class="notranslate"> `destroy` </span> |destroy LVE (configuration file remains unchanged)|
| <span class="notranslate"> `destroy all` </span> |destroy all LVE (configuration file remains unchanged)|
| <span class="notranslate"> `destroy-many` </span> |to destroy LVE limits to multiple distinct LVEs (uids of users are read from stdin)|
| <span class="notranslate"> `package-set` </span> | set LVE parameters for a package|
| <span class="notranslate"> `package-list` </span> |list LVE parameters for packages|
| <span class="notranslate"> `package-delete` </span> |delete LVE parameters for a package|
| <span class="notranslate"> `paneluserslimits` </span> |show current user's limits for control panel|
| <span class="notranslate"> `limit` </span> |limit PID into specified LVE. Parameters PID LVE_ID|
| <span class="notranslate"> `release` </span> |release PID from LVE. Parameters PID|
| <span class="notranslate"> `set-binary` </span> |add binary to be run inside LVE on execution|
| <span class="notranslate"> `del-binary` </span> |remove binary from being run inside LVE on execution|
| <span class="notranslate"> `list-binaries` </span> |list all binaries to be run inside LVE on execution|
| <span class="notranslate"> `load-binaries` </span> |load binaries (used on startup) from config file|
| <span class="notranslate"> `reload-binaries` </span> |re-load list of binaries from config file|
| <span class="notranslate"> `help (-h)` </span> |show this message|
| <span class="notranslate"> `version (-v)` </span> |version number|
| <span class="notranslate"> `lve-version` </span> |LVE version number|
| <span class="notranslate"> `set-reseller` </span> |create LVE container and set LVE parameters for a reseller|
| <span class="notranslate"> `set-reseller-default` </span> |set default limits for resellers users|
| <span class="notranslate"> `remove-reseller`</span> |delete LVE container and the record in the config, move LVE containers to the host container|

**Options**

|  |  |
|--|--|
|<span class="notranslate"> `--cpu=N`   </span> |limit <span class="notranslate">`CPU`</span> usage; (deprecated. Use <span class="notranslate">`--speed`</span>)|
| <span class="notranslate"> `--speed=N%` </span> |limit <span class="notranslate">`CPU`</span> usage in percentage; 100% is one core|
| <span class="notranslate"> `--speed=Nmhz\ghz` </span> |limit <span class="notranslate">`CPU`</span> usage in mhz\ghz|
| <span class="notranslate"> `--ncpu=N` </span> |limit VCPU usage (deprecated)|
| <span class="notranslate"> `--io=N` </span> |define io limits (KB/s)|
| <span class="notranslate"> `--nproc=N` </span> |limit number of processes|
| <span class="notranslate"> `--pmem=N`   </span> |limit physical memory usage for applications inside LVE|
| <span class="notranslate"> `--iops=N` </span> |limit io per second|
| <span class="notranslate"> `--mem=N` </span> | mem alias for vmem (deprecated)|
| <span class="notranslate"> `--vmem=N` </span> |limit virtual memory for applications inside LVE|
| <span class="notranslate"> `--maxEntryProcs=N` </span> |limit number of entry processes|
| <span class="notranslate"> `--save` </span> |save configuration settings (use with set) (deprecated)|
| <span class="notranslate"> `--save-all-parameters` </span> |save all parameters even if they match with defaults settings|
| <span class="notranslate"> `--json` </span> |returns result of command json formatted|
| <span class="notranslate"> `--unlimited` </span> |set all limits to unlimited|
| <span class="notranslate"> `--save-username` </span> |save username in the config file. This parameter is used in conjunction with <span class="notranslate">`set-user`</span>|

**Examples**

* Reset all LVEs settings based on configuration in <span class="notranslate">`/etc/container/ve.cfg`</span>:
  
    <div class="notranslate">

    ```
    $ lvectl apply all
    ```
    </div>

* Set new default <span class="notranslate">CPU & Physical memory</span> limit:
  
    <div class="notranslate">

    ```
    $ lvectl set default --speed=100% --pmem=256m
    ```
    </div>

* Reset all LVE's killing processes inside them:
  
    <div class="notranslate">

    ```
    $ lvectl destroy all
    ```
    </div>

* Show list of LVEs and their limits:
  
    <div class="notranslate">

    ```
    $ lvectl list
    ```
    </div>

### lveps

**lveps** tool shows information about running LVEs, processes and threads belonging to them, <span class="notranslate"> CPU/memory/IO </span> usage consumed by LVEs and their individual processes/threads. LVE is only reported if it is considered active (at least one thread belongs to that LVE or was running during measurement in dynamic mode).

**Usage**:

<div class="notranslate"> 

```
lveps [-p] [-n] [-o <fmt1:width1,...>] [-d] [-c <time>] [-s <style>] [-t] [-h]
```
</div>

**Options**:

| | |
|-|-|
|`-p`| to print per-process/per-thread statistics|
|`-n`| to print LVE ID instead of username|
|`-o`| to use formatted output (fmt=id,ep,pid,tid,cpu,mem,io)|
|`-d`| to show dynamic cpu usage instead of total cpu usage|
|`-c`| to calculate average cpu usage for &lt;time&gt; seconds (used with `-d`)|
|`-r`| to run under realtime priority for more accuracy (needs privileges)|
|`-s`| to sort LVEs in output (cpu, process, thread, mem, io)|
|`-t`| to run in the top-mode|
|`-h`| to print this brief help message|


Command like <span class="notranslate">`lveps -p`</span> will display processes running inside 'active' LVEs.

| | |
|-|-|
|<span class="notranslate"> CPU </span> | The number of seconds LVE/process/thread has been running (each <span class="notranslate"> CPU </span> /core is counted separately), or the average CPU load (100% is all <span class="notranslate"> CPU </span> resources) if used with <span class="notranslate">`-d`</span>.|
|<span class="notranslate">MEM</span>| The number of megabytes of resident memory in use by LVE/process/thread (shared memory is not included).|
|<span class="notranslate">IO</span> | The number of kilobytes read and written in sum by LVE, or kb/sec if used with `-d`.|
|<span class="notranslate">ID</span> | LVE ID or username.|
|<span class="notranslate">EP</span> | The number of entry processes inside  LVE.|
|<span class="notranslate">COM</span> | Command name for this process.|
|<span class="notranslate">PID</span> | <span class="notranslate">PID</span> of the process.|
|<span class="notranslate">PNO</span> | The number of processes belonging to the LVE.|
|<span class="notranslate">TID</span> | <span class="notranslate">TID</span> of the thread.|
|<span class="notranslate">TNO</span> | The number of threads belonging to the LVE.|
|<span class="notranslate">DO</span> | The number of disk operations belonging to the LVE from the time it was created.|
|<span class="notranslate">DT</span> | Total amount of disk transfer in megabytes from LVE creation time.|
|<span class="notranslate">IOPS</span> | The number of I/O operations per second|

### lvetop

**lvetop** utility allows to monitor LVE usage:

<div class="notranslate">

```
ID        EP PNO TNO SPEED MEM  IO   IPOS
testuser1 0  1   1   0%    7    0    0
testuser2 0  0   0   5%    0    3    0
testuser3 1  2   2   0%    102  2727 0
testuser4 0  1   1   0%    12   84   1
testuser5 0  2   2   1%    52   0    0
```
</div>

**lvetop fields**:

| | |
|--|--|
|<span class="notranslate"> `ID`</span>|user name if LVE id matches user id in <span class="notranslate">`/etc/passwd`</span>, or LVE id|
|<span class="notranslate"> `EP`</span>|number of entry processes (concurrent scripts executed)|
|<span class="notranslate"> `PNO`</span>|number of processes within LVE|
|<span class="notranslate"> `TNO`</span>|number of threads within LVE|
|<span class="notranslate"> `CPU`</span>|<span class="notranslate"> CPU</span> usage by LVE, relative to total <span class="notranslate"> CPU </span>  resources of the server|
|<span class="notranslate"> `MEM`</span>|Memory usage by LVE, in KB|
|<span class="notranslate"> `I/O`</span>|<span class="notranslate"> I/O </span> usage|
|<span class="notranslate"> `IOPS`</span>|number of read/write operations per second|


### cldetect

:::tip Note
<span class="notranslate">lve-utils 1.2-10+</span>
:::

**cldetect** is used to detect installed software, and adjust CloudLinux options accordingly.

**Usage**:
<div class="notranslate">

```
/usr/bin/cldetect [--options]
```
</div>


|||
|----|--|
|<span class="notranslate">`cldetect -h`/`-h`/`--help`</span>|show this message|
|<span class="notranslate">`--detect-cp`</span>|prints control panel and its version (<span class="notranslate">CP_NAME,CP_VERSION</span>)|
|<span class="notranslate">`--detect-cp-full`</span>|prints control panel, version and panel specific data (<span class="notranslate">CP_NAME,CP_VERSION</span>,...). Specific data: for <span class="notranslate">ISP Manager5 - Master/Node</span>|
|<span class="notranslate">`--detect-cp-nameonly`</span>|prints control panel name (<span class="notranslate">CP_NAME</span>)|
|<span class="notranslate">`--get-admin-email`</span>|prints control panel admin email (<span class="notranslate">CP_ADMIN_EMAIL</span>)|
|<span class="notranslate">`--cxs-installed`</span>|check if CXS is installed. Returns 0 if installed, 1 otherwise|
|<span class="notranslate">`--cpanel-suphp-enabled`</span>|check if suPHP is enabled in cPanel.Returns 0 if enabled, 1 otherwise|
|<span class="notranslate">`--detect-litespeed`</span>|check if LiteSpeed is installed. Returns 0 if installed, 1 otherwise|
|<span class="notranslate">`--detect-postgresql`</span>|check if PostGreSQL is installed. Returns 0 if installed, 1 otherwise|
|<span class="notranslate">`--print-apache-gid`</span>|prints current apache gid|
|<span class="notranslate">`--print-da-admin`</span>|prints DirectAdmin admin user|
|<span class="notranslate">`--set-securelinks-gid`</span>|changes `/etc/sysctl.conf` if apache gid != 48 (default)|
|<span class="notranslate">`--set-nagios`</span>|do some adjustments to make nagios work correctly if it's installed. Called as a part of `--setup-supergids`|
|<span class="notranslate">`--setup-supergids`</span>|do some adjustments to make special users/software (nagios, cPanel’s mailman) work correctly if it is installed to the system|
|<span class="notranslate">`--cl-setup`</span>|check if CloudLinux is installing. Returns 0 if installing, 1 otherwise|
|<span class="notranslate">`--update-license`</span>|updates license|
|<span class="notranslate">`--update-new-key`</span>|updates license with new key|
|<span class="notranslate">`--check-license`</span>|check license. Returns OK if license is not older than 3 days, error message otherwise|
|<span class="notranslate">`-q`</span>|check license. Returns 0 if license is not older than 3 days, 1 otherwise|
|<span class="notranslate">`--no-valid-license-screen`</span>|returns no valid license found screen|
|<span class="notranslate">`--license-out-of-date-email`</span>|returns License out of Date Email.|
|<span class="notranslate">`--check-openvz`</span>|returns enviroment id|


#### **clsupergid auto-configuration**

Each time <span class="notranslate">`lve-utils`</span> package is installed or upgraded it does some automatic system re-configuration to make some software (like nagios) work correctly, if it’s installed, by calling <span class="notranslate">`cldetect --setup-supergids`</span> command.

Starting from <span class="notranslate">**_lve-utils 3.0-21_**</span> a behaviour of <span class="notranslate">`cldetect --set-nagios`</span> (now, it’s a part of <span class="notranslate">`cldetect --setup-supergids`</span>) command slightly changed.

| |  | |
|-|--|--|
| | **Old behavior** | **New behavior**|
|If <span class="notranslate">**fs.proc_super_gid**</span> is 0 (which means it’s not configured) or it’s set to some GID that doesn’t exist in the system.| Command will set <span class="notranslate">`sysctl fs.proc_super_gid`</span> to point to Nagios GID. | Command will create special <span class="notranslate">`clsupergid`</span> group, setup <span class="notranslate">`sysctl fs.proc_super_gid`</span> to point to it’s GID and add Nagios user to this group.|

If **fs.proc_super_gid** was configured by an admin to some existing group, the command will just add Nagios user to this group.

### cldiag
 
`cldiag` utility is included in <span class="notranslate">`lve-utils`</span> package and is intended for:

* server diagnostics performed by a server administrator for detecting the most common errors in the configuration or software operation;
* the focused check of the servers for typical errors performed by the support engineers before proceeding to the detailed analysis of the customer tickets;
* servers automatic check by cron with the following generation of the reports and email them to the server administrator.

In all cases, for the negative checker result, the exit code will be > 0 (at the moment it will be equal to the number of failed checkers).

All the checkers support additional <span class="notranslate">`--json`</span> option with the unified output in an appropriate format.

For example:
 
<div class="notranslate"> 

```
# cldiag --symlinksifowner --json

{"total_errors": 0, "Check fs.enforce_symlinksifowner is correctly enabled in /etc/sysctl.conf": {"res": "OK", "msg": "fs.enforce_symlinksifowner = 1"}}
```
</div>

Each checker returns a typical result with the name of the check performed (brief description), one of the possible statuses of its execution, and detailed information on its fail or success.

For example:

<div class="notranslate">

```
Check fs.enforce_symlinksifowner is correctly enabled in /etc/sysctl.conf:

OK: fs.enforce_symlinksifowner = 1

Check suexec has cagefs jail:

SKIPPED: SuEXEC is not enabled
```
</div>

Possible checkers results:

1. <span class="notranslate">`OK`</span> - the check succeeded.
2. <span class="notranslate">`FAILED`</span> - the check revealed a problem.
3. <span class="notranslate">`SKIPPED`</span> - the check was skipped as it made no sense in the actual environment (e.g. wrong control panel) or it could not be executed for some reason (e.g. no users with enabled CageFS found). Such result doesn’t mean there is a problem and can be considered as a positive.
4. <span class="notranslate">`INTERNAL_TEST_ERROR`</span> - the check has failed because of a problem in the checker itself. Please report such problems using [https://cloudlinux.zendesk.com/agent/](https://cloudlinux.zendesk.com/agent/).

The utility includes several built-in checkers, and can also import and run checkers from other utilities.

Currently implemented checkers:

1. <span class="notranslate">`--diag-cp`</span>

Checks control panel and its configuration (for DirectAdmin only).

Checking control panel availability, thereby detecting it with our code. Displaying control panel name and version. Also, for DirectAdmin, checking if CloudLinux support is enabled in its config.

Fails if <span class="notranslate">`/usr/local/directadmin/custombuild/options.conf`</span> does not contain <span class="notranslate">`cloudlinux=yes`</span> line (for DirectAdmin control panel).

2. <span class="notranslate">`--symlinksifowner`</span>

Checks fs.enforce_symlinksifowner is correctly enabled in <span class="notranslate">`/etc/sysctl.conf`</span>.

Checking specified kernel setup described in [this docs section](/cloudlinux_os_kernel/#symlink-owner-match-protection) for deprecated value and displaying its current value.

Fails if <span class="notranslate">`/proc/sys/fs/enforce_symlinksifowner`</span> contains value `2` (it is deprecated and can cause issues for the system operation).
 

3. <span class="notranslate">`--check-suexec`</span>

Checks suexec has <span class="notranslate">cagefs</span> jail.

In case if <span class="notranslate">CageFS</span> is installed and SuEXEC is on, checking if <span class="notranslate">CageFS</span> is enabled for SuEXEC.
 
Fails if CageFS is not enabled for suexec binary.


4. <span class="notranslate">`--check-suphp`</span>

Checks suphp has <span class="notranslate">cagefs</span> jail.

In case if <span class="notranslate">CageFS</span> is installed and SuPHP is on, checking if <span class="notranslate">CageFS</span> is enabled for SuPHP.
 
Fails if CageFS is not enabled for suphp binary.

5. <span class="notranslate">`--check-usepam`</span>

Checks UsePAM in <span class="notranslate">`/etc/ssh/sshd_config`</span>.

Checking if <span class="notranslate">`/etc/ssh/sshd_config`</span> config file contains <span class="notranslate">`UsePAM yes`</span> line, which is required for pam_lve correct work with sshd.
 
Fails if <span class="notranslate">`/etc/ssh/sshd_config`</span> contains <span class="notranslate">`UsePAM no`</span> line. 

6. <span class="notranslate">`--check-symlinkowngid`</span>

Checks <span class="notranslate">`fs.symlinkown_gid`</span>.

First checking if user <span class="notranslate">`Apache`</span> is available in the system (on some panels users `httpd` or <span class="notranslate">`nobody`</span> with special GID are present instead of <span class="notranslate">`Apache`</span>, they are detected correctly as well). Then, if such user exists, checking that his GID equals to the one specified in sysctl or that this user belongs to this supplemental group. If these conditions are met, then the protection effect described in [this docs section](/cloudlinux_os_kernel/#symlink-owner-match-protection) is applied to this user, and the appropriate message will be displayed.
 
Fails if Apache user is not in the group specified in <span class="notranslate">`/proc/sys/fs/symlinkown_gid`</span>.

7. <span class="notranslate">`--check-cpanel-packages`</span>

Checks existence of all user's packages (cPanel only)

Reading <span class="notranslate">`PLAN=`</span> for all users from <span class="notranslate">`/var/cpanel/users`</span> and checking if all of them are present in <span class="notranslate">`/var/cpanel/packages`</span> and if not, then displaying them in pairs like <span class="notranslate">`user: plan`. `default`</span> and <span class="notranslate">`undefined`</span> packages are excluded from the check.

Fails if users from <span class="notranslate">`/var/cpanel/users/`</span> directory have non-existing packages (packages do not exist in <span class="notranslate">`/var/cpanel/packages/`</span> directory, except for <span class="notranslate">`undefined`</span> and <span class="notranslate">`default`</span>). 
 

8. <span class="notranslate">`--check-defaults-cfg`</span>

Checks <span class="notranslate">`/etc/cl.selector/default.cfg`</span>.

Checking that if this config exists, the default PHP version is not disabled in it. Also performing minimal syntax checks for PHP modules settings and displaying the incorrect.
 
Fails if there are some problems in <span class="notranslate">`/etc/cl.selector/default.cfg`</span> found.

Possible reasons for failure:
   * Default version is undefined, which means <span class="notranslate">`/etc/cl.selector/default.cfg`</span> file does not contain section [versions] with the defined default version. 
   * Default PHP version is disabled.

9. <span class="notranslate">`--check-cagefs`</span>

All checks for CageFS are described separately in [this docs section](/command-line_tools/#sanity-check) and their start from cagefsctl utility is completely equivalent to the start from cldiag and is designed only for a better experience.
 
This checker includes a set of CageFS sub-checkers, failure of one (or more) of them causes general checker failure.

10. <span class="notranslate">`--check-php-conf`</span>

Checks <span class="notranslate">`/etc/cl.selector/php.conf`</span>.

Checking the config syntax for acceptable blocks and directives.
 
Fails if <span class="notranslate">`/etc/cl.selector/php.conf`</span> has incorrect format.

 * File contains an invalid parameter (valid parameters: <span class="notranslate">`Directive`</span>, <span class="notranslate">`Default`</span>, <span class="notranslate">`Type`</span>, <span class="notranslate">`Comment`</span>, <span class="notranslate">`Range`</span>, <span class="notranslate">`Remark`</span>).
  
 * File contains an invalid setting for the parameter <span class="notranslate">`Type`</span> (valid settings for the  <span class="notranslate">`Type`</span> parameter: <span class="notranslate">`value`, `list`, `bool`</span>)

11.  <span class="notranslate">`--check-phpselector`</span>

Checks compatibility for the <span class="notranslate">PHP Selector</span>

Detecting which PHP handler has been configured on the server and checking its compatibility with the <span class="notranslate">CloudLinux PHP Selector</span> according to [this table](/limits/#compatibility-matrix) and displaying the corresponding message with the link to the documentation in case of a problem detected. No checks are performed for EasyApache3.

Failure reasons:
  * The installed <span class="notranslate">`mod_ruid`</span> package is incompatible with the <span class="notranslate">PHP Selector</span>
  * <span class="notranslate">`mod_suexec`</span> is not installed
  * <span class="notranslate">`mod_suphp`</span> is not installed
  * Absence of the <span class="notranslate">`/usr/local/lsws/conf/httpd_config.xml`</span> file (only for LiteSpeed server)

::: tip Note
The following checkers are available in <span class="notranslate">**lve-utils >= 3.1.2**</span>
:::
 

12. <span class="notranslate">`--check-lve-limits`</span>

Checks the validity of LVE limits on the server.

[See this page for detailed description](/limits/#limits-validation).
 

13. <span class="notranslate">`--check-rpmdb`</span>

Checks the RPM database integrity.

Check that rpm database is operable and utils using it (e.g. yum) can work properly.

To start all available checkers at once, the keys <span class="notranslate">`-a | --all`</span> are used. This does not include Check compatibility for PHP Selector, it must be started separately with <span class="notranslate">`--check-phpselector`</span> key.


### cloudlinux-config

**cloudlinux-config** utility shows/sets various parameters related to [LVE Manager](/lve_manager/#lve-manager-options) UI, [MySQL Governor](/cloudlinux_os_components/#configuration-and-operation) and [faults notifications for LVE-Stats 2](/cloudlinux_os_components/#configuration)

**Usage:**

<div class="notranslate">

```
cloudlinux-config get [--json] [--for-reseller resname ]
cloudlinux-config set [--json] --data <str> [--for-reseller resname ]
cloudlinux-config set [--json] --reset-inodes-limit
```
</div>

**Commands:**

| | |
|-|-|
|<span class="notranslate">`get`</span>| Shows the values of all supported parameters|
|<span class="notranslate">`set`</span>| Sets values for supported parameters|

**Options**

| | |
|-|-|
|<span class="notranslate">`--json`</span>| Sets/returns values in json format|
|<span class="notranslate">`--data`</span>| Sets values from the data string that follows|
|<span class="notranslate">`--for-reseller`</span>| Sets/limits the output only to the data related to reseller _resname_ |
|<span class="notranslate">`--reset-inodes-limit`</span>| Resets inode limits (in case disk quota breaks)|

**JSON data structure**

All options are enclosed inside <span class="notranslate">`options`</span> (Level 0) string. All options are enclosed in `" "`, while values come as is. Here's an example:

<div class="notranslate">

```
'{"options":{"L1_option1":value1, "L1_option2":value2}}'
```
</div>

Each Level1 option can have nested Level2 options specified using the same syntax, the same goes for Level2 and Level3 options respectively.

**LVE-Stats 2 faults notification settings**

| | | | | | |
|-|-|-|-|-|-|
| Level1| Level2| Level3| Level4| Possible values| Description|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>| <span class="notranslate">`concurrentConnections`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include concurrent connection value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>|<span class="notranslate">`cpu`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include CPU consumption value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>|<span class="notranslate">`io`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include IO value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>|<span class="notranslate">`iops`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include IOPS value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>|<span class="notranslate">`mem`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include RAM consumption value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`faultsToInclude`</span>|<span class="notranslate">`nproc`</span>| |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Include number of processes value in notification emails|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`fminimumNumberOfFaultsToNotify`</span>| <span class="notranslate">`admin`</span>| | `N`| The minimum number of faults to notify for admin|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`fminimumNumberOfFaultsToNotify`</span>| <span class="notranslate">`user`</span>| | `N`| The minimum number of faults to notify for users|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`fminimumNumberOfFaultsToNotify`</span>| <span class="notranslate">`reseller`</span><sup> *</sup>| | `N`| The minimum number of faults to notify for reseller|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`fminimumNumberOfFaultsToNotify`</span>| <span class="notranslate">`customer`</span><sup> *</sup>| | `N`| The minimum number of faults to notify for reseller's customers|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`admin`</span>|<span class="notranslate">`period`</span>| `N`| The period of faults notifications for admin|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`admin`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Time units of period of faults notifications for admin|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`user`</span>|<span class="notranslate">`period`</span>| `N`| The period of faults notifications for users|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`user|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Time units of period of faults notifications for users|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`reseller`</span><sup> *</sup>|<span class="notranslate">`period`</span>| `N`| The period of faults notifications for resellers|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`reseller`</span><sup> *</sup>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Time units of period of faults notifications for resellers|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`customer`</span><sup> *</sup>|<span class="notranslate">`period`</span>| `N`| The period of faults notifications for reseller's customers|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notify`</span>|<span class="notranslate">`customer*|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Time units of period of faults notifications for reseller's customers|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyAdmin`</span>| | |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send faults notifications to admin|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyResellerCustomers`</span>| | | <span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send faults notification to reseller users|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyResellerOnCustomers`</span><sup> *</sup>| | | <span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send users' faults notifications to the respective reseller|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyReseller`</span><sup> *</sup>| | |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send faults notification to reseller|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyCustomers`</span>| | |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send faults notifications to users|
|<span class="notranslate">`faultsNotification`</span>|<span class="notranslate">`notifyResellers`</span>| | |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Send faults notification to resellers|

::: tip Note  
Options marked with `*` are for reseller use only
:::

**MySQL Governor settings**

| | | | | | |
|-|-|-|-|-|-|
| Level1| Level2| Level3| Level4| Possible values| Description|
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`errorLog`</span>|<span class="notranslate">`level`</span>| | <span class="notranslate">`DEBUG`</span>/<span class="notranslate">`ERROR`</span>| Sets error log level |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`errorLog`</span>|<span class="notranslate">`logPath`</span>| |<span class="notranslate">`/var/log/dbgovernor-error.log`</span>| Sets error log destination file |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`gatherDataForDetailedStats`</span>| | |<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Enables gathering data for detailed statistics |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`logRestrictedUsersQueries`</span>| | | <span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Enables logging of restricted user queries |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`modeOfOperation`</span>| | |<span class="notranslate">`off`</span>/<span class="notranslate">`single`</span>/<span class="notranslate">`abusers`</span>/<span class="notranslate">`all`</span>| Sets the mode of operation |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictLog`</span>|<span class="notranslate">`format`</span>| |<span class="notranslate">`SHORT`</span>/<span class="notranslate">`MEDIUM`</span>/<span class="notranslate">`LONG`</span>/<span class="notranslate">`VERYLONG`</span>| Sets the format for restrict log |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictLog`</span>|<span class="notranslate">`logPath`</span>| |<span class="notranslate">`/var/log/dbgovernor-restrict.log`</span>| Sets the format for restrict log |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictType`</span>|<span class="notranslate">`mode`</span>| |<span class="notranslate">`period`</span>/<span class="notranslate">`limit`</span>| Sets the restriction mode |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictType`</span>|<span class="notranslate">`unlimit`</span>|<span class="notranslate">`period`</span>| `N`| Sets the restriction expiration period |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictType`</span>|<span class="notranslate">`unlimit`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets the restriction expiration period units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level1`</span>|<span class="notranslate">`period`</span>| `N`| Sets L1 restriction time period |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level1`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets L1 restriction time period units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level2`</span>|<span class="notranslate">`period`</span>| `N`| Sets L2 restriction time period |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level2`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets L2 restriction time period units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level3`</span>|<span class="notranslate">`period`</span>| `N`| Sets L3 restriction time period |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level3`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets L3 restriction time period units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level4`</span>|<span class="notranslate">`period`</span>| `N`| Sets L4 restriction time period |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`level4`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets L4 restriction time period units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>| <span class="notranslate">`timeout`</span>|<span class="notranslate">`period`</span>| `N`| Sets restriction time period timeout|
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`restrictedTimePeriods`</span>|<span class="notranslate">`timeout`</span>|<span class="notranslate">`unitOfTime`</span>|<span class="notranslate">`seconds`</span>/<span class="notranslate">`minutes`</span>/<span class="notranslate">`hours`</span>/<span class="notranslate">`days`</span>| Sets L1 restriction time period timeout units of time |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`scriptPath`</span>| | | <span class="notranslate">`/path/to/script`</span>| Path to script to be triggered when account is restricted |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`slowQueries`</span>|<span class="notranslate">`kill`</span>| | <span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Enables killing of slow queries |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`slowQueries`</span>|<span class="notranslate">`logPath`</span>| |<span class="notranslate">`/path/to/sqkill.log`</span>| Sets the path to slow query kill log file |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`slowQueries`</span>|<span class="notranslate">`timeout`</span>| | `N`| Time to kill slow SELECT queries for account (seconds) |
|<span class="notranslate">`mySQLGovSettings`</span>|<span class="notranslate">`userMaxConnections`</span>| | | `N`| Sets the maximum number of user connections to database |

**LVE Manager UI settings**

| | | | |
|-|-|-|-|
| Level1| Level2| Possible values| Description|
|<span class="notranslate">`inodeLimits`</span>|<span class="notranslate">`showUserInodesUsage`</span>|<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Show end user inode usage|
|<span class="notranslate">`uiSettings`</span>|<span class="notranslate">`hideLVEUserStat`</span>|<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Hide LVE end user usage statistic|
|<span class="notranslate">`uiSettings`</span>|<span class="notranslate">`hidePHPextensions`</span>|<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Hide PHP extension selection|
|<span class="notranslate">`uiSettings`</span>|<span class="notranslate">`hidePythonApp`</span>|<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Hide Python App in web-interface|
|<span class="notranslate">`uiSettings`</span>|<span class="notranslate">`hideRubyApp`</span>|<span class="notranslate">`true`</span>/<span class="notranslate">`false`</span>| Hide Ruby App in web-interface|

**Examples**

* display Python/Ruby Selector in User UI (cPanel)

<div class="notranslate">

```
$ cloudlinux-config set --json --data '{"options":{"uiSettings":{"hideRubyApp":false, "hidePythonApp":false}‌}}'
```
</div>


### Automatic problems notifications

The utility generates HTML reports and emails them to the administrator. You can change email for notifications by adding the following line to the <span class="notranslate">`/etc/sysconfig/cloudlinux`</span>.

<div class="notranslate">

```
EMAIL=username@domain.zone
```
</div>
 
The automatic checks using cldiag utility by cron job is enabled on a server by default. You can disable it in the <span class="notranslate">`/etc/sysconfig/cloudlinux`</span> config file by adding <span class="notranslate">`ENABLE_CLDIAG=no`</span> option. When calling this utility automatically by cron, it checks all limits existing on the server and sends an administrator a report with limits check results.

**Usage examples**

* Run only one checker

<div class="notranslate">

```
# cldiag --check-phpselector

Check compatibility for PHP Selector:

  OK: It looks ok [php.conf:cgi with suexec, suphp]

There are 0 errors found.
```
</div>

* Run all available checkers

<div class="notranslate">

```
# cldiag -a

Check control panel and it's configuration(for DirectAdmin only):

  OK: Control Panel - cPanel; Version 79.9999;

Check fs.enforce_symlinksifowner is correctly enabled in sysctl conf:

  OK: fs.enforce_symlinksifowner = 1

Check suexec has cagefs jail:

  OK: binary has jail

Check suphp has cagefs jail:

  OK: binary has jail

There are 0 errors found.
```
</div>

### Common problems troubleshooting

Reasons and recommendations on how to fix common cldiag checkers failures.

* <a name="diag-cp"></a><span class="notranslate">`--diag-cp`</span>

  Checks control panel and its configuration (for DirectAdmin only).
  
  On servers with DirectAdmin control panel, CloudLinux support should be enabled in custombuild config. To do so, set <span class="notranslate">`yes`</span> for the <span class="notranslate">`cloudlinux`</span> parameter via <span class="notranslate">`/usr/local/directadmin/custombuild/build`</span> utility. Please read [this article](https://cloudlinux.zendesk.com/hc/articles/115004584909-PHP-Selector-and-DirectAdmin) to see how to set values to parameters.
* <a name="symlinksifowner"></a><span class="notranslate">`--symlinksifowner`</span>

  Checks <span class="notranslate">`fs.enforce_symlinksifowner`</span> is correctly enabled in <span class="notranslate">`/etc/sysctl.conf`</span>.

  To fix warning, change the value of <span class="notranslate">`/proc/sys/fs/enforce_symlinksifowner`</span>. See [Symlink Owner Match Protection](/cloudlinux_os_kernel/#symlink-owner-match-protection) to know more about the <span class="notranslate">`fs.enforce_symlinksifowner`</span> parameter and configure it correctly.
  
  Fixing that warning makes the server more protected against symlink attacks and enables protection of PHP configs and other sensitive files.
* <a name="check-symlinkowngid"></a><span class="notranslate">`--check-symlinkowngid`</span>
  
  Checks <span class="notranslate">`fs.symlinkown_gid`</span>.

  Symlink Owner Match Protection is not enabled for the <span class="notranslate">`Apache`</span> user. To enable it, see [Symlink Owner Match Protection](/cloudlinux_os_kernel/#symlink-owner-match-protection) and set value of apache GID to the <span class="notranslate">`fs.symlinkown_gid`</span> parameter.

  Enabling Symlink Owner Match Protection provides protection for the <span class="notranslate">`Apache `</span>user and it may improve your server security.
* <a name="check-suexec"></a><span class="notranslate">`--check-suexec`</span>

  Checks <span class="notranslate">`suexec`</span> has CageFS jail.

  Check that <span class="notranslate">`suexec`</span> package was installed from CloudLinux repository and if yes, try to reinstall it, probably <span class="notranslate">`suexec`</span> binary was broken.
  
  If you are running server without a control panel, you need to configure <span class="notranslate">`suexec`</span> by yourself. Please read [this article](https://cloudlinux.zendesk.com/hc/articles/115004524005-Configuring-CloudLinux-software-and-PHP-Handlers-on-a-server-with-no-control-panel) to setup suexec on your server.
  
  Fix that warning to be sure that users run their sites inside CageFS and provide stable work of sites that are using Apache suexec module. This may improve server security.
* <a name="check-suphp"></a><span class="notranslate">`--check-suphp`</span>
  
  Checks <span class="notranslate">`suphp`</span> has CageFS jail.

  Check that <span class="notranslate">`suphp`</span> package was installed from CloudLinux repo and if yes, try to reinstall it, probably <span class="notranslate">`suphp`</span> binary was broken. 

  If you are running server without a control panel, you need to configure suphp by yourself. Please read [this article | Installation and setup of a server using suPHP](https://cloudlinux.zendesk.com/hc/articles/115004524005-Configuring-CloudLinux-software-and-PHP-Handlers-on-a-server-with-no-control-panel) to setup <span class="notranslate">`suphp`</span> on your server.

  Fix that warning to be sure that users run their sites inside CageFS and provide stable work of sites that are using Apache suphp module. This may improve server security.
* <a name="check-usepam"><span class="notranslate">`--check-usepam`</span></a>
  
  Checks UsePAM in <span class="notranslate">`/etc/ssh/sshd_config`</span>.

  To fix the issue, replace <span class="notranslate">`UsePAM no`</span> with <span class="notranslate">`Use PAM yes`</span> in the <span class="notranslate">`/etc/ssh/sshd_config`</span> file.
  
  Fix the warning to provide correct work of <span class="notranslate">`pam_lve`</span> module with sshd and CageFS ssh sessions, for details, please [read this documentation about LVE PAM](/cloudlinux_os_components/#lve-pam-module).

* <a name="check-defaults-cfg"></a><span class="notranslate">`--check-defaults-cfg`</span>

  Checks <span class="notranslate">`/etc/cl.selector/default.cfg`</span>

  * In case of <span class="notranslate">`undefined default version`</span> error, go to <span class="notranslate">LVE Manager | Selector</span> Tab and set the default PHP version;
  * In case of <span class="notranslate">`default version disabled`</span> error, enable that version to fix the warning;

  <span class="notranslate">`/etc/cl.selector/defaults.cfg`</span> config file is used by the PHP Selector and stores its global options, so it is important to keep needed configurations and valid syntax for PHP modules settings to avoid <span class="notranslate">PHP Selector</span> misconfiguration.

* <a name="check-cagefs"></a><span class="notranslate">`--check-cagefs`</span>

  Depending on the error you get, resolution options may differ. See the full list of checks that <span class="notranslate">`--check-cagefs`</span> performs [here](/command-line_tools/#sanity-check). There you also can find possible failure reasons.

* <a name="check-phpselector"></a><span class="notranslate">`--check-phpselector`</span>

  Checks compatibility for the <span class="notranslate">PHP Selector</span>.
  
  Possible failures:

  * In case of installed `mod_ruid2` package - remove it, <span class="notranslate">PHP Selector</span> is incompatible with that module.
  * In case of non-installed `mod_suexec` package - install it.
  * In case of non-installed `mod_suphp` package - install it.
  * In case of unsupported handler - see [this table](/limits/#compatibility-matrix) to set the compatible handler.