---
title: Orders
chapter: 4
layout: default
---

# Orders

At [OTC Home](https://otc.hotwallet.tech) user can place `Buy` or `Sell` orders with market makers.

`HGBP` is the only digital asset that can be traded by now.

User can choose different fiat currency to trade with `HGBP`, including GBP, USD, EUR, CNY.

## Place an order

At [OTC Home](https://otc.hotwallet.tech) user can view the [Quotation](quote) list created by market makers.

If user's account meets the requirements of the quotation, `Buy` or `Sell` button is shown at the end of the quotation.

<img src="/assets/images/place_order.png" style="width:801px;" alt="place_order">

1. The fiat currency user has selected.
2. The type of the quotation, `Buy` or `Sell`;
3. The quotation information, including:
    * Order completion info of market maker.
    * The stock info(Available/Total) of the quotation.
    * The amount limits of a single order.
    * The price of the digital asset.
    * Payment method supported by the quotation.
4. The amount user wants to buy or sell. Both blanks can be filled.
5. Payment method to be chosen.
6. Submit or cancel the order.

## Operating Order

After user places an order, the page will be redirected to the order details to complete the transaction.

<img src="/assets/images/order_details.png" style="width:801px;" alt="order_details">

This page has four main functional areas:

* Order value information including the amount of the digital asset and fiat money.
* Payment information including the seller's payment method details, the reference ID, and the expiration tips.
* Operation area that both parties can operate the order
* Chat window where both parties can chat directly in real time. The chat window will be closed one hour after the order is completed.

## Pay order

The buyer of the order must make a payment of fiat money to the counter party within 20 minutes. After the payment is completed, buyer can click the `Pay` button to finish payment.

<img src="/assets/images/order_paid.png" style="width:801px;" alt="order_paid">

* Both parties of the order can view each other's mobile phone 2 minutes after the payment is completed in case of emergency calls.
* Both parties can initiate a complaint by clicking `Appeal` button when the following situations happen:
    * Buyer does not make payment but click the `Pay` button marking the order is paid.
    * Seller does not release the digital asset for quite a long time.
    
## Appeal Order

If the application of complaint is made, the customer service will chat at the chat window to ask the proof of the payment. And Customer service can make the judgement according to the payment details supplied by the buyer of the order.

<img src="/assets/images/order_appeal.png" style="width:801px;" alt="order_appeal">

Also the applicant can withdraw the request, after that the order can be finished by the seller.

The result of losing:

* The number of complaint info will be updated.
* The market maker will be forbidden to trade for 7 days.
* The user will be forbidden to trade for 48 hours. If the total losing number reaches 3, user will be forbidden at OTC for ever.

## Release Order

In most cases, the seller can release the assets to the buyer after checking the fiat money payment by clicking the `Release` button 

* Order will be marked as completed.
* Digital asset will be added to the buyer's balance
* The chat window will be closed one hour later.

## Cancel Order/Order Expired

Buyer can cancel the order for some reasons. 

If the buyer does not pay within 20 minutes, the order will be automatically expired.

* For user who cancelled/expired 3 orders within 24 hours will be forbidden to trade until the number expires.
* For market maker who cancelled/expired 3 orders within 24 hours will result in forcing offline all quotations until the number expires.