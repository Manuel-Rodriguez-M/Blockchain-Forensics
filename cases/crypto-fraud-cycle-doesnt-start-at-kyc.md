# The Crypto Fraud Cycle Doesn't Start at KYC

**Type:** Fraud-typology synthesis, crypto / blockchain forensics context.
**Status:** Educational / portfolio artifact. Synthesizes public sources (FATF, Elliptic, Chainalysis, EU regulation, press reporting); not legal advice, not a description of any single company's proprietary detection system. Full source list in [sources](crypto-fraud-cycle-doesnt-start-at-kyc-sources.md).

---

## Why KYC isn't the finish line

Onboarding verifies who opened an account. It says nothing about what that account will be used for six weeks later. Most of the damage described below happens well after onboarding, or never touches a KYC'd account at all. Fraud in crypto has to be read across the account's whole lifecycle, not its first ten minutes.

## The pattern: onboarding, dormancy, movement, exit

A useful way to frame crypto-specific fraud is as a four-stage sequence. An account opens cleanly, sits dormant while it builds a credible history, gets used to move value, and finally exits the platform. Each stage maps onto something independently documented by blockchain-analytics firms and by the Financial Action Task Force (FATF).

Dormancy works as trust-building. Accounts with verified history built up over years get used precisely because that history reads as legitimate. Newly created accounts often test with small amounts first, then scale up. FATF separately flags a dormant account that becomes active, and multiple large transactions to a newly created or recently activated account, as recognized indicators.

Movement is the tell. Near-immediate forwarding, money leaving an account almost as fast as it arrives, is one of the clearest mule warning signs. So is a transaction volume inconsistent with the account's stated purpose, or a balance that stays consistently low in between.

Exit is the hardest point to reach. FATF's indicators describe funds passing through a chain of accounts before reaching an exchange, then converting and moving to a foreign exchange quickly. The layering isn't random. It puts a jurisdictional gap between the crime and where the money finally lands.

## Mules and network cash-out patterns

Crypto money mules aren't one type of person. Unwitting mules get recruited through romance scams, where a fake online partner asks them to receive and forward money, or through fake remote payment-processing job offers, or simply a promise of easy money for the use of an account. Witting mules know exactly what they're doing: they hand over control of an account that isn't necessarily theirs, compromised, bought, or rented, but with real verified history behind it. Mule farms sit at the other end. Accounts get created at scale using stolen or falsified identity documents, for the sole purpose of muling. The tell is a thin transaction history that shares identifying details with other accounts, fingerprints across a whole batch of accounts that each look clean on their own.

At the network level, two shapes recur. Fan-in is many source wallets converging on one. Fan-out is one source spreading across many destinations. Neither is visible looking at a single account. Both show up the moment someone maps the network instead.

One number matters more than the rest. Pig-butchering-style crypto scams are estimated to move roughly $64 billion a year in proceeds. 76% of scam proceeds in 2024, and 80% in the first half of 2025, passed through a crypto exchange at some point in the chain. The deception itself happens entirely off-platform, a fake relationship or a fake investment app, but the exchange layer is still where almost all of that money surfaces. It's the only point where a regulated, KYC'd entity has a real chance to interrupt it.

## Unhosted wallets: the ownership problem

Crypto fraud has a structural feature that bank fraud mostly doesn't. The counterparty on the other end of a transfer is frequently a wallet that no regulated institution holds at all.

Since 30 December 2024, EU Regulation 2023/1113 has required Crypto-Asset Service Providers to verify ownership of a self-hosted wallet above the regulation's thresholds. Recording an address isn't enough. The provider has to confirm the person sending or receiving actually controls it.

One real mechanism was built specifically for this problem. AOPP, the Address Ownership Proof Protocol, is an open-source standard built by 21 Analytics, originally created to meet a Swiss regulatory requirement from 2019 and later adopted in Singapore. It works through a cryptographically signed message. The wallet itself proves it controls the address, something a screenshot or a typed claim can't do.

The North Wales case below is the same problem from the opposite direction. No protocol needed to be defeated. The real owner was persuaded to hand over control willingly.

## The pattern in practice

Three real, independently reported cases land on three different points of the cycle above.

Scammers impersonating the co-chair of a US presidential inaugural committee sent emails from a typosquatted domain in 2025, differing from the real one by a single lowercase letter. They were soliciting donations. A donor sent $250,300 in USDT. The funds were dispersed across multiple addresses within minutes, including one tied to a Nigeria-based exchange account. Federal investigators used blockchain tracing to recover $40,300 of it, and officials classified the scheme as business email compromise. The money was already extracted and being fanned out to break the trail before anyone could catch up: the movement stage, in practice.

A scammer posing as a senior UK police officer told a different victim, in a separate 2025 case, that their identification documents had turned up on an arrested suspect's phone. It was a fabricated security-breach pretext. The victim was pressured into entering their wallet recovery phrase on a spoofed website, and the attacker drained roughly £2.1M, about $2.8M, in Bitcoin from a cold-storage wallet within minutes. No protocol needed to be broken here. The real owner handed over control directly. That's the ownership problem above, seen from the other side.

There's also a fictional illustration worth reading in full: [*New Account, Escalating Deposits: Tracing a Multi-Bridge Consolidation Pattern*](new-account-escalating-deposits-multi-bridge-tracing.md). It's a synthetic AML case study, no real exchange, wallet, or individual identified, built around the same mechanic: a privacy-pool origin, multi-stage bridge consolidation, and a deposit pattern that escalates in three steps before crossing a detection threshold. That staged-then-scaled shape wasn't invented for the story. It matches what gets independently documented as a mule-account testing pattern.

## The analyst's response framework

None of the three cases above would have been stopped by a single control. What they share is a moment where a proportional response mattered, not a blanket block and not silent inaction:

- **Allow.** The default, for activity with no signal cluster present.
- **Step-up.** Additional verification at a specific moment: a new device, a new payout destination, a first large withdrawal. Not friction applied everywhere equally.
- **Limit.** Capping value or velocity while a pattern is still ambiguous, without freezing the account outright.
- **Hold.** Pausing a specific transaction or withdrawal for review.
- **Block.** Reserved for high-confidence fraud, not the default first move.

Entry, escalation, and exit call for different levels of scrutiny. Treating "verified at onboarding" as "safe forever after" is what let all three cases above happen.

## Limitations

FATF's exact indicator wording was reconstructed from cross-checked secondary sources describing its 2020 red flag report, not read from the primary document directly. Readers who need verbatim wording should consult FATF's own publication. Figures and framing originally drawn from Sumsub Academy's Fraud Prevention course were not independently re-verified here; only claims attributed to FATF, Elliptic, Chainalysis, the EU regulation, AOPP, and the three real cases were checked against outside sources. This document doesn't describe how to trace funds on-chain. That's separate, unbuilt methodology. It isn't legal advice, and doesn't assert that any named platform, bank, or individual in the cases above is at fault beyond what investigators and press reported. This is a snapshot as of September 2026. Verify before reusing a figure in anything time-sensitive.
