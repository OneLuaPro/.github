# OneLuaPro
**OneLuaPro** is ...

- a portable, monolithic, and curated distribution of the [Lua](http://www.lua.org/) programming language for the Windows operation system,
- natively built with MSVC compilers,
- provided as `x64` signed binaries and signed installer for Windows 7 to Windows 11,
- targeted for corporate application scenarios on computers without permanent Internet access.

**OneLuaPro** is not ...

- made for compatibility with Lua package managers like `luarocks`.

**OneLuaPro** supports ...

- easy entry into the Lua world by providing the [ZeroBrane Studio](https://github.com/pkulchenko/ZeroBraneStudio) Integrated Development Environment (IDE) and the [luacheck](https://github.com/OneLuaPro/luacheck) linter for static code analysis.

**OneLuaPro** can ...

- be built with minimum effort and toolchain-footprint as all its components are prepared for the [CMake](https://cmake.org/) build infrastructure,
- be installed entirely without administrative privileges using the released zip-archives,
- be installed or uninstalled using the signed installer package.

## Download and Installation

Download **OneLuaPro** here: https://github.com/OneLuaPro/OneLuaPro/releases

### Install OneLuaPro using the provided Installer

Simply double-click the installer and follow the installer wizard. The installer requires administrative rights. All executables, all DLL, the installer as well as the uninstaller are signed with a valid and trustworthy certificate. The installer also creates entries in the Windows Start Menu and updates the `PATH`-variable.

### Install OneLuaPro using the provided ZIP-Archive

Unpack downloaded zip-archive into a directory of your choice. The suggested installation path is `c:\Apps`, which is typically accessible without administrative rights. Manually extend `PATH`-variable to the `bin` directory of your installation, e.g. `C:\Apps\OneLuaPro-<VERSION>-Win-x64\bin`. Documentation and code examples are located in `<OneLuaPro_Install_Path>\share\doc`. All executables, all DLL within the ZIP-archive are signed with a valid and trustworthy certificate.

### Notes for Installation on Windows 7

The provided installer can be used on Windows 7 but may have some flaws, which can be fixed manually:

- In case the installer complains about `PATH` environment variable being too long to be extended for OneLuaPro, install without updating the variable and edit `PATH` manually by adding `C:\Program Files\OneLuaPro\bin` (or the installation directory of your choice) to the content of `PATH`.
- ZeroBraneStudio may complain about a missing DLL (`vcruntime140_1.dll`). Simply copy this DLL from `C:\Program Files\OneLuaPro\bin` to `C:\Program Files\OneLuaPro\opt\ZeroBraneStudio`. This flaw may also occur after installation using the provided ZIP-archive.

## Contents of the OneLuaPro Distribution

**OneLuaPro** comprises not only the Lua programming language binaries, but also a number of mature and widely-used extensions (modules) in their respective most recent version, all of which tailored to **OneLuaPro**'s needs:

| Extension                                                    | Purpose                                                      | Version                                   | License                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------- | ------------------------------------------------------------ |
| [Lua](https://github.com/KritzelKratzel/lua)                 | The Lua Programming Language                                 | v5.4.7                                    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaSocket](https://github.com/OneLuaPro/luasocket)          | Network support for the Lua language                         | v3.1.0 with commits until Jun 29, 2024    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [librs232](https://github.com/OneLuaPro/librs232)            | Multi-platform library for serial communications over RS-232 (serial port) | v1.0.3 with commits until Oct 12, 2023    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaFileSystem](https://github.com/OneLuaPro/luafilesystem)  | Complements the set of functions related to file systems offered by the standard Lua distribution | v1.8.0 with commits until  Dec 13, 2023   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [argparse](https://github.com/OneLuaPro/argparse)            | Feature-rich command line parser for Lua inspired by argparse for Python | v0.7.1                                    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Luacheck](https://github.com/OneLuaPro/luacheck)            | Static analyzer and a linter for Lua. It detects various issues such as usage of undefined global variables, unused variables and values, accessing uninitialized variables, unreachable code and more. | v1.2.0 with commits until Aug 29, 2024    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsleep](https://github.com/OneLuaPro/lsleep)                | Adds the missing `sleep()` and `usleep()` functions to Lua.  | v1.05                                     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libffi](https://github.com/OneLuaPro/libffi)                | A Portable Foreign Function Interface Library.               | v3.4.6 with commits until  Sep 20, 2024   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua-ffi](https://github.com/OneLuaPro/lua-ffi)              | A portable lightweight C foreign function interface (FFI) for Lua, based on libffi | v1.0.0 with commits until Aug 18, 2024    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libusb](https://github.com/OneLuaPro/libusb)                | A library for USB device access.                             | v1.0.27 with commits until Jul 31, 2024   | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [MoonUSB](https://github.com/OneLuaPro/moonusb)              | Lua binding library for libusb, allowing applications to access and use USB devices. | v0.1 with commits until Jul 25, 2023      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libuv](https://github.com/libuv/libuv)                      | Cross-platform asynchronous I/O                              | v1.49.1                                   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luv](https://github.com/OneLuaPro/luv)                      | Bare libuv bindings for Lua                                  | v1.48.0-2 with commits until Oct 11, 2024 | [![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) |
| [lanes](https://github.com/OneLuaPro/lanes)                  | Lua Lanes - multithreading in Lua                            | v4.0.0 with commits until Oct 9, 2024     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luaping](https://github.com/OneLuaPro/luaping)              | The missing ping command for Lua                             | v1.1                                      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luadaqmx](https://github.com/OneLuaPro/luadaqmx)            | OneLuaPro gateway to National Instrument's DAQmx driver      | v0.1 with commits until Oct 13, 2024      | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lua4882](https://github.com/OneLuaPro/lua4882)              | OneLuaPro gateway to National Instrument's NI-488.2 (GPIB) driver | v1.2.1                                    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LPeg](https://github.com/OneLuaPro/LPeg)                    | Parsing Expression Grammars For OneLuaPro                    | v1.1.0                                    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [wxWidgets](https://github.com/wxWidgets/wxWidgets)          | wxWidgets is a free and open source cross-platform C++ framework for writing advanced GUI applications using native controls | v3.2.6                                    | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [wxLua](https://github.com/pkulchenko/wxlua)                 | wxLua is a Lua wrapper for the cross-platform wxWidgets GUI library | v3.2.0.2 with commits until Sep 4, 2023   | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [ZeroBrane Studio](https://github.com/OneLuaPro/ZeroBraneStudio) | lightweight cross-platform Lua IDE with code completion, syntax highlighting, remote debugger, code analyzer, live coding, and debugging support | v2.01 with commits until May 20, 2024     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

## Building OneLuaPro

See instructions in **OneLuaPro** head repository: https://github.com/OneLuaPro/OneLuaPro

## License

See `https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE`.
