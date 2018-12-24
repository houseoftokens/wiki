---
title: Balance Management
chapter: 3
layout: default
---

# Balance Management

## Overview

There are 2 types of balance in the OTC system: 

 * OTC balance is the balance in the OTC system, it can be used when selling assets to the Market Maker.
 * Exchange balance is the balance of the HOT chain. It's different from OTC balance. It can't be used without transferring into OTC balance.

User can transfer these two kinds of balance to each other freely. No fee will be charged during transferring.

## Transfer between OTC and Exchange

If you have bought some asset to exchange at OTC  or you have asset at HOT chain to be sold, you can transfer the balance between the two systems.

User can manages it's balance at [BALANCES Page](https://otc.hotwallet.tech/balance)

Either modifying the number of OTC, EX balance or dragging the slider to assign a suitable ratio is fine.

<img src="/assets/images/balance_convert.png" style="width:401px;" alt="balance_tranfer">

Note: Operation of transferring balance between OTC and Exchange  needs to apply transaction on the HOT chain that will result in taking minutes to finish. User can check the progress of order at the same page. And new order can't be made with unfinished order.

## OTC to Exchange

1. User makes a transferring order at the OTC [BALANCES Page](https://otc.hotwallet.tech/balance)
2. User's OTC balance is deducted at the same time when the order is created.
3. A Transfer transaction request with the corresponding amount deducted from OTC balance is made.
4. Applying transaction of receipt on the HOT chain which will take minutes to finish.
5. After the transaction is done, the transferring order's status will be change to `Finished`.

## Exchange to OTC

1. User makes a transferring order at the OTC [BALANCES Page](https://otc.hotwallet.tech/balance)
2. A Transfer transaction request with the corresponding amount is made.
3. Applying transaction of deduction on the HOT chain which will take minutes to finish.
4. After the transaction is done, amount of balance from Exchange will be added to OTC balance.

## Balance History

At the [BALANCES Page](https://otc.hotwallet.tech/balance) you can check your detailed balance history.

<img src="/assets/images/balance_history.png" style="width:501px;" alt="balance_history">

Available `Type` of balance history:

 * `Transfer In` Transfer balance from Exchange to OTC.
 * `Transfer Out` Transfer balance from OTC to Exchange.
 * `Buy` Buy asset from Market Maker(User) or Buy asset from user(Market Maker).
 * `Sell` Sell asset to Market Maker(User) or Sell asset to user(Market Maker).
 * `Margin` Amount of HGBP frozen in the system for Market Maker.


