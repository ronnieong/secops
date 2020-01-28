---
layout: post
title:  My top 3 memorable accrued interest conventions
date: 28 Jan 2020
tags: [settlement]
---

Accrued interest conventions are a pain. For anyone who has worked in product control or settlements, or been tasked to improve STP rates, you probably get what I mean. 

In this entry, I share three groups of accrued interest conventions which have proved memorable for me over the years. They are usually painfully funny and funnily painful.

## A quick background

For the uninitiated, transaction processing (TP) systems typically compute accrued interest independent of trading systems (based on security static data within the TP system). Where the TP system is unable to support the accrued interest (AI) convention, there will be an AI mismatch and a bunch of problems.

## Unconventional rounding conventions

Why do we round 0.5 to 1 and not 0? If you draw them out on a line, 0.5 is equally close to 0 and 1. Rounding 0.5 to 1 may be the dominant convention but it is also arbitary. Anyhow, most TP systems I have seen do not support the opposite convention, which is [rounding half down](https://en.wikipedia.org/wiki/Rounding#Round_half_down). This really poses an issue for the bonds out there that round half down accrued interest[^1].

Apart from making me think real hard about rounding, this group of AI convention also made me question my mathematics education growing up.

## Unsupported leap year conventions

Most TP systems I know of are able to cater for the common leap year considerations (e.g. coupon period starting in non leap year and ending in leap year). The uncommon leap year considerations are the interesting ones. 

Given their relative rarity, it is almost never economical to priortize solutions for them. Instead, they become like a team of guerilla fighters, waiting to ambush you every four years down the road.

## Highly inclusive accrued days 

How many days are between 28 Jan and 29 Jan? I reckon most would say 1 day.   
How many days are between the start of 28 Jan and end of 29 Jan? I reckon most would say 2 days 

An assumption implicitly baked into the first statement is that we are referring to the same time of the day for both dates. For better or wose, this assumption holds true for almost all bonds with some exceptions[^2]. Ignoring the operational issues they caused, these bonds made me think real hard about the implicit time stated in dates.

---

[^1]: See type 716 of the [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) for an example
[^2]: See type 852 of the [Bloomberg Calculation Types document](https://docplayer.net/12997386-Valid-calculation-types.html) for an example