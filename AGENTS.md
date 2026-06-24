# AGENTS.md — Artikle (Framer Project)

This file gives AI agents (Claude Code, Cursor, Codex, Antigravity CLI, or any other tool connecting via Framer's External Agents) the context and guardrails needed to work safely on this project.

This is different from `README.md`, which documents the template for humans. This file is read by agents before they take action on the project.

---

## What this project is

Artikle is a membership template for online publications, built in Framer. It includes article feeds, category/subcategory browsing, author profiles, and a full authentication + content-gating system powered by **FrameAuth V2**.

Live preview: https://artikle.framer.website/

---

## Critical: do not break authentication

The membership and gating functionality depends on a single code override:

```
FramerAuthV2.tsx
```

**Never delete, rename, or rewrite this file.** Components that depend on it — `Unlock Content`, `Members Only`, `Already Member`, `Subscribe Button`, `Subscribe Now`, `Pricing Card`, `Subscription Feature`, `Powered by FramerAuth`, and the My Account / Bookmarks pages — will silently stop working if this override is modified, detached, or removed.

If a task requires touching auth-related components:
- Prefer styling-only changes (color, spacing, typography) over structural changes.
- Do not detach (`?detached=true`) any component instance that wraps FrameAuth logic.
- Do not edit `FramerAuthV2.tsx` directly. If a task seems to require it, stop and ask the user first.

---

## Safe to edit freely

- CMS content in the **Articles**, **Categories**, **Subcategories**, and **Authors** collections (currently seeded with 224 / 5 / 32 / 15 placeholder items respectively).
- **Legal** collection content (Terms, Privacy Policy, Cookie Policy — 7 items).
- Visual/non-auth components: `Logo`, `Nav`, `Menu`, `Search`, `Article Card`, `Articles`, `Subcategory`, `Profile`, `My Profile`, `Commercial Banner`, `divider`, `Copyright`, `Social Media Link`, `Cookie Banner Link`, `Button`, `Link`, `Span`.
- Color Styles and Text Styles — the project uses a defined palette (`Light 98` → `Dark 2`, with Blue/Green/Orange accents) and type system (Playfair Display for headings, Inter for body/UI). Rebranding should update these styles rather than overriding inline styles on individual nodes.
- Page layout and copy on any non-auth page.

---

## Pages

| Path | Notes |
|---|---|
| `/` | Home — hero, latest articles, recommendations, category sections |
| `/articles`, `/articles/:slug` | Article index + detail. Detail page has free/gated states |
| `/categories`, `/categories/:slug` | Category index + filtered feed |
| `/subcategories`, `/subcategories/:slug` | Subcategory index + filtered feed |
| `/authors`, `/authors/:slug` | Author directory + profile |
| `/subscribe` | Pricing — **auth-critical** |
| `/sign-in`, `/sign-up`, `/sign-in-with-otp`, `/otp`, `/forgot-password`, `/reset-password` | **Auth-critical** |
| `/my-account`, `/bookmarks` | **Auth-critical**, member-only |
| `/success` | Post-payment confirmation — **auth-critical** |
| `/legal`, `/legal/:slug` | Legal index + detail |
| `/404` | Not found |

---

## Working with CMS content

When adding or bulk-importing content (e.g. turning a CSV/markdown folder into articles):

- Match existing collection fields exactly — don't introduce new fields without checking how `Article Card` and `Articles` reference them.
- Categories and Subcategories are relational — an Article should reference an existing Category/Subcategory item, not a freeform string.
- Author references on articles should point to existing Author collection items.
- Preserve the free vs. members-only flag per article; don't default new articles to one state without being told which.

---

## Branching

Per Framer's branching model, any agent-driven change happens on a branch automatically. Default to:
1. Making changes on the branch.
2. Summarizing what changed.
3. Letting the user review and merge — do not assume merge-to-main approval.

For sweeping changes (site-wide copy rewrites, recoloring, restructuring multiple pages), batch them into a single branch with a clear summary rather than many small unreviewed branches.

---

## Things this template depends on externally

- A **[FrameAuth](https://frameauth.com/pricing)** subscription must be active and connected for sign-up, sign-in, gating, and subscriptions to function. This is outside Framer/the agent's control — if auth-related testing fails, check the FrameAuth connection before assuming the template is broken.

---

## Out of scope for agents

Per Framer's external agent limitations, agents cannot move/delete pages, change project settings, assign overrides, or access analytics. Don't attempt these — flag them back to the user instead.
