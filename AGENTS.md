# Laro Tayo Agent Guide

**Human developers:** start with [README.md](README.md) and [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md).

Org-wide agent defaults: see [room-tba/AGENTS.md](https://github.com/uplbtools/room-tba/blob/main/AGENTS.md). This file tailors that playbook to **laro-tayo** (planning phase).

## Status

**Planning repo: no `apps/*` packages yet.** Jackbox-style party games with **Taglish-ready** copy. Read the implementation plan before scaffolding realtime code.

## Doc map

| When | Read |
| --- | --- |
| Game modes, architecture options | [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md) |

## Planned stack (target: not all implemented)

- **Monorepo:** npm workspaces
- **UI:** Svelte 5: separate **host** (TV/laptop) and **player** (phone) surfaces
- **Realtime:** Cloudflare **Durable Objects** (preferred) or PartyKit: WebSocket room state
- **Deploy:** Vercel (static/SSR UI) + Cloudflare Workers (game rooms)
- **Join flow:** No-install PWA / QR code into room code

Borrow **Room TBA** UX rules: calm UI, no decorative animations, 320px-first player phone layout.

## Branches and deploy

- **Default branch:** `main`
- Adopt **`staging` → `main`** before public playtests

## Realtime rules (when implemented)

- **One room code = one authoritative DO/PartyKit room**: no split-brain host state
- Reconnecting players restore nickname + score from server state
- Host disconnect should prompt transfer or graceful end: never silent stale lobby
- Latency target: playable on typical PH mobile LTE; minimize chatty round-trips

## Verify before done (when code exists)

| Step | When |
| --- | --- |
| Unit tests | Game logic pure functions |
| Integration | Two-browser Playwright or manual host + 2 phone emulators |
| 320px player UI | Primary viewport for phone join flow |

## How to work

- **Bias toward action** on vertical slices (one mini-game end-to-end) rather than broad scaffolding
- **Do not defer** websocket protocol docs: update plan when message shapes change
- **`gh` by default** for issues and PRs

## Commits

- Conventional Commits: `feat(game): …`, `fix(realtime): …`, `docs: …`

## Security

- Room codes are unlisted secrets: no public room enumeration API
- Sanitize player display names before broadcast to other clients
