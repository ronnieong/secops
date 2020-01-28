---
layout: post
title:  Memorable accrued interest conventions
date: 28 Jan 2020
tags: [settlement]
---

Accrued interest conventions are a pain. For anyone who has worked in product control or settlements, or have been tasked to improve STP rates, you probably get what I mean. 

In this blog entry, I share three groups of accrued interest conventions which have stuck with me over the years. They are usually both painfully funny and funnily painful.

## A quick background

For the uninitiated, transaction processing (TP) systems typically compute accrued interest independent of trading systems (based on security static data within the TP system). Where the TP system is unable to support the accrued interest (AI) convention, there will be an AI mismatch and a bunch of associated problems.

## Rounding half down

Why do we round 0.5 to 1 and not 0? If you draw them out on a line, 0.5 is equally close to 0 and 1. Rounding half up is the dominant convention but it is also arbitary. While uncommon, there are bond issuers out there [^1] who issue bonds which [round half down](https://en.wikipedia.org/wiki/Rounding#Round_half_down) in their accrued interest calculations.  

On the other hand, most TP systems do not support rounding half down. Heck, even Excel does not support this (at least Excel 2007). Naturally, this combination is a poor recipe for STP operations.

Side note: I feel like a weirdo for thinking so hard about rounding conventions

## Uncommon leap year day count conventions

Most TP systems can handle common leap year day count conventions -- for example, using A365 and A366 based on whether the coupon period ends in a non leap year or leap year. It is the uncommon leap year considerations where things get interesting, especially if you are a product owner.

Given these day count conventions are a) uncommon and b) happening around leap years only, prioritizing system enhancements to support them over other enhancements is close to impossible. Instead, these day count conventions typically recede into the background like guerilla fighters into the jungle as the year passes, biding their time for another metaphorical attack four years down the road.

## Inclusive accrued days 

How many days are between 28 Jan and 29 Jan? Most would say 1 day (MS Excel would agree)   
How many days are between the ~start~ of 28 Jan and the ~start~ of 29 Jan? Nearly all would say 1 day
How many days are between the ~start~ of 28 Jan and the ~end~ of 29 Jan? Nearly all would say 2 days

My point above is that when we calculate day differences between two dates without time, we typically and implicitly assume the time is the same across the two dates. When TP systems calculate accrued days, they typically make this same assumption. In my experience, this  works for almost all markets with a few exceptions[^2]. 

The interesting thing about this is that it got me wondering if time has a bigger part to play in the future of financial transactions. For example, in a intraday repo, the start date and the end date. If time was not made explicit (i.e. stated), processing the transaction would be impossible. On the other hand, stating time on every single date field would be really onerous!

---

[^1]: See type 716 of the [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) for an example of round half down
[^2]: See type 852 of the [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) for an example of inclusive accrued days