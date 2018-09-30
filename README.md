Sget
====

Sget (source get) - install software from source packages.

Example Usage
=============

    $ sudo sget install https://github.com/d99kris/heapusage

Why?
====
Standard package managers (apt, brew, yum, etc) handling dependency resolution,
updates, etc is generally the preferred way to install software. The sget
utility mainly caters for installation of softwares not (yet) available through
package managers. 

Supported Platforms
===================
Sget should work on most Linux and macOS systems.

Installation
============
Download sget script:

    curl -o /tmp/sget https://raw.githubusercontent.com/d99kris/sget/master/sget

Set executable flag:

    chmod +x /tmp/sget

Use sget script to install sget (may omit sudo for macOS):

    sudo /tmp/sget install https://github.com/d99kris/sget

Delete sget script:

    rm /tmp/sget

Usage
=====

General usage syntax:

    [sudo] sget [--prefix PREFIX] install PKG [PKG ...]
    [sudo] sget [--prefix PREFIX] remove PKG [PKG ...]
    sget --help
    sget --version

Options:

    PKG          web link to a version controlled (Subversion or Git) 
                 repository or web link to a source code package, or path 
                 to a locally stored source code package
    install      builds and installs specified package
    remove       uninstalls specified package
    PREFIX       specifies an alternative installation prefix path
    --help       display this help and exit
    --version    output version information and exit

Examples:

    sget install https://github.com/d99kris/heapusage   # install from repository

    sget install ~/Downloads/heapusage-master.zip       # install local package

    sget remove https://github.com/d99kris/heapusage    # uninstall

Technical Details
=================
The test suite can be run using these commands:

    mkdir -p build && cd build && cmake .. && make -s && ctest --output-on-failure

License
=======
Sget is distributed under the MIT license. See LICENSE file.

Keywords
========
install from source,linux,macos

