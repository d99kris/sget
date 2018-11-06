Sget
====

| **Linux + Mac** |
|-----------------|
| [![Build status](https://travis-ci.org/d99kris/sget.svg?branch=master)](https://travis-ci.org/d99kris/sget) |

Sget (source get) - is a small utility facilitating installation of software from source
packages, by automating the process of downloading the source and doing configure, make,
sudo make install.

It supports installation from a remote Git/Subversion repository, an URL to a source package,
a local file path to a source package or a local directory path.

Most common package/archive formats (tar, zip, rar, etc) are supported.

It supports plain Makefile as well as several generators: autogen, cmake, configure, qmake

Example Usage
=============

    $ sudo sget install https://github.com/tmux/tmux

Why
===
Standard package managers (apt, brew, yum, etc) handling dependency resolution,
updates, etc is generally the preferred way to install software. The sget
utility mainly caters for installation of softwares not (yet) available through
package managers. 

Supported Platforms
===================
Sget should work on most Linux and macOS systems.

Installation
============

Using sget
----------

    wget -qO - https://raw.githubusercontent.com/d99kris/sget/master/sget | sudo bash -s -- install https://github.com/d99kris/sget

From source
-----------
1. Download source:

    git clone https://github.com/d99kris/sget && cd sget

2. From source using sget itself:

    sudo ./sget install . 

Alternatively install and build manually:

    mkdir -p build && cd build && cmake .. && make -s && sudo make install

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

    sget install https://github.com/tmux/tmux           # install from repository

    sget install ~/Downloads/tmux-2.8.tar.gz            # install local package

    sget install ~/tmux-2.8                             # install local dir

    sget remove https://github.com/tmux/tmux            # uninstall

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

