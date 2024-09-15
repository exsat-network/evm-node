# exSAt EVM NODE

## Overview

The exSat EVM Node consumes Antelope blocks from a Spring node via state history (SHiP) endpoint and builds the virtual EVM blockchain in a deterministic way.
The exSat EVM RPC will talk with the exSat EVM node, and provide read-only Ethereum compatible RPC services for clients (such as MetaMask).

Clients can also push Ethereum compatible transactions (aka EVM transactions) to the Antelope blockchain, via proxy and Transaction Wrapper (TX-Wrapper), which encapsulates EVM transactions into Antelope transactions. All EVM transactions will be validated and executed by the exSat EVM Contract deployed on the Antelope blockchain.

```
         |                                                 
         |                     WRITE              +-----------------+
         |             +------------------------->|  EVM MINER      |
         |             |                          +-------v---------+
         |             |                          |    Leap node    | ---> connect to the other nodes in the blockchain network
 client  |             |                          +-------+---------+
 request |       +-----+-----+                            |
---------+------>|   Proxy   |                            |
         |       +-----------+                            v       
         |             |                          +-----------------+
         |        READ |     +--------------+     |                 |
         |             +---->|      EVM RPC |---->|       EVM Node  +
         |                   +--------------+     |                 |
         |                                        +-----------------+
```
         
## Compilation

### checkout the source code:
```
git clone https://github.com/exsat-network/evm-node.git
cd evm-node
git submodule update --init --recursive
```

### compile exsat-evm-node, exsat-evm-rpc

Prerequisites:
- Ubuntu 22 or later or other compatible Linux
- gcc 11 or later
- cmake
- conan

Conan install
```shell
pip3 install --user conan==1.58.0 chardet
```

Easy Steps:
```
mkdir build
cd build
cmake ..
make -j8
```
You'll get the list of binaries with other tools:
```
bin/exsat-evm-node
bin/exsat-evm-rpc
```

Alternatively, to build with specific compiler:
```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Debug -DCMAKE_C_COMPILER=gcc -DCMAKE_CXX_COMPILER=g++ ..
make -j8
```



See the pipeline documentation for more information.

