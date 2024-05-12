# OneLuaPro
**OneLuaPro** is ...

- a portable, monolithic, and curated distribution of the [Lua](http://www.lua.org/) programming language for the Windows operation system (Windows 10 on upwards),
- natively build with MSVC compilers, without the unnecessary overhead of a complete MS Visual Studio installation,
- provided as `Win32` and `x64` binaries,
- targeted for corporate application scenarios on computers without permanent Internet access.

**OneLuaPro** is not ...

- made for compatibility with Lua package managers like `luarocks`.

**OneLuaPro** does not ...

- provide a complete Integrated Development Environment (IDE). Instead, it is designed to have a small, portable installation footprint. However, the [luacheck](https://github.com/OneLuaPro/luacheck) linter for static code analysis is included.

**OneLuaPro** can ...

- be built and installed with minimum effort and toolchain-footprint as all its components are prepared for the [CMake](https://cmake.org/) build infrastructure,
- be installed entirely without administrative privileges using the released zip-archives.

## Download and Installation

Download **OneLuaPro** here: https://github.com/OneLuaPro/OneLuaPro/releases

Unpack downloaded zip-archive into a directory of your choice. The suggested installation path is `c:\Apps`, which is typically accessible without administrative rights. Manually extend `PATH`-variable to the `bin` directory of your installation, e.g. `C:\Apps\OneLuaPro-Win32\bin` or `C:\Apps\OneLuaPro-x64\bin`. Documentation and code examples (if available) are located in `<OneLuaPro_Install_Path>\share\doc`.

## Building OneLuaPro

See instructions in **OneLuaPro** head repository: https://github.com/OneLuaPro/OneLuaPro

## Contents of the OneLuaPro Distribution

**OneLuaPro** comprises not only the Lua programming language binaries, but also a number of mature and widely-used extensions in their respective most recent version, all of which tailored to **OneLuaPro**'s needs:

| Extension                                                   | Purpose                                                      | Version                                 | License                                                      |
| ----------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------- | ------------------------------------------------------------ |
| [Lua](https://github.com/KritzelKratzel/lua)                | The Lua Programming Language                                 | 5.4.6                                   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaSocket](https://github.com/OneLuaPro/luasocket)         | Network support for the Lua language                         | 3.1.0 with commits until Oct 27, 2023   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [librs232](https://github.com/OneLuaPro/librs232)           | Multi-platform library for serial communications over RS-232 (serial port) | 1.0.3 with commits until Oct 12, 2023   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [LuaFileSystem](https://github.com/OneLuaPro/luafilesystem) | Complements the set of functions related to file systems offered by the standard Lua distribution | 1.8.0 with commits until  Dec 13, 2023  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [argparse](https://github.com/OneLuaPro/argparse)           | Feature-rich command line parser for Lua inspired by argparse for Python | 0.7.1                                   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [Luacheck](https://github.com/OneLuaPro/luacheck)           | Static analyzer and a linter for Lua. It detects various issues such as usage of undefined global variables, unused variables and values, accessing uninitialized variables, unreachable code and more. | 1.1.2                                   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [lsleep](https://github.com/OneLuaPro/lsleep)               | Adds the missing `sleep()` and `usleep()` functions to Lua.  | 1.05                                    | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libffi](https://github.com/OneLuaPro/libffi)               | A Portable Foreign Function Interface Library.               | 3.4.6 with commits until Mar 19, 2024   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libusb](https://github.com/OneLuaPro/libusb)               | A library for USB device access.                             | 1.0.27                                  | [![License: LGPL v3](https://img.shields.io/badge/License-LGPL_v3-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0) |
| [MoonUSB](https://github.com/OneLuaPro/moonusb)             | Lua binding library for libusb, allowing applications to access and use USB devices. | 0.1 with commits until Jul 25, 2023     | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [libuv](https://github.com/libuv/libuv)                     | Cross-platform asynchronous I/O                              | 1.48.0                                  | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |
| [luv](https://github.com/OneLuaPro/luv)                     | Bare libuv bindings for Lua                                  | 1.48.0-2 with commits until Mar 2, 2024 | [![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) |
| [lanes](https://github.com/OneLuaPro/lanes)                 | Lua Lanes - multithreading in Lua                            | 3.17.0 with commits until May 7, 2024   | [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) |

## License

See `https://github.com/OneLuaPro/OneLuaPro/blob/main/LICENSE`.
