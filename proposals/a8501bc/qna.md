---
author: bee
created_utc: 2023-04-09
updated_utc: 2023-04-16
---

# Q&A for the Change PoW/PoS Subsidy Split to 1/89 and Change PoW Algorithm to BLAKE3 Proposal

Here are answers to frequent questions about the [Change PoW/PoS Subsidy Split to 1/89 and Change PoW Algorithm to BLAKE3](https://proposals.decred.org/record/a8501bc) proposal collected from public places like Politeia comments and Matrix chats. Note, the goal of this doc is to collect *answers and arguments from proposal bakers and supporters*. Analysis of arguments, counter-arguments and facts backing them should be done elsewhere.

**If I missed or misrepresented something please let me know in Matrix or open a GitHub issue**.


## Why not send more rewards to the treasury?

This was a popular question asked in different ways with different arguments and suggesting different approaches: [1](https://proposals.decred.org/record/a8501bc/comments/1), [2](https://proposals.decred.org/record/a8501bc/comments/2), [3](https://proposals.decred.org/record/a8501bc/comments/6), [4](https://proposals.decred.org/record/a8501bc/comments/30), [5](https://proposals.decred.org/record/a8501bc/comments/44), [6](https://proposals.decred.org/record/a8501bc/comments/15), [7](https://proposals.decred.org/record/a8501bc/comments/16), [8](https://proposals.decred.org/record/a8501bc/comments/45).

Common benefits expected from higher treasury block rewards can be grouped as:

- It is a way to cut PoW rewards (as intended by the proposal) but without rewarding PoS even more, and without changing the overall [issuance schedule](https://docs.decred.org/advanced/issuance/).
- More funds in the treasury may attract more proposals (esp. marketing).
- More funds in the treasury may prompt voters to approve more proposals and spend more easily (esp. on marketing).
- Coins sent to treasury may be practically taken out of the circulation, contributing to market scarcity and positive price pressure. (This idea assumes treasury will spend/sell DCR less aggressively than PoS voters.)

> The treasury has no shortage of funds, that is not our problem.
> 
> Our problem is that subsidy that was intended to be distributed widely across a larger number of people has ended up all flowing to a single monolithic entity, in the context of mining. Further, that entity is dead set on attacking the project by wrecking its price discovery. By moving the 9% from miners to stakers, we ensure stronger incentive alignment between subsidy recipients and the project and make sure that subsidy gets distributed amongst a larger group, the stakeholders. This way, 90% of the subsidy still gets distributed versus accumulated in a treasury that does not need it. \[@jy-p on [2023-03-28](https://proposals.decred.org/record/a8501bc/comments/21)\]

> our problem is not one of not having enough funds in the treasury  
> our problem is that rewards that were intended to be spread amongst ppl supporting the consensus system, mining in particular, are going to a single monolithic entity that has been attacking the project for years  
> those rewards flowing to stakeholders makes more sense than sending to treasury \[@jy-p on [2023-03-28](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$WJB3eOoYfFE6TcnbrFbG3cTFkoOlGx_JRKoUMzd8BJ0?via=decred.org&via=matrix.org&via=planetdecred.org) in #proposals\]

> Personally, I don't think it matters much if the rewards go to the Treasury or PoS.  Any split between the two would very likely be fine either way.  However, when it comes down to it, the Treasury doesn't really need more funds, so, imo, the primary reason for sending the split there instead would be solely related to optics as opposed to any specific need.  On the other hand, stakeholders provide the majority of security to the network and have to spend time actively participating in viewing, discussing, and voting on matters like this and Treasury expenditures.
> 
> Another thing that occurs to me is that sending more funds to the Treasury reduces the amount paid overall for network security.  e.g. Currently only 10% of the produced coins go to it.  Therefore the other 90% go to rewarding the work securing the network (both PoW and PoS), voting, etc.  Changing it to 1/80/19 would reduce that amount paid overall for network security to 81%. \[@davecgh on [2023-03-28](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$fI1otZ54z9IBXZ4DRKsRIDmVS3Ix3wu-AgntV7FGWnI?via=decred.org&via=matrix.org&via=planetdecred.org) in #proposals\]

Other answers from the community: [1](https://proposals.decred.org/record/a8501bc/comments/24).


## Why not remove PoW and go pure PoS?

> it would require a substantial retooling of consensus code and likely require making changes to how PoS works, e.g. adding slashing or another penalty mechanism for stakers who attempt to double spend. \[@jy-p on [2023-03-27](https://proposals.decred.org/record/a8501bc/comments/5)\]


## Why not switch to RandomX?

> After looking at Monero and RandomX, a natural follow-on thought is "RandomX is a pretty good PoW algorithm, so why not use it for Decred?". Here are some considerations:
> 
> - Once the mining subsidy is reduced to 1%, the incentive to develop ASICs will be low, making an ASIC resistant PoW algorithm less useful.
> - RandomX is a rather heavy algorithm that involves running a non-trivial virtual machine that exercises various hardware features on modern desktop CPUs, which would cause SPV wallets to perform poorly with Decred.
> - RandomX would need to be reimplemented in Go from scratch to have a proper implementation, and this algorithm is very non-trivial.
> 
> After looking at the downsides of RandomX, Dave Collins and I decided on BLAKE3 because it is fast and will allow SPV wallets to quickly check the block headers. BLAKE3 is not a huge departure from the existing Blake256R14 PoW algorithm that Decred currently uses. \[@jy-p on [2023-03-27](https://proposals.decred.org/record/a8501bc)\]

> In terms of SPV, the block time isn't releveant, rather how many there are.  Then there are the memory requirements.  For example, the "fast mode" of RandomX requires 2GiB memory, which for SPV is out of range for the most part, especially on most mobile and low power devices.  That means the "light mode" would be needed.  It's only like 20 h/s on an RPi, so 750,000 blks / 20 h/s = 37500 sec / 3600 ~= 10.4 hours just to verify the hashes in the headers.
> 
> That's before you get to any of the other things like downloading the filters, verifying their inclusion proof, checking filter matches, downloading relevant blocks, utxo application, etc.
> 
> Meanwhile, BLAKE3 can do it in less than a second. \[@davecgh on [2023-03-27](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$yGc8TZJWkomFo56MaXqe0rjIL5_hU7qGrFWTBUaeTdQ?via=decred.org&via=matrix.org&via=planetdecred.org) in #trading\]

> pivoting to RandomX or similar could allow us to have a fairer / more egalitarian distribution of mining rewards, but it has a high cost in terms of making SPV shitty \[@jy-p on [2023-03-30](https://proposals.decred.org/record/a8501bc/comments/54)\]


## Why care about SPV?

> you need spv to have an efficient non-centralized ln wallet with decent security  
> nobody wants to sync the whole dcr chain on a mobile device \[@jy-p on [2023-03-31](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$JECLYLjhy0nbaVUH8Viku1lN7WSUoq8Q7CYUq8HILGU?via=decred.org&via=matrix.org&via=planetdecred.org) in #trading\]


## Why not publish more evidence or analysis to justify the attack narrative?

Note: "tr" or "TR" refers to @tacorevenge who published [The Suppressor Part 1: War of Attrition](https://medium.com/@tacorevenge/the-suppressor-part-1-war-of-attrition-3081a61b202b) and [The Suppressor Part 2: On-Chain Analysis](https://medium.com/@tacorevenge/the-suppressor-part-2-on-chain-analysis-6561c5a478c4) in 2021. These posts were the starting point for the [Change PoW/PoS Subsidy Split From 60/30 to 10/80](https://proposals.decred.org/record/427e1d4) proposal preceding the current 1/89+BLAKE3 proposal. It is recommended to read all three as they answer more questions not covered by this doc.

> nothing substantial has changed since tr published those articles  
> correspondingly smaller amounts of coins flowing via the same cexes from the same sources \[@jy-p on [2023-03-27](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$gkmQmKPqzramLX7XQuZc98K1ru93LUAWkpEBRDlCRwE?via=decred.org&via=matrix.org&via=planetdecred.org) in #trading\]

> what's the point of doing this work when randos pop out of the woodwork to gaslight me about it. there is pretty much no upside  
> i helped tr develop the onchain analysis tools. those tools are not going to be open sourced  
> coins continue to flow from huobi to binance and back despite huobi having "delisted" dcr  
> what i find funny is how certain people push back hard despite claiming to not have any skin in the mining game \[@jy-p on [2023-03-28](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$oSHc4FNG0pvCOG1A7_GTh3I_OGZGESJY-cnVw0mDKWE?via=decred.org&via=matrix.org&via=planetdecred.org) in #trading\]

> I understand the desire for a new article and don't even fundamentally disagree that it'd potentially be nice to have for the feel goods.  However, it's a fair amount of work to make everything presentable and the reality is that the behavior hasn't changed since the original, so any new articles won't be showing anything new aside from the scale going down (as expected from the reduced subsidy).  At the end of the day, anyone who is able to look at the data presented in the last one and do further analysis can still do it now, otherwise, they'll just be taking the word of the article anyway since it will be exactly what was stated -- the behavior hasn't changed -- and the charts will look the same (because the overall behavior hasn't changed).
> 
> So, I get it, but I personally would rather put that time into just getting it over with and squashing their hardware once and for all rather than continuing to feed them and prolonging it any longer.  Keep in mind, it'll already be a minimum of 3 months before any change if the proposal passes and we still have to deal with whatever stake they have left too.  My opinion is that Decred has been exceedingly patient and tried to talk small steps that weren't enough to dissuade them, so I'm really not keen on anything that delays it even further.
> 
> I understand if people want to vote against the proposal for that reason, and that's their right to do so.  Maybe it will not pass and it'll be necessary to waste a bunch of time producing something that realistically will not provide any pertinent new information that isn't already known and available. \[@davecgh on [2023-03-29](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$P7ElQv9LNZjUBbzIm9lxTO6Lv1KZZz-r3x3qMZTybZ8?via=decred.org&via=matrix.org&via=planetdecred.org) in #proposals\]

> Yes if you've ever bought DCR in size on Binance in the last 5 years then you've probably seen them operate directly, I didn't need to see the on-chain evidence to know a malicious player was active, but having that data was nice to take it from conspiracy theory to conspiracy fact. \[@jz on [2023-04-01](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$PHeWBjjNg3TcL29AG5NtiCTpsqhUF_JRIfITeG0GQhc) in #trading\]


## Miners selling is normal. Is there really a malicious attack or just too low awareness and demand for DCR?

> Miners selling has never been an issue, it was fully expected from the start it's the intent of pow mining.  What we have is entirely different.  Let's say there's speculation around DCR because of a new release, people want to buy, and some long term holders would like to make a little profit.  But surprise, as price start moving an entity begin undercutting sellers and worse than that they start walking the price down.  If they only wanted to sell they could very well just put a wall, or follow the demand, but no.. they walk it down in price. This manipulation of the price also manipulate demand, because those who want to buy expecting a raise, stop buying ... wtf it's going down ... and those who want to sell are forced to capitulate at a lower price or just continue holding. It stops price discovery, it stops demand, it has nothing to do with selling to cover costs.
> 
> It doesn't matter even if there is demand or not.  There could be extremely high demand, but do you want to buy when you expect the price to raise and it's moving down?  It's why I said that it stops demand.
> 
> Awareness is not enough.  Let's say NVIDIA announces a new GPU, it's revolutionary, everyone is talking about it, they expect a lot of sales.  You have the good idea to buy stocks, so you check the market ... but somehow even with all the excitement in the community, the days after the announcement you see the price gradually trickling down.  Maybe you missed something, do you still have confidence in buying it?  Most people probably wouldn't, and awareness isn't an issue in this scenario.
> 
> My point is even with great awareness manipulation can be an issue. We have 2 things to deal with and we shouldn't refuse to tackle one or the other.
> 
> So as an investor or trader, would you confidently buy in a known manipulated market and think that others will do the same so that demand can surpass the manipulation?  Because that's the level of faith that you require for new users to solve the issue we have. \[@nnnko56 on [2023-03-30](https://matrix.to/#/!lDZCzVQjFoJsXMPkvr:decred.org/$w7kBgFIGKxkQXTzdFM-SbAlVAsD56MomuB0vmnO0Xqo?via=decred.org&via=matrix.org&via=planetdecred.org) in #trading, _edited to fix typos_\]


## What will happen to network's attack cost security?

> Decred's security against majority / double spend attacks is dominated by the PoS component, with PoW only adding a small amount. PoW is actively being used against the project and provides very limited security against majority attacks. \[@jy-p on [2023-03-27](https://proposals.decred.org/record/a8501bc/comments/5)\]


## Will you update dcrpool?

> I will not be adding dcrpool to this proposal. It adds complexity and this is exclusively the consensus change. \[@jy-p on [2023-03-27](https://proposals.decred.org/record/a8501bc/comments/4)\]


## Will you update gominer?

> If this proposal is approved and activated on-chain, this is a several month period during which gominer can be updated.
> 
> That work will not be included in this proposal. \[@jy-p on [2023-03-28](https://proposals.decred.org/record/a8501bc/comments/19)\]


## How the transition will happen?

Specifically, "Will there be a dramatic drop in difficulty and dramatic increase in block times?"

> The difficulty will be reset. \[@davecgh on [2023-03-28](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$tmEmmu5xL9U6SKr7UVuglmPEImZV2r5qbApBJEfeMOw?via=decred.org&via=matrix.org&via=planetdecred.org) in #proposals\]


## How will we guess the initial difficulty value?

> It'll have to be an educated guess, just like it was at initial launch.  The DAA (difficulty adjustment algorithm) will primarily handle it though just as it did before. \[@davecgh on [2023-03-28](https://matrix.to/#/!qYpAAClAYrHaUIGkLs:decred.org/$IA3_83HU3yBdgzWkURu1I_sSpmUdEpvZx_UMFyzseO4?via=decred.org&via=matrix.org&via=planetdecred.org) in #proposals\]
