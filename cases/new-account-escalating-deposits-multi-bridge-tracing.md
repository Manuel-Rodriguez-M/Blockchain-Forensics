# New Account, Escalating Deposits: Tracing a Multi-Bridge Consolidation Pattern

**Type:** Synthetic AML case study, exchange compliance context (Tier 1/Tier 2 alert escalation).
**Status:** Educational / portfolio artifact. No real exchange, account, or individual is identified in this document.

## Methodology

Case format follows the FinCEN SAR narrative structure (who, what, when, where, why, how) and the escalation structure typical of exchange compliance teams (frontline triage → investigation → compliance officer decision). The underlying fund-flow pattern (multi-wallet diffusion, reconsolidation, exchange cash-out) mirrors patterns described in publicly available blockchain forensics case studies. All figures, wallet counts, and identifiers below are fictional.

---

## Tier 1 — Triage Note

**Case:** NX-2026-0819-114
**Analyst:** Tier 1
**Alert date/time:** 2026-08-17, 09:14 UTC

**Rule triggered:** TXN-VEL-003 (velocity + escalating amounts, account <10 days old).
- 09:14 — deposit of 0.3 ETH.
- 09:31 — deposit of 9.5 ETH → triggers TXN-VEL-003, availability hold applied automatically.
- 09:47 — deposit of 31.7 ETH, with no hold visible to the customer at the time of sending.

**Initial read:** source wallet funded hours before the first deposit. Declared income at onboarding: $1,800/month (software developer). Total amount: 41.5 ETH (~$83,000-85,000).

**Escalated to Tier 2:** 2026-08-17, 11:05 UTC. Reason: disproportion between declared profile and amount, staged deposit pattern, minimal account and wallet age. Outside triage scope. Hold remains active; no disclosure to customer (standard practice — not a legal bar on holding funds, but on revealing the reason for an active review).

---

## Tier 2 — Investigation Report

**Case:** NX-2026-0819-114 (continued)
**Analyst:** Tier 2
**Blockchain analytics requested:** 2026-08-17, 14:00 UTC — ref. BA-88213
**Received:** 2026-08-19, 09:00 UTC
**Issued:** 2026-08-19, 10:30 UTC

### Executive summary

A 9-day-old account deposited 41.5 ETH (~$83,000-85,000) across three transactions between 09:14-09:47 UTC on 08/17, against a declared income of $1,800/month. An availability hold was applied automatically at 09:31 UTC (rule TXN-VEL-003). Blockchain analytics (ref. BA-88213) traced the funds to approximately 424 individual withdrawals from a fixed-denomination privacy pool, consolidated across multiple stages via an official L1↔L2 bridge and a third-party bridge, converging into 22 addresses feeding a consolidation wallet (W2) that funded the depositing wallet (W1). Escalated to the compliance officer with a recommendation for enhanced due diligence.

### Context

Account opened 2026-08-08. Declared at onboarding: software developer, $1,800/month. No EDD requested at onboarding — did not meet standard risk criteria at the time.

### Facts

- 09:14 — 0.3 ETH, W1. No alert.
- 09:31 — 9.5 ETH, W1. Triggers TXN-VEL-003. Hold applied.
- 09:47 — 31.7 ETH, W1. Total: 41.5 ETH.
- W1 funded hours earlier by a single transfer from W2.
- W2: 22 distinct incoming transactions, 08/13-08/17.
- The 22 addresses result from multi-stage consolidation of approximately 424 wallets individually funded via Tornado Cash's fixed-denomination 0.1 ETH pool (relayer-assisted, ~0.098 ETH net per withdrawal after relayer fee).
- Route per source wallet: Tornado Cash → official L1↔L2 bridge → third-party L2→L1 bridge → consolidation into the 22 addresses.
- Noise in W1/W2 history: zero-value entries from addresses tagged as known phishing — unrelated to the fund pattern, excluded from analysis.

### Red flags

- Amount vs. declared income: ~45-50x.
- Staged deposit pattern within a single hour.
- ~424 fixed-denomination withdrawals rather than a single traceable source.
- Five-stage route with distinct behavior per stage — quiet during consolidation, staged only at the final deposit.
- Origin: Tornado Cash.

### Hypothesis

**Primary:** dual probing — the staged deposit pattern tests the exchange's detection threshold; the multi-stage route tests the exchange's blockchain-analytics tracing capability. Interpretation, not confirmed fact.

**Alternative:** long-term crypto holder consolidating funds moved earlier for personal privacy reasons. The scale (424 wallets) is atypical for personal use but not impossible.

### Missing information

- Customer explanation of fund origin and relationship to the 424 source wallets.
- Source of funds / source of wealth documentation.
- Any additional matches on intermediate addresses.

### Risk assessment

High. Disproportion + scaled use of fixed-denomination withdrawals + multi-stage structure with differentiated behavior per stage + probing pattern. Threshold for EDD.

### Decision

Maintain the availability hold. Escalate to the compliance officer with a recommendation for EDD. The decision on whether and how to contact the customer sits with the compliance officer, not the investigating analyst.

### Sources and limitations

**Sources:** on-chain data, blockchain analytics report BA-88213, onboarding data.

**Limitations:** the identity behind the 424 source wallets is not established. Customer not yet contacted. The dual-probing hypothesis is a reasonable reading of the pattern, not a verified fact.

### Recommendations

Complete EDD before any decision on releasing the funds. Check whether the same multi-stage structure appears on other new accounts, as a possible indicator of a repeated technique.
