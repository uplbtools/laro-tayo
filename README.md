# Laro Tayo

**Party games you play on your phone: made for Filipinos.**

Jackbox-style nights, pero Pinoy: one screen (TV, laptop, or projector) plus everyone's phones. Join with a room code, pick a game, laugh until 2 AM.

> Status: **early planning**: see [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md) for the tentative roadmap.

## Why this exists

Most party-game apps assume Western pop culture, English-only prompts, and a paid Steam box. Filipino hangouts need:

- **Taglish-friendly** prompts and UI (English, Filipino, or both: player choice)
- **Shared cultural context**: teleserye, UAAP, jeeps, sari-sari stores, "charot", family group chats
- **Low friction**: no install, works on mid-range phones and spotty Wi‑Fi
- **Free to host**: barkada shouldn't need a credit card to start

## How a session works

```text
Host (TV/laptop) Players (phones)
──────────────── ────────────────
Creates room ──► Enter code at laro.example/join
Picks game pack Pick nickname + avatar color
Shows prompts/timer Submit answers / draw / vote
Reveals scores Feel validated or roasted
```

## Game ideas (MVP candidates)

| Game | Vibe | Phone role |
| ---- | ---- | ----------- |
| **Sino Yan?** | Pinoy charades categories (celebs, ulam, jeepney signs) | Guess + buzzer |
| **Charot o Totoo** | Bluffing: fill in a missing line from a famous quote/meme | Submit fake answer, vote for the real one |
| **Hiya o Tapang** | Mild dares vs safe choices: barkada edition, not NSFW | Tap choice, group sees aggregate |
| **Panty at Pangalan** | Name-that-thing with Filipino homonyms and boomer humor | Type answer, fuzzy match scoring |
| **Barangay Buzz** | Fast trivia: UAAP, Pinoy history, street food, showbiz | Multiple choice under time pressure |

Order and scope are **not final**: the plan doc ranks what to prototype first.

## Repo layout (planned)

```text
laro-tayo/
├── apps/
│ ├── host/ # big-screen session UI
│ └── player/ # mobile-first join + play (may merge into one app)
├── packages/
│ ├── game-core/ # shared types, scoring, round state machine
│ ├── realtime/ # room sync (WebSocket)
│ └── prompts/ # localized prompt packs (JSON)
└── docs/
 └── IMPLEMENTATION_PLAN.md
```

Monorepo tooling TBD (likely **Bun workspaces** to match other UPLB Tools projects).

## Contributing

Too early for code contributions: feedback on game ideas and Filipino localization norms welcome via issues.

## License

MIT: see [LICENSE](LICENSE).
