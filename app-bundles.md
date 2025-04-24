the .app "bundle" is actually a directory

everything sits inside the `Contents` directory

the executables are in `MacOS`

shared libraries are in `Frameworks`

Icons and whatnot are in `Resources`

.plist files for launchd are located in `Library`



/Library/LaunchAgents
/Library/LaunchDaemons
~/Library/LaunchAgents
~/Librray/LaunchDaemons



You can use plutil to make plists if you want to test out an app bundle

You can make icons with iconutil

You can sign code with codesign
