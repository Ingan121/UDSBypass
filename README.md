# UDSBypass
Magisk UDS Detection Bypass Script 1.2 by Ingan121  
Download Script
(long-tap the link and tap 'Save link' or such thing.)

# How to use?
You have to run this script with the name of the activity that you want to use.

You can get the required string ([package name]/[activity name]) easily if you're using Nova Launcher. Enable 'Show component...' in Settings > Lab (Google it if you don't know) > Debug, then open the edit dialog of the app. You can copy the string just by tapping it.

## Per-app guides

### Liapp
If you see a dialog saying
> \> ROOTED [/ RSH (if Shizuku is running)]  
> \> MAGISK
>
> Security engine: v5.0.2/5.1.0 (lower versions can be bypassed by Magisk 19.0+)

, then the app is definitely using Liapp.

For Liapp, you can just run
> su  
> sh /sdcard/path/to/udsbypass [package name]/[activity name]
to bypass it, but some other root apps might lose root before restarting magiskd, and all apps cannot start a new root shell. So, DO NOT close the terminal, otherwise you'll have to reboot to get the root back.

### Promon
If the app crashes immediately when not using Hide and crashes after while when using Hide, then it is probably using Promon.  
Since Promon has a wierd detection logic that checks if a root shell is running on terminal apps, you have to run SSH using some apps like SSHDroid and access to it by using any SSH clients (e.g. Termius, ConnectBot, JuiceSSH). Then, you can run this script in there.
Run
> su (if it's not a root shell, if # shows in left side of the command, then it's a root shell.)
> sh /sdcard/path/to/udsbypass [package name]/[activity name] 15
. Unlike Liapp, it checks root only when the app starts, so you can restart magiskd after the check is done.

# Command usage
Usage: sh udsbypass [package name]/[activity name] [delay]  
or: sh udsbypass [options]

Delay: sets the delay before restarting magiskd  
leave empty or use -1 to restart it manually

Options:  
--help: shows this message  
--version: shows the version of this script
