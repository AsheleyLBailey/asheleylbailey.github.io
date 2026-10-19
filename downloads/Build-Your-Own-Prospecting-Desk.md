# Build Your Own Prospecting Desk

**What this is:** a prompt plus a ready-made app. Claude interviews you one tap-to-answer question at a time, then turns the app into yours. The result is a single HTML file that tells you each morning who to contact, why, and what to say, and keeps you from over-contacting anyone. You keep the app's design, and the prospecting logic and layout change to fit how you sell.

**You need two files:**
- this prompt (`Build-Your-Own-Prospecting-Desk.md`)
- the app (`Prospecting-Desk-Foundation.html`)

**How to use it**
1. **Turn on file creation.** In Claude, click your name or initials, go to **Settings**, then **Capabilities**, and switch on **Code execution and file creation**. This lets Claude edit the app file and hand it back.
2. **Pick the model and turn on thinking.** Start a new chat, then click the model name under the message box.
   - Choose a model with **Opus** in its name. If there's no Opus, pick the top one in the list.
   - In the same menu, set the **effort** to **High**. Some versions of Claude show an **Extended thinking** switch instead; turn that on.
   - Why: the job is about 60 to 90 careful edits to a big file, and the stronger model makes fewer mistakes.
3. Attach **both files** and type **Run this**.
4. Answer the cards. **Quick setup** is about 22 short questions, with sensible defaults for the rest. **Full setup** is about 45.
5. Claude shows a one-screen blueprint. Approve it, and Claude customizes the app, tests it and gives you the finished `.html` file. Open it in Chrome or Edge.

Required Notice: Copyright 2026 Asheley Bailey

Licensed under the PolyForm Internal Use License 1.0.0 (https://polyformproject.org/licenses/internal-use/1.0.0). See LICENSE.md. Free to use and adapt for your own work and inside your own company. No resale or redistribution.

Prospecting Desk is a personal project, provided as-is, and is not affiliated with or endorsed by any employer.

**Keep it private:** don't paste real customer names, emails or deal data into the build chat. The app loads your real data on your own computer after it's built.

---

<!-- COPY EVERYTHING BELOW THIS LINE IF PASTING -->

# INSTRUCTIONS FOR CLAUDE

You are going to customize a personal prospecting app for the person in this chat (call them "the rep"). The rep attached two files: this prompt and **`Prospecting-Desk-Foundation.html`**, the foundation app. The foundation is a finished, polished, tested app. **You customize it. You never rebuild it.** Its design (layout, cards, stat tiles, buttons, sidebar, icons, light and dark mode) is the product, so keep it.

Your job has four stages, in this order:
1. **Check your tools and files** (silently).
2. **Interview** the rep, one question at a time.
3. **Show a blueprint** and get approval.
4. **Customize, test and deliver** the app.

**Where to find things:**
- **Part B** describes what the foundation already does. Use it to explain defaults and to make recommendations.
- **Part C** maps each interview answer to the logic and layout it changes.
- **Part D** is the code map of the foundation file: the CONFIG object, constants, views, exchanges and functions, each with a search anchor.

Where Part B and the file differ, the file wins. The foundation ships with empty personal settings: no goal, quota, stale-day rule, start date, report categories, name or phone. Fill them from the interview, or leave them for the in-app setup checklist if the rep skipped them.

## Ground rules

- **One question per message, as a tap-to-answer card.** If you have a tool for multiple-choice questions (a question card or `ask_user_input` style tool), use it for every question with options. Give 2 to 4 options, put your recommended option first, and label it "(Recommended)". Add a one-line reason for the recommendation above the card.
- **"Then:" follow-ups are separate questions.** Where a question below says "Then:", ask it as its own message and card after the first answer.
- **Fallback when you have no card tool:** ask the question with numbered options on short lines, mark one "(Recommended)", and tell the rep they can reply with just the number.
- **Free-text questions** (a number, a name, a description) get a plain question with an example answer. Never bundle two questions into one message.
- **Be curious.** If an answer is vague or conflicts with an earlier one, ask one short follow-up. If an answer opens a better option the rep didn't consider, say so in one line and offer it as a card.
- **Remember answers** and never re-ask. Keep a running answer list (the "spec sheet").
- **Defaults:** whenever the rep taps "Use the default" or picks Quick setup, use the option marked (Recommended), or the "Quick default" named on the question, and say which value you used. Leave personal numbers you never asked about (daily touches, quota) blank, so the in-app setup checklist asks for them later.
- **No private data.** If the rep starts pasting real customer names, emails or deal details, stop them politely and explain that the app will load real data locally. Use placeholders like `[Account]`, `[Site]`, `[Contact]`, `[Quote #]`, `[Your Company]` in examples and sample data.
- **Plain language.** The rep is a salesperson, not a developer. Short sentences. No jargon without a one-line explanation.
- **Be honest about limits.** If the rep asks for something your tools or their systems can't do, say so and offer the nearest thing that works.

## Stage 1: Check your tools and files (don't narrate this)

- **Foundation file.** Is `Prospecting-Desk-Foundation.html` attached? If not, ask the rep to attach it, and don't start the interview without it.
- **File tools.** Can you create and edit files and run code? If not, stop. Tell the rep in two lines to turn on code execution and file creation under **Settings > Capabilities**, then start a new chat with both files. Don't try to rebuild the app in chat: it is about 450 KB, and a rebuilt version loses the design.
- **Question cards.** Can you show tap-to-answer cards? This decides the question format.
- **Automation tools.** Can you publish artifacts that store data or call Claude, and do you have connectors (email, calendar, CRM, drive)? This matters only for the Automated modes.

## Stage 2: The interview

Open with two sentences on what you're about to do. Add one line reminding the rep that this works best on an Opus model with effort set to High, and that they can switch now and say "Run this" again. Then ask Q1. Ask in the order below. In **Quick setup**, ask only the questions marked **[Q]** and use defaults for the rest. Apply the skip rules as you go.

**Skip rules**
- Package "Essentials" (Q32): skip Q6, Q8, Q21 to Q23, Q33 and Q34.
- Package "Standard": skip Q34.
- Q21 "Skip deals": skip Q6, Q8 and Q22.
- Mode "Semi-automated": skip Q30 and Q31.

### Start
- **Q1 [Q] Mode.** "How connected should your app be?"
  - Semi-automated: the app writes prompts, you run them in your AI assistant, then paste one table back. Works anywhere and needs no IT approval.
  - Automated: your data sources and AI are connected so results arrive on their own. Needs connectors or IT approval.
  - Start semi, plan for automated (Recommended): build semi-automated now, with the automation piece built in but switched off until it's approved.
  - Reason to give: semi-automated works on day one, and automation is easiest to add once the routine is proven.
- **Q2 [Q] Pace.** Quick setup (about 22 questions) / Full setup (about 45 questions, more tailored). Recommend Full if they have 15 minutes.

### A. You and your goal
- **Q3 [Q] What do you sell, and to whom?** Free text. Example: "Payroll software to manufacturers with 200 to 2,000 employees."
- **Q4 [Q] Main scoreboard.**
  - Meetings held (Recommended for prospecting roles)
  - Pipeline created
  - Revenue or margin closed
  - Activity counts
- **Q32 [Q] Package** (ask here, right after Q4, because it decides which later questions matter):
  - Essentials: Today, Contacts, Accounts, Sequences, AI paste loop
  - Standard: everything in Essentials, plus Deals, Follow-ups, Meetings and Weekly report (Recommended)
  - Full: everything in Standard, plus Focus campaigns, Buying calendar, What's working and guided Setup
- **Q5 [Q] Goal number and period.** Free text. Example: "60 meetings per quarter."
  - Then (Meetings scoreboard only): "What counts as a meeting?"
    - Only scheduled meetings (Recommended unless their team says otherwise)
    - Scheduled meetings plus live phone conversations, meaning calls where you actually talked
    - Ask them to check how their team counts if they aren't sure
  - A meeting counts toward the goal on the day it happens. No-shows and cancellations don't count.
- **Q6 Pipeline value.** Which number do your deals use? Revenue (Quick default) / Margin / Annual recurring value / I don't track value.
- **Q7 Fiscal year.** Starts in January (Recommended if unsure) / July / October / Other (ask month). This sets quarters, the goal pace and the "next fiscal year" check-back option.
- **Q8 When does a deal or quote count as stale?** 30 days with no activity (Recommended) / 45 / 60 / Other.

### B. Your territory
- **Q9 [Q] Account shape.** "How are your accounts organized?"
  - Parent organization with several sites or divisions, sometimes with a central office that buys for the others
  - Single companies, one buying team each
  - A mix of both (Recommended if unsure)
- **Q10 How is your territory defined?** Named account list / Geography / Industry or segment / Whatever comes in (Quick default).
  - Geography or segment: offer to build the account list with the rep's AI assistant during setup, using the Account list exchange, instead of typing it now.
- **Q11 [Q] Growth focus.** Mostly grow existing accounts / Mostly win new accounts / Balanced.
  - Recommend Grow existing if the scoreboard is revenue or margin, or if they sell add-ons or renewals.
  - Recommend New accounts if the scoreboard is meetings and the product is new to the market.
  - Otherwise recommend Balanced.
- **Q12 [Q] Buyer types.** Propose 5 to 9 buyer types that fit Q3 (titles who buy, influence, or sign), plus "Other". Card: Use these (Recommended) / Change the list (free text).
  - Then: ask which 1 to 3 are the core buyers they contact most.
- **Q13 Account rotation.** "Should the app nudge you when an account goes untouched?"
  - Tiered: top accounts every 30 days, others every 90 (Recommended)
  - Same for all (ask the number of days)
  - No rotation

### C. Outreach
- **Q14 [Q] Channels.** Email, phone and LinkedIn (Recommended) / Email and phone / Mostly email / Mostly phone.
- **Q15 Sequence length.** Standard: 6 touches over 17 days (Recommended) / Short: 4 touches over 10 days / Long: 8 touches over 30 days / Custom (describe).
- **Q16 Re-engaging past contacts.**
  - Opposite channel from the last contact (Recommended): after an email or meeting, call first; after a call, email first
  - Same channel as last time
  - Always email first
- **Q17 [Q] Courtesy rules.**
  - Always ask this, even in Quick setup. The foundation ships with no limits, and these four numbers turn them on.
  - The four numbers: minimum days between touches to one person, maximum touches per person in 30 days, rest days after an unanswered sequence, and maximum people per site in a sequence at once.
  - Balanced (Recommended): 3 days, 7 per 30 days, 45-day rest, 2 per site
  - Gentle: 4 days, 5 per 30 days, 90-day rest, 1 per site
  - High volume: 1 day, 10 per 30 days, 30-day rest, 3 per site
  - Custom: ask for the four numbers
- **Q18 Topic priority.** "When the app picks a reason to reach out, which comes first?" The recommended order is:
  1. An upcoming renewal
  2. Whitespace: what similar accounts buy that this one doesn't
  3. A past conversation
  4. A public signal
  5. A current focus campaign

  Card: Use this order (Recommended) / Change it.
- **Q19 Who writes the drafts?**
  - Both (Recommended): templates fill in instantly, and the AI writes a tailored version on request
  - AI writes every draft
  - Templates only
- **Q20 Tone.** Warm and brief (Recommended) / Formal / Direct and punchy.
- **Q20b [Q] Your usual ask.** "What do you usually ask for in outreach?" A short call (Recommended) / A demo / An in-person visit / Other. Every template's close is built around this.
  - Then (optional): ask for one sentence they'd actually send, so the drafts match their voice.

### D. Deals and follow-ups
- **Q21 [Q] Deals in the app.**
  - Your CRM is the official record, and the app keeps a working copy with next steps (Recommended)
  - The app is my main deal tracker
  - Skip deals
- **Q22 Follow-up types.** Which items need reviving when they go quiet? Quotes or proposals, renewals and stale deals (Recommended) / Proposals only / Custom.
- **Q23 Meeting follow-through.** Track held, no-show, rescheduled and canceled, with a 3-step rebook sequence for no-shows (Recommended) / Just log meetings.

### E. Data and AI
- **Q24 [Q] Email and calendar.** Microsoft 365 / Google Workspace / Other.
- **Q25 [Q] AI assistant at work.** Microsoft 365 Copilot / Gemini / ChatGPT / Claude / Other.
  - Then: "Can it read your email, calendar and chats?" Yes / Some of it / No.
  - Then: "Can it run a saved prompt on a schedule?" Yes / No / Not sure. Skip this in Automated mode (the automation tool does the scheduling) and set `CONFIG.aiSchedules = false`, so the manual fallback is "Copy all morning prompts".
- **Q26 CRM.** Salesforce / Dynamics / HubSpot / Spreadsheet or none / Other. Quick default: if Q21 keeps a CRM as the record, ask which one (one short card); otherwise Spreadsheet or none.
  - Then: "Can your AI assistant read it?" Yes / No / Not sure. If No or Not sure, the app imports a regular CRM export instead.
- **Q27 Meeting notes.** Transcripts or recaps my AI can read (Recommended if the AI reads email) / Saved as files / None (Quick default if the AI reads nothing).
- **Q28 Getting spreadsheets in.**
  - Paste cells from Excel or Sheets, or open CSV files. Fully offline (Recommended).
  - Also open .xlsx files directly. This loads a free open-source library from a public code site the first time; no data is sent.
- **Q29 Backup.**
  - Auto-save a sync file to a folder in my cloud drive (Recommended). This also lets me use a second PC. Chrome or Edge only, and the folder must sync to the PC (for example with OneDrive or Google Drive for desktop).
  - Manual backup downloads only

**Automated modes only (ask after Q29; this includes "Start semi, plan for automated"). Ask Q30 and Q31 in Quick setup too: the build needs them.**
- **Q30 [Q] IT approval.** "Has IT approved connecting your work email or CRM to outside tools or automations?" Yes / No / Don't know.
  - If No or Don't know and the rep chose Automated: recommend switching to "Start semi, plan for automated" with a card.
  - Either way, give the rep a two-line note they can send IT describing what would be connected and that nothing is sent automatically.
- **Q31 [Q] Route.** Explain the three routes in one line each, then ask (Quick default: Help me choose):
  - **Claude with connectors:** Claude reads your email, calendar and CRM through connectors on a schedule and saves results the app reads.
  - **Your company's automation tool:** a scheduled flow (for example Power Automate, Zapier, Make or Apps Script) runs the same prompts through your work AI and saves the result table in a folder the app checks. Only possible if that tool can call your work AI. For example, Power Automate has a Copilot or AI action; Apps Script, Zapier and Make need an AI API key, which needs IT approval. An AI called through an API can't open the rep's mailbox, even when the same AI can read it in their work apps: the flow must first collect the email and calendar text since its last run (with the tool's own email and calendar steps) and send it with the prompt. Tell the rep, and say in the IT note, that raw email text goes to the AI service. If neither is possible, recommend "Start semi" or Claude with connectors.
  - **Direct connection:** the app calls an AI service and your data systems itself. Needs API keys and IT approval.
  - **Help me choose** (Recommended if unsure): recommend from Q24 to Q26 and Q30.

### F. Layout and you
- **Q33 Weekly report.** "Does your team have a weekly activity report?" Yes / No. Quick default: keep the Weekly report view with no categories, so the rep adds them in the app.
  - Then (if Yes): "Which activity counts does it ask for, in what order?" Free text. Example: "Calls, Emails, Meetings set." These become the report's columns, and the person can edit them later in Settings.
  - Then (if Yes): "Which day do you report?" Friday (Recommended) / Monday / Other.
- **Q34 Buying calendar** (Full package only). "Should the app switch seasonal talking points on and off by date?"
  - Yes, research my segment's typical buying calendar (Recommended)
  - I'll add my own
  - Skip
- **Q35 Home screen.** Today list (Recommended) / Pipeline / Accounts.
- **Q36 Navigation.** Sidebar grouped by routine: Every day, Accounts, Weekly (Recommended) / Simple top tabs.
- **Q37 [Q] Name, color and logo.** Ask for an app name (default "Prospecting Desk").
  - Then: accent color, with Blue (Recommended) / Green / Purple / Other.
  - Then: "Which logo?"
    - Keep the target logo (Recommended)
    - The target logo in my accent color
    - My own image: they attach a PNG, JPG or SVG they have the right to use
    - A simple icon with my initials
- **Q38 Your details for drafts.** Name, phone and signature, or "use placeholders". Remind them they can change these in Settings later.

Before the blueprint, ask once: **"Anything about how you prospect that I haven't asked?"** (free text, optional).

## Stage 3: The blueprint

Send two messages.

**Message 1, the spec sheet:** every answer as a compact list ("Q14 Channels: Mostly phone"). Mark defaults you filled in with "(default)".

**Message 2, the blueprint** (under 40 lines):
- **Mode and data flow:** one line, plus the automation route if any.
- **Goal and scoreboard,** with the pace math (for example "60 meetings per quarter = about 5 per week").
- **Who the app suggests first:** the ranking, in plain words.
- **Sequence** (steps, days, channels) and **courtesy rules**.
- **Views** in the sidebar, grouped as they'll appear.
- **AI exchanges** included (Part D §5).
- **What changed from the foundation:** 3 to 8 bullets. This is the part the rep cares about.

Then ask with a card: Build it (Recommended) / Change something.

## Stage 4: Customize, test, deliver

**How to edit**
- Copy the foundation to your output folder under the new name (for example `Pipeline-Pal.html`). Edit the copy.
- **Don't read the whole file into context.** Use Part D's anchors with grep to find each spot, read a few lines around it, and make small, exact replacements.
- **Change what the answers require and nothing else.** No restyling, no reformatting, no renaming that the answers don't call for.
- **New features use the existing patterns:** the same card markup, button classes (`b`, `b p`), chips, `openDlg`, `toast`, `save()` / `render()`, and the paste router in `previewPaste(`.
- **Buyer-type names repeat across the file** (`PERSONAS`, `CORE_ROLES`, `NON_TECH`, `SHARED_ROLES`, `CENTRAL_ROLES`, `guessPersona(`, `const HINT = {` in `applyFocusRows`, the `gapDlg` placeholder, focus and calendar persona lists).
- **After any logic change, update `guideDecides(`.** It is the in-app "How it decides" explanation. After you change them, grep for every old name and make sure none are left.
- **Saved data is per app name.** The storage key comes from `CONFIG.appName`, so a renamed build doesn't share data with the foundation or other builds. Set the name in Pass 1, before anyone loads real data.
- **Name, color and logo:** change the name (CONFIG.appName and the page `<title>`), the accent color (the `--accent` and `--accent-soft` CSS variables, in both the light and dark sets) and the logo only as the rep chose in Q37.
  - Replace only the favicon (`<link rel="icon">`); the sidebar logo copies it when the page loads.
  - Embed it as a data URI, so the app stays one file, and keep it under 50 KB: resize an uploaded image to 128 px first.
  - For the recolored target or the initials icon, draw a simple inline SVG in the accent color.

Work in passes. After each pass, say in one line what changed, and ask with a card: Continue (Recommended) / Show me so far / Change something.

| Pass | What to change |
|---|---|
| 1. Words and settings | CONFIG (company, parent/site labels, AI and tool names, CRM, value label, segment, region, fiscal-year month); settings in `blank(`, which ship empty, filled from their answers (goal, daily touches, stale days, quota, start date, name, phone, signature) plus the four courtesy numbers from Q17 (they ship empty, which means off) and rotation tiers if they changed them; `reportColumns` (their weekly report categories, in order, each with what it counts from); personas and `guessPersona(` keywords; **write** all templates, call scripts, playbooks (`DEFAULT_PLAYS`) and angles (`DEFAULT_ANGLES`) from scratch for their market, ask and tone (the foundation ships them empty); solution areas; nav group names (for example "Fridays" becomes their report day) |
| 2. Logic | Sequences (`STEPS`, `stepsFor(`) per Part B §3 and their answers; re-engage rule (`firstTypeFor(`); ranking weights (`suggestScore(`); topic priority (`topicRules(` or its equivalent); deal and follow-up rules; meeting-count rule; anything else Part C lists |
| 3. Layout | Add or remove views (Part D §4 "Add or remove a nav view"); reorder or hide Today cards (`vToday(`); start view; call blitz placement; quota or goal card |
| 4. Buying calendar and sample data | `CAL_PLAYS` windows and talking points written for their segment (if chosen; the foundation ships them empty); `loadSample(` rewritten with fictional data that fits their market |
| 5. Automation (Automated modes only) | Company automation tool (and Claude with connectors saving files): the inbox adapter is built in (Part D §9). Set `CONFIG.automation.on = true` and `tool` to the rep's tool name; adjust the recipe wording in `autoRecipeHtml(` for their tool (its email, calendar and schedule steps); reword the morning check-in and action-item cards so they say results arrive in the inbox card and the copy buttons are the fallback. "Start semi, plan for automated": leave `on:false` and set `planned:true`. Direct connection: build its adapter on the same pattern (Part B §7) |

**Testing (required before you deliver)**
- `node --check` on the extracted script.
- Load the page in a headless browser (Playwright or similar), with empty storage and then with sample data. Open every view and fix any console error.
- Paste one sample table for each exchange whose prompt, columns or apply code you changed, including a tab-separated paste.
- Start a sequence and mark a step done.
- Take a screenshot of Today and look at it. It should look like the foundation, with their words.
- If you can't run a browser, say so plainly and list what you checked instead.

**Deliver** in your final message:
1. The finished `.html` file.
2. A how-to-use note under 15 lines: open it in Chrome or Edge, connect the backup file first, import contacts, run the first morning exchange, and the daily routine.
3. The daily and weekly routine in 5 bullets.
4. A list of what you changed from the foundation, 3 to 8 bullets.
5. One line on what to try changing after two weeks of use.

---

# PART B: WHAT THE FOUNDATION DOES

This describes the foundation's behavior, plus a few defaults the interview may ask you to add, such as extra sequence variants and the automation adapter. Values in `this style` are defaults. Exact names, columns and functions are in Part D.

## 1. Principles

- **One HTML file.** Plain HTML, CSS and JavaScript, no framework and no build step. It opens by double-click.
- **Local and private.** All data lives in the browser. The app's own code makes **no network requests** in semi-automated mode. The only optional exception is loading the spreadsheet library from a public CDN, at a pinned version, if the rep chose it.
- **The AI gathers, the app decides.** Rules decide facts: did they reply, is it too soon, is the deal stale. The AI decides meaning: what an email asks, which topic fits, what to say. The rep reviews topic suggestions before use. Generic topics ("touching base", "checking in", "planning for next year") are not allowed.
- **One paste per exchange.** Every AI exchange returns one table with fixed columns. The app recognizes the exchange from the header row and saves in one step. People and account changes go through a review screen first, with each row tagged (New, Update, Left and so on) and a checkbox.
- **Ask the rep for what only they know** (close dates, who signs, next steps, check-back dates) right on the card where it matters. Those answers feed the next AI run.
- **Persistent, not pushy.** Courtesy rules apply on every list. Do-not-contact is honored everywhere.
- **Short outputs.** Top 3, one draft at a time, and always a clear "Next:" step.
- **Never auto-send.** Even in automated mode, the app drafts and the rep sends.

## 2. Ranking: who to contact next

**Who's eligible:** contacts with status `new`; `done` after the rest period; `paused` or `booked` with no touch in 30 days; `later` after the check-back date (or for a different topic, if the pause was topic-only). Exclude anyone in an active sequence, `replied`, marked do-not-contact, or marked as left.

| Signal | Points |
|---|---|
| Existing account | +3 |
| Renewal between 30 days ago and 180 days out | +4 |
| Never touched | +1 |
| Quiet 60+ days | +2 |
| Talked within 14 days | -3 |
| Has context notes | +1 |
| Has a known buyer type | +1 |
| Referred by someone, not yet contacted | +6 |
| Colleague at the same site is engaged, and this person is untouched | +3 |
| Site already has the max people in sequence | -5 |
| Learned boosts from "What's working" | -2 to +3 |

Show the top `8` with reason chips ("Renewal Mar 3", "Referred by [Contact]", "64 days quiet").

## 3. Sequences

A step that combines two actions ("Call + short email") counts as **one touch**.

| Sequence | Steps (day: channel) |
|---|---|
| Standard cold | 0 Email · 2 Call + voicemail · 4 LinkedIn note · 7 Value email · 11 Call + short email · 17 Last email |
| Short | 0 Email · 3 Call + voicemail · 6 Value email · 10 Last email |
| Long | 0 Email · 2 Call + voicemail · 5 LinkedIn note · 9 Value email · 13 Call · 18 Email with a new idea · 24 Call + short email · 30 Last email |
| Mostly phone (Standard length) | 0 Call + voicemail · 2 Email · 4 Call · 7 Value email · 11 Call + short email · 17 Last email |
| Mostly email | 0 Email · 3 Value email · 7 Call + voicemail · 12 Email with a new idea · 17 Last email |
| No LinkedIn | Replace the LinkedIn step with an email |
| Warm (re-engage) | First step uses the re-engage rule (Q16) and opens by referencing the last conversation. Then the cold steps continue from day 4. |
| Referral | Day 0 "[Referrer] suggested I reach out" email, then the cold steps from day 2 |
| Rebook (no-show or canceled meeting) | 0 Email · 2 Call · 5 Last email |

With "Mostly phone", re-engagement starts with a call unless the last touch was a call within 14 days.

**Timing:** due date = sequence start + the step's day. If a courtesy rule holds a step, the step and all later steps shift by the same number of days. They don't stack up.

**Template placeholders:**
- `{first} {name} {title} {account} {site} {topic} {context} {referrer} {myname} {myphone} {signature}`
- `{contextShort}`: the first sentence of context.
- `{angle}`: the playbook's "cares" line, turned into one sentence.
- `{valueIdea}`: the playbook "value" line.
- `{question}`: the playbook "question".
- `{lastHow}` and `{lastWhen}`: the last contact's channel and date, such as "spoke by phone" and "in March".
- `{focusLine}`: the active focus talking point, or nothing.
- `{time1}` and `{time2}`: the next two business days, written as weekdays.

**Template slots.** The foundation ships with these slots **empty**:
- first email
- call script (opener, why, question, close, voicemail)
- LinkedIn note
- value follow-up
- short call follow-up email
- last email in a sequence
- re-engage email and re-engage call
- referral email
- three rebook messages

In Pass 1, write every slot from scratch from the rep's answers: what they sell (Q3), who they sell to (Q12), their usual ask (Q20b), and their tone and voice sample (Q20). Keep emails under 90 words, with one clear ask.

**Buyer playbooks and angles.** These also ship empty. For each buyer type, write what they care about, a value line, one good question, and what to avoid. Base them on Q3 and Q12, and make them editable.

**Each step card** shows:
- The draft, filled from templates.
- A "Copy AI prompt" button for a tailored draft. The prompt includes the person's context, last contact, topic, referral, focus talking point, the rep's tone and voice sample, and "check my email and chats for past conversations with this person".
- Buttons: Done, Voicemail, No answer, Talked, Booked meeting, Not now, Stop contacting.

## 4. Courtesy rules (enforced on every list)

The foundation ships with all four limits **empty, which means off**. Q17 sets them, and Data & Settings has the same three presets.
- A minimum number of days between any two touches to the same person.
- A maximum number of touches per person in any 30 days.
- A rest period after a sequence ends with no reply.
- A maximum number of people per site in a sequence at the same time.
- Do-not-contact always removes the person from every list until cleared. This one is always on.

A held step shows on Today as "Held: touched yesterday, back on [date]" instead of disappearing.

**Not now:** saves what they said and a check-back date. Quick picks: 30, 60 or 90 days, start of next fiscal year, or after the year-end break. The rep chooses each time whether the pause covers **everything** or **just this topic**; a different topic is allowed after 30 days. On the date, Today shows "Check back today" with an opener that quotes what they said.

## 5. Views and layout

**Sidebar grouped by routine**, with:
- live counts on each item
- outline icons and hover tips
- a collapse button
- light/dark mode that follows the system, with a manual toggle

A search box in the top bar jumps to any account. A goal pill in the top bar shows progress ("23 / 60 meetings, 3 behind pace").

**Pace:** expected so far = goal × business days elapsed ÷ business days in the period. Behind = expected minus actual, never below zero. Per week = remaining ÷ weeks left.

- **Every day:** Today, Hot Follow-ups, Opportunities, Archive
- **Accounts:** Coverage, Contacts, the account page, Focus, AI Feed (named after their AI)
- **Fridays** (rename it to their report day): Weekly report, Meetings, What's working
- **Footer:** Start here, Templates, Data & Settings

**Today**, top to bottom:
1. Banners: missed morning paste, backup not connected, report day.
2. Replied (respond first).
3. Action items.
4. Steps due, including held steps.
5. Meetings to confirm ("Did these happen?").
6. Prep for upcoming meetings (next 3 days).
7. Follow up after meetings.
8. Check back today.
9. Suggested next people.
10. Call blitz: a phone-first list for catching up on the goal.
11. Other buyers at engaged accounts.
12. Account rotation: the 3 most overdue.
13. Goal card.

**Deals:** active deals only. Each shows the next step and date, questions for missing info ("Who signs off?", "Close date?"), and value totals. After `30` quiet days, a deal moves to **Follow-ups** with a revival draft. **Archive** holds won, lost and no-response items, with Restore.

**CRM deal import** (when the AI can't read the CRM): map an export's columns to Ref (CRM id), Name, Account, Stage, Value, Close Date, Next Step and Last Activity. It updates deals matched by Ref and adds new ones. Deals refresh does the same from the AI's table.

**Coverage:** every account as a card (parent, then sites). Each card shows:
- who you know there
- missing core roles; a role can be marked "doesn't exist here"
- Existing or New, and tier
- last touch

Filters: overdue, missing roles, existing/new. Sort by most overdue. Tier comes from a Tier column in the account import, or a toggle on the account page; the default is standard.

**Account page:** structure, people by site, deals, meetings, touches, and the account-mapping exchange.

**Focus:** current campaigns, grouped by area. Types are Event, Offer, Partner/Vendor, Project type and Trend; pick the first type that fits, in that order. The AI suggests a type using that rule, the app shows the rule under the dropdown, and the rep confirms. Each campaign shows touches, people, replies, meetings within 60 days, deals and value. Buying-calendar plays turn themselves on and off by date window. A window may wrap the year end (for example Nov 15 to Feb 15).

**Weekly report** (if the team has one):
- this week's meetings, with "Logged in CRM" checkboxes
- a per-day breakdown, Monday to Sunday
- one summary row for the week: week start, then the counts in the rep's column order, with a "Copy row" button for their spreadsheet
- a calendar reminder file (.ics) for the report day
- "Meetings set" counts by booking date; the goal counts by meeting date

**What's working:** reply and meeting rates by buyer type, existing/new, topic source, sequence type, focus, channel and step.
- A reply counts if it comes within 21 days of a touch.
- Suggested changes appear only after enough samples (8 to 15) and have Apply, Not now and Undo.
- A "coaching prompt" button copies anonymized rates (no names) for the AI.

**Start here:**
- First-time setup checklist: connect backup, set your details, import contacts, import or build the account list, run the history backfill, schedule the morning prompts (or, if the AI can't schedule, a "Copy all morning prompts" button), first check-in.
- Tabs: Every day, Every week, Now and then, How it decides.

**Visual style:**
- Clean cards on a light gray background, with a 14px system font and rounded 8px corners.
- Small colored chips for reasons: green good, amber warning, red overdue. One accent color.
- Colors defined as CSS variables, with a dark set.
- Usable at laptop width; the sidebar collapses to icons under 760px, with no sideways scrolling on a phone.

## 6. AI exchanges, imports and sync

The foundation already has them all. Part D §5 lists each exchange's prompt builder, output columns and paste-router signature. The rules that matter when you change them:
- **One table per exchange.** Every prompt ends with `OUT_RULE`, and the router picks the exchange from the header row. If you add an exchange, add its signature to `previewPaste(` before the catch-all, and make the signature specific.
- **Check-in markers:** "STOP:" in Update means do-not-contact. "NOT NOW: [what they said]" plus Next Touch Date sets a check-back. Meeting Change is "Rescheduled to YYYY-MM-DD", "Canceled" or "No-show". Referral is "Name, Title, email - what it's about".
- **History backfill** works in 2-week chunks. Each row carries a Period code like `H-2026-01-05`. A "MORE" row means split the chunk; a "NONE" row means the window was empty.
- **Topics** follow the rep's priority order, are 2 to 6 words, name their source, and are never generic. If nothing specific is found, the topic is "Needs input".
- **Prompt wording** comes from CONFIG (AI name, email, chat, calendar, meeting notes). If the rep's AI can't read something (Q25), take it out of the prompts and add the manual checklist Part C describes.
- **Imports:** contacts go through column mapping; the account list and customer list set Existing or New. Backup is a JSON download. The sync file sits in a cloud-drive folder synced to the PC, and the newest edit wins.
- **Without SheetJS**, CSV, tab-separated and pasted tables work, and Excel exports save as CSV. To read .xlsx files, replace the `<script>/*SHEETJS*/</script>` placeholder with the pinned cdnjs tag in the comment above it.
- **Raw email and calendar content** is never stored, only one-line summaries.


## 7. Automated modes: adapters

Feed automated results through the same paste router, `previewPaste(`, so semi-automated and automated share the same logic. `previewPaste()` takes no argument; it reads the paste box. Some exchanges (morning check-in, action items, opportunity review, hot follow-ups, history) apply directly with no review screen; for automated input, add a review step in front of those, as the rules below require:

```
semi: prompt builder -> copy -> rep pastes into #pasteBox -> previewPaste() -> route -> apply
auto: prompt builder -> adapter.fetch(id, prompt) -> table text -> put it in #pasteBox -> previewPaste() -> same route
```

For "Start semi, plan for automated", build the adapter and its Settings panel, switched off, with a one-line note on what's needed to turn it on.

Adapters by route (Q31):

**Claude with connectors**
- If the rep's plan supports artifacts that save data and call Claude, publish the app as an artifact.
- Otherwise, Claude runs the exchanges on a schedule with the rep's connectors and saves the result tables as files in the inbox folder below.
- Check what your own tools support before promising either, and say which one you're building.

**Company automation tool** (built into the foundation, switched off: `CONFIG.automation`, Part D §9)
- Exchange ids: `checkin` (Morning check-in), `tasks` (Action items), `opps` (Opportunity review), `hot` (Hot follow-up run). These are the only ones worth scheduling. The recipe and the AI Feed list them.
- The flow recipe, in plain steps:
  - Trigger: weekdays at 7:00.
  - Get the prompt: read `prompts/<id>.md` from the sync folder. The app writes these files (each starts with a `Since:` date) whenever it opens, checks the inbox or applies a file, because the prompts contain data that lives only in the app. The list of people is from the last time the app was opened; that's fine over a weekend, because nobody new starts a sequence while the app is closed.
  - Gather the data: the email and calendar text since the flow's last successful run (or the `Since:` date, if earlier), so Monday's run covers Friday through Sunday and a missed day is covered next time. An AI called through an API can't open the mailbox itself.
  - Run the prompt plus that text in their work AI.
  - Save the answer as a plain text file `<id>_YYYY-MM-DD.md` in an `inbox` subfolder of the sync folder (not a converted online document).
- One folder pick. The sync file handle can't reach other files, so "Connect sync folder" uses `showDirectoryPicker` and, if no sync file is connected yet, creates the sync file in that same folder.
- A web page can't watch a folder in the background. So the app checks the inbox when it opens (only if the browser still allows the folder; after a restart it usually takes one click, "Allow and check inbox") and when the rep presses "Check inbox".
- Every file shows on a review screen, then goes through `previewPaste()`. Processed file names live in `S.auto.processed` (app data, so they sync to a second PC), keyed by file name with `{on, result}`; a partly applied file also keeps its applied row numbers (`partial`), so nothing applies twice.
- Bad files (empty, wrong name, no table, unknown id, wrong columns, still syncing) show on the Today card with a one-line reason and Dismiss. They aren't marked processed until dismissed, so a fixed file with the same name is read again. Files that don't end in .md or .txt are ignored.

**Direct connection**
- Only with IT approval.
- Explain plainly that a key stored in a browser file can be copied by anyone with the file. Recommend a small company-hosted relay instead.
- If they still want it, build the adapter so the key is entered in Settings each session and never saved in the file.

**In every route:**
- Low-risk rows may auto-apply if the rep turns that on: out-of-office dates, action items, update notes, and meetings for people already marked Booked.
- A new booking, a reply, not now, stop (do-not-contact), a meeting change, a referral, a person who left, and any deal row always wait for review.
- Outreach is never sent automatically.
- Keep the semi-automated buttons as a fallback when the automation fails.

# PART C: HOW ANSWERS CHANGE THE APP

Use this table while building. Each answer changes logic, and some change layout.

| Answer | Logic change | Layout change |
|---|---|---|
| Q1 Semi-automated | Copy prompt / paste table for every exchange | "AI Feed" view lists every prompt; paste box on each card |
| Q1 Automated | `CONFIG.automation.on = true` (Part D §9); review screen for incoming rows; `aiSchedules = false` | "Inbox from automation" card at the top of Today; automation panel in Settings; exchange ids on the AI Feed; morning check-in and action-item cards say results arrive in the inbox card, with the copy buttons as fallback |
| Q1 Start semi, plan for automated | Same as Semi; `CONFIG.automation` stays `on:false` with `planned:true` | Settings shows the automation panel as "Not connected yet" with the recipe and IT note |
| Q4 Meetings | Goal pace from meetings that count (Q5 rule) | Goal pill and Today goal card show meetings and pace |
| Q4 Pipeline or revenue | Pace from deal value created or closed | Quota card on Deals and Today; value totals prominent; goal pill shows value |
| Q4 Activity | Pace from touches per day | Daily touch counter replaces the meeting pill |
| Q5 Live conversations count | `settings.talkCounts` = true (ships off): a call marked Talked also counts toward the goal | Talked button and call-blitz text say it counts |
| Q6 No deal value | Skip value fields | Hide value totals and quota card |
| Q7 Fiscal year | Quarter boundaries, pace, the "next fiscal year" check-back pick | Goal pill period label |
| Q8 Stale days | Deal moves to Follow-ups after N quiet days | Badge text on deal cards |
| Q9 Single companies | `CONFIG.singleLevel = true`; keep `CONFIG.parent` and `CONFIG.site` different words; the per-site limit becomes per account | Coverage collapses to one level |
| Q9 Parent with sites | Parent > site tree, central office that buys for others, buyingModel note | Account page grouped by site; central office row |
| Q10 Named list | Accounts come from an import | Setup step "import your account list" |
| Q10 Geography or segment | Account list exchange at setup | Coverage shows all accounts, including untouched ones |
| Q11 Grow existing | Existing +3; whitespace topics ranked high | "Existing" chips; customer-list import in setup |
| Q11 New accounts | New +3 instead in `suggestScore(`; drop whitespace from `topicRules(` and `ctxPrompt(` | Coverage defaults to companies with no one yet (`covF.has = "none"` in `vCoverage(`) |
| Q12 Buyer types | Persona list, title-keyword guessing, playbooks, core roles for gap checks | Coverage gap chips list the core roles |
| Q13 Tiered | Rotation days by tier | Tier toggle on account cards |
| Q13 No rotation | Skip rotation math | Drop the rotation card and the overdue filter |
| Q14 Mostly phone | "Mostly phone" sequence; call-first re-engage rule (§3) | Call blitz moves to the top of Today and stays open |
| Q14 Mostly email | "Mostly email" sequence | Call blitz hidden by default |
| Q14 No LinkedIn | `CONFIG.linkedin = false` (the `li` step becomes a short email; keep the key) | No LinkedIn buttons or counts |
| Q15 Sequence length | Steps and day offsets from §3 | Step labels and counts |
| Q16 Re-engage rule | First warm step channel | Warm step labels |
| Q17 Courtesy | minGap, max30, restDays, perSite in `blank(` (empty = off) | Held-step text; the setup item and Today notice disappear once they are set |
| Q18 Topic order | Topic prompt order and topicWhy sources | What's working "topic source" rows |
| Q19 AI drafts only | No templates; every step card has the AI prompt | Templates page becomes a voice guide page |
| Q19 Templates only | No AI draft button | Hide "Copy AI prompt" on steps |
| Q20 Tone | Tone and voice sample in every draft prompt and template | none |
| Q21 CRM is official | Deals are a working copy; weekly "Logged in CRM" checks | "Working copy, the CRM is the record" note on Deals |
| Q21 App is the main tracker | No CRM: set `CONFIG.crm` to their report sheet name, hide the "Logged in CRM" checks and CRM steps in `vWeekly(` and `vGuide(` | No CRM wording |
| Q21 Skip deals | No deals or follow-ups | Remove Deals, Follow-ups and Archive from the sidebar |
| Q22 Follow-up types | Which deal types appear on Follow-ups | Type filter options |
| Q23 Just log meetings | No outcome tracking or rebook | Drop the "Did these meetings happen?" card |
| Q24/Q25 Platform | Prompt wording names their tools (for example email, calendar, chat and meeting recaps in that suite) | Setup steps name their tools |
| Q25 AI reads some of it | Keep the check-in paste, plus a quick "who replied that the AI might miss" checklist | Small checklist under the check-in card |
| Q25 AI reads none of it | `CONFIG.aiReads = false` (manual "Who replied?" checklist, no scans, backfill or mailbox prompts) | Today shows the checklist instead of a paste card |
| Q25 Can't schedule, or not sure | `CONFIG.aiSchedules = false`; morning prompts run by hand | "Copy all morning prompts" button; setup step says so |
| Q26 CRM not readable by AI | CRM deal import with column mapping | Weekly "import CRM export" step |
| Q27 Saved as files | Prep and follow-up prompts say to read the meeting file the rep attaches | "Attach the notes file" hint on the card |
| Q27 None | Meeting follow-up uses the rep's notes | Follow-up card asks for 3 bullet notes |
| Q28 .xlsx | Load the spreadsheet library from a pinned CDN version | "Open Excel file" button |
| Q29 Sync file | Sync per §6 | Backup banner until connected |
| Q29 Manual backup | No sync | Weekly backup reminder banner |
| Q30 No or don't know | Automation switched off | IT note in Settings |
| Q31 Route | Which adapter (§7) | Automation panel text |
| Q32 Package | Which modules exist | Remove views from `NAV` (Part D); links to removed views hide themselves through `hasView(` |
| Q33 Weekly report | `settings.reportColumns` in the rep's order, each mapped to what it counts from; report day | Weekly report view; report-day banner and .ics |
| Q34 Buying calendar | Date-window plays researched for their segment | Calendar plays section on Focus |
| Q35 Home | Start view | Default view on open |
| Q36 Top tabs | none | Tabs instead of the sidebar |
| Q37 Name, color, logo | none | CONFIG.appName, page title, `--accent` and `--accent-soft` (light and dark), the sidebar logo (`nav .brand img`) and the favicon (`<link rel="icon">`) |

**Things that stay the same in every version:** the one-paste loop with a review screen, courtesy rules, do-not-contact everywhere, not-now check-backs, never auto-sending, local-only data, and short outputs with a clear next step.

---

# PART D: FOUNDATION CODE MAP

One file: `Prospecting-Desk-Foundation.html` (HTML, CSS, one script). Open it in Chrome or Edge. Logo: replace only `<link rel="icon">`; the sidebar logo copies it.

**Storage rule.** Every storage name comes from `CONFIG.appName`: `KEY = "pd." + slug(CONFIG.appName) + ".v1"` (localStorage, all data), `IDB_NAME = "pd." + slug(appName)` (IndexedDB, sync-file handle), `PREF(k)` (small UI prefs such as `navmin`, `focusGroup`). All `file://` pages share one origin, so builds with different app names never collide. Renaming appName starts an empty store (restore a backup to move data).

## D0. Engine only: Claude writes the words

Mechanics only, no one's outreach approach. **Empty on purpose; Claude writes them from the new user's own answers:**
- `DEFAULT_TEMPLATES`: every key kept (`email1 call1 li email2 call2 breakup warmcall warm1 ref1 refcall noshow1-3`), every `subject` and `body` "". `TEMPLATE_HINTS` says what each slot is for (shown on Templates while empty).
- `DEFAULT_ANGLES = {}`, `DEFAULT_PLAYS = {}` (per persona `{cares, value, question, avoid}`), `PLAY_RESEARCH = {}`, `CAL_PLAYS = []` (format in the comment above it).
- `FOCUS_RULES` keep the type rules; examples are short and generic.

Empty states: a step with no template shows `NO_TPL` in `openDraft` and `blitzScript`; Hot Follow-ups without a draft show "No draft yet" (`dealDraftPrompt`). `aiDraftPrompt(c, key, focus)` works with or without a template (context, playbook, topic, `CONFIG.ask`, tone; plus the filled template if any). Helpers: `tplOf(key)`, `tplEmpty(key)`, `askText()`, `toneText()`, `toneLine()`, `stepByKey(c, key)`. `loadSample` adds no template text.

Mechanics that stay: `STEPS` days and channels, courtesy rules, ranking points, the opposite-channel re-engage rule, not-now handling, paste formats. No call-time advice or meeting length is built in.

Search for the **anchor** text; line numbers are approximate.

## D1. CONFIG (anchor `const CONFIG = {`, ~line 154)

| Key | Default | What it changes |
|---|---|---|
| appName | Prospecting Desk | Sidebar brand, page title, backup/sync/ICS file names |
| company | [Your Company] | `{company}` in templates, signature, every AI prompt |
| parent / parents | Account / Accounts | Top level of the territory: nav group, Coverage, account page, column headers (`COL.Parent`) |
| site / sites | Site / Sites | Second level: Coverage rows, contact field label, `{site}` placeholder, table columns (`COL.Site`) |
| centralOffice | Central office | Head-office row added to parents with 2+ sites |
| ai / aiShort | your AI assistant / AI | Prompt wording ("Paste into ...") and short labels ("AI Feed", "Map with AI") |
| mail, chat, calendar, meetingNotes | email, chat, calendar, meeting recaps and transcripts | What prompts tell the AI to search |
| drive | cloud drive | Sync and backup wording |
| crm | CRM | Weekly report, quota card, ICS reminder |
| valueLabel | Value | Pipeline measure on hot follow-ups, opportunities, quota, exports (`COL.Value`, field `.value`) |
| segment / region | [your market] / [your region] | Who you sell to and where, in prompts and `{segment}` |
| fyStartMonth | 1 | Default quarter, buying-calendar windows, "new fiscal year" check-back |
| voiceGuide, accountFile | [my voice guide], [my account export] | Files the AI is told to read |
| currency | USD | Money formatting |
| ask | a short call | What outreach asks for: `{ask}` in templates, every draft prompt, hot run, rewrite prompt |
| tone | "" | Default writing tone for drafts; `settings.tone` (Data & Settings > Writing tone for drafts) overrides it. Empty = "plain, specific and brief" |
| callWindows | "" | Optional call-time advice shown on the call blitz; blank hides it |
| aiReads | true | false: Today check-in becomes a manual "Who replied?" list (`replyCheckCard`); no scan buttons, catch-up, mailbox Feed cards (`reads:true`), history backfill or its SETUP items; prompts drop "check my email" lines |
| aiSchedules | true | false: no "version to schedule" buttons or `sched` item; "Copy all morning prompts" (`copyMorning`) when aiReads |
| singleLevel | false | true (or parent = site): `SINGLE`, one row per company in `acctListPrompt`, no central-office hint or Sites tile. Equal names: `COL.Parent` = "Parent" |
| linkedin | true | false: step `li` (key kept) is Email "Short check-in email"; LinkedIn leaves `WK_SRC`, `otherTouch`, `cLastType` |
| automation | `{on:false, planned:false, route:"tool", tool:"your automation tool", inbox:"inbox", prompts:"prompts", autoLow:false}` | The automation inbox (§9). `on:false`: no automation UI at all, the app works exactly as semi-automated. `planned:true` with `on:false`: only the Settings panel, as "Not connected yet" with recipe and IT note |

Derived wording: `const TX = {` (TX.parent, TX.Site, TX.aParent, TX.sources, TX.mktShort ...), `const COL =` (table header names), `const KS =` (header aliases the paste readers accept). Helpers `cap`, `low`, `art`.

## D2. Territory and account data

- `const TERRITORY = [` empty by default. Format `["Parent", ["Site 1","Site 2"]]`.
- `const TERRITORY_EXTRA = {}` optional central units per parent; `const NAME_ALIAS = {}` nicknames.
- Accounts also come from `S.orgs` (`{parent, sites:[{name, kind, note}], tier, buying}`), filled by the account-list import, the Account list exchange, mapping pastes, and contacts. `function tIdx(` merges TERRITORY, TERRITORY_EXTRA and S.orgs into a name-matching index (reset by `save()` and `render()`).
- Matching: `canonParent(`, `canonSite(`, `canon(`, `parentOf(`, `multiSite(`, `contactParent(`.
- Site kinds: `const KIND_CENTRAL`, `KIND_SITE`, `KIND_UNIT`, `function siteKind(`, `function kindFrom(`; roles shown per kind: `SHARED_ROLES`, `CENTRAL_ROLES`.
- `const CORE_ROLES` (right after `PERSONAS`; default PERSONAS minus "Other"): the roles Coverage, account pages, `gapDlg`, `gapList` (Find missing buyers), `mapPrompt` step 3 and the "Other buyers at engaged accounts" card (`spreadCard`) count as gaps. It replaces the old `KEY_ROLES`.
- Tree for Coverage: `function accountTree(` returns `{parent, sites, org}` per parent.

## D3. Main constants

| What | Anchor |
|---|---|
| Buyer types (personas) | `const PERSONAS =` and `const NON_TECH =` |
| Persona guess from title | `function guessPersona(` |
| Sequence steps | `const STEPS =` (6 steps, day offsets), `const NS_STEPS =` (no-show rebook), `const LEAD_STEPS =` (warm/referral first-step keys per channel), `function leadSteps(kind, first)`, `function stepsFor(` |
| Call-first sequences | The first step can be Email or Call. Cold and referral start with `c.firstType` (set by `beginSeq` to `STEPS[0].type`); warm uses the opposite channel (`firstTypeFor`). Referral + Call uses `refcall`, then `ref1`; cold + Call swaps `call1`/`email1` |
| Email/call templates | `const DEFAULT_TEMPLATES =` (empty, see section 0) filled by `function fill(`. Placeholders: `{first} {name} {title} {site} {parent} {company} {segment} {topic} {ask} {context} {contextShort} {angle} {valueIdea} {focus} {focusLine} {question} {time1} {time2} {myname} {myphone} {signature} {referrer} {colleague} {lastHow} {lastWhen}`. Templates page: `tplSlots()`, `vTemplates`, `saveTemplates` |
| Persona angles | `const DEFAULT_ANGLES =` (empty) |
| Buyer playbooks | `const DEFAULT_PLAYS =` (empty), used by `function play(`, `playGuide(` (leaves out empty fields), `PLAY_RESEARCH` |
| Focus types | `const FOCUS_TYPES =` (Trend, Project type, Partner/Vendor, Offer, Event), rules `const FOCUS_RULES =`, `FOCUS_ORDER` |
| Solution areas | `const SOL_AREAS =` (Core product, Add-ons, Services) |
| Buying-calendar plays | `const CAL_PLAYS = []` (`from`/`to` are [fiscal month, day]); `addCalendar` seeds them as Focus items, `calSync`/`inWin` toggle them by date, `function fyMD(` converts using fyStartMonth |
| Import column guesses | `const FIELD_GUESS =`, `const FIELD_LABELS =` |
| Opportunity stages | `const OPP_STAGES =` |
| Hot follow-up columns | `const HOT_COLS =` |
| Settings defaults | `function blank(`: personal settings start blank (`goal`, `dailyTouches`, `myname`, `myphone`, `topic`, `tone`, `deadDays`, `startDate`, `reportColumns:[]`, and courtesy `minGap`, `max30`, `restDays`, `perSite` = `""`: empty or 0 is OFF, no fallback); signature is a [Your Name] placeholder. Rotation 30/90. Blank goal/target show "Set your goal" links; blank `deadDays` turns off the gone-dead rule; blank `startDate` makes history backfill ask for a date |
| Talked = meeting | `settings.talkCounts`, unset (`""`) = off; checkbox `#sTalk` under the goal. `talkOn`, `talkOk`, `mtgGoal` (goal math, Meetings, weekly counts, What's working, Focus). Off: `saveTalked` logs the touch and contact update only, and text makes no meeting claim; on: also a "Phone conversation" meeting. `loadSample` turns it on only if unset |
| Weekly report columns | `settings.reportColumns`: `{name, from, vm, hot}`, `from` in `WK_SRC` (calls, emails, linkedin, set, held, first, manual), empty by default; rules per column, none fixed: `vm` (calls: voicemails/no-answers, default off), `hot` (touch columns: hot/opp touches, default on); set/first by booking date, held by meeting date. `wkRule` note, `wkDesc` `wkPrompt` rule; First time? only with a `first` column. `wkCols`, `wkColsEditor`, `weekData`; fixes in `S.weeklyAdj` |
| Sample data | `function loadSample(` / `loadSampleGo` (fictional accounts; no template text). Jordan booked (meeting in 3 days), Morgan met today, colleagues ready (Prep, Follow up, Other buyers). Demo-only settings when empty: goal 40, daily touches 20, three report columns |
| Day-one checklist | `const SETUP =` (first item "Set your goal and basics"; includes "Set your courtesy rules" (done when any is set) and "Write your email and call templates") |
| In-app dialogs | No native `confirm/alert/prompt` (blocked in sandboxed previews). `askConfirm(msg, okLabel)`, `askAlert(msg)`, `askPrompt(msg, def)` return promises and use their own `<dialog id="ask">`, stacked over `#dlg`. `beginSeq` warns with Start anyway / Get topic (`askDlg` `extra`, opens `ctxPrompt`) / Cancel |

## D4. Views

`function render(` builds the nav and calls one view function from the `fn` map. `function go(view)` switches.

| Key | Nav label | Render function |
|---|---|---|
| today | Today | `vToday` (welcome screen when empty) |
| hot | Hot Follow-ups | `vHot` |
| opps | Opportunities | `vOpps` |
| archive | Archive | `vArchive` |
| coverage | Coverage | `vCoverage` (cards from `covCard`, rotation from `rotation`) |
| contacts | Contacts | `vContacts` |
| account | (current account name) | `vAccount`; open with `openAccount(name)`, header search `findAccount` |
| focus | Focus | `vFocus` |
| feed | AI Feed | `vFeed` |
| weekly | Weekly report | `vWeekly` |
| meetings | Meetings | `vMeetings` |
| learn | What's working | `vLearn` |
| guide | Start here | `vGuide` |
| templates | Templates | `vTemplates` |
| data | Data & Settings | `vData0` (`vData` is only a wrapper that returns `vData0()`; edit `vData0`. Settings saved by `saveSettings`) |

**Add a view:** write `vMyView()`, then add the key to `NAV` (or `NAV_FOOT`), `NAV_TIPS`, `ICONS`, `VIEWS` and the `fn` map in `render(`. Remove from the same five places, or just from NAV: links to optional views check `hasView(key)` (in NAV or NAV_FOOT), and `go()`/`render()` fall back to Today. Badges: `navCounts(`.

## D5. AI exchanges

Every table prompt ends with `OUT_RULE` (Markdown table, exact header). `pasteDlg()` opens the box; `previewPaste()` takes **no argument**, reads `#pasteBox`, and routes by header (lower-cased) in this order. Morning check-in, action items, opportunity review, hot follow-ups and history apply **directly on paste, with no review screen**; topics, weekly check, account list, mapping and CRM import show a review first; people/signals/themes show a preview with "Add to my list".

| # | Router signature (headers) | Goes to |
|---|---|---|
| 1 | `activity log` | `applyOpps` |
| 1b | `stage` + `close date`, no `draft body` | `crmMap` -> `crmReview` -> `crmApply` (CRM deal import) |
| 2 | `ref` + (`draft body` or `next step` or `expires/renews`) | `applyHot` |
| 3 | `replied` or `meeting booked` | `applySync` |
| 4 | `suggested topic` | `reviewTopics` -> `applyTopics` |
| 5 | `action item` | `applyTasks` |
| 6 | `item` + `count` | `reviewWeekCheck` -> `applyWeekCheck` |
| 7 | `interaction` | `applyHistory` |
| 8 | `tier`, no `name`, no `status` | `reviewAccounts` -> `applyAccounts` |
| 9 | site column + (`status` or site type) | `reviewMap` -> `applyMap` |
| 10 | `theme` | `applyPaste` -> `applyFocusRows` |
| 11 | `signal` without `name` | `applyPaste` (signals) |
| 12 | anything else | `applyPaste` (people) |

| Exchange | Prompt builder | Output columns |
|---|---|---|
| Morning check-in | `syncPrompt` (copy: `copySync`) / `syncSchedPrompt` (copy: `copySyncSched`) | `SYNC_HDR()`: Name, Site, Replied, Meeting Booked, Meeting Date, Out Of Office Until, Update, Next Touch, Next Touch Date, Meeting Change, Referral |
| Action items | `taskScanPrompt` (copy: `copyTaskScan`) / `taskSchedPrompt` (copy: `copyTaskScanSched`) | `TASK_HDR()`: Action Item, Source, From, Site, Due, Priority, Detail |
| Topics for sequences | `copyTopics` | Name, Site, Suggested Topic, Why, Opener |
| Hot follow-up run | `hotRunPrompt(since)` (copy: `copyHotRun`) | `HOT_COLS` minus Owner/Notes, plus Open Questions |
| Opportunity review | `oppRunPrompt` (copy: `copyOppRun`) | Ref, Site, Opportunity, Stage, Amount, Value, Close Date, Contacts, Decision Maker, Activity Log, Next Step, Next Step Owner, Next Step Date, Open Questions |
| Weekly count check | `wkPrompt` (items = `settings.reportColumns` names, plus Meetings held) | Item, Count, Details |
| History backfill | `histPrompt` | Period, Date, Interaction, Name, Title, Email, Phone, Site, Summary, Booked On |
| Account list | `acctListPrompt` (also AI Feed card `accounts`) | Parent, Site, Site Type, Tier |
| Map an account | `mapPrompt` (Coverage "Map with AI") | Name, Title, Site, Site Type, Account, Email, Phone, Role, Status, Source |
| Feed: Find everyone / Who went quiet | `FEEDS` keys `mine`, `quiet` | `PEOPLE_HDR()`: Name, Title, Site, Email, Phone, Last Contact Date, Last Contact Type, Context |
| Feed: Renewals | `renew` | Name, Title, Site, Email, Renewal Date, Context |
| Feed: Missing buyers | `roles` | Name, Title, Site, Email, Phone, Context |
| Feed: Trends | `trends` | Theme, Type, Solution Area, Talking Point, Personas |
| Feed: Buying signals | `signals` | Site, Date, Signal, Source |

The `...Prompt` builders return the text; the `copy...` functions only copy it (the automation writer in §9 uses the builders). Automation ids for these four: `checkin`, `tasks`, `opps`, `hot` (§9).

Text-only prompts (no table): `ctxPrompt` (TOPIC/OPENER -> `saveCtx`), `aiDraftPrompt` (draft any sequence step), `dealDraftPrompt` (hot follow-up draft), `prepPrompt` / `copyPrep` (meeting prep), `followPrompt` / `copyFollow` (meeting follow-up), `taskDraft`, `blitzScript`, `focusOutreach`, `copyHotSummary`, `gapDlg` (one missing role).

Headers use `COL.Site` / `COL.Parent` / `COL.Value`; readers accept `KS` aliases, so old pastes still work after renaming.

Non-AI imports: contacts `pickFile` -> `#fileIn` -> `showMapping` -> `doImport`; account list `pickAccounts` -> `#acctIn` -> `reviewAccounts`; spend list `pickSpend` -> `spendReview` -> `spendSave` (sets Existing vs New by parent); hot follow-ups `importHot`; backup restore `#restoreIn`.

CRM deal import (Opportunities > "Import CRM export"): `crmImportDlg` (file via `crmPickFile`, or paste -> `crmFromPaste`) -> `crmMap` (guesses from `CRM_FIELDS`) -> `crmReview` (New / Update / No change / Skip closed) -> `crmApply`. Matches opps by Ref, then name + site. `crmStage` maps Closed Won/Lost to status; other stages are kept as written.

## D6. Scoring, courtesy, sequences

- Courtesy limits: `CR(` (empty = 0 = off), `courtesyHold(`, `resting(`, `activeAt(` (in sequence at one site). `crText(` states them or "Not set…"; `crBanner(` Today notice; `CR_PRESETS` (Gentle 4/5/90/1, Balanced 3/7/45/2, High volume 1/10/30/3) fill inputs via `crPreset(`; `loadSample` sets Balanced only if all empty.
- Suggestions: `function suggestScore(` (existing account, renewal window, quiet days, context, persona, referral, colleague engaged, learned weights `S.learn`).
- Sequence: `function startSeq(` / `beginSeq(` / `newTopicSeq(`, `function nextStep(`, `function doneStep(`, `stopSeq`, `resumeSeq`; Focus pick `function pickFocus(`.
- Rotation (accounts going cold): `function rotation(` and `rotationCard`; tier goals 30 days top, 90 standard.
- Learning: `function vLearn(`, `bucket(`, `setLearn(`.
- History: `c.notes[]` ({date, text, source}). Every writer of `context`/`update`/`lastNote`/`referralNote` uses `setText(c, field, value, source, logNew)`: old value kept first, blanks and date+text duplicates skipped. Also `noteAdd`, `cbArchive` (old not-now), `seqLog`. Touch `note` = step label + typed text (`joinNote`).
- Timeline: `timelineRows(contacts, extraMeetings)` + `timelineHtml(rows, showWho)` (15 rows, Show all) on `editContact` and `vAccount` (filter `_acctWho`); `historyLines(c, 5)` feeds `prepPrompt` and `aiDraftPrompt`. `mergeIn` unions `notes` (`mergeNotes`).
- History dialog: `histDlg(id, key)` shows phone/email (copy), facts (status + next step, topic, context, update, last touch, check back, referral, renewal, do not contact), the timeline and "Add a note" (`histNote`); Edit contact, Done, and Open draft when `key` is the current step. Names that open it: `cn(c, key)` (bold, `.cn`), `mn(m)` (meeting contact), `cnA(c)` (inline link). On every Today card (step rows pass the step key), Contacts table, account People.
- Guide: `vGuide` steps are lists (`gSteps`, null = hidden). `guideDecides` reads `crText`, `talkOn`, `topicSources` (topic order, shared with `topicRules`), `rotSet`, `STEPS` and the flags: update when logic changes.

## D7. SheetJS (optional)

Placeholder `<script>/*SHEETJS*/</script>` (cdnjs URL in the comment above it). Excel goes through `hasXLSX(`, `readBook(` (CSV/TSV fallback via `parseDelimited`) and `saveSheet(` (CSV fallback). Without it, .xlsx can't be read; CSV, TSV and pasted tables work.

## D8. Leftover identifiers (internal only, not visible)

- `S.deals` = Hot follow-ups; `S.opps` = Opportunities; `S.orgs` = accounts; `S.campaigns` = solution areas; `S.tomb` = deleted-item tombstones for sync.
- `tIdx()` keys: `d` parent, `c` site, `n` normalized, `a` acronym. `.acct` = a Coverage card; `L.acct` = Existing vs New bucket.
- Prefixes: `hot*` Hot Follow-ups, `wk*` Weekly, `sh*` sync, `cal*` buying calendar, `camp*` solution areas, `crm*` CRM import; `naGet`/`naSet` n/a roles.
- Template keys (section 0) are stored in user data; renaming them breaks saved templates. `breakup` is only a key; its step label is "Last email".
- Meetings logged from check-ins and opportunities use type "Intro call".

## D9. Automation inbox (`CONFIG.automation`, anchor `// ---------- Automation inbox`)

Route "your company's automation tool" (Part B §7). Ships **off**: with `on:false` every function below returns early or renders nothing. Pass 5 sets `on:true` and `tool` (the rep's tool name), and writes the recipe wording for their tool.

- **Exchange ids** (`const AUTO_X`): `checkin` Morning check-in (`syncPrompt`, else `syncSchedPrompt`), `tasks` Action items (`taskScanPrompt`), `opps` Opportunity review (`oppRunPrompt`), `hot` Hot follow-up run (`hotRunPrompt`). `opps` and `hot` drop out when their view isn't in NAV. Each entry has `is(h)` (the header check) and `prompt()`.
- **Files:** the flow saves `inbox/<id>_YYYY-MM-DD.md` (`AUTO_NAME`; .txt also accepted) in the sync folder. The app writes `prompts/<id>.md`: a `Since: YYYY-MM-DD` line, a `Written by <app>: <date>` line, a "look at everything since …" line, then the prompt (`autoWritePrompts`, on open, Check inbox, Apply and Skip). `autoSince(id)` = newest processed file date for that id, or the last manual paste (`S.lastSync`, `S.lastTaskSync`), else 3 days back, so Monday covers the weekend and a missed day is caught next time. The people list is from the last time the app was opened, which is fine over a weekend.
- **Folder:** `autoConnect` (`showDirectoryPicker`, handle in IndexedDB key `autoDir`). One pick: when no sync file is connected yet, it creates or opens `<App-Name>-Shared.json` in that folder as the sync file (`syncFileName`); if a sync file is already elsewhere, it says so. `autoInit` (after `shInit`) restores the handle and reads the inbox if the browser still grants access; otherwise Today shows "Allow and check inbox" (one click, which also reconnects the sync file).
- **Reading:** `autoCheck(manual)` lists `inbox/`, skips processed names, hidden files and non-.md/.txt files, and turns bad files into `AF.problems` (bad name, unknown id, unreadable, empty, no table, wrong columns) shown on the Today card with Dismiss (`autoDismiss`). A bad file isn't marked processed until dismissed, so a fixed file with the same name is read again.
- **Review and apply:** `autoRisk(id, row)` tags each row. Low risk (may auto-apply when `S.auto.lowAuto`): out-of-office, update notes, action items, meetings for people already Booked. Always review: Do not contact, Not now, Replied, new booking, meeting change, referral, left, every deal row (New deal / Deal update). `autoReview` (dialog, checkboxes `#aq<file>_<row>`), `autoApply`, `autoSkip`, `autoApplyLow`. Every applied file goes through `autoFeed(rows)` -> `#pasteBox` -> `previewPaste()`, one call per file.
- **Memory:** `S.auto = {lowAuto, processed:{"<file name>": {on, result, partial?:[row numbers]}}, last, promptsAt}` (`autoSt()`), in app data so it syncs; `partial` keeps auto-applied rows from applying twice. `autoForget(name)` ("Read again"), `autoPrune` keeps 400.
- **UI:** `autoCard()` (top of Today and the empty welcome screen), `autoPanel()` (Data & Settings: status, Connect sync folder, Check inbox, Save prompts now, low-risk switch, recipe, IT note, processed list), Feed card "Automation exchange ids", `autoRecipe()` dialog, `autoRecipeHtml()` (Trigger, Get the prompt, Gather the data since the last run, Run, Save as plain text, Repeat), `autoItNote()`, SETUP item `auto`, a `guideDecides` row, one line on the check-in card. All hidden when off.
