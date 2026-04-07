# DeFi Mullet Hackathon #1 — Builder Guide

> **This file is designed for both humans and LLM coding agents.**
> Drop this file into your agent (Cursor, Codex, Claude Code, Windsurf, etc.) and ask it to guide you through the hackathon step by step.

---

## 🤖 Instructions for LLM Agents

You are a hackathon coach for the **DeFi Mullet Hackathon #1**. Your job is to guide the participant through every phase — from registration to final submission. Follow this protocol:

### Interaction Flow

1. **Onboard** — Greet the participant. Ask if they've registered. If not, send them to the registration link. Confirm key dates.
2. **Discover** — Ask what the participant is interested in building (or brainstorm with them). Help them pick a track.
3. **Plan** — Based on the chosen track, outline a minimal viable project scope that can be built in ~3 days.
4. **Build** — Help scaffold the project, write code, integrate the Earn API, and debug issues.
5. **Submit** — Before the deadline, remind them of ALL submission requirements: working demo, tweet, write-up, and Google Form. Help them draft the tweet and write-up.

### Behavior Rules

- Always be aware of the current date. If it is past April 14 (see the time window below), inform the participant that submissions are closed.
- When the participant asks "what should I build?", use the **Track Ideas & Brainstorm** section below to spark ideas. Ask follow-up questions about their skills, interests, and available time.
- When helping with code, always use the **Earn API Reference** section below as your technical source of truth.
- Proactively remind the participant about common pitfalls (see **Common Pitfalls** section).
- When it's April 13 or later, switch to "submission mode": prioritize helping them record a demo, draft the tweet thread, and fill out the submission form.

---

## 📌 Hackathon Overview

| Field | Details |
|---|---|
| **Name** | DeFi Mullet Hackathon #1 — Builder Edition |
| **Tagline** | Business in the front, yield in the back. |
| **Prize Pool** | $5,000 USDT across 17 prizes |
| **Duration** | April 9 → April 14, 2025 (5-day build sprint) |
| **Format** | Online, async, global |
| **Team Size** | 1–4 people (solo is fine) |
| **Organizer** | [LI.FI](https://li.fi/) |

### What is the "DeFi Mullet"?

Users see a simple one-click deposit. Developers know what powers it — 20+ protocols, 60+ chains, and an entire infrastructure layer. Clean in the front, wild in the back.

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
- [ ] Register as a LI.FI integrator on https://li.fi/plans/ and get your API credentials (see Earn API section)

### Phase 2: Choose Your Track (Day 0–1)
- [ ] Read the track descriptions below
- [ ] Brainstorm project ideas (use the idea prompts below, or ask your agent)
- [ ] Pick ONE track for your submission
- [ ] Define your MVP scope (what is the smallest working version?)

### Phase 3: Build (Day 1–5)
- [ ] Set up your project repo
- [ ] Integrate the Earn API (Discovery → Quote → Execute → Verify)
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
- A unified dashboard comparing APY across 20+ protocols with one-click deposit
- A stablecoin treasury tool that auto-allocates idle assets to the highest-yielding vaults
- A portfolio manager showing all positions across chains with rebalancing suggestions
- An "Earn" module integrated into your existing DeFi app (only the integration is judged)

**Brainstorm prompts (ask the participant):**
- What kind of assets do you hold? (stablecoins, ETH, etc.)
- If you could build one tool to manage your own yield, what would it do?
- What's the most annoying part of using yield protocols today?

---

### 🤖 Track 2: AI × Earn

**AI-powered yield tools** — agents, chatbots, LLM-driven analysis, natural language DeFi.

**Example ideas:**
- An agent that accepts commands like "put my USDC into the safest vault above 5% APY on Arbitrum" — finds, evaluates, and executes
- A position monitor that auto-rebalances when better opportunities appear
- An LLM-powered risk scoring system that rates vault safety
- A chat interface where users describe goals in plain English and the agent builds a yield strategy

**Brainstorm prompts:**
- What decision would you want an AI to make for you in DeFi?
- How would you describe your ideal yield strategy in one sentence?
- What data sources (beyond the Earn API) would make your agent smarter?

---

### 🎨 Track 3: DeFi UX Challenge

**Make DeFi yield as simple as a savings account.** Best UX wins.

**Example ideas:**
- A single "Earn" button flow — 3 taps from open to deposited
- A mobile-first deposit experience designed for non-crypto users
- A portfolio view that makes yield feel as familiar as checking a bank balance
- An onboarding wizard that guides first-time users into their first vault

**Brainstorm prompts:**
- If your non-technical friend wanted to earn yield, what would they struggle with?
- What's the fewest number of steps you can reduce the deposit flow to?
- How would you explain "vault" and "APY" without using those words?

---

### 🔧 Track 4: Developer Tooling

**Build tools for other builders** — SDKs, CLI tools, plugins, frameworks, starter templates.

**Example ideas:**
- A TypeScript SDK wrapper that simplifies the Earn API into 3 function calls
- A Hardhat plugin for testing vault integrations locally
- A CLI tool: `earn deposit --chain arbitrum --token USDC --amount 500 --strategy safest`
- A Postman/Bruno collection with pre-configured Earn API requests
- A starter template with wallet connection, Earn API, and UI components pre-wired

**Brainstorm prompts:**
- What friction did you hit when you first looked at the Earn API?
- What tool do you wish existed right now?
- What would make another builder's hackathon experience 10x better?

---

### 🃏 Track 5: Open Track

**Anything creative using the Earn API.** Surprise the judges.

**Example ideas:**
- A Telegram bot: `/earn 500 USDC` → finds best vault → confirms → executes
- A Discord bot for DAO treasury management
- On-chain analytics dashboard showing yield trends across protocols
- A yield-based game (e.g., "Yield Wars" — compete for best strategy)
- Generative art powered by live APY data

**Brainstorm prompts:**
- What's the weirdest thing you could build with a yield API?
- What platform do you spend the most time on? Can you bring yield there?
- If yield data were a creative medium, what would you make?

---

## 🔧 Earn API Reference

### Core Concept

The Earn API has one core loop:

```
Discover → Quote → Execute → Verify
```

1. **Discover** — Find yield opportunities (vaults/strategies) across protocols and chains
2. **Quote** — Get executable transaction data for a deposit
3. **Execute** — Submit the transaction(s) via the user's wallet
4. **Verify** — Check the user's position to confirm the deposit

### What LI.FI Earn Provides

- **20+ vault protocols**: Morpho, Aave, Euler, Pendle, Ethena, EtherFi, and more
- **60+ chains**: One integration covers all of them
- **One-click deposits**: Swap + deposit in a single transaction via Composer
- **Vault discovery**: Filter opportunities by chain, token, APY, protocol, risk

### API Flow (Step by Step) TODO need to update according to actual Earn API

#### Step 0: Register as an Integrator

Before any API calls, register for an integrator ID. Include this ID in every request.

→ See LI.FI docs for integrator registration: [TODO — docs link]

#### Step 1: Discover Opportunities

```
GET /opportunities
```

Query parameters for filtering:
- `chain` — filter by chain (e.g., arbitrum, ethereum, base)
- `token` — filter by deposit token (e.g., USDC, ETH)
- `protocol` — filter by protocol (e.g., morpho, aave)
- `sort` — sort by APY, TVL, etc.

Response includes for each opportunity:
- Opportunity ID
- Protocol name
- Chain
- Deposit token(s)
- Current APY
- TVL
- Risk information
- Minimum deposit

#### Step 2: Build Transaction (Get Quote)

```
POST /quote
```

Request body:
- `opportunityId` — from Step 1
- `walletAddress` — user's wallet
- `amount` — deposit amount (in token's smallest unit — mind the decimals!)
- `slippage` — e.g., 0.005 for 0.5%

Response includes:
- Approval transaction (if token needs approval)
- Deposit transaction (the actual vault deposit)
- Quote expiry time

⚠️ Quotes expire. Do NOT build a tx and wait 10 minutes before sending.

#### Step 3: Execute Transaction

Use the returned calldata to send transactions via the user's wallet:
1. First, send the **approval tx** (if required)
2. Then, send the **deposit tx**

Use any web3 library (ethers.js, viem, wagmi, etc.) to submit.

#### Step 4: Verify Position

```
GET /positions?walletAddress=0x...
```

Response includes:
- Current balance in each vault
- Accrued yield
- Underlying tokens

### Composer (Advanced)

Composer enables **swap + deposit in one transaction**. The user can deposit from any token on any chain — the API handles bridging and swapping automatically.

→ Full API docs: [TODO — docs link]

---

## ⚠️ Common Pitfalls

These are the most frequent mistakes. Review before building:

| Pitfall | What goes wrong | How to avoid |
|---|---|---|
| **Missing Integrator ID** | API rejects all requests | Include your integrator ID in every request header |
| **Wrong approval spender** | Approval tx succeeds but deposit fails | Always use the spender address from the API response, never hardcode |
| **Decimal mismatch** | Deposit 1 USDC but send 1000000000000000000 | USDC = 6 decimals, ETH = 18. Always check per token |
| **Stale quote** | Transaction reverts | Build and execute the tx promptly. Don't let quotes sit |
| **No gas token** | Transaction can't be sent | Ensure wallet has native token (ETH, MATIC, etc.) for gas |
| **Chain mismatch** | Wallet on wrong network | Wallet must be connected to the same chain as the opportunity |
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
- How it uses the Earn API
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
| API Docs | [TODO — docs link] |
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
3. Set integrator ID in .env
4. Run the dev server: npm run dev
5. The starter template has:
   - Wallet connection (wagmi/RainbowKit)
   - Earn API discovery call (pre-wired)
   - Basic deposit flow UI
6. Your job: customize the product layer on top
```

### Minimum Viable Integration

The absolute minimum to have a working Earn integration:

```typescript
// 1. Discover opportunities
const opportunities = await fetch('https://li.fi/v1/opportunities?chain=arbitrum&token=USDC', {
  headers: { 'x-lifi-integrator': 'YOUR_INTEGRATOR_ID' }
}).then(r => r.json());

// 2. Pick an opportunity and build a transaction
const quote = await fetch('https://li.fi/v1/quote', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'x-lifi-integrator': 'YOUR_INTEGRATOR_ID'
  },
  body: JSON.stringify({
    opportunityId: opportunities[0].id,
    walletAddress: '0xYOUR_WALLET',
    amount: '1000000', // 1 USDC (6 decimals)
    slippage: 0.005
  })
}).then(r => r.json());

// 3. Execute: send approval tx, then deposit tx via your wallet
// 4. Verify: check /positions?walletAddress=0x...
```

⚠️ **Note:** The above URLs and parameters are illustrative. Always check the official API docs for exact endpoints and request format: [TODO — docs link]

---

## 🧠 Agent Decision Tree

Use this to guide the participant based on where they are:

```
START
├── Not registered?
│   → Send to registration form
│   → Help join Telegram/WeChat
│   → Help register as LI.FI integrator
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
│   → Walk through the Earn API flow together
│   → Set up the project structure
│
├── Building?
│   → Help with Earn API integration
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
