---
title: Quick Start
chapter: 2
layout: default
---
# Quick Start

HoT comes with a number of programs. The primary ones that you will use, and the ones that are covered here, are:

- `nodehot`  - the core HoT **node** daemon that can be configured with plugins to run a node. Example uses are block production, dedicated API endpoints, and local development.
- `clhot` (cli + hot = clhot) - command line interface to interact with the blockchain and to manage wallets.
- `khotd` (key + hot = khotd) - component that securely stores HoT keys in wallets.

## Running Nodehot

`Nodehot` can be run from the command line. The behaviour of `nodehot` is determined by which plugins are used and the configuration options for each plugin. `Nodehot` itself has a few options, these allow you to set the data directory, where the blockchain data is stored, and point to configuration files for the plugins and for logging.

For example:

```shell
nodehot -e \
	-p eosio \
	--plugin eosio::producer_plugin \
	--plugin eosio::chain_api_plugin \
	--plugin eosio::http_plugin \
	--plugin eosio::state_history_plugin \
	--data-dir /hot/data \
	--config-dir /hot/config \
	--access-control-allow-origin='*' \
	--contracts-console \
	--http-validate-host=false \
	--state-history-dir /hot/data \
	--trace-history \
	--chain-state-history \
	--verbose-http-errors \
	--filter-on='*' \
	--disable-replay-opts >> nodeos.log 2>&1 &
```

## Nodehot Configuration

`Nodehot` can be configured using either the command line interface (CLI) options or a configuration file, `config.ini`. All the CLI options can be found by running `$ nodehot --help`.

Each CLI option maps to a setting in `config.ini`, for example `--plugin eosio::chain_api_plugin` can be set by adding `plugin = eosio::chain_api_plugin` to `config.ini`.

A custom `config.ini` file can be used by executing `$ nodehot --config path/to/config.ini`.

## Configuration File Location

`config.ini` can be found in the following locations:

- Mac OS: `~/Library/Application Support/hot/nodehot/config`
- Linux: `~/.local/share/hot/nodehot/config`

## Nodehot Options

An example of the output from running `$ nodehot --help` output is show below, the actual output will include options for plugins, though these have been excluded for clarity.

```
Application Options: 
Application Config Options:  
	--plugin arg                          Plugin(s) to enable, may be specified 
	                                      multiple times
Application Command Line Options:
	-h [ --help ]                         Print this help message and exit.  
	-v [ --version ]                      Print version information.  
	--print-default-config                Print default configuration template  
	-d [ --data-dir ] arg                 Directory containing program runtime 
	                                      data  
	--config-dir arg                      Directory containing configuration 
	                                      files such as config.ini  
	-c [ --config ] arg (=config.ini)     Configuration file name relative to 
	                                      config-dir  
	-l [ --logconf ] arg (=logging.json)  Logging configuration file name/path 
	                                      for library users
```