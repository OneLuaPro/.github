# OneLuaPro
**OneLuaPro** is ...

- a portable, monolithic, and curated distribution of the [Lua](http://www.lua.org/) programming language for the Windows operation system,
- natively built with MSVC compilers,
- provided as `x64` signed binaries and signed installers for Windows 7 to Windows 11,
- targeted for corporate application scenarios on computers without permanent Internet access.

**OneLuaPro** is not ...

- made for compatibility with Lua package managers like `luarocks`.

**OneLuaPro** supports ...

- easy entry into the Lua world by providing the [ZeroBrane Studio](https://github.com/pkulchenko/ZeroBraneStudio) Integrated Development Environment (IDE) and the [luacheck](https://github.com/OneLuaPro/luacheck) linter for static code analysis.

**OneLuaPro** can ...

- be built with minimum effort and toolchain-footprint as all its components are prepared for the [CMake](https://cmake.org/) build infrastructure,
- be installed entirely without administrative privileges using the released zip-archives,
- be installed or uninstalled using the provided signed installer packages.

## Download and Installation

Download **OneLuaPro** from here: https://github.com/OneLuaPro/OneLuaPro/releases

Notice that all executables, all DLL, both installer and uninstaller (in case of NSIS64 option), as well as the MSI-install package are provided as certified code-signed binaries.

### Install OneLuaPro using MSI-Package

Double-click the installer and follow the installer wizard. This installer <u>requires</u> administrative rights. A scripted installation or removal is also possible. When launched from an elevated command prompt, the User Account Control prompt will be circumvented.

```cmd
# Standard non-interactve installation into c:\Program Files\OneLuaPro
msiexec.exe /i OneLuaPro-<VERSION>-x64.msi /qb

# Customized non-interactive installation into c:\Apps\OneLuaPro
msiexec.exe /i OneLuaPro-<VERSION>-x64.msi /qb INSTALL_ROOT="C:\Apps\OneLuaPro"

# Standard non-interactve removal (from default installation path)
msiexec.exe /x OneLuaPro-<VERSION>-x64.msi /qb

# Customized non-interactive removal (from custom installation path)
msiexec.exe /x OneLuaPro-<VERSION>-x64.msi /qb INSTALL_ROOT="C:\Apps\OneLuaPro"
```

The installer creates or removes entries in the Windows Start Menu and updates the `PATH`-variable accordingly. Software removal is also possible via Windows Settings "Apps & Features".

### Install OneLuaPro using NSIS64-Installer

Double-click the installer and follow the installer wizard. This installer <u>does not require</u> administrative rights. The installer creates entries in the Windows Start Menu and updates the `PATH`-variable. Software removal is also possible via Windows Settings "Apps & Features".

### Install OneLuaPro using ZIP-Archive

Unpack downloaded zip-archive into a directory of your choice. The suggested installation path is `c:\Apps`, which is typically accessible without administrative rights. Manually extend `PATH`-variable to the `bin` directory of your installation, e.g. `C:\Apps\OneLuaPro-<VERSION>-x64\bin`. Documentation and code examples are located in `<OneLuaPro_Install_Path>\share\doc`. 

### Notes for Installation on Windows 7

The provided installer can be used on Windows 7 but may have some flaws, which can be fixed manually:

- In case the installer complains about `PATH` environment variable being too long to be extended for OneLuaPro, install without updating the variable and edit `PATH` manually by adding `C:\Program Files\OneLuaPro\bin` (or the installation directory of your choice) to the content of `PATH`.
- ZeroBraneStudio may complain about a missing DLL (`vcruntime140_1.dll`). Simply copy this DLL from `C:\Program Files\OneLuaPro\bin` to `C:\Program Files\OneLuaPro\opt\ZeroBraneStudio`. This flaw may also occur after installation using the provided ZIP-archive.

## Contents of the OneLuaPro Distribution

**OneLuaPro** comprises not only the Lua programming language binaries, but also a number of mature and widely-used extensions (modules) in their respective most recent version, all of which tailored to **OneLuaPro**'s needs. All version numbers follow the `v[Base]-[Commits]-[Hash]` format: The first part indicates the **stable base version**, followed by the **number of additional changes** since the last release, and a short **identifier (hash)** of the exact source code.

| Extension                                                    | Purpose                                                      | Version                 | License                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------- | ------------------------------------------------------------ |
| [Lua](https://github.com/KritzelKratzel/lua)                 | The Lua Programming Language                                 | `v5.4.8-1-gfdac66f`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaSocket](https://github.com/OneLuaPro/luasocket)          | Network support for the Lua language                         | `v3.1.0-71-gcb1c0e5`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [librs232](https://github.com/OneLuaPro/librs232)            | Multi-platform library for serial communications over RS-232 (serial port) | `v1.0.3-118-g1171731`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaFileSystem](https://github.com/OneLuaPro/luafilesystem)  | Complements the set of functions related to file systems offered by the standard Lua distribution | `v1.9.0-9-gc499d80`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [argparse](https://github.com/OneLuaPro/argparse)            | Feature-rich command line parser for Lua inspired by argparse for Python | `v0.7.1-13-gdebe947`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Luacheck](https://github.com/OneLuaPro/luacheck)            | Static analyzer and a linter for Lua. It detects various issues such as usage of undefined global variables, unused variables and values, accessing uninitialized variables, unreachable code and more. | `v1.2.0-35-g7580037`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsleep](https://github.com/OneLuaPro/lsleep)                | Adds the missing `sleep()` and `usleep()` functions to Lua.  | `v1.05-5-g9e4bdf2`      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-ffi](https://github.com/OneLuaPro/lua-ffi)              | A portable lightweight C foreign function interface (FFI) for Lua, based on libffi | `v1.1.0-22-gb95c731`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [MoonUSB](https://github.com/OneLuaPro/moonusb)              | Lua binding library for libusb, allowing applications to access and use USB devices. | `v0.1-28-g5d71db5`      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luv](https://github.com/OneLuaPro/luv)                      | Bare libuv bindings for Lua                                  | `v1.51.0-2-26-gbc16467` | [![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) |
| [lanes](https://github.com/OneLuaPro/lanes)                  | Lua Lanes - multithreading in Lua                            | `v4.0.0-pre-df58a33`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luaping](https://github.com/OneLuaPro/luaping)              | The missing ping command for Lua                             | `v1.1.1`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luadaqmx](https://github.com/OneLuaPro/luadaqmx)            | OneLuaPro gateway to National Instrument's DAQmx driver      | `v0.1.1`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua4882](https://github.com/OneLuaPro/lua4882)              | OneLuaPro gateway to National Instrument's NI-488.2 (GPIB) driver | `v1.2.2`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LPeg](https://github.com/OneLuaPro/LPeg)                    | Parsing Expression Grammars For OneLuaPro                    | `v1.1.0-4-g4190cdb`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [wxLua](https://github.com/OneLuaPro/wxlua)                  | wxLua is a Lua wrapper for the cross-platform wxWidgets GUI library | `v3.2.0.2-15-gf60e451`  | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [ZeroBrane Studio](https://github.com/OneLuaPro/ZeroBraneStudio) | lightweight cross-platform Lua IDE with code completion, syntax highlighting, remote debugger, code analyzer, live coding, and debugging support | `v2.01-8-g70c9b503`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Penlight](https://github.com/OneLuaPro/Penlight)            | A set of pure Lua libraries focusing on input data handling (such as reading configuration files), functional programming (such as map, reduce, placeholder expressions,etc), and OS path management. Much of the functionality is inspired by the Python standard libraries. | `v1.15.0-15-gda98756`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lcomplex](https://github.com/OneLuaPro/lcomplex)            | Lua complex numbers support module                           | `v1.0`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luaSGF](https://github.com/OneLuaPro/luaSGF)                | Lua bindings for the Savitzky-Golay-Filter Implementation for data filtering or smoothing | `v2.0.0`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luacrc32c](https://github.com/OneLuaPro/luacrc32c)          | Lua bindings for Google's CRC-32C implementation             | `v1.0`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-zlib](https://github.com/OneLuaPro/lua-zlib)            | Simple streaming interface to zlib for Lua                   | `v1.4-5-g2dd8f48`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-cjson](https://github.com/OneLuaPro/lua-cjson)          | Fast JSON encoding/parsing module for Lua                    | `v2.1.0.16-13-g5a84afa` | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luasec](https://github.com/OneLuaPro/luasec)                | Secure connections to any Lua application or script          | `v1.3.2-4-g3219920`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-openssl](https://github.com/OneLuaPro/lua-openssl)      | OpenSSL bindings for Lua                                     | `v0.11.0-3-9-gad322f2`  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [ldoc](https://github.com/OneLuaPro/ldoc)                    | Lua documentation generator which can also process C extension source files | `v1.5.0-14-gc5e6601`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luasystem](https://github.com/OneLuaPro/luasystem)          | Platform independent system calls for Lua                    | `v0.6.3-8-gfd8c2b3`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua_cliargs](https://github.com/OneLuaPro/lua_cliargs)      | Command-line argument parsing module for Lua                 | `v3.0.2-7-gc4cf5f0`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [dkjson](https://github.com/OneLuaPro/dkjson)                | JSON module written in Lua                                   | `v2.8`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [say](https://github.com/OneLuaPro/say)                      | Lua string hashing library, useful for internationalization  | `v1.4.1-2-ge4436ea`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luassert](https://github.com/OneLuaPro/luassert)            | Assertion library for Lua                                    | `v1.9.0-12-gcad10e9`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [mediator_lua](https://github.com/OneLuaPro/mediator_lua)    | Mediator pattern implementation for pub-sub management       | `v1.1.2-0-8-gefa5daf`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-term](https://github.com/OneLuaPro/lua-term)            | Terminal operations for Lua                                  | `v0.8-6-g1fc5955`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-utf8](https://github.com/OneLuaPro/luautf8)             | UTF-8 support module for Lua                                 | `v0.2.0-6-gb891069`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [inifile](https://github.com/OneLuaPro/inifile)              | A simple and complete ini-File Parser for Lua                | `v1.1-1-g43cd83d`       | [![License](https://img.shields.io/badge/License-BSD%202--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause) |
| [busted](https://github.com/OneLuaPro/busted)                | Elegant Lua unit testing                                     | `v2.3.0-5-g4bbf32a`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lunit](https://github.com/OneLuaPro/lunit)                  | Unit testing for Lua                                         | `v0.8.1-1-g61e9b3a`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsqlite3](https://github.com/OneLuaPro/lsqlite3)            | Extended lsqlite3 module for Lua: A lightweight SQLite3 wrapper featuring the complete SQLean power-pack | `v0.9.6-0`              | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

👉 Are you missing an important Lua extension or Lua library? Please let us know [here](https://github.com/orgs/OneLuaPro/discussions/categories/ideas). 👈

## Dependencies

**OneLuaPro** uses the following libraries:

| Dependency                                                   | Purpose                                                      | Used by                                                      | Version                | License                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------- | ------------------------------------------------------------ |
| [libffi](https://github.com/OneLuaPro/libffi)                | A Portable Foreign Function Interface Library.               | [lua-ffi](https://github.com/OneLuaPro/lua-ffi)              | `v3.5.2-25-ge74b641`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libusb](https://github.com/OneLuaPro/libusb)                | A library for USB device access.                             | [MoonUSB](https://github.com/OneLuaPro/moonusb)              | `v1.0.29-60-gf385e44f` | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [libuv](https://github.com/libuv/libuv)                      | Cross-platform asynchronous I/O                              | [luv](https://github.com/OneLuaPro/luv)                      | `v1.52.0`              | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [NI‑DAQmx](https://www.ni.com/en/support/downloads/drivers/download.ni-daq-mx.html) | Provides a high‑performance, unified API for controlling and acquiring data from National Instruments measurement hardware | [luadaqmx](https://github.com/OneLuaPro/luadaqmx)            | `2025 Q4`              | [See here](https://www.ni.com/en/about-ni/legal/software-license-agreement.html) |
| [NI-488.2](https://www.ni.com/en/support/downloads/drivers/download.ni-488-2.html) | Provides support for customers using NI GPIB controllers and NI embedded controllers with GPIB ports | [lua4882](https://github.com/OneLuaPro/lua4882)              | `2025 Q4`              | [See here](https://www.ni.com/en/about-ni/legal/software-license-agreement.html) |
| [wxWidgets](https://github.com/wxWidgets/wxWidgets)          | wxWidgets is a free and open source cross-platform C++ framework for writing advanced GUI applications using native controls | [wxLua](https://github.com/pkulchenko/wxlua)                 | `v3.2.9`               | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [Savitzky-Golay-Filter](https://github.com/OneLuaPro/Savitzky-Golay-Filter) | C implementation of Least-Squares Smoothing and Differentiation by the Convolution (Savitzky-Golay) Method | [luaSGF](https://github.com/OneLuaPro/luaSGF)                | `v2.0-14-gb9af1a1`     | [![License](https://img.shields.io/badge/License-BSD_2--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause) |
| [crc32c](https://github.com/google/crc32c)                   | Google's implantation of the CRC-32C hashing algorithm       | [luacrc32c](https://github.com/OneLuaPro/luacrc32c)          | `v1.1.2-8-g1f21644`    | [![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause) |
| [zlib-ng](https://github.com/zlib-ng/zlib-ng)                | zlib replacement with optimizations for "next generation" systems | [lua-zlib](https://github.com/OneLuaPro/lua-zlib)            | `v2.3.3`               | [![License: Zlib](https://img.shields.io/badge/License-Zlib-lightgrey.svg)](https://opensource.org/licenses/Zlib) |
| [api-ms-win-core-path-l1-1-0](https://github.com/OneLuaPro/api-ms-win-core-path-l1-1-0) | A minimal implementation of `api-ms-win-core-path-l1-1-0.dll` for Windows 7 | OneLuaPro Windows 7 Support                                  | `v1.0.0-4-g5eb63bf`    | [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) |
| [dlfcn-win32](https://github.com/dlfcn-win32/dlfcn-win32)    | dlfcn-win32 is an implementation of `dlfcn` for Windows      | Prerequisite for building [lua-ffi](https://github.com/OneLuaPro/lua-ffi) | `v1.4.2`               | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libressl](https://www.libressl.org/)                        | An [open-source](https://en.wikipedia.org/wiki/Open-source_software) implementation of the [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) protocol | [luasec](https://github.com/OneLuaPro/luasec), [lua-openssl](https://github.com/OneLuaPro/lua-openssl) | `v4.2.1`               | [See here](https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE.txt) |
| [SQLite](https://www.sqlite.org/)                            | SQL database engine                                          | [sqlean](https://github.com/OneLuaPro/sqlean)                | `v3.51.2`              | Public Domain                                                |
| [sqlean](https://github.com/OneLuaPro/sqlean)                | The ultimate set of SQLite extensions                        | [lsqlite3](https://github.com/OneLuaPro/lsqlite3)            | `v0.28.1-9-gd134592`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

## Building OneLuaPro

See instructions in **OneLuaPro** head repository: https://github.com/OneLuaPro/OneLuaPro

## Licenses

See `https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE.txt`.
