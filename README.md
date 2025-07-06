# Bitgesell RPC Explorer

<img src="Icon.png" style="height: 60px;" />

## Self-Hosted Bitgesell explorer for everyone running [Bitgesell Core](https://github.com/BitgesellOfficial/bitgesell).

[![npm version][npm-ver-img]][npm-ver-url] [![NPM downloads][npm-dl-alltime-img]][npm-dl-url]


---


![homepage](./public/img/screenshots/homepage.png)



This is a self-hosted explorer for the Bitgesell blockchain, driven by RPC calls to your own [Bitgesell](https://github.com/Bitgesell/Bitgesell) node. It is easy to run and can be connected to other tools (like Electrum servers) to achieve a full-featured explorer.

Whatever reasons you may have for running a full node (trustlessness, technical curiosity, supporting the network, etc) it's valuable to appreciate the *fullness* of your node. With this explorer, you can explore not just the blockchain database, but also explore all of the functional capabilities of your own node.

Live demos:



# Features

* Network Summary dashboard
* View details of blocks, transactions, and addresses
* Analysis tools for viewing stats on blocks, transactions, and miner activity
* JSON REST API
* See raw JSON content from BGLd used to generate most pages
* Search by transaction ID, block hash/height, and address
* Optional transaction history for addresses by querying from Electrum-protocol servers (e.g. Electrs, ElectrumX), blockchain.com, blockchair.com, or blockcypher.com
* Mempool summary, with fee, size, and age breakdowns
* RPC command browser and terminal


# Changelog / Release notes

See [CHANGELOG.md](/CHANGELOG.md).


# Getting started

## Prerequisites

1. Install `Bitgesell Core` - [instructions](https://docs.bitgesell.org). Ensure that `Bitgesell Core`'s' RPC server is enabled (`server=1`).
2. Allow `Bitgesell Core` to synchronize with the Bitgesell network (you *can* use this tool while sychronizing, but some pages may fail).
3. Install Node.js (16+ required, 18+ recommended).

### Note about pruning and indexing configurations

This tool is designed to work best with full transaction indexing enabled (`txindex=1`) and pruning **disabled**. 

In particular, with `pruning` enabled and/or `txindex` disabled, the following functionality is altered:

* You will only be able to search for mempool, recently confirmed, and wallet transactions by their txid. Searching for non-wallet transactions that were confirmed over 3 blocks ago is only possible if you provide the confirmed block height in addition to the txid.
* Pruned blocks will display basic header information, without the list of transactions. Transactions in pruned blocks will not be available, unless they're wallet-related. Block stats will only work for unpruned blocks.
* The address and amount of previous transaction outputs will not be shown, only the txid:vout.
* The mining fee will only be available for unconfirmed transactions.


## Install / Run

If you're running on mainnet with the default datadir and port, the default configuration should *Just Work*. Otherwise, see the **Configuration** section below.

#### Install via `npm`:

*Note: npm v7+ is required*

```bash
npm install -g bgl-rpc-explorer
bgl-rpc-explorer
```

#### Run from source:

1. `git clone https://github.com/naftalimurgor/bgl-rpc-explorer`
2. `cd bgl-rpc-explorer`
3. `npm install`
4. `npm start`


After a default installation+startup using any of the above methods, the app can be viewed at [http://127.0.0.1:3002/](http://127.0.0.1:3002/)


## Configuration

Configuration options may be set via environment variables or CLI arguments.

#### Configuration with environment variables

To configure with environment variables, you need to create one of the 2 following files and enter values in it:

1. `~/.config/bgl-rpc-explorer.env`
2. `.env` in the working directory for bgl-rpc-explorer

In either case, refer to [.env-sample](.env-sample) for a list of the options and formatting details.

## Run via Docker

1. `docker build -t bgl-rpc-explorer .`
2. `docker run -it -p 3002:3002 -e BTCEXP_HOST=0.0.0.0 bgl-rpc-explorer`


## Reverse proxy with HTTPS

See [instructions here](docs/nginx-reverse-proxy.md) for using nginx+certbot (letsencrypt) for an HTTPS-accessible, reverse-proxied site.


# Support

If you get value from this project, please consider supporting my work with a donation. All donations are truly appreciated.

Donate USDT(Ethereum):

* [https://donate.Bitgesellexplorer.org](https://donate.bitcoinexplorer.org)

Or, via a BTC address:



