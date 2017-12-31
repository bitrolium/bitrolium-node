Bitrolium Node

  

## Details

features:
- Bitrolium payment Gateway
- Removed sidechains (deprecated in favor of smartbridge)
- Removed custom node version
- Removed UI for stability and security reasons
- Changed some constants (block rewards, blocktime etc...)
- Added simple PBFT before forging new block
- Ditch addresses from the protocol in favor of bitcoin like system, enabling HD Wallet as for BIP32
- Completely rewritten node management using a single NodeManager and messaging system
- Completely rewritten round management (removed mem_round, reward block fees to forger)
- Added 64 bytes vendorField as first iteration of smart bridge
- Made peers management entirely in-memory for efficiency
- Strengthened the transaction management and broadcast (reject often, reject soon)
- Rearchitect with relay nodes and forging nodes
- Nodes broadcast only block headers.

### Planned features:
- Simple blockchain validation for SPV and use in lite clients
- Add IPFS as first class citizen (using smartbridge addressing)
- Protocol improvements (uncle forging, voting weights).
- Remove unsecured API
- Routing tables

 


## Node Installation

Install essentials:

```
sudo apt-get update
sudo apt-get install -y curl build-essential python git
```

Install PostgreSQL (min version: 9.5.2)

```
sudo apt-get install -y postgresql postgresql-contrib
sudo -u postgres createuser --createdb --password $USER
 
sudo apt-get install -y nodejs
sudo npm install -g n
sudo n 6.9.2
```

Install grunt-cli (globally):

```
sudo npm install grunt-cli -g
```

Clone this repository
```
git clone https://github.com/bitrolium/bitrolium-node
cd bitrolium-node
```

Install node modules:
```
npm install forever -g
npm install grunt-cli -g
npm install libpq
npm install secp256k1
npm install bindings
npm install

```

## Launch
To launch Bitrolium  :
```
createdb bitrolium
sudo -u postgres psql -c "CREATE USER $USER WITH PASSWORD '****' CREATEDB;" >&- 2>&-
forever start app.js --config config.bitrolium.json --genesis genesisBlock.bitrolium.json

```

## Authors
- Bitrolium Development Team <develop@bitrolium.com>
- FX Thoorens <fx.thoorens@ark.io>
- Boris Povod <boris@crypti.me>
- Pavel Nekrasov <landgraf.paul@gmail.com>
- Sebastian Stupurac <stupurac.sebastian@gmail.com>
- Oliver Beddows <oliver@lisk.io>

## License

The MIT License (MIT)

Copyright (c) 2017 Bitrolium
Copyright (c) 2016 Lisk
Copyright (c) 2016-2017 Ark
Copyright (c) 2014-2015 Crypti

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:  

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
