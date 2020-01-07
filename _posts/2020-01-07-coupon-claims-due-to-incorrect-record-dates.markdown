---
layout: post
title:  Record dates and coupon claims
date: 07 Jan 2020
tags: [settlement, asset-servicing]
---

You can find the previous post on [negative accrued interest here]({% post_url 2020-01-01-understanding-negative-accrued-interest %})

In the previous post, we discussed how settlement date can fall between record date and end date, leading to trades which should settle with negative accrued interest. 
In this post, we look at what happens when trading platforms do not contain accurate record dates and the operational burdens it creates.

## Record Dates in Trading Platforms

I hate to say this but in my experience, most trading platforms simply do not contain accurate record date information. 
Certain trading platforms do not even have the concept of record date. 
I have tried finding out why to no avail - let me know if you know why!

## The Operational Burden

Due to the missing record date information, bonds which should trade with negative accrued interest trade end up trading with postive accrued interest instead.

![Coupon Bar Diagram]({{ site.baseurl }}/assets/images/bar.png)

    A = Coupon from Start Date to Record Date
    B = Coupon from Record Date to Contractual Settlement Date
    C = Coupon from Contractual Settlement Date to End Date

As the trading platform is unaware of the record date, its calculations will be for the buyer to compensate the seller the accrued interest between start date to record date `(A + B)`.
As the seller holds the bond on record date, the seller ends up also receiving the coupon `(A + B + C)` which the seller should send back to the buyer through the coupon claim process

## The (Dreaded) Coupon Claim Process

The coupon claim is a deceptively tedious process[^1]. 
As the buyer, you will need to prepare a claim letter[^2] with your cash settlement instructions and email it to the seller[^3]. 
As the seller, you will need to verify the authenticity of the cash settlement instructions[^4] and process the payment[^5].
Depending on the volume and complications (refer to the footnotes) faced, this process has the potential to become a monstrosity.

## How This Might Be Resolved One Day (I Hope)

Coupon claims caued by incorrect record dates is simply unnecessary misery. We could cross our figners and hope that bond issuers eventually eliminate the gap between record date and end date. In the meantime, below are some of the actions you could possibly consider:

- If you work on trading platforms, ensure that record dates are present and used for accrued interest calculations.
- If you are a bond trader, speak to your trading platform and operations staff about this
- If you perform bond operations, advocate for accurate record dates on trading platforms in whatever ways you can

---

[^1]: Depending on the systems of the buyer (seller), they might not be even aware about the need for a coupon claim until they receive (do not recieve) the coupon
[^2]: As far as I am aware, there is no standardized or automated way  of performing a coupon claim (like a specific MT message) on a counterparty
[^3]: Operations teams of counterparties who do not trade bonds frequently often have issues understanding the coupon claim - perhaps you could direct them to this post
[^4]: Signature verification, callbacks, and the whole shebang
[^5]: I have heard of cases where the buyer refuses to accept the coupon for months - causing long outstanding nostro breaks for the seller