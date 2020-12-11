### Mac and Linux
Put your fmod api in `lib/Linux` or `lib/Mac` so that you have the following folder structure :
```
lib/$OS/api
    /core
        /lib
        /inc
    /studio
        /lib
        /inc
```

### Using fmod with Hxcpp
If you are using lime, it will automatically copy the fmod libs to where it generates your executable

Hxcpp should do the same thing.

### Using fmod on Html5

If you are not using lime, you will have to manually copy over the files in `lib/html5` and `jaxe/jaxe.js`, and include them in your .html file

### Using fmod with Hashlink
If you are using lime, then just add `<haxelib name="haxe-fmod">` to your project xml, and lime will automatically copy faxe.hdll, and the fmod libs to your output folder.

If you are not using lime you will need to put faxe.hdll, and the fmod libs somewhere where your hashlink executable can see them

### Building the hashlink wrapper
You will need a working C compiler (MSVC on windows, xcode on macos, gcc on linux), and install hxcpp (`haxelib install hxcpp`)

You will also need to have a working hashlink installation :
- Windows : Grab a release from the hashlink repo and make the env variable HASHLINK point to where you unzipped it
- Macos : `brew install hashlink` or follow the instructions in the hashlink readme to build from source
- Linux : Follow the instructions in the hashlink readme and build hashlink from source

```sh
$ cd path/to/haxe-fmod
$ cd faxe
$ haxelib run hxcpp Build.xml # Add -DHXCPP_M32 to force 32 bit (needed for lime on windows), or -DHXCPP_M64 to force x64
```
You should now have faxe.hdll in `path/to/haxe-fmod/ndll/$OS`.
