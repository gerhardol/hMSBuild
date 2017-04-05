# [hMSBuild](https://github.com/3F/hMSBuild)

A lightweight tool (a single compiled batch file ~17 Kb that can be embedded inside any scripts or other batch files) - an easy helper for searching of available MSBuild tools. Supports tools from VS2017+ (does not requires additional vswhere.exe), VS2015 or less, other versions from .NET Framework.


[![Build status](https://ci.appveyor.com/api/projects/status/tusiutft7a0ei109/branch/master?svg=true)](https://ci.appveyor.com/project/3Fs/hmsbuild/branch/master) [![License](https://img.shields.io/badge/License-MIT-74A5C2.svg)](https://github.com/3F/hMSBuild/blob/master/License.txt)


## Why hMSBuild ?

*because you need to access to msbuild tools...* 

It based on **GetNuTool core** https://github.com/3F/GetNuTool, and msbuild helper initially was as a part of this tool. But with latest changes from MS (i do not have any decent words to describe all this -_- ) we extracted this to new project for more support of all this.

### What supports ?

* Versions from VS2017+ 
    * https://github.com/Microsoft/vswhere/issues/41 - But it solves our problem **only** for online machines. that is, you should have internet connection if you want to use msbuild from VS2017+
    
* Versions from VS2015, VS2013, .NET Framework
    * Still easy to find even for offline.
    
## Usage

Usage is same as it would be same for msbuild. But you also have additional keys to access to GetNuTool core and to settings of hMSBuild:

```bash
Usage: hMSBuild [args to hMSBuild] [args to msbuild.exe or GetNuTool core]
------

----------
Arguments:
----------
hMSBuild -novswhere            - Do not search via vswhere.
hMSBuild -novs                 - Disable searching from Visual Studio.
hMSBuild -nonet                - Disable searching from .NET Framework.
hMSBuild -vswhereVersion {num} - To use special version of vswhere. Use `latest` keyword to get latest version.
hMSBuild -nocachevswhere       - Do not cache vswhere. Use this also for reset cache.
hMSBuild -notamd64             - To use x32 bit version of found msbuild.exe if it's possible.
hMSBuild -eng                  - Try to use english language for all build messages.
hMSBuild -GetNuTool {args}     - Access to GetNuTool core.
hMSBuild -help                 - Shows this help. Aliases: -help -h /? -?


--------
Samples:
--------
hMSBuild -vswhereVersion 1.0.50 -notamd64 "Conari.sln" /t:Rebuild
hMSBuild -vswhereVersion latest "Conari.sln"

hMSBuild -novswhere -novs -notamd64 "Conari.sln"
hMSBuild -novs "DllExport.sln"
hMSBuild vsSolutionBuildEvent.sln

hMSBuild -GetNuTool -unpack
hMSBuild -GetNuTool /p:ngpackages="Conari;regXwild"

"hMSBuild -novs "DllExport.sln" || goto err"

---------------------
Possible Error Codes: ERROR_FILE_NOT_FOUND (0x2), ERROR_PATH_NOT_FOUND 3 (0x3), ERROR_SUCCESS (0x0)
---------------------
```

## License

The [MIT License (MIT)](https://github.com/3F/hMSBuild/blob/master/License.txt)

```
Copyright (c) 2017 Denis Kuzmin <entry.reg@gmail.com>
```

[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=entry%2ereg%40gmail%2ecom&lc=US&item_name=3F%2dOpenSource%20%5b%20github%2ecom%2f3F&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_SM%2egif%3aNonHosted)