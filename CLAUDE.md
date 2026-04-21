# Caspi Law — Design Rules & Architecture

## Project
One-page landing site for Israeli lawyer Yair Caspi (יאיר כספי, עו״ד).
Language: Hebrew, RTL layout.
Stack: Single `index.html` + Tailwind CSS CDN + Lucide icons CDN + Decap CMS.
Deployed on Netlify + GitHub.

---

## Design Rules

### DO:
- Minimal, elegant, prestigious law firm aesthetic — inspired by agmon-law.co.il
- Dark/deep palette: near-black (#111) for hero + dark sections
- Alternating sections: dark (#111) and light off-white (#faf8f5)
- Accent color: warm gold/champagne (#c9a96e) — used sparingly
- Typography: Frank Ruhl Libre (Google Fonts) for headings, Inter for body
- Full RTL (`dir="rtl"` on `<html>`, `text-align: right` throughout)
- Generous section padding (py-24 minimum)
- Scroll animations via IntersectionObserver (fade-up on enter)
- Smooth hover transitions (transition-all duration-300)
- Mobile responsive with hamburger menu
- Sticky navbar with backdrop-blur

### DON'T:
- NO bright saturated gradients or gradient text
- NO emoji icons — Lucide icons only
- NO "revolutionary", "game-changing" copy
- NO heavy shadows or busy patterns
- NO dark mode toggle
- NO border-radius > rounded-2xl
- NO fonts below 14px

---

## Typography Scale

| Element | Font | Size | Weight | Color |
|---------|------|------|--------|-------|
| Hero H1 | Frank Ruhl Libre | 72px | 700 | white |
| Hero tagline | Inter | 20px | 300 | #d4d0ca |
| Section H2 dark bg | Frank Ruhl Libre | 44px | 600 | white |
| Section H2 light bg | Frank Ruhl Libre | 44px | 600 | #111 |
| Card H3 | Inter | 20px | 600 | — |
| Body light bg | Inter | 16px | 400 | #444, line-height 1.8 |
| Body dark bg | Inter | 16px | 400 | #aaa, line-height 1.8 |
| Gold labels | Inter | 12px | 500 | #c9a96e, uppercase, letter-spacing 0.1em |
| Nav links | Inter | 14px | 500 | white |
| Stat numbers | Frank Ruhl Libre | 48px | 700 | #c9a96e |
| Stat labels | Inter | 14px | 400 | #666 |
| CTA primary | Inter | 15px | 600 | bg #c9a96e, text #111, px-8 py-3, rounded-xl |
| CTA secondary | Inter | 15px | 500 | border white/30, text white, px-8 py-3, rounded-xl |
| Blog/article tag | Inter | 12px | 500 | uppercase, #c9a96e |

---

## Sections Order
1. Navbar
2. Hero
3. About
4. Practice Areas
5. Why Us
6. Articles
7. Daily Blog
8. Media
9. Contact
10. Footer

---

## Admin System Architecture
- Admin access: hidden "כניסת מנהל" link in footer
- Password: `CASPI2025` (compared via btoa)
- Netlify Personal Access Token stored in `localStorage("caspi_netlify_token")`
- Publish: POST to Netlify API with ZIP of updated `index.html`
- Site ID placeholder: `YOUR_NETLIFY_SITE_ID` — replace after first deploy

## Decap CMS
- Blog posts: `_posts/` folder, frontmatter: title, date, excerpt, body, published
- Articles: `_articles/` folder, frontmatter: title, date, category, excerpt, body, published
- Media uploads: `images/uploads/`
- Admin panel: `/admin/`
