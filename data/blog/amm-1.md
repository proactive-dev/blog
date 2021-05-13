---
title: Automated Market Makers (AMM) Explained (1)
date: '2021-05-12'
tags: ['blockchain', 'defi', 'amm']
draft: false
summary: This post introduces Automated Market Makers, a key protocol powering decentralized exchanges.
images: ['/static/img/amm/amm-banner.png']
---

## Preface

This article is a summary of what I have learnt from the decentralized finance space - written in a friendly and accessible way. I get questions on DeFi fairly often in my day to day work but a two-sentence answer often feels insufficient to explain the innovation in the space. In this post, I contextualised such protocols in the wider financial market and explore the evolution of DeFi, or more specifically automated market makers, in an incremental fashion. By peeling off the layers of complexity of the topic, I hope you gain a broader appreciation and understanding of the topic.

![amm-banner](/static/images/amm/amm-banner.png)

## Table of contents

- [Background](#background)
  - [Automated market makers and Uniswap](#automated-market-makers-and-uniswap)
  - [A brief history of Uniswap](#a-brief-history-of-uniswap)
- [Liquidity Pools](#liquidity-pools)
- [Automated pricing via algorithms](#automated-pricing-via-algorithms)
- [Incentives for liquidity providers](#incentives-for-liquidity-providers)
- [Incentives for users](#incentives-for-users)
- [Popular AMM projects](#popular-amm-projects)
  - [SushiSwap and yield farming](#sushiswap-and-yield-farming)
  - [Balancer and ETFs](#balancer-and-etfs)
  - [Curve, slippage and stableswap](#curve-slippage-and-stableswap)
- [Conclusion](#conclusion)

## Background

![orderbook](/static/images/amm/orderbook.png)

If you carry out a trade on a brokerage or stocks exchange platform, you might notice a side feed containing a list of buy and sell orders for a specific security or financial product. That is known as the order book and it shows the number of shares / securities being bid on or offered at each price point.

This information on market depth is very valuable. In fact companies like Robinhood make most of their money by [selling data on order flow](https://www.ft.com/content/4a439398-88ab-442a-9927-e743a3ff609b) to trading giants like Citadel Securities. For example, each time you buy a share of Tesla, Robinhood sends that order to Citadel and receives a few pennies in return. Citadel also automatically takes the other side of the order, then returns to the market to flip the trade i.e. it "makes the market". Fun fact - Citadel's platform trades approximately 47% of U.S. listed retail volume.^[From [Citadel's website](https://www.citadelsecurities.com/products/equities-and-options/): Our automated equities platform trades approximately 26% of U.S. equities volume1 across more than 8,900 U.S.-listed securities and trades over 16,000 OTC securities. We execute approximately 47% of all U.S.-listed retail volume, making us the industry’s top wholesale market maker.]

By standing ready to buy or sell a tradable asset on a regular basis at a publicly quote price, market makers (also known as liquidity providers) facilitate the speed and ease in which financial instruments can be bought or sold. Market makers like Citadel can be found in all types of markets from equity to currency exchanges to forex markets and are regarded as an important part of a well functioning and liquid market.

For a large part of the history of finance, market making activity was carried out by institutions with large capital and resources. However, the rise of cryptocurrency and decentralized finance has presented new alternative models of finance. This includes decentralized exchanges and automated market makers (AMM), the focus of this post.

In the first part of the post, I cover how market making can be carried out in a decentralized environment. I show how Uniswap the pioneer in the AMM space managed to automate the pricing of assets in a decentralized setting and how it incentivises traders and liquidity providers. Next, I cover major innovations in the AMM space - SushiSwap, Balancer and Curve and show how they refined the value proposition of decentralized trading.

### Automated market makers and Uniswap

Imagine market making happening without any centralized institution in control. How could that happen? Perhaps, it is better to flip the question around and ask why can't it happen?

After all prices for goods and services in many well functioning markets are thought to be determined not through any central authority but through the "invisible hand" of the market. The innovation in that AMM introduces is the removal of a central market maker and converting what was a once a one-sided market into a two-sided market of traders and liquidity providers.

For such two-sided market making to happen without any central party in control, it needs to solve a series of challenges:

1. Decentralized buying and selling of an asset
2. Automated pricing and price discovery
3. Incentivise liquidity providers
4. Incentivise users

### A brief history of Uniswap

![uniswap](/static/images/amm/uniswap.png)

The initial idea of using an AMM mechanism for decentralized exchanges original from a [proposal in reddit](https://www.reddit.com/r/ethereum/comments/55m04x/lets_run_onchain_decentralized_exchanges_the_way/) by Vitalik Buterin in 2016.

> My proposed solution is to use the style of "on-chain automated market maker" used in prediction markets in a decentralized exchange context.

Hayden Adams launched [Uniswap](https://uniswap.org/) in November 2018 and it began to quickly attract liquidity and trading volume. Its governance token (UNI) was introduced on September 2020 and allows token holders to participate in the governance of the protocol such as usage of the treasury and upgrade decisions. At the point of time of writing, the protocol has facilitated 55M trades worth $295B.

Note: It's important to make a distinction between Uniswap the decentralized exchange and Uniswap the governance token (UNI). Unless specified explicitly, Uniswap in the course of the article refers to the exchange rather than the token.

Let's examine how Uniswap, the pioneer in the Automated Market Maker (AMM) solves the 4 challenges highlighted above.

## Liquidity pools

![liquidity-pools](/static/images/amm/liquidity-pool.jpg)

Prior to the invention of AMMs, decentralized exchanges face a problem of low liquidity as it is hard to find enough people willing to make trades on token pairs at the same time.

Instead of trading between buyers and sellers or relying on a centralized market maker, on AMM platforms, **users trade against a shared pool of tokens**. The more assets in the pool, the higher the liquidity and the easier trades are being carried out. To visualize how it works, I describe an imaginary example involving two tokens - a token A and a token B.^[The example holds for any asset pair, but as the idea and adoption of AMM originated within the cryptocurrency space, I will explain in the context of a trade involving two different tokens.]

In our example, we have an A-B liquidity pool filled with a relatively equal value of each token. Having equal value ensures that there is sufficient liquidity for trades in both directions and also plays a part in the pricing decisions.

## Automated pricing via algorithms

Users will only trade if there is sufficient liquidity and prices are clear and transparent. Pools promote liquidity, but how does that determine the pricing of assets in the pool?

In a centralized exchange, one can easily infer this information from the order book, but in a decentralized setting this is determined by an algorithm. These algorithms are coded into smart contracts (computer programs on the blockchain created to execute certain code or logic in a permissionless setting), and are executed each time a trade is carried out.

### Constant product formula

An example of a pricing formula is the constant product formula:

$$
d * c = k
$$

Let $d$ and $c$ represent our two assets token A and B respectively. Assume we have 100 of each token - the constant $k$ is simply 100 \* 100 or 10,000.

The algorithm works but requiring the trader to maintain the constant value. For example, in order to buy 1 token B, a trader must deposit a proportional amount of token A to maintain the $k$.^[We ignore transaction fees for simplicity.] For an infinitesimally small quantity of token B, we get the marginal price of 1 token B is to 1 token A.

For 1 token B, the true quantity of token A that is has to be exchanged is:

$$
\begin{aligned}
Q_{c} &= \frac{10000}{99} - 100 \\
&= 101.01010 - 100 \\
&= 1.01010
\end{aligned}
$$

Price is then simply a construct of the ratio of both tokens i.e. the price of 1 token B is 1.0101 token A.

The following picture illustrates the ratio of token As required for token Bs.

![equation](/static/images/amm/equation.jpg)

Importantly, the market price changes as the ratio of the tokens in the pool changes. To put it another way, the price would approach infinity if someone plans to buy up all of a particular coin due to the parabolic nature of the curve.

How does an AMM ensure that the price is "right"? Through the invisible hand of arbitrageurs. Imagine that each token B is actually worth 2 token As. Arbitrageurs would sell token As and buy up the token Bs in the pool until the next unit of token B cost 2 token As. This simple formula allows pricing to be determined automatically and price discovery to happen.

## Incentives for liquidity providers

Our discussion so far takes for granted that there already exists a pool of tokens for users to trade with. But how are pools formed and why should individuals contribute tokens to the pool? In this section, we look at the tokenomics behind AMM protocols to entice liquidity providers.

### Liquidity providers, tokens and shares

Recall that a pool is created through the combination of two tokens of proportional value. Each time that a user deposits token pairs in the pool, he gets a share of it. For example, if 10 A token and 10 token Bs are deposited in our A-B pool to bring it to 100 A token and token Bs in total, the user contributing those tokens, also known as the liquidity providers (LP) gets a 10% share of the pool. This allows him to claim the share and withdraw 10% worth of tokens from the pool (assuming no further contributions or removal).

This happens automatically via smart contracts which "mints" liquidity tokens and distributes them to the user as proof of his share of the pool. The number of tokens that are "minted" is proportional to the value of coins that users contribute to the pool. For every withdrawal, the user gets back his share of the pool and the liquidity token will be "burn".

A pool created by a single user can hardly be characterised as decentralized. In fact, a common scam known as rug pulls rely on tricking users to low liquidity pools which can be easily manipulated by the single liquidity provider. Thus, it is crucial that AMMs have a strong incentive mechanism to attract more liquidity provides to the pool.

### AMM LP incentives

Unlike a centralized market maker system like Citadel in which revenue is dependent on the ability to flip good trades, in a decentralized system there is no flipping. Instead, a portion of every trade is distributed as fees to the liquidity providers. In Uniswap, 0.3% of all trade volume would be distributed proportionally to the liquidity providers.^[https://uniswap.org/docs/v2/advanced-topics/understanding-returns/]

**Technical side note**: Rather than distributing tokens for every trade that takes place to every liquidity provider, which would just add to "shoe leather cost", the fees are added back to the pool and the same number of liquidity tokens held by a liquidity provider can now be redeemed for a higher value.

If every pool were to provide the same fees, liquidity providers who are hoping to maximise profit would choose pools that have the highest trade activity.^[To be more precise, profit maximisation is a function of trading fee share, trading activity, additional bonuses and token prices. LPs can suffer a loss due to a decline in token prices and/or fluctuation in prices, also known as impermanent loss.] For new pools consisting of less well-known tokens, additional incentives can be offered to liquidity providers such as bonus token distributions.

## Incentives for users

Why should users use decentralized exchanges over centralized exchanges? Fees, user experience and a preference for things decentralized.

### Fees

For token pairs with high liquidity and large pools, fees (trading price spreads + transaction fees) are often comparable to centralized exchanges. This is due to arbitrageur activity across centralized and decentralized exchanges resulting in comparable trading prices, though transaction fees tend to be relatively high for small exchanges (ETH specific). For illiquid token pairs, centralized exchanges offer better spreads.

### User experience

Decentralized exchanges require no registration, KYC or verification procedures. One can easily execute a transfer and carry out other activities with a single wallet address without having to transfer funds in and out of exchanges. This contributes to a seamless [Web3](https://ethereum.org/en/developers/docs/web2-vs-web3) experience. On the other hand, centralized exchanges tend to support more sophisticated trading functionalities (e.g. stop losses, trading margins etc.) and provide faster execution speed and customer support.

### Preference for decentralization

"Not your keys, not your coins", as the popular saying goes. Relying on a centralized exchange means trusting the custody of your funds to a third-party which can be hacked, stolen or compromised. With a decentralized exchange, the responsibility falls on the user to verify the trustworthiness of the contract that he is interacting with.

(Post will be continued in the next)