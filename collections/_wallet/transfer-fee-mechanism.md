---
title: Transfer Fee Mechanism
chapter: 3
layout: default
---

# Transfer Fee Mechanism

Most tokens on `HoT` platform are created and managed by  `eosio.token` contract, like `HOT` and `HGBP` . When transfering these tokens between `HoT` accounts, an extra amount of fee will be charged by `HoT` system.

We introduce this transfer fee mechanism for 2 reasons-

## 1. Avoid resource abuse

`HoT` is built based on `EOSIO` system. `EOSIO` provides a stake system to prevent system resource abuse, which works well most of the time. But when transaction traffic is heavy on `EOS` platform, resouse price may become extremely high. One has to stake thousands of `EOS` token to send a transaction on the platform.

To improve this situation, we charge a small share of fee for the `transfer` transaction, which is the most frequent type of transaction. 

This mechanism works togather with the original stake mechanism, which helps `HoT` platform to avoid resource abuse more effectively.

## 2. A way to sponsor producers

Producers are decentralized entities that govern the `HoT` platform. Producers will produce the blocks of the blockchain. 

As there is no regular inflation to sponsor producers on `HoT` platform, we need a different way to sponsor producers. Fees collected by transfer generates a pool for producers sponsor.

Every producer successfully created some blocks can claim it's share of earnings from the fee pool. This sponsor mechanism attractes more participant of the platform.

## Fee Rate

Fees are charged base on the amount of assets one  transfers. No matter what asset one transfers, HoT platform only charges HOT asset for fee. This means one has to have enough HOT asset to transfer any kind of asset.

For now, `HoT` fee rate is 1‰ or at least 0.001 HOT. 

> For example, Alice transfers  1011.2 HOT to Bob. Alice will spend 1011.2 + 1011.2 * 1 / 1000 = 1012.2112 HOT, and Bob will receive 1011.2 HOT,  1011.2 * 1 / 1000 = 1.0112 HOT will go to the fee pool.

> Another example, Alice transfers  0.00021 HGBP  to Bob. Alice will spend  0.00021 HGBP and  0.001 HOT for fee , and Bob will receive  0.00021 HGBP, 0.001 HOT will go to the fee pool.