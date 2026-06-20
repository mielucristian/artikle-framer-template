# Artikle — Membership Template for Framer

Artikle is a premium Framer template for online publications. It combines a clean, editorial design with full membership functionality — gated articles, subscriber authentication, and content access control — powered by **FrameAuth V2**.

🔗 Live preview: [artikle.framer.website](https://artikle.framer.website/)

---

## Table of Contents

- [About this Template](#about-this-template)
- [Requirements](#requirements)
- [Pages](#pages)
- [Components](#components)
- [Design System](#design-system)
- [Setting Up FrameAuth V2](#setting-up-frameauth-v2)
- [Customization Guide](#customization-guide)
- [Support](#support)

---

## About this Template

Artikle gives writers, journalists, and independent publishers everything they need to launch a professional online publication — without writing code. It includes a full content structure (articles, categories, subcategories, authors), member-only gating, and a complete authentication flow, all wired together natively inside Framer.

**Core features:**

- Hero article spotlight + latest articles grid on the homepage
- Multi-category feed: News & Analysis, Science & Technology, Sports, Lifestyle, Culture & Arts
- Subcategory pages with sidebar widgets
- Free and members-only (gated) article states
- Full authentication flow: sign-up, sign-in, OTP/magic link, password reset
- Subscription / pricing page with payment success confirmation
- Member dashboard (My Account) and Bookmarks
- Author directory and individual author profile pages
- Built-in search
- Responsive, typographic editorial design (Playfair Display + Inter)

---

## Requirements

Artikle requires a **[FrameAuth](https://frameauth.com/pricing)** subscription to enable membership, authentication, and content-gating functionality. Plans start at **$14.99/month** (billed yearly) and include a 14-day free trial.

Without an active FrameAuth account connected to the project, sign-up, sign-in, and content-gating components will not function.

---

## Pages

| Path | Page | Description |
|---|---|---|
| `/` | Home | Hero article, latest articles grid, recommendations, and category sections with subcategory spotlights. |
| `/articles` | Articles (Index) | Full collection feed of all published articles. |
| `/articles/:slug` | Article | Full article view with free/members-only states, author info, category tag, and bookmark action. |
| `/categories` | Categories (Index) | Overview of all available categories. |
| `/categories/:slug` | Category | Filtered feed of all articles within a specific category. |
| `/subcategories` | Subcategories (Index) | Overview of all available subcategories. |
| `/subcategories/:slug` | Subcategory | Filtered feed for a specific subcategory (e.g. Personal Finance, Football). |
| `/authors` | Authors | Directory of all contributing authors. |
| `/authors/:slug` | Author Profile | Individual author bio and their article feed. |
| `/subscribe` | Subscribe | Pricing plans and membership upsell. Powered by FrameAuth V2. |
| `/sign-in` | Sign In | Email/password login. |
| `/sign-in-with-otp` | Sign In with OTP | Passwordless login entry point. |
| `/otp` | OTP Verification | Magic link / one-time password confirmation. |
| `/sign-up` | Sign Up | New member registration. |
| `/forgot-password` | Forgot Password | Password reset request. |
| `/reset-password` | Reset Password | Set a new password after reset link. |
| `/my-account` | My Account | Member dashboard for account & subscription management. |
| `/bookmarks` | Bookmarks | Saved articles for logged-in members. |
| `/success` | Success | Post-payment confirmation page. |
| `/legal` | Legal (Index) | Overview of available legal documents. |
| `/legal/:slug` | Legal | Dynamic page for Terms, Privacy Policy, Cookie Policy. |
| `/404` | 404 | Custom not-found page. |

### CMS Collections

| Collection | Items included |
|---|---|
| Articles | 224 |
| Subcategories | 32 |
| Authors | 15 |
| Legal | 7 |
| Categories | 5 |

These are pre-populated with placeholder content so you can see the template fully working out of the box. Swap them out with your own content, or connect your own CMS collection with matching fields.

---

## Components

Artikle is built from modular, reusable components so you can restyle or rearrange without rebuilding from scratch.

**Layout & Navigation**
- `Logo`, `Nav`, `Menu`, `Search`, `Copyright`

**Content**
- `Article Card`, `Articles`, `Subcategory`, `divider`, `Commercial Banner`

**Authors & Profiles**
- `Profile`, `My Profile`

**Membership & FrameAuth (V2)**
- `Pricing Card`, `Subscribe Button`, `Subscribe Now`
- `Unlock Content` (×2 — teaser & full unlock states)
- `Teaser Intro and Unlocked Content`
- `Members Only`, `Already Member`
- `Subscription Feature`
- `Powered by FramerAuth`

**Reader Actions**
- `Actions/Bookmark`, `Bookmarks`

**Utility**
- `Button`, `Link`, `Framer Link`, `Social Media Link`, `Span`, `Cookie Banner Link`

> Components tied to membership logic rely on the `FramerAuthV2.tsx` code override — do not delete or rename this file, as auth-dependent components will stop functioning.

---

## Design System

**Typography**

| Style | Font | Size |
|---|---|---|
| Heading 1 | Playfair Display, 600 | 44px |
| Heading 2 | Playfair Display, 600 | 32px |
| Heading 3 | Playfair Display, 600 | 18px |
| Body | Inter | 16px |
| Button | Inter Medium | 16px |
| Span / Span Small / Span Tiny | Inter | 14px / 12px / 10px |

Headings use **Playfair Display** for an editorial, print-like feel; body and UI text use **Inter** for clarity and readability at smaller sizes.

**Color Palette**

A neutral light/dark grayscale system (`Light 98` → `Dark 2`) forms the base UI, accented by:
- **Blue** — primary actions, links (`Blue 50` / `Blue 96`)
- **Green** — success / confirmation states (`Green 30` / `Green 95`)
- **Orange** — highlights / tags (`Orange 60`)

All colors are defined as reusable Color Styles, so updating your brand palette is a matter of editing the style swatches — changes propagate across the entire template.

---

## Setting Up FrameAuth V2

1. Create a [FrameAuth](https://frameauth.com/pricing) account and choose a plan (14-day free trial available).
2. Follow FrameAuth's setup guide to connect your Framer project.
3. Configure your products/plans in FrameAuth to match the pricing tiers shown on the `/subscribe` page.
4. Confirm the `FramerAuthV2.tsx` code override is active in your project — this powers sign-up, sign-in, OTP, password reset, content gating, and the member dashboard.
5. Test the full flow: sign up → verify gated content locks/unlocks correctly → check `/my-account` and `/bookmarks`.

For detailed setup steps, refer to FrameAuth's own documentation at [frameauth.com](https://frameauth.com/).

---

## Customization Guide

- **Branding** — update the `Logo` component and color styles to match your publication's identity.
- **Categories** — edit the category list on the homepage and corresponding `/categories/:slug` and `/subcategories/:slug` pages to reflect your content verticals.
- **Article content** — Articles, Categories, Subcategories, and Authors are all pre-built as Framer CMS collections with placeholder content. Edit the existing entries or add new ones directly in Framer's CMS panel — the `Article Card` and `Articles` components will reflect changes automatically.
- **Gating rules** — use the `Unlock Content`, `Members Only`, and `Already Member` components to control what's visible to free vs. paying visitors.
- **Pricing** — update the `Pricing Card` and `Subscription Feature` components to reflect your actual membership tiers, then mirror those tiers in your FrameAuth product setup.

---

## Support

For template-specific questions, reach out at [mielucristian@gmail.com](mailto:mielucristian@gmail.com).
For FrameAuth V2 setup, authentication, or billing issues, refer to [frameauth.com](https://frameauth.com/) or their support channels directly.

---

*Artikle is built independently for Framer and is not affiliated with or endorsed by Framer or FrameAuth.*
