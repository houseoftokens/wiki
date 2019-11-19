---
title: Setup Nodehot
chapter: 3
layout: default
---

# Setup Nodehot

## Nodehot Modes

`Nodehot` generally runs in two modes:

- Producing Node
- Non-Producing Node

`Producing Nodes` will connect to the peer to peer network and actively produce new blocks. `Non-Producing Nodes` will connect to the peer to peer network, however, in this mode `nodehot` does not actively produce new blocks, it will simply verify blocks and maintain a local copy of the blockchain. `Non-Producing Nodes` can be used for monitoring the blockchain.

## Producing Node

### Register your account as a producer

In order for your account to be eligible as a producer, you will need to register the account as a producer.

#### Example using `clhot system regproducer`

```shell
clhot system regproducer accountname1 HOT1234534... http://producer.site Europe
```

### Set Producer Name

Set the `producer-name` option in config.ini to your account, like so

```shell
producer-name = youraccount
```

### Set the Producer's signature-provider

You will need to set the private key for your producer. The public key should have an authority for the producer account defined above.

`signature-provider` is defined with a tuple

- `public-key` - A valid HOT public key in form of a string.
- `provider-spec` - It's a string formatted like <provider-type>:<data>

Like so

```ini
signature-provider = PUBLIC_SIGNING_KEY=KEY:PRIVATE_SIGNING_KEY 
# Example 
# signature-provider = HOT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV=KEY:5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3 
```

### Define a peers list

```ini
# Default p2p port is 9011
p2p-peer-address = s1.hotwallet.tech:9011
```

### Load the Required Plugins

In your config.ini, confirm the following plugins are loading or append them if necessary.

```ini
plugin = eosio::chain_plugin 
plugin = eosio::producer_plugin
```

## Non-Producing Node

A non-producing node is a node that is not configured to produce blocks. An example use case would be to provide a synchronized node that provides a public HTTP-RPC API for developers or as a dedicated private endpoint for your app.

To setup a non-producing node is simple.

### Set Peers

You need to set some peers in your config ini, for example

```ini
p2p-peer-address = s1.hotwallet.tech:9011
```

Or you can include the peer in as a boot flag, like so

```shell
--p2p-peer-address=s1.hotwallet.tech:9011
```

