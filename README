Patching a Package
==================

Let's suppose you need to patch a package because it would not compile on
android. A common problem is that config.guess and config.sub are too old
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
just edit the file and rerun quilt refresh.
