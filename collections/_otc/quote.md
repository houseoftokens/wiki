---
title: Quotations
chapter: 2
layout: default
---

#Quotations

##Create a new quotation

First of all, you should become a market maker before you can make a new quotation. 

For more information about Market Maker, please check [Apply to be a Market Maker](marketmaker)

1. If you have already became a market marker, you can find the '+' on the [OTC HOME](https://otc.hotwallet.tech/)

    <img src="/assets/images/otc_quote_creation_entrance.png" style="width:202px;" alt="entrance">

2. Click the '+' you'll see the creation tab

    <img src="/assets/images/otc_creation_tab.png" style="width:400px;" alt="creation tab">

    1. `Type` (Buy,Sell) represents whether the quotation is for purchase or for sale. Please note that this refers to the user's perspective, it means when a quotation with `Buy` type is created, it's a sell quotation for the market maker.
    2. `Quote Currency` represents the digital currency which you sell or buy.
    3. `Pricing Strategies` has only one value `Limit Pricing` you can choose currently.
    4. `Price` represents the price of the digital currency. In the strategy of `Limit Pricing` you must make manual adjustment while pricing is changed.
    5. `Base Currency` represents the currency of the fiat money which used in this quotation for trading.
    6. `Stock` represents the total volume of this quotation.
    7. `Min Amount` and `Max Amount` represents the limit of min and max amount that can be traded in one single order.
    8. `Payment Method` represents payment method you can support.
    9. `Requires ID verify` is a restriction on the order user. When checked, user with ID verification approved can make order.
    10. `Requires Mobile Phone` is a restriction on the order user. When checked, user with mobile phone bound can make order.
    11. `Serving only designated users` is a restriction on the order user. If you want to serve designated customers you can fill in these nicks here, 3 at most.
    
3. Precautions

    1. When a quotation of type `Buy` is creating, system will check if the market maker's OTC balance is enough and the corresponding amount of balance will be froze till the quotation is cancelled or finished. 
    2. Only one quotation with same `Quote Currency`, `Base Currency` and `Type` value can be put online, set it `Offline` before you create a new one.
    
##Manage quotation

You can manage you quotations on the [QUOTATIONS page](https://otc.hotwallet.tech/my/quotations)

The fields you can modify is listed below:

1. `Price`
2. `Min Amount`
3. `Max Amount`
4. `Visibility`
5. `Payment Method`
6. `Requires ID verify`
7. `Requires Mobile Phone`
8. `Serving only designated users`

##Status of quotation

the values of status is listed below:

1. `Normal` means the quotation is online and user can view it at [Quotation List](https://otc.hotwallet.tech/)
2. `Offline` means the quotation is offline and will be removed from the online quotation list.
3. `Cancelled` means the quotation is deleted by the market maker.
4. `System Off` means the quotation is forced offline by the system, when:
    1. Market maker cancels at least 3 orders within 24h.
    2. The quotation has 5 unfinished orders.
5. `End` means the quotation is finished.
    1. Total amount of finished orders is equal to the stock of the quotation.
    2. The available stock is less than the `Min Amount`.