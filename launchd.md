launchd is like systemd
launchctl is like systemctl

man launchctl

fundamental structures
* domains - manages execution policy for one or more services
* services - a process
* endpoints - hosted by the service. using any endpoint will cause the service to launch automatically

domains
* system
* user
* login
* gui
* pid

launchctl print system
launchctl print system/<service name>
launchctl print user/1001
etc..

launchctl print-disabled system
launchctl print-disabled user/1001

launchctl reboot
launchctl reboot system - same as with no argument




---------


A LaunchDaemon is run as root and starts before any user sessions begin

A LaunchAgent is run as your user and starts when you log in

Both are controlled by `launchd` and `.plist` files in 
* /System/Library/LaunchAgents
* /System/Library/LaunchDaemons
* /Library/LaunchAgents
* /Librray/LaunchDaemons
* ~/Library/LaunchAgents
* ~/Library/LaunchDaemons

I verified a bit by looking at the files in /System/Library/LaunchAgents and they are all running and owned by my user

There is a LOT of stuff that runs at launch in macOS

