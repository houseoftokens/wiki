---
title: Clhot
chapter: 4
layout: default
---

# Clhot

`clhot` is a command line tool that interfaces with the REST API exposed by `nodehot`. In order to use `clehot` you will need to have the end point (IP address and port number) to a `nodehot` instance and also configure `nodehot` to load the 'eosio::chain_api_plugin'. `clhot` contains documentation for all of its commands. For a list of all commands known to `clhot`, simply run it with no arguments:

```
Command Line Interface to HoT Client
Usage: ./clhot [OPTIONS] SUBCOMMAND

Options:
  -h,--help                   Print this help message and exit
  -u,--url TEXT=http://localhost:8888/
                              the http/https URL where nodehot is running
  --wallet-url TEXT=http://localhost:8900/
                              the http/https URL where khotd is running
  -r,--header                 pass specific HTTP header; repeat this option to pass multiple headers
  -n,--no-verify              don't verify peer certificate when using HTTPS
  -v,--verbose                output verbose actions on error

Subcommands:
  version                     Retrieve version information
  create                      Create various items, on and off the blockchain
  get                         Retrieve various items and information from the blockchain
  set                         Set or update blockchain state
  transfer                    Transfer HOT from account to account
  net                         Interact with local p2p network connections
  wallet                      Interact with local wallet
  sign                        Sign a transaction
  push                        Push arbitrary transactions to the blockchain
  multisig                    Multisig contract commands
  system                      Send eosio.system contract action to the blockchain.
```

To get help with any particular subcommand, run it with no arguments as well:

```
Create various items, on and off the blockchain
Usage: ./clhot create SUBCOMMAND

Subcommands:
  key                         Create a new keypair and print the public and private keys
  account                     Create an account, buy ram, stake for bandwidth for the account


Create an account, buy ram, stake for bandwidth for the account
Usage: ./clhot create account [OPTIONS] creator name OwnerKey [ActiveKey]

Positionals:
  creator TEXT                The name of the account creating the new account (required)
  name TEXT                   The name of the new account (required)
  OwnerKey TEXT               The owner public key for the new account (required)
  ActiveKey TEXT              The active public key for the new account

Options:
  -h,--help                   Print this help message and exit
  -x,--expiration             set the time in seconds before a transaction expires, defaults to 30s
  -f,--force-unique           force the transaction to be unique. this will consume extra bandwidth and remove any protections against accidently issuing the same transaction multiple times
  -s,--skip-sign              Specify if unlocked wallet keys should be used to sign transaction
  -j,--json                   print result as json
  -d,--dont-broadcast         don't broadcast transaction to the network (just print to stdout)
  -r,--ref-block TEXT         set the reference block num or block id used for TAPOS (Transaction as Proof-of-Stake)
  -p,--permission TEXT ...    An account and permission level to authorize, as in 'account@permission'
  --max-cpu-usage-ms UINT     set an upper limit on the milliseconds of cpu usage budget, for the execution of the transaction (defaults to 0 which means no limit)
  --max-net-usage UINT        set an upper limit on the net usage budget, in bytes, for the transaction (defaults to 0 which means no limit)
```