[简体中文](README-zh.md)

# DeferSwap WhitePaper - V1.0

## 1 Background

As of today, almost all DEXs are in AMM mode and the market lacks an order book trading model. The fact that all centralized exchanges are order book trading shows that the demand for order book trading is universal.

### 1.1 AMM Uncompensated Losses

The simple explanation of gratuitous loss is: when we deposit a pair of tokens into the AMM-based DEX, if the price of one token is rising with another token, then after the price rises and you take them out, the total price is lower than the two tokens directly in hand, the lower part is the loss, the bigger the price deviation the bigger the loss, so The bigger the deviation from the price, the bigger the loss, so it may cause a loss, especially if both tokens are actually denominated in other stablecoins. There is no way to avoid AMM's self-inflicted gratuitous losses.

### 1.2 Impact of AMM slippage

AMM is traded through a liquidity pool. The larger the percentage of the pool an order takes up, the higher the slippage.

### 1.3 AMM trades will not be 100% successful

Long trade confirmations are likely to fail in the event of market volatility causing the price at the time of final trade confirmation to exceed a pre-set tolerance range. The failure rate is especially high in case of network congestion.

### 1.4 Low utilization of AMM funds

One of the main problems with AMMs today is the way liquidity is allocated to LPs. As an example, UniswapV2 allocates funds uniformly throughout the price range, which means that only funds allocated around the market price are actually utilized efficiently, while the rest of the funds are left idle. This leads to high slippage as well as capital inefficiencies.

## 2 DeferSwap

DeferSwap is an order book based trading protocol. With DeferSwap, users can create limit orders and wait for them to be filled. Orders are automatically taken if the user's buy price is higher than the counterparty's price, or if the user's sell price is lower than the counterparty's price.
 
### 2.1 Trading flow

The user creates a limit order -> the system sets up the transaction (if the price matches the counterparty price, it will be automatically filled) -> the order is completed 

### 2.2 Summary trading

DeferSwap supports aggregated trading. When the user creates a limit order, the user interface automatically matches the price with the orders that can be filled, and then submits the data with the limit order to the DeferSwap contract for processing, and if the parameters are correct, the DeferSwap contract will automatically complete the order taking operation.

### 2.3 Partial Fulfillment

Considering that not every user can fully take a limit order at the right price, DeferSwap supports partial transactions. This means that the user can fill a part of the limit order, for example, one third, one half, etc.

### 2.4 Batch order taking

DeferSwap supports batch order taking. That is, if you are satisfied with the price of several limit orders and want to take all of them, DeferSwap supports this too. Batch order taking operation can save operation time, improve efficiency, and promote order completion.

## 3 Token

+ Token symbol: `DEFER`
+ Total amount: `1,000,000,000`

## 3.1 DEFER Allocation

+ 50% for trading mining [500,000,000]
+ 35% allocated to investors [350,000,000]
+ 15% allocated to team members for linear release over four years [150,000,000]

### 3.2 DEFER Token Rights

+ Decide on the use of the community vault
+ Trading pairs go live
+ Trading fee rate setting
+ Transaction fee usage
+ LP rewards
+ Governance of other parameters

### 3.3 Governance requirements

+ Minimum 1% of DEFER supply required to create a proposal
+ 4% of DEFER supply requires an affirmative vote to meet the required number
+ 7-day voting period
+ Implementation of a 2-day lockout delay

## 4 Trading Mining

In order to promote trading on the platform and develop trading habits among users, DeferSwap has decided to use 50% of the total DEFER supply for trading mining rewards.

### 4.1 Rules

All users who have successfully traded on DeferSwap can participate in DeferSwap's trading mining activities. The rules for transaction mining rewards are as follows.

| Parameters | Symbols |
| --- | --- |
| `r` | the actual reward the user receives |
| `R` | Total number of DEFERs in the reward pool |
| `f` | total number of user transactions |
| `d` | Total User DEFER Pledges |
| `α` | Total transaction weight constant, default: 0.5 |
| `k` | the number of participants in the transaction mining |
| `s` | User transaction score |
| ![](https://latex.codecogs.com/gif.image?\sum_{n}s_{n}) | the sum of all user transaction scores |
  
  
First, calculate the user's score.  
  
![](https://latex.codecogs.com/gif.image?s=f^{\alpha}\times%20d^{(1-\alpha)})

  
Calculate the reward received based on the score: !  
  
![](https://latex.codecogs.com/gif.image?r=R\times\frac{s}{\sum_{n}s_{n}},n=1,2...k)
  
  
### 4.2 Reward pooling

After the DeferSwap protocol is started, a block is designated as the start block and 20 DEFERs are released into the reward pool for each block until all 500,000,000 DEFERs have been released.

### 4.3 DEFER Staking

The more `DEFER`s are staking, the more rewards are received. There is a 30-day withdrawal limit for staked `DEFER`.

## 5 Transaction Fee

Transaction fee is tentatively set at 0.5%.

### 5.1 Usage

Initial usage purposes are as follows.

+ 100% of the transaction fee to buy back DEFER and destroy it

> DeferSwap community can vote to redefine usage.
