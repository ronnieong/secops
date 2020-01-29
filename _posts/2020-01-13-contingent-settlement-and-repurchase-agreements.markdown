---
layout: post
title:  Contingent settlement and repurchase agreements
date: 13 Jan 2020
tags: [bonds, settlement, repurchase-agreements, securities-lending, operational-risk]
---

Did you know that the second leg of a repurchase agreement [(Investopedia)](https://www.investopedia.com/terms/r/repurchaseagreement.asp)[^1] can settle while the first leg continues to fail? 

Take a moment to think about that. Since only the second leg settles, the position of the parties are actually reversed -- the securities giver becomes the securities taker and vice versa. In other words, a trader looking to borrow money by pledging bonds might end up lending money instead! How is all this even possible?

## Depository Behavior

The first thing to note is that the majority of central securities depositories (e.g. HK CMU) treat the two legs of a repurchase agreement as `seperate and independent`. These depositories expect a seperate instructions for each leg and are absolutely oblivious about the relationship between the two instructions[^2]. 

Therefore, parties cannot rely on the depository to settle the second leg contingent on the first leg being settled[^3]. The responsbility of contingent settlement falls squarely on the repurchase agreement parties.

## Contingent Instruction

One school of thought is for the parties to send instructions for the second leg `only after the first leg settles`. This eliminates the risk of incorrect settlement but presents two problems:

1. The significant amount of manual work if the process is not automated. For the process to be automated, the system needs to be able to a) consume settlement status updates and b) release instructions for second leg only upon successful settlement of the first. Such automation is not straightforward.

2. Delaying the instruction of the second leg present its own set of issues. STP numbers in management reports could be impacted. The time to discover and work out any financial discrepancies (e.g. settlement proceeds) through matching is also reduced.   

## Mitigating Factors

The other school of thought is to `accept the risk` and to continue instructing the second leg regardless of the settlement status of the first leg. After all, what are the chances of the second leg settling when the first leg has not? 

1. If I was the securities taker in the first leg of a repurchase agreement, what are the chances I have the same securities to return for the second leg without the first leg settling? 

2. Additionally, if all of my repurchase agreements are of a long tenor, what are the chances of the first leg failing all the way until my second leg settles?

## No Easy Answer

I hope this post brings some light to this often underappreciated operational risk of repurchase agreements. All in all, I do not see an easy answer for securities operations practicioners. Do you agree? Is the current state good enough? Can depositories do more? Let me know.

---

[^1]: The same issue exists for all two legged transactions such as security lending 
[^2]: Depositories which treat repurchase agreements as a single entity usually expect only a single instruction -- additional information about the second leg needs to be provided (e.g. [sequence D in a MT543](https://www.iso20022.org/15022/uhb/finmt543.htm))
[^3]: I am not advocating that depositories should consider the two legs of a repurchase agreement as singular -- doing so presents its own set of issues (to be explored in a separate post?)