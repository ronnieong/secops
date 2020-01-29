---
layout: post
title:  Memorable accrued interest conventions
date: 28 Jan 2020
tags: [bonds, settlement]
---

Accrued interest conventions are a pain. For anyone who has worked in product control or settlements, or have been tasked to improve STP rates, you probably get what I mean. 

In this blog entry, I share three groups of accrued interest conventions which have stuck with me over the years. They are usually both painfully funny and funnily painful.

## A quick background

For the uninitiated, transaction processing (TP) systems typically compute accrued interest independent of trading systems (based on security static data within the TP system). Where the TP system is unable to support the accrued interest (AI) convention, there will be an AI mismatch and a bunch of associated problems.

## Rounding half down

Why do we round 0.5 to 1 and not 0? If you draw them out on a line, 0.5 is equally close to 0 and 1. Rounding half up is the dominant convention but it is also arbitrary. While uncommon, there are bond issuers out there [^1] who issue bonds which [round half down](https://en.wikipedia.org/wiki/Rounding#Round_half_down) in their accrued interest calculations.  

![Coupon Bar Diagram]({{ site.baseurl }}/assets/images/equidistant.png)

On the other hand, most TP systems do not support rounding half down. Heck, even Excel does not support this (at least Excel 2007). Naturally, this combination is a poor recipe for STP operations.

Side note: I feel like a weirdo for thinking so hard about rounding conventions

## Uncommon leap year day count conventions

Most TP systems can handle common leap year day count conventions -- for example, using A365 and A366 based on whether the coupon period ends in a non leap year or leap year. It is the uncommon leap year considerations where things get interesting, especially if you are a product owner.

Given these day count conventions are a) uncommon and b) happening around leap years only, prioritizing system enhancements to support them over other enhancements is close to impossible. Instead, these day count conventions typically recede into the background like guerilla fighters into the jungle as the year passes, biding their time for another metaphorical attack four years down the road.

## Inclusive accrued days 

    How many days are between 28 Jan and 30 Jan? Most would say 2 days (MS Excel would agree)   
    How many days are between the SOD of 28 Jan and the SOD of 30 Jan? Nearly all would say 2 days
    How many days are between the SOD of 28 Jan and the EOD of 30 Jan? Nearly all would say 3 days

My point above is that when we calculate day differences between two dates without time being provided, we typically and implicitly assume that time is the same across the two dates. When TP systems calculate accrued days, they typically make this same assumption. Unfortunately, this does not work for all markets. I have seen markets where accrued days is calculated using the SOD of start date and EOD of settlement date[^2]. 

This got me wondering about the implicit time assumptions we make with dates. This can become real important in certain scenarios. For example, selling a bond on its record date. Does the settlement come first or the recording come first? For that, I am grateful.

---

[^1]: Type 716 of [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) is an example of round half down
[^2]: Type 852 of [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) is an example of inclusive accrued days