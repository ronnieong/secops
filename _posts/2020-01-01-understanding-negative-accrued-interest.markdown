---
layout: post
title:  How negative accrued interest occurs
date: 01 Jan 2020
tags: [settlement, asset-servicing]
---

In a typical bond trade, accrued interest [(Investopedia)](https://www.investopedia.com/terms/a/accruedinterest.asp) is paid by the bond buyer to the bond seller.
This is because the bond buyer is expected to receive the entire coupon and thus needs to compensate the bond seller for the period they have held the bond for. 

Negative accrued interest is when the opposite occurs.
Due to the contractual settlement date falling between record date and coupon end date, the bond seller is expected to receive the entire coupon instead.

## Record Date

The record date is the date on which the bond issuer refers to the `book of records` to determine which party is eligible to receive the upcoming coupon. For certain bonds, the record date can be significantly earlier than the coupon end date [^1].

Negative accrued interest occurs when contractual settlement date falls between record date and coupon end date. Since the seller holds the security on record date, they will receive the entire coupon and therefore need to compensate the buyer accordingly.

> Negative accrued interest occurs when contractual settlement date falls between record date and coupon end date

## A Diagram Perspective

Below is elaboration in the form of a diagram.

![Coupon Bar Diagram]({{ site.baseurl }}/assets/images/bar.png)

    A = Coupon from Start Date to Record Date
    B = Coupon from Record Date to Contractual Settlement Date
    C = Coupon from Contractual Settlement Date to End Date

As the seller holds the security on record date, the seller receives the entire coupon (A + B + C). However, as the buyer holds the bond from settlement date to end date, the buyer is required to be compensated by the seller for the interest accrued during that period (C).

## Trading Platforms

Accrued interest is determined at the point of trade by traders using `trading platform`. However, are the static data and accrued interest logic on these systems reliable? What implications would that have on operational staff? Stay tune for the followup post on static data and coupon claims headaches.

The follow up post has been published and can be found [here]({{ site.baseurl }}{% post_url 2020-01-07-coupon-claims-due-to-incorrect-record-dates %})

---

[^1]: Probably due to operational requirements. Hopefully, the typical gap between record date and end date can be narrowed and eliminated eventually.
