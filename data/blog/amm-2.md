---
title: Automated Market Makers (AMM) Explained (2)
date: '2021-05-17'
tags: ['blockchain', 'defi', 'amm']
draft: false
summary: This post introduces Automated Market Makers, a key protocol powering decentralized exchanges.
images: ['/static/img/amm/amm-banner.png']
---

![amm-banner](/static/images/amm/amm-banner.png)

## Preface

In the 1st part of the post, I covered how market making can be carried out in a decentralized environment. I showed how Uniswap the pioneer in the AMM space managed to automate the pricing of assets in a decentralized setting and how it incentivises traders and liquidity providers. 
In the 2nd part of the post here, I cover major innovations in the AMM space - SushiSwap, Balancer and Curve and show how they refined the value proposition of decentralized trading.

## Table of contents (2nd part)

- [Popular AMM projects](#popular-amm-projects)
  - [SushiSwap and yield farming](#sushiswap-and-yield-farming)
  - [Balancer and ETFs](#balancer-and-etfs)
  - [Curve, slippage and stableswap](#curve-slippage-and-stableswap)
- [Conclusion](#conclusion)

## Popular AMM projects

The above points summarise Uniswap in a nutshell. While there are other concepts like [flash swaps](https://uniswap.org/docs/v2/core-concepts/flash-swaps/), [price oracles](https://uniswap.org/docs/v2/core-concepts/oracles/) and [governance](https://gov.uniswap.org/t/community-governance-process/7732), they are ancillary to the operations of an AMM system.

If you have made it this far, congratulations - you now have a good understanding of the most popular decentralized finance (DeFi) protocol by market capitalisation, one that has powered 55M trades and nearly $295B by market volume^[Accurate as at 10 May 2021, source: https://uniswap.org/]. The rest of the article covers other protocols that have innovated on Uniswap.

While there has been an explosive growth of AMM protocols in the DeFi space, many of them are just clones of a few popular ones with minor tweaks to the front-end user interface and deployed on alternative chains. Unfortunately, the DeFi space does not really value originality that highly and there are many clone projects abound. I choose to focus on 3 protocols that bring something new to the table - SushiSwap, Balancer and Curve.

![defi-amm-ranking](/static/images/amm/defi-amm-ranking.png)

_Ranking of decentralized exchanges by total value locked as at 10 May 2021. Data from [DeFi Pulse](https://defipulse.com/)_

### SushiSwap and yield farming

![sushiswap](/static/images/amm/sushi.svg)

[SushiSwap](https://sushi.com/) was launched by its anonymous "chef" Nomi in August 2020 as a fork of Uniswap with some minor modifications. On launch, it managed to attract nearly a billion dollars in staked liquidity from Uniswap sparking much discussion and debate within the Ethereum community on the ethics of copying. It is also famous for the exit scam fiasco in which chef Nomi liquidated his holders of the token before apologizing and transferring control of the protocol to FTX exchange CEO Sam Bankman-Fried.^[https://news.bitcoin.com/sushiswap-returns-14-million-exit-scam/]

While seemingly a Uniswap copycat, SushiSwap introduced the idea of yield farming in the decentralized exchange space. Yield farming is the idea of staking cryptocurrency assets into platforms in return for payouts over time, popularised by the likes of Compound, an algorithmic, autonomous interest rate protocol.

In order to attract liquidity providers to its platform, SushiSwap gave out its governance tokens (SUSHI) as rewards to liquidity providers. These tokens also allow holders to receive a portion of the 0.3% trading fee - liquidity providers receive 0.25% of the fee and SUSHI holders receive the remaining 0.05%.^[This prompted Uniswap to issue its own governance token a few months later and shows how allowing people to own a stake in the protocol helps to create user loyalty via an "illusion" of aligned interest.]

Liquidity tokens are also not used for bookkeeping sake and can be used for yield farming. This incentive system helped SushiSwap attract liquidity providers and users to the platform, creating a network effect that cementing its place as the next most popular platform after Uniswap.^[Most clone projects on other platforms seem to be based on the SushiSwap model.]

### Balancer and ETFs

![balancer](/static/images/amm/balancer.svg)

In Uniswap a pool consists of two assets, predominantly a very popular token like Ethereum and a less popular one. What happens when a user wants to trade between two less popular tokens? She would need to do multiple trades incurring higher transaction fees in the process. The two asset pool structure is also not capital efficient for liquidity providers who could potentially get more transaction fees is capital can flow freely across pools.

[Balancer](https://balancer.fi/) was born out of a research project at BlockScience in 2018, founded by Fernando Martinelli and Mike McDonald. It was created with the idea of smart pools that allows for greater customizability. It allows up to 8 assets in a pool with arbitrary weights and fees, which can be dynamically adjusted and allow for more complex logic to be programmed. Thus, pools in balancer can be thought of as "inverse exchange traded funds (ETFs)". Like ETFs they are continuously rebalanced but differ as liquidity providers are paid for providing capital. Their documentation summarises it well:

> Balancer turns the concept of an index fund on its head: instead of a paying fees to portfolio managers to rebalance your portfolio, you collect fees from traders, who rebalance your portfolio by following arbitrage opportunities.

![balancer-formula.png](/static/images/amm/balancer-formula.png)

It uses a generalised version of the constant product formula:

$$
const = \prod_{t} B_{t}^{W_{t}}
$$

where the constant, is derived by the product of the balance of tokens $B$ weighted by $W$ for all $t$ tokens in the pool. $\sum_{t} W_{t} = 1$, giving a constant returns to scale function.

### Curve, slippage and stableswap

![curve](/static/images/amm/curve.png)

Trades conducted on AMM platforms affect the price of each of the tokens in the pool. This movement may be insignificant for pools with large liquidity or trades with low volume. But a large swap order for a token with a small market cap or liquidity can move the price significantly. This is known as price slippage.

In the constant product formula used by Uniswap and generalised in Balancer, a small change in the quantity bought or sold of particular tokens could result in negative price slippage of a couple of percentage points. How can we reduce price slippage, especially for assets like stablecoins (tokens pegged to fiat currency like the USD) where we have a good sense of the "ideal" price of the exchange?

[Curve](https://curve.fi/), a brainchild of Michael Egorov, solves this problem by introducing a StableSwap formula, where the rate of change of price around the ideal price (i.e. 2nd derivative) does not change as quickly compared to the constant product formula. The stableswap invariant curve is shown below:

![stableswap-formula.png](/static/images/amm/stableswap-formula.png)

For the stableswap invariant curve, price changes very slowly at the "ideal" price of 1.0 at the initial portfolio composition of x = 5, y = 5. The graph is very close to a straight line like a "zoomed in" version of the constant product formula. In some way, this could be thought of as leveraging the existing liquidity of the tokens in the pool.

The capital efficiency benefit for liquidity providers as a result of Curve's invariant formula also leads to lower price slippage for users trading stable assets (stablecoins and wrapped coins). Since its launch in 2020, Curve has emerged as the leading decentralized exchange market for stable assets.

## Conclusion

Since the introduction of AMM technology, adoption and usage of decentralized exchanges have grown significantly. Uniswap is now in the top 10 cryptocurrency exchanges by daily traded volume, behind Binance, Upbit, Okex, Huobi, Coinbase and Bitfinex.^[Data taken from [Coinmarketcap centralized exchange data](https://coinmarketcap.com/rankings/exchanges/), filtering out exchanges with scores greater than 5, and [Coinmarketcap DEX data](https://coinmarketcap.com/rankings/exchanges/dex/)]

I hope this article gives you a good introduction and broader appreciation of the AMM space. To what extent will algorithmic protocols successfully replace or complement traditional exchanges? Can decentralized governance of AMM protocol truly happen? Will AMM technology branch out from crypto to other asset classes? It's still early days in the space but an interesting one to keep track of.

## Related Resources

- [Uniswap v2 whitepaper](https://uniswap.org/whitepaper.pdf)
- [Balancer whitepaper](https://balancer.fi/whitepaper.pdf)
- [Curve stableswap whitepaper](https://curve.fi/files/stableswap-paper.pdf)
- [Calculating the value of a liquidity provider token](https://dailydefi.org/articles/lp-token-value-calculation/)
- [Understanding Uniswap returns](https://pintail.medium.com/understanding-uniswap-returns-cc593f3499ef)
- [Impermanent loss explained](https://chainbulletin.com/impermanent-loss-explained-with-examples-math/)
