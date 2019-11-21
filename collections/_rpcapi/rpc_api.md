---
title: RPC API
chapter: 1
layout: default
---
# RPC API
{: .no_toc }
### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc} 
## Chain API

### get_account
Returns an object containing various details about a specific account on the blockchain.

>`POST` http://{host}:{port}/v1/chain/get_account

#### PARAMETERS
{: .no_toc }
* account_name:  String representation of basic NODEHOT name type

#### CURL
{: .no_toc }
```bash
curl --request POST \
    --url http://{host}:{port}/v1/chain/get_account \
    --header 'accept: application/json' \
    --header 'content-type: application/json' \
    --data '{"account_name":"hottestaccnt"}'
```

#### Response
{: .no_toc }
```json
{
  "account_name": "hottestaccnt",
  "head_block_num": 2257147,
  "head_block_time": "2019-10-09T06:31:19.000",
  "privileged": false,
  "last_code_update": "1970-01-01T00:00:00.000",
  "created": "2019-10-08T11:33:23.500",
  "core_liquid_balance": "200.000000 HOT",
  "ram_quota": 9544,
  "net_weight": 1000000,
  "cpu_weight": 1000000,
  "net_limit": {
    "used": 0,
    "available": 116126106,
    "max": 116126106
  },
  "cpu_limit": {
    "used": 0,
    "available": 22149297,
    "max": 22149297
  },
  "ram_usage": 2996,
  "permissions": [
    {
      "perm_name": "active",
      "parent": "owner",
      "required_auth": {
        "threshold": 1,
        "keys": [
          {
            "key": "HOT848tbvzPQHR6Qq4eUJCE6BFXUmHtTxiTgpkpe7ap3xGEn4oXAf",
            "weight": 1
          }
        ],
        "accounts": [],
        "waits": []
      }
    },
    {
      "perm_name": "owner",
      "parent": "",
      "required_auth": {
        "threshold": 1,
        "keys": [
          {
            "key": "HOT848tbvzPQHR6Qq4eUJCE6BFXUmHtTxiTgpkpe7ap3xGEn4oXAf",
            "weight": 1
          }
        ],
        "accounts": [],
        "waits": []
      }
    }
  ],
  "total_resources": {
    "owner": "hottestaccnt",
    "net_weight": "1.000000 HOT",
    "cpu_weight": "1.000000 HOT",
    "ram_bytes": 8144
  },
  "self_delegated_bandwidth": null,
  "refund_request": null,
  "voter_info": null
}
```
### get_block
Returns an object containing various details about a specific block on the blockchain.

>`POST` http://{host}:{port}/v1/chain/get_block

#### PARAMETERS
{: .no_toc }
* block_num_or_id:  String Provide a block number or a block id

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_block \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"block_num_or_id":"1000"}'
```

#### Response
{: .no_toc }
```json
{
  "timestamp": "2019-09-26T06:24:45.500",
  "producer": "prod3.hot",
  "confirmed": 0,
  "previous": "0000270fe7e13ef37f32b76c4f83c456294e2aac1c727f12137bab166f3c128b",
  "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
  "action_mroot": "49a022bba51c2a59d3a7669345ea9d892b39ecab386e782833164a0bd89c8df1",
  "schedule_version": 1,
  "new_producers": null,
  "header_extensions": [],
  "producer_signature": "SIG_K1_KAmmZ9D1gVHUuAmjHEA4TmKEeMJDsd3VfFTg2sxvNxmsgHqCVv6jgcC7QgVonoojhzDMV3sN4HTPLnG9caFgsu1EeMNsdu",
  "transactions": [],
  "block_extensions": [],
  "id": "000027109edd969619eeeaaf50c052d1710bddfd2132e468df1e22e528ecd124",
  "block_num": 10000,
  "ref_block_prefix": 2951409177
}
```
### get_info
Returns an object containing various details about the blockchain.

>`POST` http://{host}:{port}/v1/chain/get_info

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_info \
  --header 'accept: application/json'
```

#### Response
{: .no_toc }
```json
{
  "server_version": "7cf577a7",
  "chain_id": "1b59a7b14d8d56ee659c76dc8fdb4092b5f73fbd8d093da1246f2bba2b1e5a5d",
  "head_block_num": 2276742,
  "last_irreversible_block_num": 2276680,
  "last_irreversible_block_id": "0022bd488945e228b415b7a98cd16c9dfd601cf12c0c087c37c36d1741966187",
  "head_block_id": "0022bd86a47698830bc6e0a719dd2b8b81e03432102b672e0de664805d83c24d",
  "head_block_time": "2019-10-09T09:14:36.500",
  "head_block_producer": "prod2.hot",
  "virtual_block_cpu_limit": 200000000,
  "virtual_block_net_limit": 1048576000,
  "block_cpu_limit": 199900,
  "block_net_limit": 1048576,
  "server_version_string": "v1.8.2-3-g7cf577a72",
  "fork_db_head_block_num": 2276742,
  "fork_db_head_block_id": "0022bd86a47698830bc6e0a719dd2b8b81e03432102b672e0de664805d83c24d"
}
```
### push_transaction
This method expects a transaction in JSON format and will attempt to apply it to the blockchain.

>`POST` http://{host}:{port}/v1/chain/push_transaction

#### PARAMETERS
{: .no_toc }

* signatures:  string, array of signatures required to authorize transaction
* compression: boolean, compression used, usually false
* packed_context_free_data: string, json to hex
* packed_trx: string, Transaction object json to hex

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/push_transaction \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "signatures": [
    "SIG_K1_JzZXUk8hc254iT4KJDkB6g8CntXP8fCjm8Cfmc9Pz7fDhRrXtMV6bbfajU51T9AZrQxbkzDQUphwEQ9Gj8oW5AjMVcn9e4"
  ],
  "compression": "none",
  "packed_context_free_data": "",
  "packed_trx": "f3af9d5df93c646a83e6000000000100a6823403ea3055000000572d3ccdcd01000000000000326d00000000a8ed323229000000000000326d0000c8b48190e8ad907612000000000006484f540000000008686920746865726500"
}'
```


#### Response
{: .no_toc }
```json
{
  "transaction_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
  "processed": {
    "id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
    "block_num": 2243905,
    "block_time": "2019-10-09T10:00:53.500",
    "producer_block_id": null,
    "receipt": {
      "status": "executed",
      "cpu_usage_us": 342,
      "net_usage_words": 17
    },
    "elapsed": 342,
    "net_usage": 136,
    "scheduled": false,
    "action_traces": [{
        "action_ordinal": 1,
        "creator_action_ordinal": 0,
        "closest_unnotified_ancestor_action_ordinal": 0,
        "receipt": {
          "receiver": "eosio.token",
          "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
          "global_sequence": 2244142,
          "recv_sequence": 62,
          "auth_sequence": [[
              "hot",
              180
            ]
          ],
          "code_sequence": 1,
          "abi_sequence": 1
        },
        "receiver": "eosio.token",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [{
              "actor": "hot",
              "permission": "active"
            }
          ],
          "data": {
            "from": "hot",
            "to": "prod1.hot",
            "quantity": "1.210000 HOT",
            "memo": "hi there"
          },
          "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
        },
        "context_free": false,
        "elapsed": 118,
        "console": "",
        "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
        "block_num": 2243905,
        "block_time": "2019-10-09T10:00:53.500",
        "producer_block_id": null,
        "account_ram_deltas": [],
        "except": null,
        "error_code": null,
        "inline_traces": [{
            "action_ordinal": 2,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244143,
              "recv_sequence": 51,
              "auth_sequence": [[
                  "hot",
                  181
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 4,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          },{
            "action_ordinal": 3,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "prod1.hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244144,
              "recv_sequence": 3,
              "auth_sequence": [[
                  "hot",
                  182
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "prod1.hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 6,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          }
        ]
      }
    ],
    "account_ram_delta": null,
    "except": null,
    "error_code": null
  }
}
```
### send_transaction
This method expects a transaction in JSON format and will attempt to apply it to the blockchain.

>`POST` http://{host}:{port}/v1/chain/send_transaction

#### PARAMETERS
{: .no_toc }

* signatures:  string, array of signatures required to authorize transaction
* compression: boolean, compression used, usually false
* packed_context_free_data: string, json to hex
* packed_trx: string, Transaction object json to hex

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/send_transaction \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "signatures": [
    "SIG_K1_JzZXUk8hc254iT4KJDkB6g8CntXP8fCjm8Cfmc9Pz7fDhRrXtMV6bbfajU51T9AZrQxbkzDQUphwEQ9Gj8oW5AjMVcn9e4"
  ],
  "compression": "none",
  "packed_context_free_data": "",
  "packed_trx": "f3af9d5df93c646a83e6000000000100a6823403ea3055000000572d3ccdcd01000000000000326d00000000a8ed323229000000000000326d0000c8b48190e8ad907612000000000006484f540000000008686920746865726500"
}'
```


#### Response
{: .no_toc }
```json
{
  "transaction_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
  "processed": {
    "id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
    "block_num": 2243905,
    "block_time": "2019-10-09T10:00:53.500",
    "producer_block_id": null,
    "receipt": {
      "status": "executed",
      "cpu_usage_us": 342,
      "net_usage_words": 17
    },
    "elapsed": 342,
    "net_usage": 136,
    "scheduled": false,
    "action_traces": [{
        "action_ordinal": 1,
        "creator_action_ordinal": 0,
        "closest_unnotified_ancestor_action_ordinal": 0,
        "receipt": {
          "receiver": "eosio.token",
          "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
          "global_sequence": 2244142,
          "recv_sequence": 62,
          "auth_sequence": [[
              "hot",
              180
            ]
          ],
          "code_sequence": 1,
          "abi_sequence": 1
        },
        "receiver": "eosio.token",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [{
              "actor": "hot",
              "permission": "active"
            }
          ],
          "data": {
            "from": "hot",
            "to": "prod1.hot",
            "quantity": "1.210000 HOT",
            "memo": "hi there"
          },
          "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
        },
        "context_free": false,
        "elapsed": 118,
        "console": "",
        "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
        "block_num": 2243905,
        "block_time": "2019-10-09T10:00:53.500",
        "producer_block_id": null,
        "account_ram_deltas": [],
        "except": null,
        "error_code": null,
        "inline_traces": [{
            "action_ordinal": 2,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244143,
              "recv_sequence": 51,
              "auth_sequence": [[
                  "hot",
                  181
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 4,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          },{
            "action_ordinal": 3,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "prod1.hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244144,
              "recv_sequence": 3,
              "auth_sequence": [[
                  "hot",
                  182
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "prod1.hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 6,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          }
        ]
      }
    ],
    "account_ram_delta": null,
    "except": null,
    "error_code": null
  }
}
```
### push_transactions
This method expects a transaction in JSON format and will attempt to apply it to the blockchain.

>`POST` http://{host}:{port}/v1/chain/push_transactions

#### PARAMETERS
{: .no_toc }

* expiration:  string, Time that transaction must be confirmed by.
* ref_block_num: int32
* ref_block_prefix: int32
* max_net_usage_words: number
* max_cpu_usage_ms: number
* delay_sec: int32
* context_free_actions: array of objects
* actions: array of objects
  * account: String representation of privileged NODEHOT name type
  * name: String C++ variable signature
  * authorization: array of objects
    * actor: String representation of privileged NODEHOT name type
    * permission: String representation of privileged NODEHOT name type
  * data: string
  * hex_data: string
* transaction_extensions: array


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/send_transaction \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '[ {
    "expiration": "2019-10-09T09:46:52",
    "ref_block_num": 2242033,
    "ref_block_prefix": 3357684371,
    "net_usage_words": 0,
    "max_cpu_usage_ms": 0,
    "delay_sec": 0,
    "context_free_actions": [],
    "actions": [
      {
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [
          {
            "actor": "hot",
            "permission": "active"
          }
        ],
        "data": "000000000000326d50a420c47a1e326d809698000000000006484f540000000000"
      }
    ],
    "transaction_extensions": []
  }]'
```


#### Response
{: .no_toc }
```json
{
  "transaction_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
  "processed": {
    "id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
    "block_num": 2243905,
    "block_time": "2019-10-09T10:00:53.500",
    "producer_block_id": null,
    "receipt": {
      "status": "executed",
      "cpu_usage_us": 342,
      "net_usage_words": 17
    },
    "elapsed": 342,
    "net_usage": 136,
    "scheduled": false,
    "action_traces": [{
        "action_ordinal": 1,
        "creator_action_ordinal": 0,
        "closest_unnotified_ancestor_action_ordinal": 0,
        "receipt": {
          "receiver": "eosio.token",
          "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
          "global_sequence": 2244142,
          "recv_sequence": 62,
          "auth_sequence": [[
              "hot",
              180
            ]
          ],
          "code_sequence": 1,
          "abi_sequence": 1
        },
        "receiver": "eosio.token",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [{
              "actor": "hot",
              "permission": "active"
            }
          ],
          "data": {
            "from": "hot",
            "to": "prod1.hot",
            "quantity": "1.210000 HOT",
            "memo": "hi there"
          },
          "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
        },
        "context_free": false,
        "elapsed": 118,
        "console": "",
        "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
        "block_num": 2243905,
        "block_time": "2019-10-09T10:00:53.500",
        "producer_block_id": null,
        "account_ram_deltas": [],
        "except": null,
        "error_code": null,
        "inline_traces": [{
            "action_ordinal": 2,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244143,
              "recv_sequence": 51,
              "auth_sequence": [[
                  "hot",
                  181
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 4,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          },{
            "action_ordinal": 3,
            "creator_action_ordinal": 1,
            "closest_unnotified_ancestor_action_ordinal": 1,
            "receipt": {
              "receiver": "prod1.hot",
              "act_digest": "aafc194fe988b4628e34ef3d730bffdbeebfa43c6c98efc50aa540047a07ec83",
              "global_sequence": 2244144,
              "recv_sequence": 3,
              "auth_sequence": [[
                  "hot",
                  182
                ]
              ],
              "code_sequence": 1,
              "abi_sequence": 1
            },
            "receiver": "prod1.hot",
            "act": {
              "account": "eosio.token",
              "name": "transfer",
              "authorization": [{
                  "actor": "hot",
                  "permission": "active"
                }
              ],
              "data": {
                "from": "hot",
                "to": "prod1.hot",
                "quantity": "1.210000 HOT",
                "memo": "hi there"
              },
              "hex_data": "000000000000326d0000c8b48190e8ad907612000000000006484f5400000000086869207468657265"
            },
            "context_free": false,
            "elapsed": 6,
            "console": "",
            "trx_id": "dcfc412e0ee79bff46a1d85320327bb978d6392e6707d30a88b197444a4dbccb",
            "block_num": 2243905,
            "block_time": "2019-10-09T10:00:53.500",
            "producer_block_id": null,
            "account_ram_deltas": [],
            "except": null,
            "error_code": null,
            "inline_traces": []
          }
        ]
      }
    ],
    "account_ram_delta": null,
    "except": null,
    "error_code": null
  }
}
```
### get_block_header_state

>`POST` http://{host}:{port}/v1/chain/get_block_header_state

#### PARAMETERS
{: .no_toc }

* block_num_or_id:  string, Provide a block_number or a block_id


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_block_header_state \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"block_num_or_id":"2411871"}'
```


#### Response
{: .no_toc }
```json
{
  "block_num": 2411871,
  "dpos_proposed_irreversible_blocknum": 2411836,
  "dpos_irreversible_blocknum": 2411800,
  "active_schedule": {
    "version": 1,
    "producers": [
      {
        "producer_name": "prod1.hot",
        "block_signing_key": "HOT5FnwawMysMptrt2Xdmm3Zu5qM9vnujBfEnjeePbZTeTMvEQBne"
      },
      {
        "producer_name": "prod2.hot",
        "block_signing_key": "HOT8dWpgG4AezD4o7f8iTCCmsVicJ51TQ9Q59L1gbyWDGfNu8W8ga"
      },
      {
        "producer_name": "prod3.hot",
        "block_signing_key": "HOT8TEjsFF7SZTNRhCLizTWnxCCM62tDEu8VnfQBfqQCN8PPb5JrK"
      },
      {
        "producer_name": "prod4.hot",
        "block_signing_key": "HOT859jY6iaj7u2P7BJSZJYk4ARXtdDqopiqkRbcNyxC5E6rtdaty"
      },
      {
        "producer_name": "prod5.hot",
        "block_signing_key": "HOT81vBGxvkHTodeQZpc3wbqnrf3Ass89U8H7sirCb5eWSnNkUjiz"
      }
    ]
  },
  "blockroot_merkle": {
    "_active_nodes": [
      "e8524ec7ec83b82ffa1d7a71c13e14a9cf4518661b8b8f1f4aeaebb2f80b5db9",
      "0d7d7391eeba71c4fab58db1cdfea13a81770b72bd946bf0f4fd8a5f5777f98e",
      "1839ae56d70ef3526250e92b9dea6b37a13ad9d6009597399b206608bac89134",
      "6ee5c276c0f8c6e299ff54b8ff42872d0fbab63a4fdf6917d531394bdb6a920e",
      "5d5495fe5b5ce8d7449345856f340621aeea2372ea35b5f9ef34f73a988bb675",
      "01a9c1d1c0d8583b643dea1c6bd87259d914dbfcd92ad6a4e95a2faf680458bb",
      "3cd7bbcf7e4f1a71d183747078cd66b5f208e43821a326b19e36f6b66b43ccdc",
      "0d9c88a069fa10a3e7d54eca1154e022020d57dc26a33967b7bdc132c765873d",
      "f678dd0bf9739652583d5b62de33553993f8102779406072b732f096db1d8e96",
      "8f60212afddde3a51f85a032daa1a8eee225968518cbfd36e470a407ea2297f4",
      "d3b0d331b46356e85b600cac1c89888b358f2aab8ae75705474e5e02e8d3df6a",
      "1fc4618b6112d6b228101f4061228e9d93767573af0bb986d89d12e7ef235c33",
      "5d340f31cfcc489fec73ec6f2d0295ce7abb8ad0f4b401c0b33da68fb615a09c"
    ],
    "_node_count": 2411870
  },
  "producer_to_last_produced": [
    [
      "eosio",
      217
    ],
    [
      "prod1.hot",
      2411860
    ],
    [
      "prod2.hot",
      2411871
    ],
    [
      "prod3.hot",
      2411824
    ],
    [
      "prod4.hot",
      2411836
    ],
    [
      "prod5.hot",
      2411848
    ]
  ],
  "producer_to_last_implied_irb": [
    [
      "prod1.hot",
      2411824
    ],
    [
      "prod2.hot",
      2411836
    ],
    [
      "prod3.hot",
      2411788
    ],
    [
      "prod4.hot",
      2411800
    ],
    [
      "prod5.hot",
      2411812
    ]
  ],
  "block_signing_key": "HOT8dWpgG4AezD4o7f8iTCCmsVicJ51TQ9Q59L1gbyWDGfNu8W8ga",
  "confirm_count": [ 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3 ],
  "id": "0024cd5f1c00f4bbdf4a93df6f48c6293dc74d0d09414d24258d6a6cd207cab4",
  "header": {
    "timestamp": "2019-10-10T04:00:41.000",
    "producer": "prod2.hot",
    "confirmed": 0,
    "previous": "0024cd5eea050062d0534488c02e657fdc1817cdd0a1b3d1a7bd423089336395",
    "transaction_mroot": "0000000000000000000000000000000000000000000000000000000000000000",
    "action_mroot": "ad3ecd914d1f2405f7911e56a1e4fcac73081c2dcf4916fd29fe9aadc329fa9d",
    "schedule_version": 1,
    "header_extensions": [],
    "producer_signature": "SIG_K1_KYQLhFMEVTQLWX4JRk3ttnXa7SiXMMvpSUFtJ2j664BnkeWgUXgwqLR8G4E8gn92zHpT9Bw6p18y9VAJQKMkB31TFRNJbd"
  },
  "pending_schedule": {
    "schedule_lib_num": 216,
    "schedule_hash": "3f3d35ea44eeb7831a8945f7fc090c841dc20f358a96d414d5fbc4110c5925a2",
    "schedule": {
      "version": 1,
      "producers": []
    }
  },
  "activated_protocol_features": {
    "protocol_features": []
  }
}
```
### get_abi

>`POST` http://{host}:{port}/v1/chain/get_abi

get ABI of contract by account name.

#### PARAMETERS
{: .no_toc }

* account_name:  representation of privileged NODEHOT name type


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_abi \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"account_name":"eosio.token"}'
```


#### Response
{: .no_toc }
```json
{
  "account_name": "eosio.token",
  "abi": {
    "version": "eosio::abi/1.1",
    "types": [],
    "structs": [
      {
        "name": "account",
        "base": "",
        "fields": [
          {
            "name": "balance",
            "type": "asset"
          }
        ]
      },
      {
        "name": "close",
        "base": "",
        "fields": [
          {
            "name": "owner",
            "type": "name"
          },
          {
            "name": "symbol",
            "type": "symbol"
          }
        ]
      },
      {
        "name": "create",
        "base": "",
        "fields": [
          {
            "name": "issuer",
            "type": "name"
          },
          {
            "name": "maximum_supply",
            "type": "asset"
          }
        ]
      },
      {
        "name": "currency_stats",
        "base": "",
        "fields": [
          {
            "name": "supply",
            "type": "asset"
          },
          {
            "name": "max_supply",
            "type": "asset"
          },
          {
            "name": "issuer",
            "type": "name"
          }
        ]
      },
      {
        "name": "issue",
        "base": "",
        "fields": [
          {
            "name": "to",
            "type": "name"
          },
          {
            "name": "quantity",
            "type": "asset"
          },
          {
            "name": "memo",
            "type": "string"
          }
        ]
      },
      {
        "name": "open",
        "base": "",
        "fields": [
          {
            "name": "owner",
            "type": "name"
          },
          {
            "name": "symbol",
            "type": "symbol"
          },
          {
            "name": "ram_payer",
            "type": "name"
          }
        ]
      },
      {
        "name": "retire",
        "base": "",
        "fields": [
          {
            "name": "quantity",
            "type": "asset"
          },
          {
            "name": "memo",
            "type": "string"
          }
        ]
      },
      {
        "name": "transfer",
        "base": "",
        "fields": [
          {
            "name": "from",
            "type": "name"
          },
          {
            "name": "to",
            "type": "name"
          },
          {
            "name": "quantity",
            "type": "asset"
          },
          {
            "name": "memo",
            "type": "string"
          }
        ]
      }
    ],
    "actions": [
      {
        "name": "close",
        "type": "close",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Close Token Balance\nsummary: 'Close {{nowrap owner}}’s zero quantity balance'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/token.png#207ff68b0406eaa56618b08bda81d6a0954543f36adc328ab3065f31a5c5d654\n---\n\n{{owner}} agrees to close their zero quantity balance for the {{symbol_to_symbol_code symbol}} token.\n\nRAM will be refunded to the RAM payer of the {{symbol_to_symbol_code symbol}} token balance for {{owner}}."
      },
      {
        "name": "create",
        "type": "create",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Create New Token\nsummary: 'Create a new token'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/token.png#207ff68b0406eaa56618b08bda81d6a0954543f36adc328ab3065f31a5c5d654\n---\n\n{{$action.account}} agrees to create a new token with symbol {{asset_to_symbol_code maximum_supply}} to be managed by {{issuer}}.\n\nThis action will not result any any tokens being issued into circulation.\n\n{{issuer}} will be allowed to issue tokens into circulation, up to a maximum supply of {{maximum_supply}}.\n\nRAM will deducted from {{$action.account}}’s resources to create the necessary records."
      },
      {
        "name": "issue",
        "type": "issue",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Issue Tokens into Circulation\nsummary: 'Issue {{nowrap quantity}} into circulation and transfer into {{nowrap to}}’s account'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/token.png#207ff68b0406eaa56618b08bda81d6a0954543f36adc328ab3065f31a5c5d654\n---\n\nThe token manager agrees to issue {{quantity}} into circulation, and transfer it into {{to}}’s account.\n\n{{#if memo}}There is a memo attached to the transfer stating:\n{{memo}}\n{{/if}}\n\nIf {{to}} does not have a balance for {{asset_to_symbol_code quantity}}, or the token manager does not have a balance for {{asset_to_symbol_code quantity}}, the token manager will be designated as the RAM payer of the {{asset_to_symbol_code quantity}} token balance for {{to}}. As a result, RAM will be deducted from the token manager’s resources to create the necessary records.\n\nThis action does not allow the total quantity to exceed the max allowed supply of the token."
      },
      {
        "name": "open",
        "type": "open",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Open Token Balance\nsummary: 'Open a zero quantity balance for {{nowrap owner}}'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/token.png#207ff68b0406eaa56618b08bda81d6a0954543f36adc328ab3065f31a5c5d654\n---\n\n{{ram_payer}} agrees to establish a zero quantity balance for {{owner}} for the {{symbol_to_symbol_code symbol}} token.\n\nIf {{owner}} does not have a balance for {{symbol_to_symbol_code symbol}}, {{ram_payer}} will be designated as the RAM payer of the {{symbol_to_symbol_code symbol}} token balance for {{owner}}. As a result, RAM will be deducted from {{ram_payer}}’s resources to create the necessary records."
      },
      {
        "name": "retire",
        "type": "retire",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Remove Tokens from Circulation\nsummary: 'Remove {{nowrap quantity}} from circulation'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/token.png#207ff68b0406eaa56618b08bda81d6a0954543f36adc328ab3065f31a5c5d654\n---\n\nThe token manager agrees to remove {{quantity}} from circulation, taken from their own account.\n\n{{#if memo}} There is a memo attached to the action stating:\n{{memo}}\n{{/if}}"
      },
      {
        "name": "transfer",
        "type": "transfer",
        "ricardian_contract": "---\nspec_version: \"0.2.0\"\ntitle: Transfer Tokens\nsummary: 'Send {{nowrap quantity}} from {{nowrap from}} to {{nowrap to}}'\nicon: http://127.0.0.1/ricardian_assets/eosio.contracts/icons/transfer.png#5dfad0df72772ee1ccc155e670c1d124f5c5122f1d5027565df38b418042d1dd\n---\n\n{{from}} agrees to send {{quantity}} to {{to}}.\n\n{{#if memo}}There is a memo attached to the transfer stating:\n{{memo}}\n{{/if}}\n\nIf {{from}} is not already the RAM payer of their {{asset_to_symbol_code quantity}} token balance, {{from}} will be designated as such. As a result, RAM will be deducted from {{from}}’s resources to refund the original RAM payer.\n\nIf {{to}} does not have a balance for {{asset_to_symbol_code quantity}}, {{from}} will be designated as the RAM payer of the {{asset_to_symbol_code quantity}} token balance for {{to}}. As a result, RAM will be deducted from {{from}}’s resources to create the necessary records."
      }
    ],
    "tables": [
      {
        "name": "accounts",
        "index_type": "i64",
        "key_names": [],
        "key_types": [],
        "type": "account"
      },
      {
        "name": "stat",
        "index_type": "i64",
        "key_names": [],
        "key_types": [],
        "type": "currency_stats"
      }
    ],
    "ricardian_clauses": [],
    "error_messages": [],
    "abi_extensions": [],
    "variants": []
  }
}
```
### get_currency_balance

>`POST` http://{host}:{port}/v1/chain/get_currency_balance

#### PARAMETERS
{: .no_toc }

* code:  String representation of privileged NODEHOT name type
* account:  representation of privileged NODEHOT name type
* symbol:  A string representation of an NODEHOT symbol, composed of a float with a precision of 4, and a symbol composed of capital letters between 1-7 letters separated by a space, example `1.0000 ABC`.


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_currency_balance \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"code":"eosio.token","account":"hottestaccnt","symbol":"HOT"}'
```

#### Response
{: .no_toc }
```json
["200.000000 HOT"]
```
### get_currency_stats

>`POST` http://{host}:{port}/v1/chain/get_currency_stats

#### PARAMETERS
{: .no_toc }

* code:  String representation of privileged NODEHOT name type
* symbol:  A string representation of an NODEHOT symbol, composed of a float with a precision of 4, and a symbol composed of capital letters between 1-7 letters separated by a space, example `1.0000 ABC`.


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_currency_stats \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"code":"eosio.token","symbol":"HOT"}'
```

#### Response
{: .no_toc }
```json
{
  "HOT": {
    "supply": "10000000.000000 HOT",
    "max_supply": "10000000000.000000 HOT",
    "issuer": "eosio"
  }
}
```
### get_required_keys

Returns the required keys needed to sign a transaction.

>`POST` http://{host}:{port}/v1/chain/get_required_keys

#### PARAMETERS
{: .no_toc }

* transaction:  transaction object
  * expiration:  string, Time that transaction must be confirmed by.
  * ref_block_num: int32
  * ref_block_prefix: int32
  * max_net_usage_words: number
  * max_cpu_usage_ms: number
  * delay_sec: int32
  * context_free_actions: array of objects
  * actions: array of objects
    * account: String representation of privileged NODEHOT name type
    * name: String C++ variable signature
    * authorization: array of objects
      * actor: String representation of privileged NODEHOT name type
      * permission: String representation of privileged NODEHOT name type
    * data: string
    * hex_data: string
  * transaction_extensions: array
* available_keys: Provide the available keys


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_required_keys \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "transaction": {
    "expiration": "2019-10-10T05:02:23",
    "ref_block_num": 21457,
    "ref_block_prefix": 174944974,
    "max_net_usage_words": 0,
    "max_cpu_usage_ms": 0,
    "delay_sec": 0,
    "context_free_actions": [],
    "actions": [{
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [{
            "actor": "hot",
            "permission": "active"
          }
        ],
        "data": "000000000000326d0000c8b48190e8ade0c810000000000006484f54000000000568656c6c6f"
      }
    ],
    "transaction_extensions": []
  },
  "available_keys": [
    "key1",
    "key2",
    "key3"
  ]
}'
```

#### Response
{: .no_toc }
```json
{
  "required_keys": [
    "key2"
  ]
}
```
### get_code

Returns an object containing rows from the specified table.

>`POST` http://{host}:{port}/v1/chain/get_code

#### PARAMETERS
{: .no_toc }

* account_name: string, representation of privileged NODEHOT name type
* code_as_wasm: int32, This must be 1 (true)


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_code \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"account_name":"hottestaccnt","code_as_wasm":1}'
```

### get_table_rows

Returns an object containing rows from the specified table.

>`POST` http://{host}:{port}/v1/chain/get_table_rows

#### PARAMETERS
{: .no_toc }

* code\*: string, The name of the smart contract that controls the provided table
* table\*: string, The name of the table to query
* scope\*: string, The account to which this data belongs
* json: boolean, return result in JSON format
* index_position: string, Position of the index used, accepted parameters primary, secondary, tertiary, fourth, fifth, sixth, seventh, eighth, ninth , tenth
* key_type: string, Type of key specified by index_position (for example - uint64_t or name)
* encode_type: string, 
* upper_bound: string, Filters results to return the first element that is greater than provided value in set
* lower_bound: string, Filters results to return the first element that is not less than provided value in set
* limit: int32, Limit number of results returned.


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/chain/get_table_rows \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"json": true,"code": "eosio","scope": "eosio","table": "rammarket","limit": 10}'
```

#### Response
{: .no_toc }
```json
{
    "rows": [
        {
            "supply": "10000000000.0000 RAMCORE",
            "base": {
                "balance": "68640913783 RAM",
                "weight": "0.50000000000000000"
            },
            "quote": {
                "balance": "10011.445540 HOT",
                "weight": "0.50000000000000000"
            }
        }
    ],
    "more": false
}
```
## HISTORY API
> This API endpoint relies on history_plugin which has been deprecated.
### get_actions

>`POST` http://{host}:{port}/v1/history/get_actions

#### PARAMETERS
{: .no_toc }

* pos: int32
* offset: int32
* account_name: string


#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/history/get_actions \
  --header 'content-type: application/json' \
  --data '{"pos":"-1","offset":"-20","account_name":"hottestaccnt"}'
```

#### Response
{: .no_toc }
```json
{
  "actions": [
    {
      "global_action_seq": 2123622,
      "account_action_seq": 0,
      "block_num": 2121061,
      "block_time": "2019-10-08T11:37:16.000",
      "action_trace": {
        "action_ordinal": 3,
        "creator_action_ordinal": 1,
        "closest_unnotified_ancestor_action_ordinal": 1,
        "receipt": {
          "receiver": "hottestaccnt",
          "act_digest": "c91f6fb3a9db9fa3141b6aeea3136e530d74d3411f672816102afa342147d6a1",
          "global_sequence": 2123622,
          "recv_sequence": 1,
          "auth_sequence": [
            [
              "hot2u335csy1",
              21
            ]
          ],
          "code_sequence": 1,
          "abi_sequence": 1
        },
        "receiver": "hottestaccnt",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [
            {
              "actor": "hot2u335csy1",
              "permission": "active"
            }
          ],
          "data": {
            "from": "hot2u335csy1",
            "to": "hottestaccnt",
            "quantity": "200.000000 HOT",
            "memo": ""
          },
          "hex_data": "103c46650c2d326d902742266395336d00c2eb0b0000000006484f540000000000"
        },
        "context_free": false,
        "elapsed": 6,
        "console": "",
        "trx_id": "0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8",
        "block_num": 2121061,
        "block_time": "2019-10-08T11:37:16.000",
        "producer_block_id": "00205d65433af1c0177f9e2afe69c704834ee50371438f8988ed417961a5de0e",
        "account_ram_deltas": [],
        "except": null,
        "error_code": null
      }
    }
  ],
  "last_irreversible_block": 2421424
}
```
> This API endpoint relies on history_plugin which has been deprecated.
### get_transaction

>`POST` http://{host}:{port}/v1/history/get_transaction

#### PARAMETERS
{: .no_toc }

* id: string, tx id
* block_num_hint: int32

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/history/get_actions \
  --header 'content-type: application/json' \
  --data '{"id":"0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8", "block_num_hint":"2121061"}'
```

#### Response
{: .no_toc }
```json
{
  "id": "0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8",
  "trx": {
    "receipt": {
      "status": "executed",
      "cpu_usage_us": 488,
      "net_usage_words": 16,
      "trx": [
        1,
        {
          "signatures": [
            "SIG_K1_Kfdwr3t1saMmSgNwG73t6J9nwpq3ocL7o6n1wXXph6SHf3Ur2nYRb8mnYfQEsfz2W9KAPsySqjzvko4GzrkuBxF3VxhdwC"
          ],
          "compression": "none",
          "packed_context_free_data": "",
          "packed_trx": "27759c5d205d8ec3a859000000000100a6823403ea3055000000572d3ccdcd01103c46650c2d326d00000000a8ed323221103c46650c2d326d902742266395336d00c2eb0b0000000006484f54000000000000"
        }
      ]
    },
    "trx": {
      "expiration": "2019-10-08T11:38:15",
      "ref_block_num": 23840,
      "ref_block_prefix": 1504232334,
      "max_net_usage_words": 0,
      "max_cpu_usage_ms": 0,
      "delay_sec": 0,
      "context_free_actions": [],
      "actions": [
        {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [
            {
              "actor": "hot2u335csy1",
              "permission": "active"
            }
          ],
          "data": {
            "from": "hot2u335csy1",
            "to": "hottestaccnt",
            "quantity": "200.000000 HOT",
            "memo": ""
          },
          "hex_data": "103c46650c2d326d902742266395336d00c2eb0b0000000006484f540000000000"
        }
      ],
      "transaction_extensions": [],
      "signatures": [
        "SIG_K1_Kfdwr3t1saMmSgNwG73t6J9nwpq3ocL7o6n1wXXph6SHf3Ur2nYRb8mnYfQEsfz2W9KAPsySqjzvko4GzrkuBxF3VxhdwC"
      ],
      "context_free_data": []
    }
  },
  "block_time": "2019-10-08T11:37:16.000",
  "block_num": 2121061,
  "last_irreversible_block": 2422684,
  "traces": [
    {
      "action_ordinal": 1,
      "creator_action_ordinal": 0,
      "closest_unnotified_ancestor_action_ordinal": 0,
      "receipt": {
        "receiver": "eosio.token",
        "act_digest": "c91f6fb3a9db9fa3141b6aeea3136e530d74d3411f672816102afa342147d6a1",
        "global_sequence": 2123620,
        "recv_sequence": 645,
        "auth_sequence": [
          [
            "hot2u335csy1",
            19
          ]
        ],
        "code_sequence": 1,
        "abi_sequence": 1
      },
      "receiver": "eosio.token",
      "act": {
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [
          {
            "actor": "hot2u335csy1",
            "permission": "active"
          }
        ],
        "data": {
          "from": "hot2u335csy1",
          "to": "hottestaccnt",
          "quantity": "200.000000 HOT",
          "memo": ""
        },
        "hex_data": "103c46650c2d326d902742266395336d00c2eb0b0000000006484f540000000000"
      },
      "context_free": false,
      "elapsed": 136,
      "console": "",
      "trx_id": "0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8",
      "block_num": 2121061,
      "block_time": "2019-10-08T11:37:16.000",
      "producer_block_id": "00205d65433af1c0177f9e2afe69c704834ee50371438f8988ed417961a5de0e",
      "account_ram_deltas": [
        {
          "account": "hot2u335csy1",
          "delta": 240
        }
      ],
      "except": null,
      "error_code": null
    },
    {
      "action_ordinal": 2,
      "creator_action_ordinal": 1,
      "closest_unnotified_ancestor_action_ordinal": 1,
      "receipt": {
        "receiver": "hot2u335csy1",
        "act_digest": "c91f6fb3a9db9fa3141b6aeea3136e530d74d3411f672816102afa342147d6a1",
        "global_sequence": 2123621,
        "recv_sequence": 10,
        "auth_sequence": [
          [
            "hot2u335csy1",
            20
          ]
        ],
        "code_sequence": 1,
        "abi_sequence": 1
      },
      "receiver": "hot2u335csy1",
      "act": {
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [
          {
            "actor": "hot2u335csy1",
            "permission": "active"
          }
        ],
        "data": {
          "from": "hot2u335csy1",
          "to": "hottestaccnt",
          "quantity": "200.000000 HOT",
          "memo": ""
        },
        "hex_data": "103c46650c2d326d902742266395336d00c2eb0b0000000006484f540000000000"
      },
      "context_free": false,
      "elapsed": 6,
      "console": "",
      "trx_id": "0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8",
      "block_num": 2121061,
      "block_time": "2019-10-08T11:37:16.000",
      "producer_block_id": "00205d65433af1c0177f9e2afe69c704834ee50371438f8988ed417961a5de0e",
      "account_ram_deltas": [],
      "except": null,
      "error_code": null
    },
    {
      "action_ordinal": 3,
      "creator_action_ordinal": 1,
      "closest_unnotified_ancestor_action_ordinal": 1,
      "receipt": {
        "receiver": "hottestaccnt",
        "act_digest": "c91f6fb3a9db9fa3141b6aeea3136e530d74d3411f672816102afa342147d6a1",
        "global_sequence": 2123622,
        "recv_sequence": 1,
        "auth_sequence": [
          [
            "hot2u335csy1",
            21
          ]
        ],
        "code_sequence": 1,
        "abi_sequence": 1
      },
      "receiver": "hottestaccnt",
      "act": {
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [
          {
            "actor": "hot2u335csy1",
            "permission": "active"
          }
        ],
        "data": {
          "from": "hot2u335csy1",
          "to": "hottestaccnt",
          "quantity": "200.000000 HOT",
          "memo": ""
        },
        "hex_data": "103c46650c2d326d902742266395336d00c2eb0b0000000006484f540000000000"
      },
      "context_free": false,
      "elapsed": 6,
      "console": "",
      "trx_id": "0d40ff25a0f4e55e61b84f8caa2db69ef6f6bf79a5ab7b4a2f2bbe83e17cb4f8",
      "block_num": 2121061,
      "block_time": "2019-10-08T11:37:16.000",
      "producer_block_id": "00205d65433af1c0177f9e2afe69c704834ee50371438f8988ed417961a5de0e",
      "account_ram_deltas": [],
      "except": null,
      "error_code": null
    }
  ]
}
```
### get_key_accounts

>`POST` http://{host}:{port}/v1/history/get_key_accounts

#### PARAMETERS
{: .no_toc }

* public_key: string

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://localhost:8080/v1/history/get_key_accounts \
  --header 'content-type: application/json' \
  --data '{"public_key":"key"}'
```

#### Response
{: .no_toc }
```json
{
    "account_names": [
        "cryptkeeper",
        "example"
    ]
}
```
