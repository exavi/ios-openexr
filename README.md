ios-openexr
===========

This project builds an OpenEXR framework for iOS ready for arm7, arm7s and 386 architectures.

The versions used to build the framework are:
- IlmBase 1.2.0
- OpenEXR 1.7.0

In addition to the generated framework, you will need to include zlib to the libraries linked in your project as is an OpenEXR dependency. (There are several versions pre-packaged with the iOS SDK, I used "libz.1.2.5.dylib")

When compiling make sure any "*.m" files that use this framework have the "File Type" set to "Objective-C++ Source".


This is basically a thing I quickly hacked together, that should get you around compiling OpenEXR for iOS, there is probably a smarter way to go around it but this works fine. If you want to know what I did  in case you want to improve it, the only edits done to the original OpenEXR distributed files are:

- POSIX Semaphores are disabled (this seems to crash on iOS)
- Disabled HAVE_LARGE_STACK as this crashes on iOS devices (not on the simulator) this should make ImfAutoArray allocate from the heap and thus avoid the crashing when doing using the stack.
- All includes have <filename.h> replaced by "filename.h" as all header files are packaged in the framework at the same level, this makes code including these nicer.
- Pregenerated Half headers.

Enjoy!
