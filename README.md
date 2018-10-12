![sovrinlogo](https://github.com/sovrin-foundation/sovrin/blob/master/banner.png "insert humor here")
# Table of Contents


1.  [Requirements](#requirements)
    1.  [Installing Indy-SDK](#installing-indy-sdk)
2.  [Running Indy Pool](#running-indy-pool)
    1.  [Build the pool](#build-the-pool)
    2.  [run the poool](#run-the-poool)
    3.  [Compiling libsovtoken and running tests](#compiling-libsovtoken-and-running-tests)
3.  [How To Contribute](#how-to-contribute)

<a href="https://www.apache.org/licenses/LICENSE-2.0.txt" target="_blank">![Hex.pm](https://img.shields.io/hexpm/l/plug.svg?style=plastic)</a>
<a href="https://badge.fury.io/gh/sovrin-foundation%2Flibsovtoken">[![GitHub version](https://badge.fury.io/gh/sovrin-foundation%2Flibsovtoken.svg)](https://badge.fury.io/gh/sovrin-foundation%2Flibsovtoken)</a>
# LibSovToken

This is a payment handler library to work with libindy. It may one day
be merged into libindy.


<a id="requirements"></a>


# Requirements

-   Rust Lang (Stable)
-   LibIndy (Stable)
-   Indy Pool (Provided)


<a id="installing-indy-sdk"></a>

## Installing Indy-SDK

1.  Ubuntu

        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 68DB5E88
        sudo add-apt-repository "deb https://repo.sovrin.org/sdk/deb xenial stable"
        sudo apt-get update
        sudo apt-get install -y libindy>=1.6.0

2.  macOS

        git clone https://github.com/hyperledger/indy-sdk.git
        cd indy-sdk
        git checkout stable 
        cd libindy
        cargo clean 
        cargo update
        cargo build
    
    Libsovtoken build needs to know how to find Indy-SDK. This is done
    through the environment variable LIBINDY<sub>DIR</sub>.
    
    Create an environment variable LIBINDY<sub>DIR</sub>. Have it point the directory
    containing indy-sdk binaries.
    
    Use `pwd` to get path to current directory
    
    Add this to your bash profile:
    
        # EXAMPLE 
        export LIBINDY_DIR='/my/path/to/indy-sdk/libindy/target/debug/'
    
    *Note* anytime you get latest for indy-sdk, you must rebuild the
    libraries before building libsovtoken, as the libsovtoken build does not
    compile indy-sdk.


<a id="running-indy-pool"></a>

# Running Indy Pool


<a id="build-the-pool"></a>

## Build the pool

    cd devops/indy-pool/ && docker build -t indy_pool . 


<a id="run-the-poool"></a>

## run the poool

    docker run -itd -p 9701-9708:9701-9708 indy_pool


<a id="compiling-libsovtoken-and-running-tests"></a>

## Compiling libsovtoken and running tests

1.  Make sure you meet the requirements above, including building the
    projects, if you elect to use source code.
2.  Get latest for libsovtoken from master at
    <https://github.com/evernym/libsovtoken.git>
3.  The source code is in a sub-directory called libsovtoken
4.  Run the following commands from the libsovtoken subdirectory
    1.  cargo update
    2.  cargo build

5.  Run the tests to ensure everything is in good order.
    1.  cargo test

***Please keep in mind*** (at the time this document was written) some of
the cargo crates are github repositories. If you update libsovtoken code
from github you need to re-build libsovtoken as follows: 1) cargo clean

1.  cargo update 3) cargo build

The cargo update command is necessary to make sure you get latest from
the cargo crates in github


<a id="how-to-contribute"></a>

# How To Contribute

Please follow the guide [here](./doc/pull-request.md).

