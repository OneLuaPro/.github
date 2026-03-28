# OneLuaPro
**OneLuaPro** is ...

- a portable, monolithic, and curated distribution of the [Lua](http://www.lua.org/) programming language for the Windows operation system,
- natively built with Intel<sup>®</sup> oneAPI C++ compiler,
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

## Hardware Requirements & Performance

**OneLuaPro** is optimized for high-performance numerical computing using modern CPU instruction sets. To achieve the best balance between compatibility and speed, the complete distribution is compiled with **Intel oneAPI C-compiler** using multi-target dispatching.

### Minimum Requirements

- **Intel:** 2nd Generation Core processors (Sandy Bridge, 2011) or newer,
- **AMD:** Bulldozer-based processors (FX-series, 2011) or newer,
- **OS:** Windows 7 SP1, Windows 10, or Windows 11 (required for AVX state management).

> [!IMPORTANT]
>
> CPUs older than 2011 (e.g., Core 2 Duo, 1st Gen i5) are not supported and will result in an "Illegal Instruction" error.

### Automatic Hardware Acceleration
All OneLuaPro binaries feature **Dynamic Dispatch**, meaning they automatically detect your CPU's capabilities at runtime and activate the fastest available code path:

- **AVX (Standard):** Provides 256-bit vectorization on older systems (e.g., i5-2xxx/3xxx),
- **AVX2 (Advanced):** Enabled automatically on Intel Haswell (4th Gen) and newer, as well as all AMD Ryzen processors,
- **AVX-512 (Ultra):** Leverages 512-bit registers on modern Intel Xeon and high-end Core i7/i9 processors (11th Gen+) for maximum throughput.

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

> [!TIP]
>
> This section applies to all OneLuaPro releases prior to **v5.5.0.0**. Starting with this version, all runtime libraries are statically linked.

The provided installer can be used on Windows 7 but may have some flaws, which can be fixed manually:

- In case the installer complains about `PATH` environment variable being too long to be extended for OneLuaPro, install without updating the variable and edit `PATH` manually by adding `C:\Program Files\OneLuaPro\bin` (or the installation directory of your choice) to the content of `PATH`.
- ZeroBraneStudio may complain about a missing DLL (`vcruntime140_1.dll`). Simply copy this DLL from `C:\Program Files\OneLuaPro\bin` to `C:\Program Files\OneLuaPro\opt\ZeroBraneStudio`. This flaw may also occur after installation using the provided ZIP-archive.

## OneLuaPro Help Center

Documentation and reference manuals are available via the **OneLuaPro Help Center**. A link to the Help Center is automatically added to the **Start menu entry**. You can also access it directly at `<INSTALL_PATH>\share\doc\index.html`.

## Contents of the OneLuaPro Distribution

**OneLuaPro** comprises not only the Lua programming language binaries, but also a number of mature and widely-used extensions (modules) in their respective most recent version, all of which tailored to **OneLuaPro**'s needs. All version numbers follow the `v[Base]-[Commits]-[Hash]` format: The first part indicates the **stable base version**, followed by the **number of additional changes** since the last release, and a short **identifier (hash)** of the exact source code.

| Extension                                                    | Purpose                                                      | Version                 | License                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------- | ------------------------------------------------------------ |
| [Lua](https://github.com/KritzelKratzel/lua)                 | The Lua Programming Language                                 | `v5.5.0-5-g4154493`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [distro](https://github.com/OneLuaPro/distro)                | OneLuaPro Distro Information                                 | `v2.1.0`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaSocket](https://github.com/OneLuaPro/luasocket)          | Network support for the Lua language                         | `v3.1.0-72-gd6bd8b5`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [librs232](https://github.com/OneLuaPro/librs232)            | Multi-platform library for serial communications over RS-232 (serial port) | `v1.0.3-119-gda35def`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaFileSystem](https://github.com/OneLuaPro/luafilesystem)  | Complements the set of functions related to file systems offered by the standard Lua distribution | `v1.9.0-10-g707cb06`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [argparse](https://github.com/OneLuaPro/argparse)            | Feature-rich command line parser for Lua inspired by argparse for Python | `v0.7.1-13-gdebe947`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Luacheck](https://github.com/OneLuaPro/luacheck)            | Static analyzer and a linter for Lua. It detects various issues such as usage of undefined global variables, unused variables and values, accessing uninitialized variables, unreachable code and more. | `v1.2.0-40-g68c84bd`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsleep](https://github.com/OneLuaPro/lsleep)                | Adds the missing `sleep()` and `usleep()` functions to Lua.  | `v1.05-6-g531d702`      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-ffi](https://github.com/OneLuaPro/lua-ffi)              | A portable lightweight C foreign function interface (FFI) for Lua, based on libffi | `v1.1.0-31-ga8ae836`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [MoonUSB](https://github.com/OneLuaPro/moonusb)              | Lua binding library for libusb, allowing applications to access and use USB devices. | `v0.1-30-gebc05a5`      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luv](https://github.com/OneLuaPro/luv)                      | Bare libuv bindings for Lua                                  | `v1.52.1-0-30-gb115c8a` | [![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) |
| [lanes](https://github.com/OneLuaPro/lanes)                  | Lua Lanes - multithreading in Lua                            | `v4.0.0-42-g70389ef`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luaping](https://github.com/OneLuaPro/luaping)              | The missing ping command for Lua                             | `v1.1.1`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luadaqmx](https://github.com/OneLuaPro/luadaqmx)            | OneLuaPro gateway to National Instrument's DAQmx driver      | `v0.1.2`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua4882](https://github.com/OneLuaPro/lua4882)              | OneLuaPro gateway to National Instrument's NI-488.2 (GPIB) driver | `v1.2.3`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LPeg](https://github.com/OneLuaPro/LPeg)                    | Parsing Expression Grammars For OneLuaPro                    | `v1.1.0-6-g645d404`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [wxLua](https://github.com/OneLuaPro/wxlua)                  | wxLua is a Lua wrapper for the cross-platform wxWidgets GUI library | `v3.2.0.2-18-gc5e0cbb`  | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [ZeroBrane Studio](https://github.com/OneLuaPro/ZeroBraneStudio) | lightweight cross-platform Lua IDE with code completion, syntax highlighting, remote debugger, code analyzer, live coding, and debugging support | `v2.01-12-g14b97a19`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Penlight](https://github.com/OneLuaPro/Penlight)            | A set of pure Lua libraries focusing on input data handling (such as reading configuration files), functional programming (such as map, reduce, placeholder expressions,etc), and OS path management. Much of the functionality is inspired by the Python standard libraries. | `v1.15.0-19-g9ece351`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lcomplex](https://github.com/OneLuaPro/lcomplex)            | Lua complex numbers support module                           | `v1.1.0`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luaSGF](https://github.com/OneLuaPro/luaSGF)                | Lua bindings for the Savitzky-Golay-Filter Implementation for data filtering or smoothing | `v2.0.1`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luacrc32c](https://github.com/OneLuaPro/luacrc32c)          | Lua bindings for Google's CRC-32C implementation             | `v1.0.1`                | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-zlib](https://github.com/OneLuaPro/lua-zlib)            | Simple streaming interface to zlib for Lua                   | `v1.4-6-gdb5b875`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-cjson](https://github.com/OneLuaPro/lua-cjson)          | Fast JSON encoding/parsing module for Lua                    | `2.1.0.16-16-g7eee8b5`  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luasec](https://github.com/OneLuaPro/luasec)                | Secure connections to any Lua application or script          | `v1.3.2-5-gc02dd57`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-openssl](https://github.com/OneLuaPro/lua-openssl)      | OpenSSL bindings for Lua                                     | `0.11.0-3-25-gd068708`  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [ldoc](https://github.com/OneLuaPro/ldoc)                    | Lua documentation generator which can also process C extension source files | `v1.5.0-23-g38be0fa`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luasystem](https://github.com/OneLuaPro/luasystem)          | Platform independent system calls for Lua                    | `v0.7.0-7-gf61f8f5`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua_cliargs](https://github.com/OneLuaPro/lua_cliargs)      | Command-line argument parsing module for Lua                 | `v3.0.2-7-gc4cf5f0`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [dkjson](https://github.com/OneLuaPro/dkjson)                | JSON module written in Lua                                   | `v2.8-1-gf1b7c93`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [say](https://github.com/OneLuaPro/say)                      | Lua string hashing library, useful for internationalization  | `v1.4.1-2-ge4436ea`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luassert](https://github.com/OneLuaPro/luassert)            | Assertion library for Lua                                    | `v1.9.0-13-g0e2569d`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [mediator_lua](https://github.com/OneLuaPro/mediator_lua)    | Mediator pattern implementation for pub-sub management       | `v1.1.2-0-8-gefa5daf`   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-term](https://github.com/OneLuaPro/lua-term)            | Terminal operations for Lua                                  | `v0.8-7-g75066e0`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-utf8](https://github.com/OneLuaPro/luautf8)             | UTF-8 support module for Lua                                 | `v0.2.1-7-g3ae0b91`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [inifile](https://github.com/OneLuaPro/inifile)              | A simple and complete ini-File Parser for Lua                | `v1.1-2-gf7b742d`       | [![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause) |
| [busted](https://github.com/OneLuaPro/busted)                | Elegant Lua unit testing                                     | `v2.3.0-9-gfddc67b`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lunit](https://github.com/OneLuaPro/lunit)                  | Unit testing for Lua                                         | `v0.8.1-1-g61e9b3a`     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsqlite3](https://github.com/OneLuaPro/lsqlite3)            | Extended lsqlite3 module for Lua: A lightweight SQLite3 wrapper featuring the complete SQLean power-pack | `v0.9.6-2`              | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Lua-cURLv3](https://github.com/OneLuaPro/Lua-cURLv3)        | Lua binding to libcurl                                       | `v0.3.13-6-gbd885bd`    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

👉 Are you missing an important Lua extension or Lua library? Please let us know [here](https://github.com/orgs/OneLuaPro/discussions/categories/ideas). 👈

## Dependencies

**OneLuaPro** uses the following libraries:

| Dependency                                                   | Purpose                                                      | Used by                                                      | Version                    | License                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------- | ------------------------------------------------------------ |
| [libffi](https://github.com/OneLuaPro/libffi)                | A Portable Foreign Function Interface Library.               | [lua-ffi](https://github.com/OneLuaPro/lua-ffi)              | `v3.5.2-34-g26c59e0`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libusb](https://github.com/OneLuaPro/libusb)                | A library for USB device access.                             | [MoonUSB](https://github.com/OneLuaPro/moonusb)              | `v1.0.30-rc1-38-gaea2f056` | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [libuv](https://github.com/libuv/libuv)                      | Cross-platform asynchronous I/O                              | [luv](https://github.com/OneLuaPro/luv)                      | `v1.52.1`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [NI‑DAQmx](https://www.ni.com/en/support/downloads/drivers/download.ni-daq-mx.html) | Provides a high‑performance, unified API for controlling and acquiring data from National Instruments measurement hardware | [luadaqmx](https://github.com/OneLuaPro/luadaqmx)            | `2025 Q4`                  | [See here](https://www.ni.com/en/about-ni/legal/software-license-agreement.html) |
| [NI-488.2](https://www.ni.com/en/support/downloads/drivers/download.ni-488-2.html) | Provides support for customers using NI GPIB controllers and NI embedded controllers with GPIB ports | [lua4882](https://github.com/OneLuaPro/lua4882)              | `2025 Q4`                  | [See here](https://www.ni.com/en/about-ni/legal/software-license-agreement.html) |
| [wxWidgets](https://github.com/wxWidgets/wxWidgets)          | wxWidgets is a free and open source cross-platform C++ framework for writing advanced GUI applications using native controls | [wxLua](https://github.com/pkulchenko/wxlua)                 | `v3.2.10`                  | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [Savitzky-Golay-Filter](https://github.com/OneLuaPro/Savitzky-Golay-Filter) | C implementation of Least-Squares Smoothing and Differentiation by the Convolution (Savitzky-Golay) Method | [luaSGF](https://github.com/OneLuaPro/luaSGF)                | `v2.0-16-gabed543`         | [![License](https://img.shields.io/badge/License-BSD_2--Clause-orange.svg)](https://opensource.org/licenses/BSD-2-Clause) |
| [crc32c](https://github.com/google/crc32c)                   | Google's implantation of the CRC-32C hashing algorithm       | [luacrc32c](https://github.com/OneLuaPro/luacrc32c)          | `v1.1.2-12-g10693bf`       | [![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause) |
| [zlib-ng](https://github.com/zlib-ng/zlib-ng)                | zlib replacement with optimizations for "next generation" systems | [lua-zlib](https://github.com/OneLuaPro/lua-zlib)            | `v2.3.3`                   | [![License: Zlib](https://img.shields.io/badge/License-Zlib-lightgrey.svg)](https://opensource.org/licenses/Zlib) |
| [dlfcn-win32](https://github.com/dlfcn-win32/dlfcn-win32)    | dlfcn-win32 is an implementation of `dlfcn` for Windows      | Prerequisite for building [lua-ffi](https://github.com/OneLuaPro/lua-ffi) | `v1.4.2-19-g614073d`       | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libressl](https://www.libressl.org/)                        | An [open-source](https://en.wikipedia.org/wiki/Open-source_software) implementation of the [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) protocol | [luasec](https://github.com/OneLuaPro/luasec), [lua-openssl](https://github.com/OneLuaPro/lua-openssl) | `v4.2.1-1-gc88f4da`        | [See here](https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE.txt) |
| [SQLite](https://www.sqlite.org/)                            | SQL database engine                                          | [sqlean](https://github.com/OneLuaPro/sqlean)                | `v3.51.3`                  | Public Domain                                                |
| [sqlean](https://github.com/OneLuaPro/sqlean)                | The ultimate set of SQLite extensions                        | [lsqlite3](https://github.com/OneLuaPro/lsqlite3)            | `v0.28.1-12-g4141d89`      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [brotli](https://github.com/google/brotli)                   | Brotli compression format                                    | [curl](https://github.com/curl/curl)                         | `v1.2.0`                   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [zstd](https://github.com/facebook/zstd)                     | Fast real-time compression algorithm                         | [curl](https://github.com/curl/curl)                         | `v1.5.7`                   | [![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause) |
| [nghttp2](https://github.com/nghttp2/nghttp2)                | HTTP/2 C Library and tools                                   | [curl](https://github.com/curl/curl)                         | `v1.68.1`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [ngtcp2](https://github.com/ngtcp2/ngtcp2)                   | IETF QUIC protocol implementation                            | [curl](https://github.com/curl/curl)                         | `v1.21.0`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [nghttp3](https://github.com/ngtcp2/nghttp3)                 | HTTP/3 library written in C                                  | [curl](https://github.com/curl/curl)                         | `v1.15.0`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [curl](https://github.com/curl/curl)                         | Library for transferring data with URL syntax                | [Lua-cURLv3](https://github.com/OneLuaPro/Lua-cURLv3)        | `v8.19.0`                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

## Building OneLuaPro

See instructions in **OneLuaPro** head repository: https://github.com/OneLuaPro/OneLuaPro

## Licenses

See `https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE.txt`.
