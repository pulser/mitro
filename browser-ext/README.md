browser-ext
===========

Setup 
=====

1. (Mac): [Install Homebrew](http://mxcl.github.io/homebrew/). Run `brew install node` or download node from the web. (apt-get is too old).

1. (Ubuntu Linux): Install dependencies for build, and use a symlink to handle build.sh looking for node being installed as "node" rather than "nodejs"

        sudo apt-get install nodejs npm openjdk-7-jdk git
        sudo ln -s /usr/bin/nodejs /usr/bin/node

2. Get node dependencies and crypto dependencies (run this once)

        git clone git@github.com:mitro-co/browser-ext.git
        cd browser-ext/api; ./build.sh



3. Build

        cd browser-ext/login && make

4. Go to [chrome://extensions](chrome://extensions). Check the developer mode box.

5. Click Load unpacked extension -> `browser-ext/login/build/chrome/release`



If you want to run regression tests:
====================================

This requires server code.

1. Checkout dependencies in the directory above `browser-ext`:

        git clone git@github.com:mitro-co/mitro-core.git

2. Symlink mitro-core to `browser-ext/api/server`:

        ln -s ../../mitro-core/ browser-ext/api/server

3. Run regression tests:

        cd api/js/cli && ./runtests.sh


Notes
=====

We can't use symlinks to edit files in place because Chrome does not load symlinked resources:

http://code.google.com/p/chromium/issues/detail?id=27185


Make Configurations
===================

There are multiple build configurations set up (see configuration files of the form `X.release.conf` or similar. Select the appropriate release type through the appropriate make command

Build the "release" configuration for Chrome (output as a CRX), and attempt to do some testing

    make

Build the "release" configuration for Chrome (output as a folder)

    make release

Build the "debug" configuration for Chrome (output as a folder)

    make debug
    
Build the "release" configuration for Firefox (output as XPI)

    make firefox

Build the "debug" configuration for Firefox (output as XPI)

    make firefox-debug
    
Build the "release" configuration for Safari (output as a folder)

    make safari

Build the "debug" configuration for Safari (output as a folder)

    make safari-debug
    
Build the "release" configuration for a webpage (output as a folder)

    make webpage
    
Build the "debug" configuration for a webpage (output as a folder)

    make webpage-debug

Cleans the build directory

    make clean
    
