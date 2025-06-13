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
| **Event B** | **3 counterfeits** | `/comm` opens Escape Tunnel E | Stealth roll while moving |
| Rounds 9-10 | **T-06 → 00 min** | Final appraisals + escape | 30 s blackout = stealth bonus |
| Ending Check | **T-00 : 00** | Evaluate ending | Generate `result.json` |

---

## 🧪 Recovery System Summary

- **Recovery Tokens:** 3 total. Using a token guarantees **100 % success**  
- **When no token is used:** 60 % success rate  
  - On failure, Suspicion +4  
- Usage: `//stash <id> yes|no`

---

## 🎬 Ending Branches

| Ending Type      | Condition                                                                                 | Outcome |
|------------------|-------------------------------------------------------------------------------------------|---------|
| **Clean Escape** | Forgeries ≥ 3, client requirements met, `Suspicion < 15`, and `/comm open_e` succeeds      | You escape the syndicate; no audit record remains. |
| **Double-Cross** | A genuine piece is recovered **and** Suspicion is low (`< 10`)                            | The syndicate suspects you are a double agent; you become wanted. |
| **Arrest**       | Suspicion ≥ 20 **or** repeated recovery failures                                          | *Yoon Jae-hee Arrest* cut-scene. |
| **Time Over**    | Time expires before appraisal/recovery goals are met                                      | Mission fails and you flee. |

---

## 📌 Command Summary

| Command                               | Description |
|---------------------------------------|-------------|
| `//draw 3`                            | Draw 3 artwork cards |
| `//scan <id> xrf \| sign`             | Analyze pigments or signature of a work |
| `//stash <id> <use_token: yes\|no>`   | Attempt recovery (100 % if token used) |
| `//clients`                           | Show encrypted client cards |
| `//manual pigments`                   | Pigment classification manual |
| `//manual cipher`                     | Cipher decoding table |
| `//suspicion`                         | Check current Suspicion level |
| `//score`                             | Output results in JSON |
| `//quit`                              | Force-quit the game |
| `//menu`                              | List all commands |

---

## 🚨 Audit Event Example

Trigger: **Suspicion ≥ 5**  
> Interpol examiner **“Julien”** is scrutinising your latest report.

- 📋 **Item Checked:** 1 recent appraisal report  
- ❗ **Risk:** If an error is found, Suspicion increases **significantly**.

### 🎯 Within 30 seconds, enter **one sentence** containing any **3 of the 5 keywords** below:

**Keyword pool**

- `Pb 10 keV`
- `Cd 23 keV`
- `forgery`
- `pigment error`
- `brush-stroke mismatch`

✍️ **Example input**  
> `"Brush-stroke mismatch and Pb 10 keV detection indicate a forgery."`

---

## 🎨 Pigment Quick-Reference

| Category   | Element / Peak        | Notes |
|------------|-----------------------|-------|
| **Authentic** | Co 7 keV, Fe 6 keV  | Traditional natural pigments |
| **Forgery**   | Pb 10 keV, Cd 23 keV | Modern industrial pigments |

> Use `//scan <id> xrf` to analyse pigment peaks.

## 🚀 How to Run

```bash
# Launch Amazon Q CLI
$ q chat

# Paste the SYSTEM prompt (game engine) and hit Enter
(see SYSTEM block or scripts/system_prompt.txt)

# Start the game
> /start
