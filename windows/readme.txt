#General Build Instructions

- Set WINBUILDS_ROOT environtment variable to specify a target directory. If 
WINBUILDS_ROOT is not set it is assumed to be ".", that is, the same 
directory where the  .vcxproj resides.

Developer packages will be created in %WINBUILDS_ROOT% according to the 
following schema:

$(WINBUILDS_ROOT)build_msvc15_$(Platform)/$(Configuration)/bin/: 
.exe , .dll, .exp, .pdb go here

$(WINBUILDS_ROOT)build_msvc15_$(Platform)/$(Configuration)/lib/ : 
.lib go here

$(WINBUILDS_ROOT)build_msvc15_$(Platform)/$(Configuration)/include/ : 
.h go here

- Open windows\VS2017\*.sln with Visual Studio and Rebuild.

##Building Libraries
For library projects, both static and shared libraries will be produced. 
The static libraries will assume static C and C++ runtimes and the shared 
libraries will link to dynamic C and C++ runtime libraries.

Static libraries do not link to their dependendcies, shared libraies do.

Shared libraries with static runtimes and static libraries with dynamic
runtimes are normally not produced but you are welcome to add those
build options if you need them or you just feel like it.

Target naming convention:
<name>dll.dll - dynamic library
<name>dll.lib - import library
<name>lib.lib - static library

This naming schema produces names different from the original projects, but it 
is consistent, and it is believed that it is easier to use than ad-hoc names.

##Specific Build Instructions for ZLIB
- The manifest constant ZLIB_WINAPI need to be #defined in your application
  when linking to zlibdll.dll. Do not define the old ZLIB_DLL.

- zlibdll.dll uses the WINAPI calling convention for the exported functions,
  and includes the minizip functionality.

- zlibdll.dll is compatible with zlib.dll built by Gilles Vollant from the
  zlib 1.1.x sources, and distributed at http://www.winimage.com/zLibDll

- The official DLL build, named zlib1.dll is exporting the functions using
  the CDECL convention.

Above comments are an updated concise version of the original comments by
Gilles Vollant
info@winimage.com

