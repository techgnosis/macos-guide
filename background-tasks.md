backgroundtaskmanagementd
this process controls the `Allow in the Background` section

you can view what it controls via
sfltool dumpbtm

btm = background task management
sfl = SharedFileList

https://www.kandji.io/blog/macos-ventura-login-background-items


also check out launchctl

SMAppService


Here we go
https://developer.apple.com/documentation/servicemanagement

3 types of services
* LoginItems (i think these get called "startup items" sometimes)
* LaunchAgents
* LaunchDaemons

If .plist files are used, LaunchDaemons can only start from /System/Library and /Library. LaunchAgents can start from ~/Library as well.

What is this about? I thought `LoginItems` was supposed to hold .plist file that contained the path to the executable
/Applications/1Password.app/Contents/Library/LoginItems/1Password Browser Helper.app/


OK
The application itself is responsible setting up login/launch items.

If you use SMAppService, then your app needs to use those APIs when it launches and tell macOS where to find all the helper executables bundled in their own bundles.

If you want to use .plist files then the app needs to copy the .plist file from its bundle to a known discovery location like ~/Library/LoginItems