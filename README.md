BitZeny Core integration/staging tree
=====================================

http://bitzeny.org (old website)  
http:// (New website) << in preparation  
http://bitzeny.info (Forum)

* Copyright (c) 2014      BitZeny Core Developers
* Copyright (c) 2009-2014 Bitcoin Core Developers
* Copyright (c) 2013-2014 DarkCoin Developers (DarkGravityWave3)
* Copyright (c) 2014      Alexander Peslyak   (Yescrypt)

License
-------

BitZeny Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see http://opensource.org/licenses/MIT.

## Overview 

symbol

![Representation](https://github.com/BitzenyDevTeam/bitzeny-copy/blob/z1.1.x/src/qt/res/icons/bitcoin.png?raw=true)

### concept

Simple and concise.  
It is as sharp as **Katana**.

### Load map

* ~~New wallet~~
* ~~Online Wallet~~
* ~~Mining pool~~ 
* ~~Forum~~
* zenyhive(coinhive)
* electrum-zeny
* Exchange listing
	* ~~C-CEX~~
    * ~~Novaexchange~~
	* Tradesatoshi >> Vote now
    * Yo-bit
    * coinexchange
    * cryptopia
    * Bleutrade
    * Bittrex
    * Poloniex
* Accessory function	
* Segwit attachment
* Anonymous attachment
* DEX attachment
* Asset attachment
* Crosschain platform attachment


Build bitzenyd on Ubuntu 16.04
-------------------

    sudo apt-get install build-essential
    sudo apt-get install libtool autotools-dev autoconf
    sudo apt-get install libssl-dev
    sudo apt-get install libboost-all-dev
    sudo apt-get install pkg-config
    sudo add-apt-repository ppa:bitcoin/bitcoin
    sudo apt-get update
    sudo apt-get install libdb4.8-dev
    sudo apt-get install libdb4.8++-dev
    
    git clone https://github.com/BitzenyCoreDevelopers/bitzeny.git
    cd bitzeny
    ./autogen.sh
    ./configure --without-miniupnpc --without-gui --disable-tests
    make

Development tips and tricks
---------------------------

**compiling for debugging**

Run configure with the --enable-debug option, then make. Or run configure with
CXXFLAGS="-g -ggdb -O0" or whatever debug flags you need.

**debug.log**

If the code is behaving strangely, take a look in the debug.log file in the data directory;
error and debugging message are written there.

The -debug=... command-line option controls debugging; running with just -debug will turn
on all categories (and give you a very large debug.log file).

The Qt code routes qDebug() output to debug.log under category "qt": run with -debug=qt
to see it.

**testnet and regtest modes**

Run with the -testnet option to run with "play bitcoins" on the test network, if you
are testing multi-machine code that needs to operate across the internet.

If you are testing something that can run on one machine, run with the -regtest option.
In regression test mode blocks can be created on-demand; see qa/rpc-tests/ for tests
that run in -regest mode.

**DEBUG_LOCKORDER**

Bitcoin Core is a multithreaded application, and deadlocks or other multithreading bugs
can be very difficult to track down. Compiling with -DDEBUG_LOCKORDER (configure
CXXFLAGS="-DDEBUG_LOCKORDER -g") inserts run-time checks to keep track of what locks
are held, and adds warning to the debug.log file if inconsistencies are detected.
