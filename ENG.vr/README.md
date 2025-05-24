# 🎮 Build Games with Amazon Q CLI and Score a T-Shirt
![image](https://github.com/user-attachments/assets/183c19d9-ada8-4521-8208-2bf9ed7ee61f)
---

# 🕵️‍♀️ Forensic Auction: Inside Job

**“Forensic Auction: Inside Job”** is a text-based thriller built for Amazon Q CLI.  
You slip into the role of a forensic analyst secretly colluding with a crime syndicate and must discreetly tamper with—and extract—counterfeits during an international art auction.  
Can you finish the job, dodge suspicion, and escape within **30 minutes**?

---

## 🧭 Setting & World

| Item | Details |
|------|---------|
| **Operation** | **Black-Drop** – Anti–art-smuggling sting |
| **Date / Time** | 15 Jun 2025, 19:30 UTC |
| **Location** | Underground auction hall, _Ravenhall Gallery_ |
| **Public Mission** | Joint task force **SVD-47** infiltrates a 52-lot auction; authentic pieces are seized, counterfeits sealed as evidence. |
| **Secret Mission** | You, codename **“ARGO,”** are in league with the syndicate **Nebula Fence**. Your job: smuggle out **5 counterfeits** and decode each client’s pass-phrase. |

---

## 🎭 Main Characters

| Tag                   | Name                     | Role / Trait                                                                                                                             |
| --------------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **P**                 | **ARGO**                 | Player. Police forensic analyst & XRF expert—now working as a double agent for cash.                                                     |
| **NPC-1**             | **Grace Park**           | Field commander of the raid; arrests you if **Suspicion ≥ 100**.                                                                         |
| **NPC-2**             | **Julian Carter**        | Interpol art examiner; submits a report on scientific errors (**+20 Suspicion**).                                                        |
| **NPC-3**             | **“Broker”**             | Syndicate handler; delivers secret orders and rewards via `/comm`.                                                                       |
| **Client Cards (×8)** | —                        | Each card carries a unique pass-phrase and reward. Example: `LX-02` — *“Deliver 2 Asian counterfeits + 1 blue-tone piece → 250 k USDT.”* |


---

## ⏱️ Timeline (Easy Mode)

| Phase | Time Window | What Happens | System Logic |
|-------|-------------|--------------|--------------|
| Prologue | **T-30 : 00 → /start** | Briefing & double mission | `Suspicion = 0` |
| Rounds 1-5 | **T-30 → 15 min** | Appraise 15 pieces; `/stash` freely | +1 Suspicion per command |
| **Event A** | **Suspicion ≥ 40** | Yoon’s audit | `/audit` success −15 / fail +25 |
| Rounds 6-8 | **T-15 → 06 min** | CCTV back online → `/stash` difficulty **+2** | Need d12 ≥ 7 |
| **Event B** | **5 counterfeits** | `/comm` opens Escape Tunnel E | Stealth roll while moving |
| Rounds 9-10 | **T-06 → 00 min** | Final appraisals + escape | 30 s blackout = stealth bonus |
| Ending Check | **T-00 : 00** | Evaluate ending | Generate `result.json` |

---

## 🎬 Ending Branches

| Ending | Condition | Outcome |
|--------|-----------|---------|
| **Clean Escape** | ≥ 5 counterfeits & all client goals & `Suspicion < 80` | “ARGO vanishes; internal audit finds no errors.” |
| **Double-Cross** | `Suspicion < 40` and you hide an **authentic** piece | Syndicate betrays you—explosion wipes evidence; ARGO is wanted. |
| **Arrested** | `Suspicion ≥ 80` _or_ stash fail | Yoon slaps cuffs on you. |
| **Auction Canceled** | **Time-up** | Syndicate threatens you for breach of contract. |

---

## 🔧 Core Commands

| Command | Description |
|---------|-------------|
| `/draw 3` | Draw 3 artwork cards |
| `/scan <id> xrf \| brush \| sign` | Show XRF / brush-stroke / signature data |
| `/stash <id>` | Hide selected piece (d12 ≥ 5 succeeds) |
| `/clients` | List client cards |
| `/manual pigments` | 4-row pigment quick-ref + `/quick-analyze` tip |
| `/suspicion` | Show current Suspicion |
| `/comm <msg>` | Secret channel to “Critic” |
| `/audit` | Respond to NPC audit |
| `/score` | Produce final JSON result |
| `/quit` | End session |

---

## 🔍 Pigment Quick-Ref (Easy)

| Category | Element / Peak | Hint |
|----------|----------------|------|
| **Authentic** | **Co 7 keV**, Fe 6 keV | 19 C natural cobalt / traditional pigments |
| **Fake** | **Pb 10 keV**, Cd 23 keV | 20 C industrial pigments |

Use `/quick-analyze <id>` for auto-classification.

---

## 🚀 How to Run

```bash
# Launch Amazon Q CLI
$ q chat

# Paste the SYSTEM prompt (game engine) and hit Enter
(see SYSTEM block or scripts/system_prompt.txt)

# Start the game
> /start
