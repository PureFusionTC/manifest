PureFusionTC TOOLCHAIN MANIFEST
===========

What is PureFusionTC?  PureFusionTX is a toolchain closely based on AOSP but with latest merges to toolchain components from gnu.org. Patches will be used from linaro or aosp as seen fit to improve performance but build folder will always stay as close to aosp as possible.

To build all you have to do is sync sources:

    $ repo init -u https://github.com/PureFusionTC/manifest.git -b master 

    Then to sync up:

    $ repo sync -f -j8 --force-sync --no-clone-bundle --no-tags

Also make sure to install dependencies (while you wait for it to sync)

    sudo apt-get install flex bison ncurses-dev texinfo gcc gperf patch libtool automake g++ libncurses5-dev gawk subversion expat libexpat1-dev python-all-dev binutils-static libgcc1:i386 bc libcloog-isl-dev libcap-dev autoconf libgmp-dev build-essential gcc-multilib g++-multilib pkg-config libmpc-dev libmpfr-dev

**Note: I also have an entire android environment setup as well apart from these.  I currently use Ubuntu 15.04 repos on my build server.  You may be missing dependencies that already came preinstalled with my android environment setup.  I'll let you figure out what you need for any other distro you may be running. Usually though errors will tell you the dependency you are missing.**


PureFusionTC TOOLCHAINS also make use of multilib support on androideabi (ROM) toolchains. In order to enable mutilib on ubuntu there's some header files that need to be linked from asm-generic which you can easily do by running the following command from terminal:

    sudo ln -s /usr/include/asm-generic /usr/include/asm;


Once you have everything synced locally go to the scripts directory and run any of the scripts (ie cd scripts then bash arm-eabi-4.9).  There are many different cpu tuning options or if you don't know or are planning on building for many different cpus make sure to run the scripts that do not have cortex labels. All scripts will checkout the needed GCC version before build so don't worry which branch you ran repo init with you can build them all using master branch.

When you finished running the script you will find a toolchain located wherever the script tells you it is found.  Usually in the toolchain_repo_init_location/out/ and labeled accordingly.

Enjoy!
