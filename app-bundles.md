the .app "bundle" is actually a directory

everything sits inside the `Contents` directory

the executables are in `MacOS`

shared libraries are in `Frameworks`

Icons and things are in `Resources`

.plist files for launchd are located in `Library`




You can use `plutil` to make plists if you want to test out an app bundle

You can make icons with `iconutil`

You can sign code with `codesign`
