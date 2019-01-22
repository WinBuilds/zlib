Build instructions
==================

- Open windows\VS2017\zlib.sln with Microsoft Visual C++ 2017 and Rebuild.
- The manifest constant ZLIB_WINAPI need to be #defined in your application
  when linking to zlibdll.dll. Do not define the old ZLIB_DLL.

Notes
-----

- zlibdll.dll uses the WINAPI calling convention for the exported functions,
  and includes the minizip functionality.

- zlibdll.dll is compatible with zlib.dll built by Gilles Vollant from the
  zlib 1.1.x sources, and distributed at http://www.winimage.com/zLibDll

- The official DLL build, named zlib1.dll is exporting the functions using
  the CDECL convention.

Above comments are an updated concise version of the original comments by
Gilles Vollant
info@winimage.com

