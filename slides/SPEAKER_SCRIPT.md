# MindPay · M3 Demo Speaker Script (Team 13)

**Slot:** 12 minutes (14:29–14:41) · about 6 minutes of slides + 5 minutes of live demo + 1 minute for questions
**Order:** Slides 1–8 → Slide 9 live demo → Slides 10–11

**Team (from the M1 Charter):** 6931503089 Aoengthai Saesae · 6931503077 Sithikan Potiyun · 6931503072 Witchayapong Lamchaona · 6931503069 Vorachon Srijariyakorn · 6931503055 Patcharapornchai Khapai. Write each person's name next to the speaker number that matches the part they built.

| Speaker | Owns | Speaks on |
|---|---|---|
| Speaker 1 | FR-1 Transactions · FR-2 Overview | Slides 1, 2, 3 + demo steps 1–2 |
| Speaker 2 | FR-3 Voice · accounts · design system | Slides 4, 5 + demo step 3 |
| Speaker 3 | FR-4 Slip scan · browser tests | Slides 6, 7 + demo step 4 |
| Speaker 4 | FR-5 AI Coach | Demo step 5 + slide 10 |
| Speaker 5 | FR-6 Money Runway · app setup, CI | Slide 8 + demo step 6 + slide 11 |

---

### Slide 1 · Title (Speaker 1, ~20 s)
"Good afternoon. We are Team 13, Socrates and Skeletons, and this is MindPay, a money assistant that tells you how many days your money will last. Each of us built one part, so you'll hear from all five of us."

### Slide 2 · Problem (Speaker 1, ~40 s)
"Our users are students and first jobbers who pay by mobile banking many times a week. They mean to track spending, but logging means retyping every detail and hunting for slips, so they put it off. The result: incomplete records, and they only see their balance, not how fast it's going. Our idea is to log with almost no typing, and to warn them before the balance gets too low."

### Slide 3 · What each FR does (Speaker 1, ~60 s)
"This release covers six requirements, and all six are built. FR-1 lets users add, edit, categorize and delete transactions, with undo. FR-2 is the Home dashboard: balance, income, expenses and spending by category over any period. FR-3 lets users speak a transaction, like 'rice 50 baht', and confirm it before saving. FR-4 finds payment slips in the gallery and reads them automatically; anything the AI isn't sure about waits as a draft. FR-5 is Nong Kla, our AI coach, who explains spending using confirmed numbers only. And FR-6, Money Runway, predicts the day the balance gets too low. You'll see all six working today."

### Slide 4 · Architecture and APIs (Speaker 2, ~45 s)
"MindPay is one React Native codebase that runs on Android and on the web. Data lives in Supabase: email sign-in, and a PostgreSQL database where row-level security means each user can only see their own rows. Two Edge Functions, parse-slip and coach, call the Google Gemini API. The AI key stays on the server and never ships in the app. Money is stored as whole satang, so totals never drift."

### Slide 5 · Design diagrams (Speaker 2, ~30 s)
"Every Must FR has a design diagram in docs/design: a use case diagram, the architecture, this ER diagram taken from our database migrations, the screen flow, and a sequence or flow diagram for each FR. The transactions table, for example, carries the slip reference and image hash we use to block duplicate slips."

### Slide 6 · Golden Thread (Speaker 3, ~50 s)
"This is our Golden Thread, and it's complete for every requirement in this release. Each row starts from a user problem, goes to the requirement, then the design diagram, then the screen you can open in the app, and ends at the tests that prove it. For FR-4, the problem is searching for and retyping slips, the design is the slip sequence diagram, the page is the Scan screen, and it's covered by unit tests, browser tests and manual tests. The full table is in our Final Report."

### Slide 7 · Where each FR lives (Speaker 3, ~20 s)
"This is the screen flow. After sign-in you land on Home, which is FR-2. Transactions, Runway and Coach are tabs, and Voice, Scan and the Add screen open from Home. You'll see every one of them live in a minute."

### Slide 8 · Money Runway (Speaker 5, ~45 s)
"FR-6 is the heart of MindPay. We take confirmed expenses from the last seven days and get a daily average. Runway is your balance minus your low-balance line, divided by that average, which gives the date your money may run low. If the average is zero, we show 'No depletion date from current data' instead of dividing by zero. Unit tests TC-12 to TC-18 cover each of these cases."

### Slide 9 · Live demo (~5 min, one person drives the phone or laptop; each owner narrates their step)
1. **Speaker 1:** "I'm signed in. Home shows my balance, income, expenses and spending by category." Add ฿85 Food → "The balance and categories update at once." Edit it, delete it, tap Undo → "Delete asks first, and Undo brings it back."
2. **Speaker 2:** Tap the gold mic, say "rice 50 baht, water 15" → "It heard two items. I can fix anything before saving." Save → "Both are in, and the balance dropped by 65."
3. **Speaker 3:** Tap Scan slips, pick the prepared slip → "The app finds the QR on the phone, then the AI reads the amount, date and bank. Every field is checked against an 80% confidence threshold; anything less becomes a draft for the user to check." *(If it's slow: "The AI reads every slip twice with two different models, so it can take a little while.")*
4. **Speaker 4:** Open Coach, ask "Can I spend 500 baht today?" → "Nong Kla answers from confirmed numbers only, and the answer is marked as AI guidance. If the AI is down, the user still gets a rule-based summary."
5. **Speaker 5:** Open Runway → "Here's the date my money may hit the low-balance line. If I drag this slider to cut spending, the runway grows."

### Slide 10 · Worth knowing (Speaker 4, ~30 s)
"On security: each user sees only their own data, the AI key never leaves the server, and the coach only receives totals, not individual transactions. Users changed two things along the way, which we'll update in the SRS: one coach persona instead of three tones, and clear slips counted automatically. Our main limitation is that some slips take up to about 50 seconds to read. Every use of AI is logged in our AI usage log."

### Slide 11 · Thank you (Speaker 5, ~15 s)
"You can try MindPay right now on the web or as an Android app, using the links on screen. Thank you, and we're happy to take questions."

---

**Before 14:29:** sign in on the demo device, open the web app in Chrome with microphone access allowed, and have one slip image ready that has not been scanned before (a slip that's already been saved shows as a duplicate).
