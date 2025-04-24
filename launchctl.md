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

Just run launchctl on its own to get