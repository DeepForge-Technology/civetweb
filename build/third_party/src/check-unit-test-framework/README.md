# About Check

[![Travis Build Status](https://api.travis-ci.com/civetweb/check.svg?branch=master)](https://app.travis-ci.com/github/civetweb/check)

Check is a unit testing framework for C. It features a simple interface
for defining unit tests, putting little in the way of the
developer. Tests are run in a separate address space, so Check can
catch both assertion failures and code errors that cause segmentation
faults or other signals. The output from unit tests can be used within
source code editors and IDEs.

See https://libcheck.github.io/check for more information, including a
tutorial.  The tutorial is also available as `info check`.

# Installation

Check has the following dependencies:

* [automake](https://www.gnu.org/software/automake/)-1.9.6 (1.11.3 on OS X if you are using /usr/bin/ar)
* [autoconf](https://www.gnu.org/software/autoconf/)-2.59
* [libtool](https://www.gnu.org/software/libtool/)-1.5.22
* [pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config/)-0.20
* [texinfo](https://www.gnu.org/software/texinfo/)-4.7 (for documentation)
* tetex-bin (or any texinfo-compatible TeX installation, for documentation)
* POSIX [sed](https://en.wikipedia.org/wiki/Sed)

The versions specified may be higher than those actually needed.

## autoconf

    $ autoreconf --install
    $ ./configure
    $ make
    $ make check
    $ make install

in this directory to set everything up.  autoreconf calls all of the
necessary tools for you, like autoconf, automake, autoheader, etc.  If
you ever change something during development, run autoreconf again
(without --install), and it will perform the minimum set of actions
necessary.

## cmake

    $ mkdir build
    $ cd build
    $ cmake ../
    $ make
    $ CTEST_OUTPUT_ON_FAILURE=1 make test

# Linking against Check

Check uses variadic macros in check.h, and the strict C90 options for
gcc will complain about this.  In gcc 4.0 and above you can turn this
off explicitly with `-Wno-variadic-macros`.  In a future API it would be
nice to eliminate these macros.
