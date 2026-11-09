# Design · MindPay (Team 13)

Design diagrams for every Must FR (FR-1 to FR-6). Each diagram has a Mermaid source (`.mmd`, re-render at mermaid.live after editing) and a `.png`. All diagrams are also combined in `MindPay-design-diagrams.pdf`.

| File | Shows | FR |
|---|---|---|
| [01-use-case](01-use-case.png) | The user, UC-1 to UC-6, and external systems | All Must FRs |
| [02-architecture](02-architecture.png) | React Native app → Supabase (Auth, PostgreSQL + RLS, Edge Functions) → Gemini | All FRs |
| [03-er-diagram](03-er-diagram.png) | Tables profiles, transactions, savings_goals, ai_usage | FR-1, FR-4, FR-6 |
| [04-screen-flow](04-screen-flow.png) | Screen order and tabs | All FRs |
| [05-seq-fr1-fr2](05-seq-fr1-fr2.png) | Save a transaction → Home recalculates totals | FR-1, FR-2 |
| [06-seq-fr3-voice](06-seq-fr3-voice.png) | Speech → parsed entries → confirm → save | FR-3 |
| [07-seq-fr4-slip](07-seq-fr4-slip.png) | Find slips → read twice → ≥ 0.80 counted / lower becomes a draft | FR-4 |
| [08-seq-fr5-coach](08-seq-fr5-coach.png) | AI coach, with a rule-based summary when AI is unavailable | FR-5 |
| [09-flow-fr6-runway](09-flow-fr6-runway.png) | Money Runway formula and the zero-average case | FR-6 |
