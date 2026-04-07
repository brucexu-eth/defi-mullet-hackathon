# DeFi Mullet Hackathon #1 — Builder Guide (LLM.md)

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
- When helping with code, always use the **Earn API Reference** section below as your technical source of truth. Pay special attention to the two-layer architecture (Earn Data API + Composer).
- Proactively remind the participant about common pitfalls (see **Common Pitfalls** section).
- When it's April 13 or later, switch to "submission mode": prioritize helping them record a demo, draft the tweet thread, and fill out the submission form.

---

## 📌 Hackathon Overview

| Field | Details |
|---|---|
| **Name** | DeFi Mullet Hackathon #1 — Builder Edition |
| **Tagline** | Business in the front, yield in the back. |
| **Prize Pool** | $5,000 USDT across 17 prizes |
| **Duration** | April 9 → April 14, 2026 (5-day build sprint) |
| **Format** | Online, async, global |
| **Team Size** | 1–4 people (solo is fine) |
| **Organizer** | [LI.FI](https://li.fi/) |

### What is the "DeFi Mullet"?

Users see a simple one-click deposit. Developers know what powers it — 20+ protocols, multi-chain execution, and an entire infrastructure layer. Clean in the front, wild in the back.

---

## 📅 Key Dates & Deadlines

```
April 9 ......... Registration opens + Hackathon begins
                   API docs & starter templates go live
April 9–13 ...... Build sprint (5 days)
April 13 ........ ⚠️  Recommended: finalize demo video & draft tweet
April 14 ........ ⏰ SUBMISSION DAY (also LI.FI Earn public launch)
~April 21 ....... 🏆 Winners announced
```

### Submission Windows (April 14)

You MUST post your submission tweet within one of these windows:

| Window | Timezone | Time |
|---|---|---|
| **Global** | Eastern Time (ET) | April 14, 09:00 AM – 12:00 PM |
| **APAC** | UTC+8 | April 14, 09:00 AM – 12:00 PM |

Choose the window that matches your region. Tweets posted outside these windows will NOT be accepted.

**Pro tip:** Write your tweet and record your demo by April 13. Use X's scheduled post feature to auto-publish on April 14 morning.

---

## ✅ Step-by-Step Participation Checklist

Use this as your master checklist. Ask your coding agent to track your progress.

### Phase 1: Register (Day 0)
- [ ] Fill out the registration form: https://forms.gle/RFLGG8RiEKC3AqnQA
- [ ] Join the Telegram builder group: [TODO — tg link]
- [ ] (Optional, for Chinese speakers) Add WeChat: **brucexu-eth**, reply "DeFi Mullet"
- [ ] Create an account on [LI.FI Portal](https://portal.li.fi/) and get your API key

### Phase 2: Choose Your Track (Day 0–1)
- [ ] Read the track descriptions below
- [ ] Brainstorm project ideas (use the idea prompts below, or ask your agent)
- [ ] Pick ONE track for your submission
- [ ] Define your MVP scope (what is the smallest working version?)

### Phase 3: Build (Day 1–5)
- [ ] Set up your project repo
- [ ] Integrate the Earn API — two layers:
  - [ ] **Earn Data API** — vault discovery, portfolio & positions
  - [ ] **Composer** — transaction building & execution (deposit/withdraw)
- [ ] Build your product layer on top
- [ ] Test with real funds (small amounts — see FAQ on test funds)
- [ ] Deploy or prepare a screen-recorded demo

### Phase 4: Submit (Day 5 — April 14)
- [ ] Record a demo video showing your project working
- [ ] Write your submission tweet/thread including ALL required elements (see below)
- [ ] Schedule your tweet for your region's submission window
- [ ] Write a brief project description (what it does, how it uses Earn, what's next)
- [ ] Fill out the submission Google Form: [TODO — link]

---

## 🏁 Tracks

Each track has a description, example ideas, and brainstorm prompts your agent can use to help you pick a direction.

---

### 🏗️ Track 1: Yield Builder

**Build a yield product** — dashboard, aggregator, portfolio manager, treasury tool, or integrate Earn into an existing project.

**Example ideas:**
- A unified dashboard comparing APY (1d/7d/30d) across 20+ protocols with one-click deposit via Composer
- A stablecoin treasury tool that auto-allocates idle assets to the highest-yielding vaults
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
- An LLM-powered risk scoring system that rates vault safety using protocol metadata from `/v1/earn/protocols`
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
- A Postman/Bruno collection with pre-configured Earn API requests for all endpoints
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

### Architecture: Two Layers

LI.FI Earn is a **unified DeFi yield API** with two layers:

```
┌─────────────────────────────────────────────────────┐
│                   LI.FI Earn                        │
│                                                     │
│  Layer 1: Earn Data API                             │
│  ┌───────────────────────────────────────────────┐  │
│  │ Vault discovery, metadata, APY, TVL,          │  │
│  │ portfolio positions & returns                 │  │
│  │ Endpoints: /v1/earn/vaults, /v1/earn/chains,  │  │
│  │ /v1/earn/protocols, /v1/earn/portfolio         │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
│  Layer 2: Composer (Transaction Execution)          │
│  ┌───────────────────────────────────────────────┐  │
│  │ Swap + bridge + deposit in one transaction    │  │
│  │ Endpoint: /v1/quote                           │  │
│  └───────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
```

Together, they give you a **single integration point** to discover yield opportunities AND execute deposits — same-chain or cross-chain.

### The Core Flow

```
User wants top APY for USDC
        │
        ▼
   ┌─────────┐    GET /v1/earn/vaults       ┌──────────────┐
   │  Your   │ ──────────────────────────►  │ Earn Data API │
   │  App    │ ◄──────────────────────────  │ (Data Service)│
   │         │    [{vault1, APY: yy%},      └──────────────┘
   │         │     {vault2, APY: nn%}...]
   │         │
   │         │  User picks vault & clicks "Deposit"
   │         │
   │         │    GET /v1/quote              ┌──────────────┐
   │         │ ──────────────────────────►  │   Composer    │
   │         │ ◄──────────────────────────  │(Tx Execution) │
   │         │    {transactionRequest}       └──────────────┘
   └─────────┘
        │
        ▼  Send tx to wallet → 1-click sign → done
```

### Authentication

1. Create an account on **[LI.FI Portal](https://portal.li.fi/)**
2. Generate a dedicated **API key**
3. Include the API key in every request

This is step zero — do this before writing any code.

---

### Layer 1: Earn Data API

Full documentation: [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview)

#### `GET /v1/earn/vaults` — Discover Vaults

List all supported vaults with filtering.

| Parameter | Type | Description |
|---|---|---|
| `chainId` | string | Filter by chain (e.g., `ethereum`, `base`) |
| `asset` | string | Filter by underlying asset address |
| `minTvl` | number | Minimum TVL in USD |
| `sortBy` | string | Sort field (e.g., `apy`, `tvl`) |

**Example response:**

```json
{
  "vaults": [
    {
      "address": "0x7BfA7C4f149E7415b73bdeDfe609237e29CBF34A",
      "network": "base",
      "protocol": "morpho",
      "underlyingAssets": {
        "address": "0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913",
        "symbol": "USDC",
        "decimals": 6
      },
      "apy": {
        "1d": 4.82,
        "7d": 5.01,
        "30d": 4.95
      },
      "tvl": 125000000,
      "type": "ERC-4626"
    }
  ]
}
```

**APY data:** Available in 1-day, 7-day, and 30-day time ranges. Updated periodically (not real-time).

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

### Layer 2: Composer (Transaction Execution)

Full documentation: [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview)

Composer orchestrates multi-step DeFi flows (swap → bridge → deposit) into a **single ready-to-sign transaction**.

#### `GET /v1/quote` — Build Transaction

**Base URL:** `https://li.quest/v1/quote`

**⚠️ This is a GET request with query parameters, NOT a POST.**

**Example: Deposit USDC into a Morpho vault on Base**

```
GET https://li.quest/v1/quote
  ?fromChain=8453
  &toChain=8453
  &fromToken=0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
  &toToken=0x7BfA7C4f149E7415b73bdeDfe609237e29CBF34A
  &fromAddress=0xYOUR_WALLET
  &toAddress=0xYOUR_WALLET
  &fromAmount=1000000
```

**Parameters explained:**

| Parameter | Description |
|---|---|
| `fromChain` | Chain ID where user's tokens are (e.g., `8453` for Base) |
| `toChain` | Chain ID where the vault is |
| `fromToken` | Token address user is depositing from |
| `toToken` | **Vault address** (the vault IS the "toToken") |
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
| **Withdrawals** | Exit vault position back to any token on any chain |

This is the "mullet" — the user sees one click, Composer handles the multi-step DeFi plumbing behind the scenes.

---

### Typical Full Integration Flow

```
Step 1: Your app calls GET /v1/earn/vaults
        → Earn Data API fetches from Data Service
        → Returns vault list (APY, TVL, protocol, chain)
        → You display this to the user

Step 2: User picks a vault
        → Your app calls GET /v1/earn/vaults/:network/:address
        → Shows vault detail page

Step 3: User clicks "Deposit"
        → Your app calls GET /v1/quote with fromToken + toToken (= vault address)
        → Composer builds the full transaction (swap + bridge + deposit if needed)
        → Returns ready-to-sign transactionRequest
        → User signs in wallet (1-click)

Step 4: User checks portfolio
        → Your app calls GET /v1/earn/portfolio/:userAddress/positions
        → Shows all positions with current value and returns
```

---

### Supported Chains (21)

Arbitrum, Avalanche, Base, Berachain, BNB Chain, Celo, Ethereum, Gnosis Chain, HyperEVM, Katana, Linea, Mantle, MegaETH, Monad, OP Mainnet, Polygon POS, Scroll, Soneium, Sonic, Unichain, World Chain

### Supported Protocols (20+)

| Protocol | Data API | Composer |
|---|---|---|
| Aave | ✅ | ✅ |
| Avon | ✅ | ✅ |
| Concrete | — | ✅ |
| Ethena | ✅ | ✅ |
| Etherfi | ✅ | ✅ |
| Euler | ✅ | ✅ |
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

**Note:** Some protocols are Composer-only (can deposit but no data in Earn Data API). Some have full support in both layers.

### Technical Details

| Item | Value |
|---|---|
| API Rate Limit | 150 requests per second |
| Authentication | API key via [LI.FI Portal](https://portal.li.fi/) |
| APY Update Frequency | Periodic sync (not real-time) |
| APY Time Ranges | 1-day, 7-day, 30-day |
| Vault Standard | ERC-4626 |
| API Docs | [docs.li.fi](https://docs.li.fi) |
| Composer Docs | [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview) |
| Earn Data Docs | [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview) |

---

## ⚠️ Common Pitfalls

These are the most frequent mistakes. Review before building:

| Pitfall | What goes wrong | How to avoid |
|---|---|---|
| **Missing API key** | API rejects all requests | Get your key from [LI.FI Portal](https://portal.li.fi/), include in every request |
| **POST instead of GET for /quote** | Request fails | Composer's `/v1/quote` is a **GET** with query params, not a POST |
| **Wrong toToken for deposits** | Quote returns wrong result | `toToken` should be the **vault address**, not the underlying token |
| **Decimal mismatch** | Deposit 1 USDC but send 1e18 | USDC = 6 decimals, ETH = 18 — always check `decimals` from vault response |
| **Stale quote** | Transaction reverts | Build and execute the tx promptly. Don't let quotes sit for minutes |
| **No gas token** | Transaction can't be sent | Ensure wallet has native token (ETH, MATIC, etc.) for gas |
| **Chain mismatch** | Wallet on wrong network | Wallet must be on `fromChain` when signing the transaction |
| **Ignoring Composer for cross-chain** | Building manual bridge+deposit flows | Use Composer — it handles swap + bridge + deposit in one tx |
| **Submitting outside window** | Entry rejected | Schedule your tweet for April 14 within your region's window |

---

## 🏆 Prizes

| Prize | Amount (USDT) |
|---|---|
| 🏆 Grand Prize (best overall) | $800 |
| 🥇 1st place per track (×5) | $400 each |
| 🥈 2nd place per track (×5) | $200 each |
| 🥉 3rd place per track (×5) | $100 each |
| 🌟 Best Launch Day Content | $400 |

**Total: $5,000 USDT across 17 prizes.**

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
- [TODO — required hashtag]
- [TODO — required @mention]

### 3. Brief Write-Up
Cover these points:
- What your project does
- How it uses the Earn API (both Data API and Composer)
- What you'd build next
- Any feedback on the API experience

### 4. Submission Google Form
Fill out the form with your project details, links, and feedback: [TODO — link]

---

## 💬 Support & Community

| Channel | Link |
|---|---|
| Telegram (all hackers) | [TODO — tg link] |
| WeChat (APAC / Chinese) | Add **brucexu-eth**, reply "DeFi Mullet" |
| API Docs (Earn Data) | [docs.li.fi/earn/overview](https://docs.li.fi/earn/overview) |
| API Docs (Composer) | [docs.li.fi/composer/overview](https://docs.li.fi/composer/overview) |
| LI.FI Portal (API key) | [portal.li.fi](https://portal.li.fi/) |
| Starter Template Repo | [TODO — repo link] |

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
In USDT, within 1–2 weeks of the winner announcement (~April 21). Winners will be contacted for wallet addresses.

**Will there be more hackathons?**
Yes. This is edition #1 (Builder Edition). A larger Ecosystem Edition with partner involvement and a bigger prize pool is planned. Strong builders from #1 get early access.

---

## 🚀 Quick-Start for Coding Agents

If you're a coding agent helping a participant, here's the fastest path to a working project:

```
1. Clone the starter template: [TODO — repo link]
2. Install dependencies: npm install
3. Get API key from https://portal.li.fi/ and set in .env
4. Run the dev server: npm run dev
5. The starter template has:
   - Wallet connection (wagmi/RainbowKit)
   - Earn Data API vault discovery (pre-wired)
   - Composer quote + deposit flow
   - Basic UI
6. Your job: customize the product layer on top
```

### Minimum Viable Integration

The absolute minimum to have a working Earn integration:

```typescript
// Step 0: Get your API key from https://portal.li.fi/

const API_KEY = 'YOUR_API_KEY';
const headers = { 'x-lifi-api-key': API_KEY };

// Step 1: Discover vaults
const vaults = await fetch(
  'https://li.quest/v1/earn/vaults?chainId=base&asset=USDC&sortBy=apy',
  { headers }
).then(r => r.json());

// Step 2: Pick a vault — toToken IS the vault address
const vault = vaults.vaults[0];
console.log(`${vault.protocol} on ${vault.network}: ${vault.apy['7d']}% APY`);

// Step 3: Build transaction via Composer (⚠️ GET request, not POST)
const quoteParams = new URLSearchParams({
  fromChain: '8453',                    // Base chain ID
  toChain: '8453',                      // Same chain for same-chain deposit
  fromToken: vault.underlyingAssets.address, // e.g., USDC address
  toToken: vault.address,               // Vault address = toToken
  fromAddress: '0xYOUR_WALLET',
  toAddress: '0xYOUR_WALLET',
  fromAmount: '1000000'                 // 1 USDC (6 decimals)
});

const quote = await fetch(
  `https://li.quest/v1/quote?${quoteParams}`,
  { headers }
).then(r => r.json());

// Step 4: Execute — send quote.transactionRequest via user's wallet (ethers/viem/wagmi)

// Step 5: Verify — check user's positions
const positions = await fetch(
  `https://li.quest/v1/earn/portfolio/0xYOUR_WALLET/positions`,
  { headers }
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
│   → Help create account on portal.li.fi and get API key
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
│   → Walk through the two-layer API architecture:
│       • Earn Data API for discovery + portfolio
│       • Composer for transaction execution
│   → Set up the project structure
│
├── Building?
│   → Help with Earn API integration (check: are they using GET for /quote?)
│   → Debug issues (check Common Pitfalls first — especially decimal mismatches and toToken confusion)
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
