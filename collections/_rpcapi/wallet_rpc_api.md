---
title: Wallet RPC API
chapter: 2
layout: default

---

# Wallet RPC API

{: .no_toc }
### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc} 

### create

Creates a new wallet with the given name.

>`POST` http://{host}:{port}/v1/wallet/create

#### PARAMETERS
{: .no_toc }
* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/create \
  --header 'content-type: application/json' \
  --data '"Provide the name of the wallet to create"'
```

#### Response
{: .no_toc }
```json
"PW5JfVLr1z9937vq2RkeoyMLHzjpN4o5cja5smosZxA56ex4dP26m"
```

### open

Opens an existing wallet of the given name.

>`POST` http://{host}:{port}/v1/wallet/open

#### PARAMETERS
{: .no_toc }
* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/open \
  --header 'content-type: application/json' \
  --data '"Provide the name of the wallet to open"'
```

#### Response
{: .no_toc }
```json
{}
```

### lock

Locks an existing wallet of the given name.

>`POST` http://{host}:{port}/v1/wallet/lock

#### PARAMETERS
{: .no_toc }
* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/lock \
  --header 'content-type: application/json' \
  --data '"Provide the name of the wallet to lock"'
```

#### Response
{: .no_toc }
```json
{}
```

### lock_all

Locks all existing wallets.

>`POST` http://{host}:{port}/v1/wallet/lock_all

#### PARAMETERS
{: .no_toc }
* none

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/lock_all \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8'
```

#### Response
{: .no_toc }
```json
{}
```

### unlock

Unlocks a wallet with the given name and password.

>`POST` http://{host}:{port}/v1/wallet/unlock

#### PARAMETERS
{: .no_toc }

* name string: name of wallet
* Password string: password of wallet

```json
[
  "default",
  "PW5JfVLr1z9937vq2RkeoyMLHzjpN4o5cja5smosZxA56ex4dP26m"
]
```

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/unlock \
  --header 'content-type: application/json' \
  --data '["default","PW5JfVLr1z9937vq2RkeoyMLHzjpN4o5cja5smosZxA56ex4dP26m"]'
```

#### Response
{: .no_toc }
```json
{}
```

### import_key

Imports a private key to the wallet of the given name.

>`POST` http://{host}:{port}/v1/wallet/import_key

#### PARAMETERS
{: .no_toc }
* name string: wallet name
* private_key string: private key to import
```json
[
  "default",
  "5JEKna11vakEhKVxtRn7WsfoR62hqcvQE4cButSgEi7BGrhEqdV"
]
```

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/import_key \
  --header 'content-type: application/json' \
  --data '["default","5JEKna11vakEhKVxtRn7WsfoR62hqcvQE4cButSgEi7BGrhEqdV"]'
```

#### Response
{: .no_toc }
```json
{}
```

### list_wallets

Lists all wallets.

>`POST` http://{host}:{port}/v1/wallet/list_wallets

#### PARAMETERS
{: .no_toc }
* none

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/list_wallets \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8'
```

#### Response
{: .no_toc }

Wallets managed by RPC service

```json
[
  "default *"
]
```

### create_key

Create a key pair in wallet

>`POST` http://{host}:{port}/wallet/create_key

#### PARAMETERS
{: .no_toc }

* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }

```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/create_key \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8' \
  --data '"Provide the name of the wallet"'
```

#### Response
{: .no_toc }

```json
"HOT8G8RDUuHbtic2x4hjRhWvZVaSemukRABwFohsej5L9Kcq3tMkF"
```

### list_keys

Lists all key pairs across all wallets.

>`POST` http://{host}:{port}/v1/wallet/list_keys

#### PARAMETERS
{: .no_toc }
* Wallet name and wallet password
```json
[
  "default",
  "PW5JfVLr1z9937vq2RkeoyMLHzjpN4o5cja5smosZxA56ex4dP26m"
]
```

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/list_keys \
  --header 'content-type: application/json' \
  --data '["default","PW5JfVLr1z9937vq2RkeoyMLHzjpN4o5cja5smosZxA56ex4dP26m"]'
```

#### Response
{: .no_toc }
```json
[[
    "HOT7QeAEonn6LZ8X7oCiBFo26Ab8QaUACfu66XftY9ZrUbRYYH3HF",
    "5HryZkxonggWK9mq24zfaYEZSqTf3Bosws7rspe42n4Lboqsibf"
  ],[
    "HOT7uy4dDjvhUC94vu4E1Mo7mDDKVDSRmw6BWRTmoMgdXfLT6HH1k",
    "5JEKna11vakEhKVxtRn7WsfoR62hqcvQE4cButSgEi7BGrhEqdV"
  ]
]
```


### get_public_keys

Lists all public keys across all wallets.

>`POST` http://{host}:{port}/v1/wallet/get_public_keys

#### PARAMETERS
{: .no_toc }
* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/list_keys \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8' \
  --data '"Provide the name of the wallet"'
```

#### Response
{: .no_toc }
```json
[
  "HOT7QeAEonn6LZ8X7oCiBFo26Ab8QaUACfu66XftY9ZrUbRYYH3HF",
  "HOT7uy4dDjvhUC94vu4E1Mo7mDDKVDSRmw6BWRTmoMgdXfLT6HH1k"
]
```

### get_public_keys

Lists all public keys across all wallets.

>`POST` http://{host}:{port}/v1/wallet/get_public_keys

#### PARAMETERS
{: .no_toc }
* RAW_BODY string: name of wallet

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/list_keys \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8' \
  --data '"Provide the name of the wallet to create"'
```

#### Response
{: .no_toc }
```json
[
  "HOT7QeAEonn6LZ8X7oCiBFo26Ab8QaUACfu66XftY9ZrUbRYYH3HF",
  "HOT7uy4dDjvhUC94vu4E1Mo7mDDKVDSRmw6BWRTmoMgdXfLT6HH1k"
]
```

### sign_transaction

Signs a transaction.

>`POST` http://{host}:{port}/wallet/create_key

#### PARAMETERS
{: .no_toc }
* txn string: transaction to be signed
* keys string: public keys to sign this transaction
* id string: transaction id

```json
[{
    "expiration": "2019-12-02T08:37:33",
    "ref_block_num": 1785,
    "ref_block_prefix": 3041157403,
    "max_net_usage_words": 0,
    "max_cpu_usage_ms": 0,
    "delay_sec": 0,
    "context_free_actions": [],
    "actions": [{
        "account": "eosio.token",
        "name": "transfer",
        "authorization": [{
            "actor": "hottestacct",
            "permission": "active"
          }
        ],
        "data": "0000000000ea3055000000000000326de0c810000000000006484f54000000000568656c6c6f"
      }
    ],
    "transaction_extensions": [],
    "signatures": [],
    "context_free_data": []
  },[
    "HOT8G8RDUuHbtic2x4hjRhWvZVaSemukRABwFohsej5L9Kcq3tMkF"
  ],
  "bbead5089c0f2aa7da26a555d2901e82c179745eac26622bed4307137df75663"
]
```

#### CURL
{: .no_toc }
```bash
curl --request POST \
  --url http://{host}:{port}/v1/wallet/create_key \
  --header 'content-type: application/x-www-form-urlencoded; charset=UTF-8' \
  --data '[{"expiration":"2019-12-02T08:37:33","ref_block_num":1785,"ref_block_prefix":3041157403,"max_net_usage_words":0,"max_cpu_usage_ms":0,"delay_sec":0,"context_free_actions":[],"actions":[{"account":"eosio.token","name":"transfer","authorization":[{"actor":"hottestacct","permission":"active"}],"data":"0000000000ea3055000000000000326de0c810000000000006484f54000000000568656c6c6f"}],"transaction_extensions":[],"signatures":[],"context_free_data":[]},["HOT8G8RDUuHbtic2x4hjRhWvZVaSemukRABwFohsej5L9Kcq3tMkF"],"bbead5089c0f2aa7da26a555d2901e82c179745eac26622bed4307137df75663"]'
```

#### Response
{: .no_toc }
```json
{
  "expiration": "2019-12-02T08:37:33",
  "ref_block_num": 1785,
  "ref_block_prefix": 3041157403,
  "max_net_usage_words": 0,
  "max_cpu_usage_ms": 0,
  "delay_sec": 0,
  "context_free_actions": [],
  "actions": [{
      "account": "eosio.token",
      "name": "transfer",
      "authorization": [{
          "actor": "hottestacct",
          "permission": "active"
        }
      ],
      "data": "0000000000ea3055000000000000326de0c810000000000006484f54000000000568656c6c6f"
    }
  ],
  "transaction_extensions": [],
  "signatures": [
    "SIG_K1_K6bgndosj9c2i6ShyFuiqMLCBDsbT5SXxn9iiTUGg3zaaTdxXXkihp76k3pUvhs5F7zyQ9y9M4zi9ugNkqjeFUL9BohGar"
  ],
  "context_free_data": []
}
```