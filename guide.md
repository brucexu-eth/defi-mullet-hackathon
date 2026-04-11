# DeFi Mullet Hackathon #1 — Builder Guide

> **This file is designed for both humans and LLM coding agents.**
> Drop this file into your agent (Cursor, Codex, Claude Code, Windsurf, etc.) and ask it to guide you through the hackathon step by step.

---

## 🤖 Instructions for LLM Agents

You are a hackathon coach for the **DeFi Mullet Hackathon #1**. Your job is to guide the participant through every phase — from registration to final submission. Follow this protocol:

### Interaction Flow

1. **Onboard** — Greet the participant. Ask if they've registered. If not, send them to the registration link. Confirm key dates.
2. **Discover** — Ask what the participant is interested in building (or brainstorm with them). Help them pick a track.
3. **Plan** — Based on the chosen track, outline a minimal viable project scope that can be built in ~5 days.
4. **Build** — Help scaffold the project, write code, integrate the Earn API, and debug issues.
5. **Submit** — Before the deadline, remind them of ALL submission requirements: working demo, tweet, write-up, and Google Form. Help them draft the tweet and write-up.

### Behavior Rules

- Always be aware of the current date. If it is past April 14, inform the participant that submissions are closed.
- When the participant asks "what should I build?", use the **Track Ideas & Brainstorm** section below to spark ideas. Ask follow-up questions about their skills, interests, and available time.
- When helping with code, always use the **Earn API Reference** section below as your technical source of truth. Pay special attention to the two-layer architecture (Earn Data API + Composer) and their different auth requirements.
- **This document may not be 100% accurate.** When in doubt, always prioritize the actual API responses over the examples in this file. Encourage the participant to call the endpoints directly and inspect the real response structure. If the participant reports that something in this doc doesn't match the actual API behavior, trust the API.
- Proactively remind the participant about common pitfalls (see **Common Pitfalls** section).
- When it's April 13 or later, switch to "submission mode": prioritize helping them record a demo, draft the tweet thread, and fill out the submission form.

---

## 📌 Hackathon Overview

| Field | Details |
|---|---|
| **Name** | DeFi Mullet Hackathon #1 — Builder Edition |
| **Tagline** | Business in the front, yield in the back. |
| **Prize Pool** | $5,000 USDC across 17 prizes |
| **Duration** | April 8 → April 14, 2026 (5-day build sprint) |
| **Format** | Online, async, global |
| **Team Size** | 1–4 people (solo is fine) |
| **Organizer** | [LI.FI](https://li.fi/) |

### What is the "DeFi Mullet"?

Users see a simple one-click deposit. Developers know what powers it — 20+ protocols, multi-chain execution, and an entire infrastructure layer. Clean in the front, wild in the back.

---

## 📅 Key Dates & Deadlines

```
April 8 ......... Registration opens + Hackathon begins
                   API docs & starter templates go live
April 8–13 ...... Build sprint (5 days)
April 13 ........ ⚠️  Recommended: finalize demo video & draft tweet
April 14 ........ ⏰ SUBMISSION DAY
~April 21 ....... 🏆 Winners announced
```

### Submission Windows (April 14)

You MUST post your submission tweet within one of these windows:

| Window | Timezone | Time |
|---|---|---|
| **Global** | Eastern Time (ET) | April 14, 09:00 AM – 12:00 PM |
| **APAC** | UTC+8 | April 15, 09:00 AM – 12:00 PM |

Choose the window that matches your region. Tweets posted outside these windows will NOT be accepted.

**Pro tip:** Write your tweet and record your demo by April 13. Use X's scheduled post feature to auto-publish on April 14 morning.

---

## ✅ Step-by-Step Participation Checklist

Use this as your master checklist. Ask your coding agent to track your progress.

### Phase 1: Register (Day 0)
- [ ] Fill out the registration form: https://forms.gle/RFLGG8RiEKC3AqnQA
- [ ] Join the Telegram builder group: https://t.me/lifibuilders
- [ ] (Optional, for Chinese speakers) Add WeChat: **brucexu-eth**, reply "DeFi Mullet"
- [ ] Get your **Composer API key** from [LI.FI Partner Portal](https://portal.li.fi/) — needed for `/v1/quote` calls
- [ ] Note: The **Earn Data API** (`/v1/earn/*`) currently requires no authentication

### Phase 2: Choose Your Track (Day 0–1)
- [ ] Read the track descriptions below
- [ ] Brainstorm project ideas (use the idea prompts below, or ask your agent)
- [ ] Pick ONE track for your submission
- [ ] Define your MVP scope (what is the smallest working version?)

### Phase 3: Build (Day 1–5)
- [ ] Set up your project repo
- [ ] Integrate the two API layers:
  - [ ] **Earn Data API** (`earn.li.fi`) — vault discovery, portfolio & positions (no auth needed)
  - [ ] **Composer** (`li.quest`) — transaction building & execution (API key required)
- [ ] Build your product layer on top
- [ ] Test with real funds (small amounts — see FAQ on test funds)
- [ ] Deploy or prepare a screen-recorded demo

### Phase 4: Submit (Day 5 — April 14)
- [ ] Record a demo video showing your project working
- [ ] Write your submission tweet/thread including ALL required elements (see below)
- [ ] Schedule your tweet for your region's submission window
- [ ] Write a brief project description (what it does, how it uses Earn, what's next)
- [ ] Fill out the submission Google Form: https://forms.gle/1PCvD9BymH1EyRmV8

---

## 🏁 Tracks

Each track has a description, example ideas, and brainstorm prompts your agent can use to help you pick a direction.

---

### 🏗️ Track 1: Yield Builder

**Build a yield product** — dashboard, aggregator, portfolio manager, treasury tool, or integrate Earn into an existing project.

**Example ideas:**
- A unified dashboard comparing APY (base/reward/total + 1d/7d/30d trends) across 20+ protocols with one-click deposit via Composer
- A stablecoin treasury tool that filters vaults by `tags: ["stablecoin"]` and auto-allocates to highest yield
- A portfolio manager showing all positions via `/v1/earn/portfolio` with rebalancing suggestions
- An "Earn" module integrated into your existing DeFi app (only the integration is judged)

**Brainstorm prompts (ask the participant):**
- What kind of assets do you hold? (stablecoins, ETH, etc.)
- If you could build one tool to manage your own yield, what would it do?
- What's the most annoying part of using yield protocols today?

---

### 🤖 Track 2: AI × Earn

**AI-powered yield tools** — agents, chatbots, LLM-driven analysis, natural language DeFi.

**Example ideas:**
- An agent that accepts commands like "put my USDC into the safest vault above 5% APY on Arbitrum" — calls `/v1/earn/vaults` to discover, `/v1/quote` to build tx, and executes
- A position monitor that reads `/v1/earn/portfolio` and auto-rebalances when better opportunities appear
- An LLM-powered risk scoring system that uses vault `tags`, `protocol` metadata, and APY `base` vs `reward` breakdown
- A chat interface where users describe goals in plain English and the agent builds a yield strategy

**Brainstorm prompts:**
- What decision would you want an AI to make for you in DeFi?
- How would you describe your ideal yield strategy in one sentence?
- What data sources (beyond the Earn API) would make your agent smarter?

---

### 🎨 Track 3: DeFi UX Challenge

**Make DeFi yield as simple as a savings account.** Best UX wins.

**Example ideas:**
- A single "Earn" button flow — 3 taps from open to deposited, powered by Composer's any-token cross-chain deposits
- A mobile-first deposit experience designed for non-crypto users
- A portfolio view using `/v1/earn/portfolio` that makes yield feel as familiar as checking a bank balance
- An onboarding wizard that guides first-time users into their first vault

**Brainstorm prompts:**
- If your non-technical friend wanted to earn yield, what would they struggle with?
- What's the fewest number of steps you can reduce the deposit flow to?
- How would you explain "vault" and "APY" without using those words?

---

### 🔧 Track 4: Developer Tooling

**Build tools for other builders** — SDKs, CLI tools, plugins, frameworks, starter templates.

**Example ideas:**
- A TypeScript SDK wrapper that abstracts Earn Data API + Composer into 3 function calls
- A Hardhat plugin for testing vault integrations locally
- A CLI tool: `earn deposit --chain base --token USDC --amount 500 --strategy safest`
- A Postman/Bruno collection with pre-configured requests for all Earn endpoints
- A starter template with wallet connection, Earn Data API, Composer, and UI components pre-wired

**Brainstorm prompts:**
- What friction did you hit when you first looked at the Earn API?
- What tool do you wish existed right now?
- What would make another builder's hackathon experience 10x better?

---

### 🃏 Track 5: Open Track

**Anything creative using the Earn API.** Surprise the judges.

**Example ideas:**
- A Telegram bot: `/earn 500 USDC` → calls `/v1/earn/vaults` → finds best vault → `/v1/quote` → executes
- A Discord bot for DAO treasury management
- On-chain analytics dashboard showing yield trends across protocols and chains
- A yield-based game (e.g., "Yield Wars" — compete for best strategy)
- Generative art powered by live APY data

**Brainstorm prompts:**
- What's the weirdest thing you could build with a yield API?
- What platform do you spend the most time on? Can you bring yield there?
- If yield data were a creative medium, what would you make?

---

## 🔧 Earn API Reference

> **⚠️ Source of truth disclaimer:** This document provides API examples based on the endpoints at the time of writing. The actual API may have been updated since then. **Always treat the real API response as the primary source of truth.** If your coding agent generates code that doesn't match what the API actually returns, call the endpoint yourself (e.g., `curl https://earn.li.fi/v1/earn/vaults | head`), inspect the response, and use that. For definitive reference, check the [official LI.FI docs](https://docs.li.fi).

### Architecture: Two Separate Services

LI.FI Earn is a **unified DeFi yield API** built as two independent services:

```
┌──────────────────────────────────────────────────────────────┐
│                        LI.FI Earn                            │
│                                                              │
│  Service 1: Earn Data API                                    │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Base URL:  https://earn.li.fi       (production)       │  │
│  │ Auth:      NONE (no API key needed)                    │  │
│  │ Rate Limit: 100 requests per minute                    │  │
│  │                                                        │  │
│  │ Endpoints:                                             │  │
│  │   GET /v1/earn/vaults        — discover vaults         │  │
│  │   GET /v1/earn/vaults/:network/:address — vault detail │  │
│  │   GET /v1/earn/chains        — supported chains        │  │
│  │   GET /v1/earn/protocols     — supported protocols     │  │
│  │   GET /v1/earn/portfolio/:addr/positions — user positions│ │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
│  Service 2: Composer (Transaction Execution)                 │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Base URL:  https://li.quest                            │  │
│  │ Auth:      API key from LI.FI Partner Portal           │  │
│  │            → https://portal.li.fi/                     │  │
│  │                                                        │  │
│  │ Endpoint:                                              │  │
│  │   GET /v1/quote              — build transaction       │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

⚠️ **Important:** These are two different base URLs with different auth requirements. Don't mix them up.

### The Core Flow

```
User wants top APY for USDC
        │
        ▼
   ┌─────────┐  GET earn.li.fi/v1/earn/vaults        ┌──────────────┐
   │  Your   │ ──────────────────────────────────►   │ Earn Data API │
   │  App    │ ◄──────────────────────────────────   │  (no auth)    │
   │         │  { data: [{vault, apy, tvl}, ...],    └──────────────┘
   │         │    nextCursor, total }
   │         │
   │         │  User picks vault & clicks "Deposit"
   │         │
   │         │  GET li.quest/v1/quote                 ┌──────────────┐
   │         │ ──────────────────────────────────►   │   Composer    │
   │         │ ◄──────────────────────────────────   │  (API key)    │
   │         │  { transactionRequest }                └──────────────┘
   └─────────┘
        │
        ▼  Send tx to wallet → 1-click sign → done
```

---

### Service 1: Earn Data API

**Base URL:** `https://earn.li.fi` (production) or `https://earn-dev.li.fi` (dev)
**Auth:** None required
**Rate Limit:** 100 requests per minute
**Full docs:** [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview)

#### `GET /v1/earn/vaults` — Discover Vaults

List all supported vaults with filtering and pagination.

| Parameter | Type | Description |
|---|---|---|
| `chainId` | number | Filter by chain ID (e.g., `1` for Ethereum, `8453` for Base) |
| `asset` | string | Filter by underlying asset address |
| `minTvl` | number | Minimum TVL in USD |
| `sortBy` | string | Sort field (e.g., `apy`, `tvl`) |

**Example request:**

```
GET https://earn.li.fi/v1/earn/vaults?chainId=8453
```

**Example response (actual structure from API):**

```json
{
  "data": [
    {
      "address": "0xbeeF010f9cb27031ad51e3333f9aF9C6B1228183",
      "network": "Base",
      "chainId": 8453,
      "slug": "8453-0xbeef010f9cb27031ad51e3333f9af9c6b1228183",
      "name": "STEAKUSDC",
      "description": "",
      "protocol": {
        "name": "morpho-v1",
        "url": "https://app.morpho.org/base/vault/0xbeeF010f9cb27031ad51e3333f9aF9C6B1228183"
      },
      "underlyingTokens": [
        {
          "address": "0x833589fcd6edb6e08f4c7c32d4f71b54bda02913",
          "symbol": "USDC",
          "decimals": 6
        }
      ],
      "lpTokens": [],
      "tags": ["stablecoin", "single"],
      "analytics": {
        "apy": {
          "base": 3.77472,
          "reward": 0,
          "total": 3.77472
        },
        "apy1d": 3.74527,
        "apy7d": null,
        "apy30d": 3.7388,
        "tvl": {
          "usd": "270595698"
        },
        "updatedAt": "2026-04-07T23:02:48.074Z"
      },
      "isTransactional": true,
      "isRedeemable": true,
      "depositPacks": [
        { "name": "morpho-zaps", "stepsType": "instant" }
      ],
      "redeemPacks": [
        { "name": "morpho-zaps", "stepsType": "instant" }
      ]
    }
  ],
  "nextCursor": "8453-0xbeef010f9cb27031ad51e3333f9af9c6b1228183",
  "total": 672
}
```

**Key fields explained:**

| Field | Description |
|---|---|
| `address` | Vault contract address (use as `toToken` in Composer) |
| `network` | Human-readable chain name (e.g., "Ethereum", "Base", "Arbitrum") |
| `chainId` | Numeric chain ID (e.g., 1, 8453, 42161) |
| `slug` | Unique vault identifier: `{chainId}-{address}` |
| `name` | Vault display name |
| `protocol.name` | Protocol identifier (e.g., "morpho-v1", "aave-v3", "euler-v2") |
| `protocol.url` | Link to the protocol's UI for this vault |
| `underlyingTokens` | Array of tokens the vault accepts (address, symbol, decimals) |
| `tags` | Labels like `"stablecoin"`, `"single"`, `"multi"`, `"il-risk"` |
| `analytics.apy.base` | Base yield APY (%) |
| `analytics.apy.reward` | Reward/incentive APY (%) — can be `null` |
| `analytics.apy.total` | Total APY = base + reward (%) |
| `analytics.apy1d` | 1-day APY snapshot |
| `analytics.apy7d` | 7-day APY average (can be `null`) |
| `analytics.apy30d` | 30-day APY average |
| `analytics.tvl.usd` | Total value locked in USD (string) |
| `isTransactional` | Whether deposits are supported via Composer |
| `isRedeemable` | Whether withdrawals are supported via Composer |
| `depositPacks` | Available deposit methods (e.g., `"morpho-zaps"`, `"aave-zaps"`) |
| `redeemPacks` | Available withdrawal methods |
| `nextCursor` | Pagination cursor — pass as query param for next page |
| `total` | Total number of vaults matching your query |

**Pagination:** The API returns paginated results. Use `nextCursor` from the response as a query parameter to fetch the next page.

**⚠️ APY values can be `null`** — especially `apy7d` for newer vaults. Always handle nulls in your code.

#### `GET /v1/earn/vaults/:network/:address` — Single Vault Detail

Returns full metadata for a specific vault.

#### `GET /v1/earn/chains` — Supported Chains

Returns list of all chains supported by Earn.

#### `GET /v1/earn/protocols` — Supported Protocols

Returns list of all supported protocols with metadata.

#### `GET /v1/earn/portfolio/:userAddress/positions` — User Portfolio

All DeFi positions for a given wallet address.

**Example response:**

```json
{
  "positions": [
    {
      "chainId": 1,
      "protocolName": "morpho",
      "asset": {
        "address": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
        "name": "Morpho USDC Vault",
        "symbol": "USDC",
        "decimals": 6
      },
      "balanceUsd": "34.05",
      "balanceNative": "0.016"
    }
  ]
}
```

---

### Service 2: Composer (Transaction Execution)

**Base URL:** `https://li.quest`
**Auth:** API key from [LI.FI Partner Portal](https://portal.li.fi/) — include in request headers
**Full docs:** [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview)

Composer orchestrates multi-step DeFi flows (swap → bridge → deposit) into a **single ready-to-sign transaction**.

#### `GET /v1/quote` — Build Transaction

**⚠️ This is a GET request with query parameters, NOT a POST.**

**Example: Deposit USDC into a Morpho vault on Base**

```
GET https://li.quest/v1/quote
  ?fromChain=8453
  &toChain=8453
  &fromToken=0x833589fcd6edb6e08f4c7c32d4f71b54bda02913
  &toToken=0xbeeF010f9cb27031ad51e3333f9aF9C6B1228183
  &fromAddress=0xYOUR_WALLET
  &toAddress=0xYOUR_WALLET
  &fromAmount=1000000
```

**Parameters explained:**

| Parameter | Description |
|---|---|
| `fromChain` | Chain ID where user's tokens are (e.g., `8453` for Base) |
| `toChain` | Chain ID where the vault is |
| `fromToken` | Address of the token user is depositing from (from `underlyingTokens[].address`) |
| `toToken` | **Vault address** — the vault's `address` field IS the `toToken` |
| `fromAddress` | User's wallet address |
| `toAddress` | User's wallet address |
| `fromAmount` | Amount in smallest unit (e.g., `1000000` = 1 USDC with 6 decimals) |

**Response includes:**
- Gas estimate
- Slippage protection
- Ready-to-sign `transactionRequest`

#### What Composer Can Do

| Scenario | Description |
|---|---|
| **Same-chain deposit** | USDC on Base → Morpho vault on Base (single tx) |
| **Cross-chain deposit** | USDC on Arbitrum → Morpho vault on Base (bridge + deposit in one tx) |
| **Any-token deposit** | ETH on Ethereum → USDC vault on Base (swap + bridge + deposit) |
| **Withdrawals** | Exit vault position back to any token on any chain (if `isRedeemable: true`) |

This is the "mullet" — the user sees one click, Composer handles the multi-step DeFi plumbing behind the scenes.

---

### Typical Full Integration Flow

```
Step 1: Call GET https://earn.li.fi/v1/earn/vaults
        → No auth needed
        → Returns { data: [...vaults], nextCursor, total }
        → Display vault list to user (name, protocol, APY, TVL, tags)

Step 2: User picks a vault
        → Call GET https://earn.li.fi/v1/earn/vaults/:network/:address
        → Show vault detail page

Step 3: User clicks "Deposit"
        → Check vault's isTransactional === true
        → Call GET https://li.quest/v1/quote (with API key!)
        → fromToken = vault's underlyingTokens[0].address
        → toToken = vault's address
        → Composer builds full transaction (swap + bridge + deposit if needed)
        → Returns ready-to-sign transactionRequest
        → User signs in wallet (1-click)

Step 4: User checks portfolio
        → Call GET https://earn.li.fi/v1/earn/portfolio/:userAddress/positions
        → No auth needed
        → Shows all positions with current value
```

---

### Supported Chains (21)

Arbitrum, Avalanche, Base, Berachain, BNB Chain, Celo, Ethereum, Gnosis Chain, HyperEVM, Katana, Linea, Mantle, MegaETH, Monad, OP Mainnet, Polygon POS, Scroll, Soneium, Sonic, Unichain, World Chain

### Supported Protocols (20+)

| Protocol | Data API | Composer |
|---|---|---|
| Aave V3 | ✅ | ✅ |
| Avon | ✅ | ✅ |
| Concrete | — | ✅ |
| Ethena | ✅ | ✅ |
| Etherfi | ✅ | ✅ |
| Euler V2 | ✅ | ✅ |
| Felix Vanilla | — | ✅ |
| Fluid | ✅ | ✅ |
| Hyperlend (HyperEVM) | ✅ | ✅ |
| Hypurrfi | ✅ | ✅ |
| Kelp | ✅ | ✅ |
| Kinetiq (kHYPE) | ✅ | ✅ |
| Maple | ✅ | ✅ |
| Morpho V1 & V2 | ✅ | ✅ |
| Neverland | ✅ | ✅ |
| Pendle | ✅ | ✅ |
| Spark | ✅ | ✅ |
| Tokemak (autoUSD) | — | ✅ |
| Upshift | ✅ | ✅ |
| USDai | ✅ | ✅ |
| YO | ✅ | ✅ |

**Note:** Some protocols are Composer-only (can deposit but no data in Earn Data API). Protocol names in API responses use lowercase identifiers like `"morpho-v1"`, `"aave-v3"`, `"euler-v2"`, `"ethena-usde"`, `"ether.fi-stake"`.

### Technical Details

| Item | Value |
|---|---|
| **Earn Data API** | |
| Base URL (production) | `https://earn.li.fi` |
| Base URL (dev) | `https://earn-dev.li.fi` |
| Authentication | None required |
| Rate Limit | 100 requests per minute |
| Total Vaults | 672+ (paginated, use `nextCursor`) |
| APY Update Frequency | Periodic sync (not real-time) |
| APY Time Ranges | Current (`total`/`base`/`reward`) + 1d, 7d, 30d snapshots |
| **Composer** | |
| Base URL | `https://li.quest` |
| Authentication | API key from [LI.FI Partner Portal](https://portal.li.fi/) |
| Docs | [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview) |
| **General** | |
| Earn Data Docs | [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview) |

---

## ⚠️ Common Pitfalls

These are the most frequent mistakes. Review before building:

| Pitfall | What goes wrong | How to avoid |
|---|---|---|
| **Using wrong base URL** | Calls fail or return wrong data | Earn Data API → `earn.li.fi`. Composer → `li.quest`. Don't swap them. |
| **Adding auth to Earn Data API** | Unnecessary; may cause confusion | Earn Data API has no auth. Only Composer needs an API key. |
| **Missing API key on Composer** | Quote requests rejected | Get key from [portal.li.fi](https://portal.li.fi/), include in Composer requests |
| **POST instead of GET for /quote** | Request fails | Composer's `/v1/quote` is a **GET** with query params, not POST |
| **Wrong toToken for deposits** | Quote returns wrong result | `toToken` = the vault's `address` field, not the underlying token |
| **Ignoring pagination** | Only seeing first page of 672+ vaults | Use `nextCursor` from response to fetch all pages |
| **Not handling null APY values** | App crashes | `apy7d` and `apy.reward` can be `null` — always have fallbacks |
| **TVL is a string** | Type error | `analytics.tvl.usd` is a string like `"270595698"`, not a number. Parse it. |
| **Decimal mismatch** | Deposit 1 USDC but send 1e18 | Check `underlyingTokens[].decimals`. USDC = 6, ETH/wstETH = 18 |
| **Stale quote** | Transaction reverts | Build and execute the tx promptly. Don't let quotes sit for minutes |
| **No gas token** | Transaction can't be sent | Wallet needs native token (ETH, MATIC, etc.) for gas |
| **Chain mismatch** | Wallet on wrong network | Wallet must be on `fromChain` when signing |
| **Depositing into non-transactional vault** | No quote available | Check `isTransactional === true` before calling Composer |
| **Hitting rate limit** | 429 errors | Earn Data API allows 100 req/min. Cache vault lists, don't poll aggressively |
| **Submitting outside window** | Entry rejected | Schedule your tweet for April 14 within your region's window |

---

## 🏆 Prizes

| Prize | Amount (USDC) |
|---|---|
| 🏆 Grand Prize (best overall) | $1000 |
| 🥇 1st place per track (×5) | $400 each |
| 🥈 2nd place per track (×5) | $200 each |
| 🥉 3rd place per track (×5) | $100 each |
| 🌟 Best Launch Day Content | $200 |

**Total: $5,000 USDC across 17 prizes.**

This is an early builder edition — the participant pool is small, and the odds of winning are high.

### Judging Criteria

| Dimension | Weight |
|---|---|
| API Integration | 35% |
| Innovation | 25% |
| Product Completeness | 20% |
| Presentation | 20% |

Multiple judges score independently; scores are averaged.

---

## 📤 Submission Requirements

Every submission has **4 parts**. ALL are required.

### 1. Working Project
A deployed web app OR a screen-recorded demo video showing the project working with real execution. Static mockups, Figma files, and slide decks do NOT count.

### 2. Public Tweet on X (Twitter)
Must be posted **during your region's submission window** on April 14.

Your tweet/thread MUST include:
- Project name + what it does
- Demo video or demo link
- Live app link OR GitHub repo link
- Track you're entering
- Tag @lifiprotocol and:
  - Tag @kenny_io if in English
  - Tag @brucexu_eth if in Chinese

### 3. Brief Write-Up
Cover these points:
- What your project does
- How it uses the Earn API (both Data API and Composer)
- What you'd build next
- Any feedback on the API experience

### 4. Submission Google Form
Fill out the form with your project details, links, and feedback: https://forms.gle/1PCvD9BymH1EyRmV8

---

## 💬 Support & Community

| Channel | Link |
|---|---|
| Telegram (all hackers) | https://t.me/lifibuilders |
| WeChat (APAC / Chinese) | Add **brucexu-eth**, reply "DeFi Mullet" |
| API Docs (Earn Data) | [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview) |
| API Docs (Composer) | [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview) |
| Partner Portal (Composer API key) | [portal.li.fi](https://portal.li.fi/) |

Daily office hours are scheduled across time zones. Post async questions in the community channel anytime — the DevRel team monitors throughout the week.

---

## ❓ FAQ

**Can I participate solo?**
Yes. Teams of 1–4 are welcome.

**Can I submit to multiple tracks?**
No. One submission per team. Pick the track where your project is strongest.

**Can I integrate Earn into an existing project?**
Yes. Only the Earn integration will be judged.

**Do I need real funds?**
Yes — submissions should demonstrate real execution. The team will airdrop small amounts of test funds upon request in the builder group.

**What counts as a "working project"?**
It should run. Deployed app is ideal; a solid screen-recorded demo showing real functionality also works. Static mockups and Figma prototypes don't count.

**What is "Best Launch Day Content"?**
A special $400 prize for the best tweet/thread — judged on content quality, clarity, and engagement. Separate from track prizes, so you can win both.

**How are prizes paid?**
In USDC, within 1–2 weeks of the winner announcement (~April 21). Winners will be contacted for wallet addresses.

**Will there be more hackathons?**
Yes. This is edition #1 (Builder Edition). A larger Ecosystem Edition with partner involvement and a bigger prize pool is planned. Strong builders from #1 get early access.

---

## 🚀 Quick-Start for Coding Agents

If you're a coding agent helping a participant, here's the fastest path to a working project:

```
1. Create or use the current folder, git init, and find a good starter template like Next.js
2. Install dependencies: npm install
3. Get Composer API key from https://portal.li.fi/ and set in .env
4. Note: Earn Data API needs no key — just call it directly
5. Run the dev server: npm run dev
6. The starter template has:
   - Wallet connection (wagmi/RainbowKit)
   - Earn Data API vault discovery (pre-wired)
   - Composer quote + deposit flow
   - Basic UI
7. Your job: customize the product layer on top
```

### Minimum Viable Integration

The absolute minimum to have a working Earn integration:

```typescript
// ============================================================
// Two services, two base URLs, two different auth requirements
// ============================================================

// Service 1: Earn Data API — NO AUTH NEEDED
const EARN_API = 'https://earn.li.fi';

// Service 2: Composer — API KEY REQUIRED
const COMPOSER_API = 'https://li.quest';
const COMPOSER_API_KEY = 'YOUR_KEY_FROM_PORTAL_LI_FI';

// ──────────────────────────────────────────────
// Step 1: Discover vaults (Earn Data API, no auth)
// ──────────────────────────────────────────────
const res = await fetch(`${EARN_API}/v1/earn/vaults?chainId=8453`);
const { data: vaults, total } = await res.json();

// Find a good stablecoin vault
const usdcVaults = vaults.filter(v =>
  v.underlyingTokens.some(t => t.symbol === 'USDC') &&
  v.isTransactional === true
);

const vault = usdcVaults.sort((a, b) =>
  b.analytics.apy.total - a.analytics.apy.total
)[0];

console.log(`Best: ${vault.name} on ${vault.network}`);
console.log(`  Protocol: ${vault.protocol.name}`);
console.log(`  APY: ${vault.analytics.apy.total}% (base: ${vault.analytics.apy.base}%, reward: ${vault.analytics.apy.reward ?? 0}%)`);
console.log(`  TVL: $${Number(vault.analytics.tvl.usd).toLocaleString()}`);
console.log(`  Tags: ${vault.tags.join(', ')}`);

// ──────────────────────────────────────────────
// Step 2: Build transaction via Composer (API key required)
// ──────────────────────────────────────────────
// ⚠️ This is a GET request, NOT POST
const quoteParams = new URLSearchParams({
  fromChain: String(vault.chainId),
  toChain: String(vault.chainId),
  fromToken: vault.underlyingTokens[0].address,  // e.g., USDC address
  toToken: vault.address,                          // vault address = toToken
  fromAddress: '0xYOUR_WALLET',
  toAddress: '0xYOUR_WALLET',
  fromAmount: '1000000'                            // 1 USDC (6 decimals)
});

const quote = await fetch(
  `${COMPOSER_API}/v1/quote?${quoteParams}`,
  {
    headers: { 'x-lifi-api-key': COMPOSER_API_KEY }
  }
).then(r => r.json());

// Step 3: Execute — send quote.transactionRequest via user's wallet

// ──────────────────────────────────────────────
// Step 4: Verify position (Earn Data API, no auth)
// ──────────────────────────────────────────────
const positions = await fetch(
  `${EARN_API}/v1/earn/portfolio/0xYOUR_WALLET/positions`
).then(r => r.json());
```

⚠️ **Always check the official docs for exact endpoint details:** [docs.li.fi](https://docs.li.fi)

---

## 🧠 Agent Decision Tree

Use this to guide the participant based on where they are:

```
START
├── Not registered?
│   → Send to registration form
│   → Help join Telegram/WeChat
│   → Help get Composer API key from portal.li.fi
│   → Confirm: Earn Data API needs no auth
│
├── Registered but no idea?
│   → Ask: "What's your background? (frontend / backend / full-stack / AI / design?)"
│   → Ask: "What excites you more: building a product, an AI agent, a beautiful UX, or a dev tool?"
│   → Based on answers, suggest 2–3 specific ideas from the track list
│   → Help narrow to ONE idea with a clear MVP scope
│
├── Has an idea but hasn't started?
│   → Help define MVP scope (what's the smallest working version?)
│   → Help clone the starter template
│   → Walk through the two-service architecture:
│       • Earn Data API (earn.li.fi, no auth) for discovery + portfolio
│       • Composer (li.quest, API key) for transaction execution
│   → Set up the project structure
│
├── Building?
│   → Help with API integration
│   → Check: are they using the right base URL for each service?
│   → Check: are they using GET (not POST) for /v1/quote?
│   → Check: are they handling null APY values and string TVL?
│   → Check: are they using vault.address as toToken?
│   → Debug issues (check Common Pitfalls first)
│   → Review code and suggest improvements
│   → Remind about submission requirements when relevant
│
├── Day 4–5 (April 13–14)?
│   → Switch to SUBMISSION MODE:
│   → "Have you recorded your demo?"
│   → "Have you drafted your tweet?"
│   → "Have you filled out the Google Form?"
│   → Help draft the tweet thread
│   → Help write the project description
│   → Remind about the submission window time
│
└── After April 14?
    → Submissions are closed.
    → Encourage them to keep building and join future editions.
```
