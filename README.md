Android Build Scripts for Native Libraries
==========================================

This repository contains build scripts and patches that can be used to build
selected native libraries using the Android Native Development Toolkit (NDK). 
Often, existing libraries need small changes to the build system or simple
tweaks to the source code to be usable on Android. This repository collects
such tweaks for selected packages.

Prerequisites
-------------
You will need the Android tools or SDK, as well as the Android NDK to build
the packages. 
  1. Install Android tools
  1. Install Android NDK into the directory of Android tools and rename to ndk
  1. Install cmake, git, and ant
  1. Set path to something like: PATH=SDK/tools:SDK/platform-tools:SDK/ndk:$PATH

Build
-----
To build all libraries, make sure the Android NDK is on your path and run `build-all`
in the top-level directory. The script will download release tarballs for individual
libraries from the internet.

Add a Library
-------------
Let's suppose you need to patch a package because it would not compile on
android. A common problem is that `config.guess` and `config.sub` are too old
and don't recognize the android platform.

Enter the package's directory and create patches subdirectory:

    $ mkdir patches

Download config.guess and config.sub from savannah. Untar the package's
source tarball.

Create a new patch:

    $ quilt new 01-config_guess.patch
    $ quilt add package/config.guess

Now replace the file with the downloaded version, then refresh the patch:

    $ quilt refresh

After that repeat the same for config.sub. At the end delete the extracted
source tarball and the subdirectory .pc and try to build the package.

Each time you want to add another modification to the topmost patch you can
just edit the file and rerun `quilt refresh`.
