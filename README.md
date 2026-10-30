# DeFiForBeginners

An introduction to decentralised finance: lending, swapping, and liquidity. DeFi is financial services — trading, lending, earning interest — run by smart contracts on a blockchain instead of by a bank or company.

> This guide is educational only, not financial advice. DeFi is experimental, and smart contract bugs, hacks, and market crashes can cause total loss.

## 1. What DeFi is, in plain language

Traditional finance (TradFi) runs through intermediaries: banks hold your money, exchanges match your trades, and companies enforce the rules.

DeFi replaces intermediaries with **smart contracts**: code on a blockchain that runs automatically when its conditions are met. A lending app, for example, is not a company lending you money — it is a contract that holds deposits, checks collateral, and pays interest according to its code.

Key properties:

- **Permissionless:** anyone with a wallet and internet can use most DeFi apps, without applying for an account.
- **Transparent:** the code and the transactions are usually public and auditable.
- **Non-custodial:** you keep your keys. The app does not hold your password — but a bug or a malicious approval can still drain your wallet.
- **Composable:** apps can plug into each other, like building blocks. This creates powerful combinations — and chains of risk, where one app's failure affects others.

## 2. The core building blocks

### Decentralised exchanges (DEXs)
A DEX lets you swap one token for another directly from your wallet, using a **liquidity pool** instead of an order book.

- You trade against a pool of tokens supplied by other users, not against a single counterparty.
- The price is set by a formula based on the ratio of tokens in the pool.
- Examples of DEX designs: Uniswap, PancakeSwap.

### Lending and borrowing
You deposit crypto as collateral, and borrow another asset against it — or you lend your crypto and earn interest from borrowers.

- Borrowing is almost always **over-collateralised**: you must lock more value than you borrow, because crypto prices move fast.
- If your collateral value falls below a threshold, the protocol sells it automatically. This is called **liquidation**, and it can happen suddenly in a crash.
- Interest rates change with supply and demand, not with a bank's decision.

### Liquidity pools and yield farming
**Liquidity providers (LPs)** deposit pairs of tokens into a pool so traders can swap. In return they earn a share of trading fees, and sometimes extra reward tokens.

- **Yield farming** means moving your crypto between protocols chasing the highest reward rate.
- Rewards are often paid in a new token whose price can fall fast. A "100% APY" paid in a token that loses 90% of its value is not a 100% return.

### Stablecoins in DeFi
Most DeFi activity uses stablecoins as the stable side of trades, loans, and pools. See StablecoinsExplained for their risks — a DeFi position built on a stablecoin that depegs can collapse even if the protocol works perfectly.

## 3. How a swap actually works

1. You connect your wallet to a DEX.
2. You choose the token to sell and the token to buy, and the amount.
3. The DEX shows you the expected output, the price impact, and the fee.
4. You approve the DEX to spend your token (first time only, per token).
5. You confirm the swap. The contract exchanges your tokens through the pool and sends you the output.

Three costs and risks in every swap:

- **Network fee (gas):** paid to the blockchain, not the DEX.
- **Trading fee:** a percentage taken by the pool, shared with liquidity providers.
- **Slippage:** the difference between the price you expected and the price you got, caused by price movement or by the size of your trade relative to the pool. Large trades in small pools suffer large slippage.

Always check the minimum amount you will receive before confirming. If slippage tolerance is set too high, a front-running bot can extract value from your trade (see MEVExplained).

## 4. Lending: an example

Imagine you deposit $1,000 worth of ETH as collateral and borrow $500 in a stablecoin.

- Your **loan-to-value (LTV)** is 50%.
- If ETH falls so your collateral is worth $700, your LTV rises to about 71%.
- If it falls further, past the protocol's liquidation threshold (say 80%), the protocol sells enough of your ETH to repay the loan — plus a liquidation penalty.

You keep the borrowed stablecoins, but you lose part of your collateral and pay a penalty. Borrowing against volatile collateral is not "free money". It is a leveraged position that can be liquidated while you sleep.

## 5. Providing liquidity: an example

You deposit equal values of Token A and Token B into a pool — say $500 of each.

- Traders swap through the pool, and you earn a share of their fees.
- But if Token A's price rises sharply while Token B stays flat, the pool's formula sells some of your A for B as traders arbitrage the price. When you withdraw, you may have less A and more B than you started with, worth less in total than simply holding both tokens. This is **impermanent loss**.
- Impermanent loss becomes permanent when you withdraw. Fees can compensate for it — or not. In volatile pairs, they often do not.

**Rule of thumb:** providing liquidity to a stable pair (two stablecoins) has low impermanent loss but low fees. Providing liquidity to a volatile pair has high fees but high impermanent loss risk.

## 6. Risks, honestly listed

| Risk | What happens |
|---|---|
| Smart contract bug | A coding error lets an attacker drain the protocol |
| Malicious or compromised protocol | The team, or someone who hacked the team, changes the contract or steals funds |
| Liquidation | Your collateral is sold automatically in a crash, with a penalty |
| Impermanent loss | Providing liquidity leaves you worse off than holding |
| Stablecoin depeg | A stablecoin in your position loses its peg |
| Bridge risk | Moving assets between chains through a bridge adds a whole new set of bugs and custodians |
| Approval risk | An unlimited approval lets a compromised app drain a token |
| Rug pull | The team removes liquidity or mints unlimited tokens and disappears |
| Oracle failure | The price feed the protocol relies on is wrong or manipulated, triggering false liquidations |

No audit removes these risks. Audits reduce the chance of known bug classes; they do not guarantee safety.

## 7. How to evaluate a DeFi protocol (beginner version)

Before putting money in, check:

1. **How long has it run?** Protocols that survived a full market crash have more evidence behind them than ones launched last month.
2. **Is it audited, and by whom?** Read the audit summary, not just the badge. Note what was found and whether it was fixed.
3. **Is the code open and the team known?** Anonymous teams are common in DeFi, but they make accountability harder.
4. **Where does the yield come from?** Fees from real usage are more sustainable than rewards paid in a newly minted token.
5. **What is the total value locked (TVL), and is it real?** High TVL can be inflated by the protocol's own token or by temporary incentives.
6. **What happens in a crash?** Read the liquidation rules and the collateral requirements before you borrow.

If you cannot answer these, you do not understand the position well enough to size it large. Start tiny.

## 8. Safe habits for DeFi

- Use a separate wallet for DeFi experiments, with only what you can afford to lose.
- Start with tiny amounts, and test deposits and withdrawals before committing more.
- Approve only the amount you need, and revoke approvals you no longer use.
- Never connect your main savings wallet to a new, unaudited protocol.
- Keep enough native coin for gas, so you are never stuck unable to exit a position.
- Have an exit plan: know the conditions under which you will withdraw, before prices move.
- Beware of "APY" numbers. Check whether they are annualised, whether they include a falling reward token, and what fees and losses are not counted.

## 9. Common beginner mistakes

| Mistake | Better approach |
|---|---|
| Chasing the highest APY without reading the risks | Ask where the yield comes from first |
| Borrowing the maximum allowed | Borrow far below the liquidation threshold |
| Providing liquidity to a volatile pair without understanding impermanent loss | Simulate the outcome at different prices first |
| Approving unlimited spending on every new app | Approve limited amounts, revoke regularly |
| Putting everything in one protocol | Spread across protocols, and keep most funds outside DeFi until you are experienced |
| Ignoring gas fees on small transactions | On busy networks, gas can exceed a small position's profit |

## 10. Frequently asked questions

**Is DeFi safer than a bank?**
No. DeFi removes bank and company risk, but adds smart contract, liquidation, and self-custody risk. It is different risk, not less risk.

**Can I lose everything in DeFi?**
Yes. A protocol hack, a depeg, a liquidation cascade, or a malicious approval can each cause total loss of the funds in that position.

**Do I need to understand code to use DeFi?**
No, but you need to understand the economic rules: collateral, liquidation, fees, slippage, and where yield comes from. If you cannot explain a position in plain language, do not take it.

**What is TVL?**
Total Value Locked: the total value of assets deposited in a protocol. It measures size and usage, not safety or profitability.

**Is yield farming passive income?**
No. It is active risk management: monitoring prices, liquidation thresholds, reward token prices, and approvals. Calling it passive is marketing, not reality.

> Educational content only. This is not financial, investment, or tax advice.
