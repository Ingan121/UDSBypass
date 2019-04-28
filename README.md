# UDSBypass
Magisk UDS Detection Bypass Script 1.2 by Ingan121  
[Download Script](https://github.com/Ingan121/UDSBypass/raw/master/udsbypass)  
(Long-tap the link and tap 'Save link' or such thing. Check the filename after downloading, since some browsers add a .txt extension when downloading.)

# How to use?
You have to run this script with the name of the activity that you want to use, see below for more.

The required string ([package name]/[activity name]) can be obtained easily if you're using Nova Launcher. Enable 'Show component...' in Settings > Lab (Google it if you don't know) > Debug, then open the edit dialog of the app. You can copy the string just by tapping it.

Since this script kills the Magisk daemon (magiskd), some other root apps might lose root before restarting magiskd, and all apps cannot start a new root shell while magiskd is not running. So, DO NOT kill the terminal before relaunching magiskd, otherwise you'll have to reboot to get the root back.

## Per-app guides

### [Liapp](https://liapp.lockincomp.com)
If you see a dialog saying
> \> ROOTED [/ RSH (if Shizuku is running)]  
> \> MAGISK
>
> Security engine: v5.0.2/5.1.0 (lower versions can be bypassed by Magisk 19.0+)

, then the app is definitely using Liapp.

For these, you can just run
> su  
> sh /sdcard/path/to/udsbypass [package name]/[activity name]

in terminal to bypass it.

### [Promon](https://promon.co)
If the app crashes immediately when not using Hide and crashes after a while when using Hide, then probably it is using Promon.  
Since Promon has a wierd detection logic that checks if a root shell is running on terminal apps, you have to run a SSH server using some apps like [SSHDroid](https://play.google.com/store/apps/details?id=berserker.android.apps.sshdroid) and access to it by using any SSH client (e.g. [Termius](https://play.google.com/store/apps/details?id=com.server.auditor.ssh.client), [ConnectBot](https://play.google.com/store/apps/details?id=org.connectbot), [JuiceSSH](https://play.google.com/store/apps/details?id=com.sonelli.juicessh)). Then, you can run this script there.

Command:  
> su (if it's not a root shell. if # shows in left side of the command, then it's a root shell.)  
> sh /sdcard/path/to/udsbypass [package name]/[activity name] 15

Unlike Liapp, it checks root only when the app starts, so you can restart magiskd after the check is done.

# Command usage
Usage: sh udsbypass [package name]/[activity name] [delay]  
or: sh udsbypass [options]

Delay: sets the delay before restarting magiskd  
leave empty or use -1 to restart it manually

Options:  
--help: shows this message  
--version: shows the version of this script
