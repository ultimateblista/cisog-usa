# CISOG USA — MASTER BUILD SPECIFICATION

**CISOG Technology Consults LLC — U.S. Digital Business Development Platform**

Version 2.2 · Reconciled build specification · Supersedes all prior documents

---

## 0. DOCUMENT CONTROL

### 0.1 What this document is

This is the single authoritative specification for the CISOG USA build. It reconciles four source documents into one buildable contract:

| # | Source document | Role in this spec |
|---|---|---|
| S1 | CISOG USA — WEBSITE BUILD SPECIFICATION | Design system, wireframes, technical requirements |
| S2 | Sitemap and page-by-page wireframe | Information architecture, page inventory |
| S3 | CISOG USA digital business | Commercial strategy, funnel, CRM, KPIs |
| S4 | Copy A — CISOG USA digital business | Draft page copy, positioning language |

Where the four disagree, **this document wins**. Every conflict is logged in §1 with the resolution and the reasoning behind it. Nothing has been resolved silently.

### 0.2 Who uses which section

| Role | Read |
|---|---|
| Client / sponsor | §1, §2, §16, §18 |
| UI/UX designer | §3, §4, §5, §6, §12 |
| Front-end developer | §4, §5, §6, §12, §15, §17 |
| Back-end developer | §7, §8, §9, §10, §13 |
| Content / SEO lead | §3, §7, §11, §16 |
| QA | §12, §17 |

### 0.3 Status legend

- **[DECIDED]** — resolved, build to this
- **[GATED]** — blocked pending client verification, see §18
- **[PHASE 2/3]** — deliberately deferred, do not build now

---

## 1. CONFLICT RESOLUTION REGISTER

Twenty-two conflicts, gaps and risks were identified across S1–S4. Each is resolved below.

### C-01 · Primary navigation — three incompatible versions [DECIDED]

**Conflict.** S1 specifies 6 nav items. S2 specifies 9. S4 specifies 8 including Careers and a "Risk & Compliance" item that appears nowhere else.

**Resolution.** Six primary items plus one CTA:

`Services ▾ · Industries ▾ · Solutions ▾ · Insights · Resources ▾ · About ▾` `[Schedule a Consultation]`

**Reasoning.** Contact becomes the CTA button — it is a conversion action, not a browse action, and duplicating it in the nav dilutes the button. *Client Success* is demoted to a featured panel inside the Solutions and About mega-menus plus the footer, because at launch it will contain zero published case studies (see C-10) and an empty top-level nav item advertises the absence. *Careers* moves under About (see C-19). *Risk & Compliance* is absorbed into GRC — it is not a distinct offer.

### C-02 · Service grouping — vCISO merged or standalone [DECIDED]

**Conflict.** S4 merges "Cybersecurity & vCISO" into one page. S1, S2 and S3 treat vCISO as a standalone service.

**Resolution.** Standalone. `/services/vciso/` is its own page.

**Reasoning.** "virtual CISO services" and "vCISO services" are among the highest commercial-intent, lowest-competition keywords in this space, and S3 §33 explicitly targets them. A merged page cannot rank for both "cybersecurity consulting" and "virtual CISO" — the title tag, H1 and internal anchor text can only be optimised for one. vCISO is also the only offer in the portfolio with recurring-revenue mechanics (S3 §12), which makes it the most commercially valuable page on the site. It gets its own URL.

### C-03 · Solution naming — "360" family vs descriptive names [DECIDED]

**Conflict.** S1 and S2 use *CyberSecure 360, GRC 360, AI Governance 360, Digital Transformation 360*. S3 §11 uses *Cybersecurity Readiness, GRC Transformation, Technology Strategy*.

**Resolution.** The 360 family.

**Reasoning.** The stated strategy (S3 §11–15) is to move from selling consulting hours to selling packaged, productised offerings. Descriptive names ("GRC Transformation") read as service categories and invite hourly-rate comparison. Named products carry fixed scope, fixed deliverables and are protectable as marks. This also fixes a downstream problem: a named product can be referenced consistently in proposals, the capability statement and case studies.

### C-04 · vCISO listed as both a Service and a Solution [DECIDED]

**Conflict.** S2 lists vCISO under both `/services/vciso/` and `/solutions/vciso/`.

**Resolution.** One page: `/services/vciso/`. The Solutions hub shows a vCISO card that links there. `/solutions/vciso/` is a 301 redirect, never a live page.

**Reasoning.** Two pages targeting the same query is keyword cannibalisation — they compete against each other in the index, split inbound link equity, and Google picks the canonical for you, usually the wrong one.

### C-05 · Government appears twice in the IA [DECIDED]

**Conflict.** S2 defines both `/industries/government/` and a top-level `/government/` hub with overlapping capability lists.

**Resolution.** Single canonical hub at `/government/`. `/industries/government/` 301 redirects to it. The Industries hub card for Government links to `/government/`.

**Reasoning.** Same cannibalisation problem as C-04, with an added factor: public-sector buyers evaluate differently (capability statement, NAICS, contract vehicles, past performance) and need a distinct page treatment. Nesting that under Industries buries it. Government gets top-level status in the footer and a featured panel in the Industries mega-menu, without consuming a primary nav slot it cannot yet justify.

### C-06 · Duplicate SEO landing pages [DECIDED]

**Conflict.** S3 §34 specifies twelve flat SEO landing pages — `/cybersecurity-consulting/`, `/vciso-services/`, `/grc-consulting/`, `/ai-governance/` and so on — that duplicate the nested service pages in S1/S2.

**Resolution.** **Do not build them.** One canonical URL per topic, nested: `/services/cybersecurity/`. All twelve flat URLs are registered as 301 redirects to their nested equivalent.

**Reasoning.** This is the single most damaging idea in the source documents. Two near-identical pages targeting one query is the classic self-inflicted SEO wound: crawl budget wasted, link equity split, and an algorithmic canonical choice you do not control. URL depth has negligible direct ranking weight — keyword-in-URL is a very weak signal relative to title, content and internal anchor text. The correct move is to concentrate every internal link and every backlink on one strong page. The redirects are still worth registering so the URLs cannot be taken by a competitor and so any existing external links resolve.

### C-07 · IT Governance — merged with GRC or standalone [DECIDED]

**Conflict.** S1 lists "GRC & IT GOVERNANCE" as one service. S2 gives IT Governance its own page at `/services/it-governance/`.

**Resolution.** Two pages, with enforced separation of intent:

- `/services/grc/` — compliance, controls, audit readiness, framework alignment. Buyer: risk/compliance officer under audit or regulatory pressure.
- `/services/it-governance/` — decision rights, technology risk, IT performance, governance committees. Buyer: CIO/board dealing with accountability and technology spend.

**Reasoning.** These are genuinely different buying triggers and different search queries. But they are close enough that a lazy build produces two thin, overlapping pages — which is worse than one strong page. The separation is conditional: if content review at build time cannot produce 800+ words of genuinely distinct material for each, merge them into `/services/grc/` and redirect. This is a build-time gate, not a design-time assumption.

### C-08 · Assessment maturity bands — direct contradiction [DECIDED]

**Conflict.** S1 §35 shows a score of 72 as maturity level **"Managed"** (band 61–80). S2 §43 shows a score of 72 as **"Developing"**. These cannot both be true.

**Resolution.** S1's five-band scale is correct. S2 §43 is an error.

| Score | Maturity level |
|---|---|
| 0–20 | Initial |
| 21–40 | Developing |
| 41–60 | Defined |
| 61–80 | Managed |
| 81–100 | Optimized |

**Reasoning.** This ladder maps to CMMI and COBIT maturity vocabulary, which the CISO/CIO audience already reads fluently. Renaming levels invents a scale nobody recognises. Full scoring algorithm in §9.

### C-09 · "Since 2003" on a U.S. entity [GATED — legal]

**Conflict.** S2 §5 and S3 §23 put "Since 2003" in the homepage trust strip. The 2003 date belongs to CISOG Consults Limited (the Nigerian parent), not to CISOG Technology Consults LLC.

**Resolution.** Never render "Since 2003" as a bare claim on the U.S. site. Approved wording: **"Part of the CISOG Group — operating internationally since 2003."** The LLC's own U.S. formation date is stated separately on `/about/` once confirmed.

**Reasoning.** An unqualified founding-date claim attached to the U.S. entity is a misrepresentation risk under FTC advertising rules and, more practically, is the kind of thing a procurement officer or a competitor checks against state incorporation records. The attribution is free to make correctly and expensive to get wrong.

### C-10 · Quantified client outcomes [GATED — client evidence]

**Conflict.** S3 §22 cites "90% reduction in real-world phishing clicks over three months" for a fintech engagement. S1 §30 states "Do not launch with fabricated case studies" and "Only publish verified numbers."

**Resolution.** No metric ships without (a) the underlying measurement methodology in writing and (b) written client permission to publish, anonymised or named. Build the case study CMS collection now; publish zero case studies at launch if the evidence is not in hand.

**Reasoning.** A cybersecurity consultancy publishing an unverifiable security metric is a self-inflicted credibility wound — this audience will ask how it was measured. The design must therefore work with zero case studies at launch (see §5, `CaseStudyRail` empty state).

### C-11 · Logos and certifications [GATED — client verification]

**Conflict.** S1 §11 and S3 §24 both want client logos, partner logos, certifications and memberships in the trust strip, while simultaneously warning "Do not publish logos until verified."

**Resolution.** **The trust strip is designed to work with zero logos.** It carries capability wordmarks and the group-provenance line only. A `LogoStrip` component is built and unit-tested but ships disabled behind a CMS flag.

**Reasoning.** This is a hard design constraint, not a content note. A trust strip designed around six logo slots looks broken with zero. Designing it text-first means logos become an upgrade later rather than a launch dependency.

### C-12 · CRM undecided [DECIDED — see §13]

S3 §38 and S1 §42 both flag that CRM choice must precede development because forms and API architecture depend on it, then never decide. Resolved in §13: **HubSpot**.

### C-13 · CMS never specified [DECIDED — see §13]

All four documents specify CMS *content types* in detail and never name a CMS. Resolved in §13: **Sanity**.

### C-14 · Phase 1 page count [DECIDED]

**Conflict.** S1 §65 says 20–25 pages. S2 §60 lists 20. S4 says 15–20.

**Resolution.** **24 pages**, enumerated exactly in §3.2. No ambiguity, no scope drift.

### C-15 · Assessments described as "free" but gated [DECIDED]

**Conflict.** S4 §12 markets "FREE DIGITAL ASSESSMENTS". S1 §33 and S3 §10 gate the result behind email capture.

**Resolution.** Split the deliverable. The **score, maturity band and top three priority gaps display immediately on screen, ungated.** Email is required only for the detailed PDF report with per-domain breakdown and recommended actions.

**Reasoning.** Asking for 10–15 minutes of a CISO's time and then withholding the result at the end is the highest-abandonment pattern in lead-gen, and it generates hostile fake-email submissions that pollute the CRM. Giving the score away costs nothing — the score is a hook, the report is the asset. It also removes the "free" claim problem entirely.

### C-16 · Pricing display [DECIDED]

S1 §22 says "Avoid publishing fixed prices initially" while showing three vCISO tiers. **Resolution:** publish tiers with scope, deliverable and cadence differences; no dollar figures. CTA is *Request Scope & Pricing*.

### C-17 · Government contracting identifiers [GATED]

UEI, CAGE code, NAICS codes, contract vehicles and past performance (S3 §25) are all rendered fields in the capability statement template. **None render until verified.** Each is a nullable CMS field with a conditional block — the page must look complete without them.

### C-18 · Accessibility target vs measurement method [DECIDED]

**Conflict.** S1 §56 sets WCAG 2.2 AA. S1 §54 sets a Lighthouse accessibility score of 90+. These are not the same thing.

**Resolution.** **WCAG 2.2 AA is the contractual conformance target**, verified by manual audit plus axe-core. Lighthouse 90+ is a CI smoke test only and is never accepted as evidence of conformance.

**Reasoning.** Automated tooling detects roughly 30–40% of WCAG failures. A Lighthouse score of 100 is entirely compatible with a site that is unusable with a screen reader. Conflating them is how organisations end up with an accessibility statement they cannot defend — which matters more than usual here, because the site itself is a credibility artifact for a governance and compliance consultancy.

### C-19 · Careers in primary navigation [PHASE 2]

S4 puts Careers in the main nav. **Resolution:** page exists at `/about/careers/` from launch with a general-interest form; it enters the nav only when there are live roles. A Careers page reading "no open positions" in primary navigation signals contraction.

### C-20 · Insights launching empty [DECIDED — content gate]

**Resolution.** Insights does not go live with fewer than **eight published articles**. S3 §20's Month 1 and Month 2 calendars supply exactly this. This is a launch blocker, not a nice-to-have.

**Reasoning.** An empty blog is worse than no blog: it dates the site, it signals abandonment, and the "Latest Insights" homepage module has no fallback that does not look broken.

### C-21 · Global search at launch [PHASE 2]

S1 §48 specifies a global search overlay indexing six content types. **Resolution:** deferred until Insights and Resources exceed 30 items. Search across 24 pages returns near-empty result sets and makes the site feel thinner than it is.

### C-22 · CISOG Academy [PHASE 3]

S2 §44 and S3 §18 describe a multi-track training programme. This is a learning-management platform, not a website section — enrolment, payment, progress tracking, certification. **Resolution:** at launch, `/resources/academy/` is a single interest-capture page. LMS evaluation is a separate project.

---

## 2. STRATEGIC POSITION

### 2.1 The decision that governs everything else

All four source documents converge on one point (S1 §66, S3 "One important strategic change", S4 §17): **CISOG USA must not mirror the CISOG Group site.** The parent presents a diversified portfolio — consulting, cybersecurity, EPC, energy, distribution, textiles. That breadth reads as capability in its home market and as unfocused in the U.S. one.

```
CISOG GROUP                    International corporate ecosystem
        │                      Broad multi-sector portfolio
        ↓
CISOG USA                      U.S. technology advisory — the specialist front door
        │
        ↓
SIX FLAGSHIP PRACTICES         Cybersecurity · vCISO · GRC · AI Governance ·
        │                      Digital Transformation · Technology Advisory
        ↓
COMMERCIAL OUTCOME             Assess → Advise → Transform → Govern → Sustain
```

The Group is the credibility layer, referenced and linked — never the lead.

### 2.2 The design test

Every page is judged against the perception sequence in S2 §65. In order:

1. *"These people understand cybersecurity and technology at an executive level."*
2. *"They understand governance and business risk."*
3. *"They understand emerging technology such as AI."*
4. *"They can actually implement what they recommend."*
5. *"I should talk to them about our problem."*

If a page does not advance one of these, it does not ship.

### 2.3 Differentiation priority

AI Governance is the wedge. Every mid-tier U.S. firm sells cybersecurity consulting and vCISO; comparatively few have a credible, structured AI governance practice, and demand is being manufactured by regulation and board pressure rather than by vendor marketing. **`/services/ai-governance/` receives the highest design investment of any page on the site** (S1 §24). It is the page most likely to earn links, and links to it lift the whole domain.

### 2.4 Primary conversion objective

Three actions, in ascending commitment:

| | Action | Instrument |
|---|---|---|
| 1 | **ASSESS** — "Evaluate my organization" | Four assessment products |
| 2 | **ADVISE** — "Talk to an expert" | Consultation booking |
| 3 | **ENGAGE** — "Start a project" | Scoped proposal |

Learn → Assess → Discuss → Engage → Expand.

---

## 3. INFORMATION ARCHITECTURE

### 3.1 Navigation model

**Primary (desktop):**

```
CISOG USA    Services ▾  Industries ▾  Solutions ▾  Insights  Resources ▾  About ▾   [Schedule a Consultation]
```

**Mega-menu contents:**

| Menu | Columns | Featured panel (right) |
|---|---|---|
| Services | Security & Risk (Cybersecurity, vCISO) · Governance (GRC, IT Governance, AI Governance) · Technology (Digital Transformation, Technology Advisory, Cloud & Infrastructure, Software & Applications) | AI Governance 360 → |
| Industries | 7 industries in two columns | Government & Public Sector → |
| Solutions | 6 solution products | Client Success → |
| Resources | Guides · White Papers · Reports · Webinars · Assessments · Academy | Take an Assessment → |
| About | CISOG Technology Consults · CISOG Group · Leadership · Why CISOG · Our Approach · Partners · Careers | Client Success → |

**Mobile:** accordion drawer, both CTAs pinned at the base of the panel, `[Take an Assessment]` secondary and `[Schedule a Consultation]` primary.

### 3.2 Phase 1 page inventory — exactly 24 pages

| # | Page | URL | Template | Priority |
|---|---|---|---|---|
| 1 | Home | `/` | `home` | P0 |
| 2 | About CISOG Technology Consults | `/about/` | `about` | P0 |
| 3 | CISOG Group | `/about/cisog-group/` | `content` | P1 |
| 4 | Leadership | `/about/leadership/` | `people` | P1 |
| 5 | Why CISOG | `/about/why-cisog/` | `content` | P1 |
| 6 | Our Approach | `/about/our-approach/` | `process` | P1 |
| 7 | Services hub | `/services/` | `hub` | P0 |
| 8 | Cybersecurity | `/services/cybersecurity/` | `service` | P0 |
| 9 | vCISO | `/services/vciso/` | `service` | P0 |
| 10 | GRC | `/services/grc/` | `service` | P0 |
| 11 | IT Governance & Technology Risk | `/services/it-governance/` | `service` | P1 |
| 12 | AI Governance | `/services/ai-governance/` | `service-flagship` | P0 |
| 13 | Digital Transformation | `/services/digital-transformation/` | `service` | P0 |
| 14 | Technology Advisory | `/services/technology-advisory/` | `service` | P0 |
| 15 | Industries hub | `/industries/` | `hub` | P1 |
| 16 | Financial Services | `/industries/financial-services/` | `industry` | P1 |
| 17 | SMEs & Growth Companies | `/industries/smes/` | `industry` | P1 |
| 18 | Government & Public Sector | `/government/` | `government` | P1 |
| 19 | Solutions hub | `/solutions/` | `hub` | P1 |
| 20 | Client Success | `/client-success/` | `hub` | P2 |
| 21 | Insights hub | `/insights/` | `insights` | P0 |
| 22 | Resources hub | `/resources/` | `hub` | P1 |
| 23 | Contact | `/contact/` | `contact` | P0 |
| 24 | Schedule a Consultation | `/contact/schedule-consultation/` | `booking` | P0 |

Plus non-indexed utility pages: `/legal/privacy/`, `/legal/terms/`, `/legal/cookies/`, `/legal/accessibility/`, `/thank-you/`, `/404/`, `/search/` (Phase 2).

Phase 1 templates also cover the *article* and *case study* detail templates, driven by CMS entries rather than fixed pages.

### 3.3 Redirect map (register at launch)

| From | To | Reason |
|---|---|---|
| `/cybersecurity-consulting/` | `/services/cybersecurity/` | C-06 |
| `/vciso-services/` | `/services/vciso/` | C-06 |
| `/grc-consulting/` | `/services/grc/` | C-06 |
| `/it-governance/` | `/services/it-governance/` | C-06 |
| `/ai-governance/` | `/services/ai-governance/` | C-06 |
| `/ai-risk-management/` | `/services/ai-governance/` | C-06 |
| `/digital-transformation/` | `/services/digital-transformation/` | C-06 |
| `/technology-advisory/` | `/services/technology-advisory/` | C-06 |
| `/cybersecurity-assessment/` | `/resources/assessments/cybersecurity/` | C-06 |
| `/board-cybersecurity-advisory/` | `/solutions/board-advisory/` | C-06 |
| `/government-cybersecurity/` | `/government/` | C-05 |
| `/financial-services-cybersecurity/` | `/industries/financial-services/` | C-06 |
| `/industries/government/` | `/government/` | C-05 |
| `/solutions/vciso/` | `/services/vciso/` | C-04 |

Rule: URLs are lowercase, hyphenated, trailing-slashed. No dates in article URLs — `/insights/{slug}/`, so evergreen content can be updated without changing its address.

### 3.4 Conversion architecture

Every page carries exactly one dominant next action.

```
INFORMATION PAGE → RELEVANT RESOURCE → ASSESSMENT → LEAD CAPTURE → CONSULTATION → OPPORTUNITY
```

| Page type | Primary CTA | Secondary CTA |
|---|---|---|
| Home | Schedule a Consultation | Take a Readiness Assessment |
| Cybersecurity | Request a Cybersecurity Assessment | Download the Readiness Guide |
| vCISO | Talk to a vCISO Advisor | Request Scope & Pricing |
| GRC | Assess Your GRC Maturity | Download the GRC Guide |
| AI Governance | Assess Your AI Governance Readiness | Request an AI Governance Workshop |
| Digital Transformation | Discuss Your Transformation Roadmap | Take the Readiness Assessment |
| Technology Advisory | Request an Executive Technology Briefing | Schedule a Consultation |
| Industry pages | Schedule a Consultation | Relevant assessment |
| Government | Download the Capability Statement | Contact the Government Practice |
| Insight article | Related assessment | Subscribe to CISOG Insights |
| Resource | Download the Guide | Take the related assessment |

---

## 4. DESIGN SYSTEM

### 4.1 Design tokens — colour

Every value below has been contrast-tested. Ratios are computed against WCAG 2.x relative luminance.

**Neutrals — ink (dark surfaces)**

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--ink-950` | `#050D1A` | Deepest surface, footer base | — |
| `--ink-900` | `#0A1628` | Primary dark surface | 18.13:1 vs white |
| `--ink-800` | `#0F2035` | Raised card on dark | — |
| `--ink-700` | `#1A2E4A` | Border on dark | — |
| `--ink-600` | `#2B4368` | Divider on dark | — |

**Neutrals — light**

| Token | Hex | Use | Contrast on white |
|---|---|---|---|
| `--slate-700` | `#33415C` | Body copy | **10.24:1** ✓ AAA |
| `--slate-600` | `#4A5878` | Secondary body | **7.10:1** ✓ AAA |
| `--slate-500` | `#5D6A85` | Captions, meta — **light surfaces only** | 5.43:1 white · **4.96:1 slate-100** ✓ AA |
| `--slate-450` | `#8B98B4` | Muted text — **dark surfaces only** | 6.26:1 on ink-900 ✓ AA |
| `--slate-300` | `#C7D0E0` | Body on dark | 11.68:1 on ink-900 ✓ AAA |
| `--slate-200` | `#E2E8F2` | Borders | — |
| `--slate-100` | `#F1F5FA` | Alternating section background | — |
| `--blue-50` | `#F5F8FF` | Selected state on light surfaces | 5.11:1 w/ slate-500 ✓ AA |

**Note on `--slate-500`.** The first pass set this to `#64728F`, which passes on white at 4.83:1 but drops to **4.41:1 on `--slate-100`** — a failure, and one that only appears on alternating sections. Because captions sit on both surfaces, the token is specified against the *darkest* background it will ever occupy, not against white. Verify muted tokens against every surface they can land on, not the default one.

**Brand**

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--blue-700` | `#0F3FA8` | Link hover, pressed | 9.14:1 on white ✓ AAA |
| `--blue-600` | `#1454D4` | Primary action, links | **6.46:1** on white ✓ AA |
| `--blue-500` | `#2B6BEF` | Hover fill | — |
| `--blue-400` | `#5B93FF` | Links on dark | 6.10:1 on ink-900 ✓ AA |
| `--cyan-400` | `#22D3EE` | Accent — **dark surfaces only** | 10.03:1 on ink-900 ✓ AAA |
| `--cyan-500` | `#00B8D9` | Accent fill; **never for text on white** (2.37:1) | navy-on-cyan 7.65:1 ✓ |

**Semantic**

| Token | Hex | Contrast on white |
|---|---|---|
| `--success` | `#0F7B4F` | 5.29:1 ✓ AA |
| `--warning` | `#B45309` | 5.02:1 ✓ AA |
| `--danger` | `#C2261A` | 5.86:1 ✓ AA |

**Three hard rules.**

1. **`--cyan-500` at 2.37:1 on white fails AA for text at any size.** It is a fill and graphic colour only. S1 §5 proposed "electric cyan" as an accent without qualifying the surface; on light backgrounds it is unusable for text, and this is the most common way a navy/cyan system fails audit.
2. **`--slate-500` and `--slate-450` are not interchangeable.** slate-500 passes on white (4.83:1) and fails on navy (3.75:1). Muted text on dark surfaces must use slate-450. A single "muted grey" token applied to both surfaces is the second most common failure in a dark/light hybrid system, and it is invisible to a designer working only in light mode.
3. **Semantic colour never carries meaning alone** (WCAG 1.4.1). Assessment result states pair colour with an icon and a text label.

**Dark section allocation** (S1 §5): cybersecurity pages, executive advisory, assessment engine module, final CTA band, footer.

### 4.2 Typography

Typeface: **Inter** (variable). Fallback stack: `Inter var, Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif`.

Self-host as WOFF2 with `font-display: swap` and preload the two weights used above the fold. Do not link Google Fonts — it is a third-party request in the critical path and a CSP entry you do not need.

| Role | Desktop | Mobile | Weight | Line height | Tracking |
|---|---|---|---|---|---|
| Display / H1 | 60px | 40px | 700 | 1.05 | −0.03em |
| H2 | 44px | 32px | 700 | 1.12 | −0.02em |
| H3 | 26px | 23px | 600 | 1.25 | −0.01em |
| H4 | 20px | 19px | 600 | 1.35 | 0 |
| Body large | 20px | 17px | 400 | 1.6 | 0 |
| Body | 18px | 17px | 400 | 1.65 | 0 |
| Body small | 16px | 15px | 400 | 1.6 | 0 |
| Caption | 14px | 13px | 500 | 1.5 | 0.01em |
| Eyebrow | 13px | 12px | 600 | 1.4 | 0.12em, uppercase |

Measure is capped at **68 characters** for body copy. Headings never exceed **20 words**.

### 4.3 Grid and spacing

| Breakpoint | Range | Container | Columns | Gutter | Outer margin |
|---|---|---|---|---|---|
| Desktop L | ≥1440px | 1280px max | 12 | 24px | 80px |
| Desktop | 1025–1439px | `calc(100% − 96px)` | 12 | 24px | 48px |
| Tablet | 768–1024px | `calc(100% − 64px)` | 8 | 20px | 32px |
| Mobile | ≤767px | `calc(100% − 32px)` | 4 | 16px | 16px |

Content column caps at **1180px** inside the 1280px container. Spacing is an 8px base scale: `4 · 8 · 12 · 16 · 24 · 32 · 40 · 48 · 64 · 80 · 96 · 128`. Vertical section rhythm: 128px desktop / 80px tablet / 64px mobile.

### 4.4 Elevation, radius, borders

| Token | Value |
|---|---|
| `--radius-sm` | 6px (inputs, tags) |
| `--radius-md` | 10px (cards, buttons) |
| `--radius-lg` | 16px (feature cards, modals) |
| `--shadow-sm` | `0 1px 2px rgb(10 22 40 / .06)` |
| `--shadow-md` | `0 4px 16px rgb(10 22 40 / .08)` |
| `--shadow-lg` | `0 12px 32px rgb(10 22 40 / .12)` |
| `--shadow-header` | `0 1px 0 rgb(10 22 40 / .08)` |

Borders are `1px solid var(--slate-200)` on light, `1px solid var(--ink-700)` on dark. No border on a surface that already has a shadow.

### 4.5 Motion

S1 §53 mandates restrained motion. Durations and easings:

| Interaction | Change | Duration | Easing |
|---|---|---|---|
| Card hover | `translateY(-4px)` + shadow-md→lg | 180ms | `cubic-bezier(.2,.8,.2,1)` |
| Button hover | background shift, arrow `translateX(4px)` | 150ms | `ease-out` |
| Section reveal | opacity 0→1, `translateY(16px)`→0 | 500ms | `cubic-bezier(.16,1,.3,1)` |
| Stat count-up | 0→value | 1200ms | `ease-out` |
| Mega-menu | opacity + `translateY(-6px)` | 200ms | `ease-out` |
| Mobile drawer | `translateX` | 260ms | `cubic-bezier(.4,0,.2,1)` |

**`prefers-reduced-motion: reduce` disables all transforms and count-ups; reveals become instant opacity 1.** This is WCAG 2.3.3 and is not optional. Section reveals fire once via `IntersectionObserver` and never re-trigger — repeated animation on scroll-up is the most common complaint about this pattern.

### 4.6 Imagery

Direction from S1 §50–51, restated as build rules:

**Required:** executive technology environments, security operations with people present, AI and data visualisation with human oversight visible, boardroom and advisory settings, abstract technology architecture.

**Prohibited:** hooded figures, padlock icons as hero imagery, matrix/green-code motifs, circuit-board wallpaper, people pointing at monitors, "cyber warrior" imagery, any science-fiction styling.

**Master generation prompt** (S1 §51, use for all hero imagery):

> Premium enterprise technology consulting photography, diverse senior executives and technology professionals collaborating in a sophisticated modern corporate environment, cybersecurity, artificial intelligence and digital transformation visual elements subtly integrated into transparent displays, realistic photography, sophisticated U.S. corporate aesthetic, premium consulting firm website, restrained navy and blue technology atmosphere, natural human interaction, no logos, no text, no hacker imagery, no futuristic science-fiction styling.

**Technical:** AVIF with WebP fallback, `srcset` at 480/768/1200/1920, `loading="lazy"` below the fold, explicit `width`/`height` to reserve layout space (CLS), LCP hero image preloaded and never lazy-loaded. Every image needs meaningful `alt`; decorative images get `alt=""`.

### 4.7 Iconography

One family, minimal line style, 1.5px stroke, 24px grid. Recommended: Lucide (MIT, tree-shakeable, consistent optical weight). Icons are `aria-hidden="true"` when adjacent to a text label.

| Concept | Icon |
|---|---|
| Cybersecurity | shield |
| vCISO | user-cog |
| GRC | clipboard-check |
| IT Governance | scale |
| AI Governance | network / brain-circuit |
| Digital Transformation | refresh-cw |
| Technology Advisory | compass |
| Cloud & Infrastructure | cloud |
| Software & Applications | code |
| Government | landmark |

---

## 5. COMPONENT LIBRARY

Twenty-eight components. Every one is built once, typed, and documented with variants, states and empty states. No page-specific markup.

| # | Component | Variants | States | Notes |
|---|---|---|---|---|
| 1 | `SiteHeader` | transparent, solid | default, scrolled, menu-open | Sticky at scroll >80px |
| 2 | `MegaMenu` | 5 configurations | closed, open, focused | Keyboard: Esc closes, focus trapped, arrow-key traversal |
| 3 | `MobileDrawer` | — | closed, open, submenu | Focus trap, background inert |
| 4 | `SkipLink` | — | focus-visible | First focusable element |
| 5 | `Breadcrumb` | desktop trail, mobile back | — | Emits `BreadcrumbList` schema |
| 6 | `Hero` | home, service, flagship, industry, government, article | — | 680–760px home / 520–620px inner |
| 7 | `TrustStrip` | wordmark, logo (disabled) | — | **Must render correctly with zero logos** (C-11) |
| 8 | `CTAButton` | primary, secondary, ghost, dark | default, hover, active, focus, disabled, loading | Min target 44×44px |
| 9 | `SplitFeature` | image-left, image-right | — | 50/50 at ≥1025px, stacked below |
| 10 | `ServiceCard` | default, compact | default, hover, focus | Icon, H3, 2-line description, arrow |
| 11 | `SolutionCard` | large, standard | default, hover, focus | Product name, 3-word promise, CTA |
| 12 | `IndustryCard` | grid, scroller | default, hover | Horizontal scroll-snap on mobile |
| 13 | `PillarRow` | 4-up, 5-up | — | Why CISOG differentiators |
| 14 | `ProcessFlow` | horizontal, vertical | active step | Assess → Prioritize → Design → Implement → Monitor |
| 15 | `FrameworkGrid` | — | — | NIST CSF, NIST AI RMF, ISO 27001, ISO 27701, COBIT, CIS, SOC 2, PCI DSS |
| 16 | `StatCard` | up, down, neutral | in-view count-up | Direction arrow + label, never colour alone |
| 17 | `InsightCard` | featured, standard, compact | default, hover | Category, title, date, reading time |
| 18 | `CaseStudyRail` | populated, **empty** | — | Empty state renders a capability statement CTA (C-10) |
| 19 | `Testimonial` | quote, card | — | Hidden until verified attribution exists |
| 20 | `FAQAccordion` | — | collapsed, expanded | `<details>`-based; emits `FAQPage` schema |
| 21 | `AssessmentCard` | — | default, hover | Product, duration, CTA |
| 22 | `AssessmentRunner` | 4 products | question, transition, scoring, complete | Progress "Question 4 of 10", back navigation, state persisted |
| 23 | `AssessmentResult` | ungated, gated-report | — | Score dial, band, strengths, gaps (C-15) |
| 24 | `ResourceCard` | gated, ungated | — | Type badge, description, download |
| 25 | `LeadForm` | contact, download, consultation, newsletter | idle, validating, submitting, success, error | Inline validation, `aria-describedby` errors. **See 5.2** |
| 26 | `SiteFooter` | — | — | 5 columns desktop, accordion mobile |
| 27 | `CookieBanner` | — | initial, preferences | Consent Mode v2 |
| 28 | `MobileStickyCTA` | — | visible, hidden-on-form | **Must not obscure form fields** (S1 §46) |

### 5.1 Page templates

| Template | Section sequence |
|---|---|
| `home` | Hero → TrustStrip → Problem → Services → Problem-based nav → Why CISOG → Solutions → Industries → Assessments → Insights → Final CTA |
| `service` | Breadcrumb → Hero → Problem → Capabilities → Methodology → Deliverables → Outcomes → Frameworks → Industries → Case study → FAQ → CTA |
| `service-flagship` | As `service`, plus a bespoke interactive governance diagram and lifecycle module (AI Governance only) |
| `industry` | Breadcrumb → Hero → Challenges → Risk landscape → Capabilities → Solutions → Use cases → Regulatory considerations → Case study → Insights → CTA |
| `government` | Breadcrumb → Hero → Capability matrix → Core competencies → Differentiators → Past performance [GATED] → Contracting info [GATED] → Capability statement CTA → Partner CTA |
| `hub` | Breadcrumb → Hero → Card grid → Cross-sell → CTA |
| `insights` | Hero → Category filter → Featured → Grid → Newsletter |
| `article` | Breadcrumb → Title block → Executive summary → Body → Key takeaways → Related service → Related insights → CTA |
| `contact` | Hero → Intent selector → Form → Alternative contact → FAQ |
| `booking` | Service → Meeting type → Date/time → Details → Confirmation |

---

### 5.2 Form control rule — do not style inputs with a blanket selector

A rule such as `.field input { width: 100%; min-height: 48px; padding: 13px 15px }` is the normal way to style text entry, and it silently destroys every checkbox and radio in the form. The checkbox inflates to full container width, the adjacent label text collapses into a narrow column, and the consent row becomes unusable — while every automated check still passes, because the markup and the contrast are both fine.

**Required:** all text-entry styling is scoped with `input:not([type="checkbox"]):not([type="radio"])`. Checkboxes and radios are styled explicitly and separately.

**Consent and multi-select rows** are wrapped in a `<label>` so the entire row is the click target. The checkbox itself is 20px, below the 24×24 minimum in SC 2.5.8 — conformance comes from the label, which is the target, not from the box. If a design ever places a bare checkbox outside a label, it must be 24×24 or larger.

This was caught by eye during prototype review, not by tooling. Automated accessibility checking validates relationships and contrast; it does not know that a control looks wrong. Visual review of every form state remains a required acceptance step (§17).

## 6. HOMEPAGE SPECIFICATION

Section-by-section, with copy locked from the reconciled sources.

### Section 01 — Hero
Height 680–760px desktop / 600–700px mobile. Dark navy with a restrained network visualisation; content left, visual right at ≥1025px, stacked on mobile with full-width CTAs.

> **SECURE. TRANSFORM. GOVERN. GROW.**
> Technology Consulting for a More Secure, Resilient and Intelligent Future.
>
> CISOG Technology Consults helps organizations strengthen cybersecurity, manage technology risk, govern artificial intelligence and transform their digital operations.
>
> `[Schedule a Consultation]` `[Take a Readiness Assessment]`

Resolves C-07: the "Resilient" variant is used because resilience recurs throughout the service propositions; the secondary CTA is a conversion action, not "Explore Our Services", which the navigation already provides.

### Section 02 — Trust strip
Height 100–130px. Zero logos (C-11).

> Cybersecurity · vCISO · GRC & IT Governance · AI Governance · Digital Transformation · Technology Advisory
> Part of the CISOG Group — operating internationally since 2003 · United States · Africa · Middle East

Wording resolves C-09.

### Section 03 — The problem
50/50 split, image right.

> **Technology creates opportunity. It also creates risk.**
> Organizations are under pressure to secure increasingly complex environments, respond to evolving threats, meet regulatory and customer requirements, manage third-party risk, adopt AI responsibly, modernize legacy systems and improve operational resilience.
>
> `See How We Help →`

### Section 04 — Core services
3×2 grid: Cybersecurity · vCISO · GRC & IT Governance · AI Governance · Digital Transformation · Technology Advisory. Each: icon, H3, two-line description, arrow.

### Section 05 — Problem-based navigation
S3 §8 — the strongest single idea in the source material, because it speaks the buyer's language rather than the consultant's.

> **What are you trying to solve?**

| Statement | Routes to |
|---|---|
| "We need stronger cybersecurity." | Cybersecurity + vCISO |
| "We have governance or compliance gaps." | GRC + IT Governance |
| "We are adopting AI." | AI Governance |
| "Our technology needs modernization." | Digital Transformation |
| "We need strategic technology leadership." | Technology Advisory + vCISO |

### Section 06 — Why CISOG
Five pillars: Global Perspective · Business-First Advisory · Security by Design · Strategy to Execution · Emerging Technology Expertise.

### Section 07 — Solutions
Six large cards: CyberSecure 360 · GRC 360 · AI Governance 360 · Digital Transformation 360 · Executive Technology Advisory · Board Cybersecurity & AI Advisory. (vCISO is deliberately absent — C-04.)

### Section 08 — Assessment engine
**Dark section.** The commercial engine of the page.

> **How ready is your organization?**
> Evaluate your cybersecurity, governance, AI and digital transformation readiness in 10–15 minutes. Get your score immediately.

Four cards → Cybersecurity Readiness · GRC Maturity · AI Governance Readiness · Digital Transformation Readiness. "Get your score immediately" is load-bearing copy — it is the C-15 resolution made visible.

### Section 09 — Insights
Three latest articles. Does not render below eight published articles (C-20).

### Section 10 — Final CTA
Dark, 360–450px.

> **Ready to secure, transform and govern your organization?**
> Let's discuss your technology priorities and risks.
> `[Schedule a Consultation]`

---

## 7. CMS CONTENT MODEL

Six collections plus global singletons. Fields marked `*` are required; `[GATED]` fields are nullable and render conditionally.

### 7.1 `service`

| Field | Type | Notes |
|---|---|---|
| `title`* | string | |
| `slug`* | slug | unique, immutable after publish |
| `navLabel` | string | falls back to `title` |
| `eyebrow` | string | |
| `heroHeadline`* | string | ≤ 12 words |
| `heroSubhead`* | text | ≤ 30 words |
| `heroImage`* | image + alt* | |
| `primaryCta`* | ref → `cta` | |
| `secondaryCta` | ref → `cta` | |
| `problemStatement`* | portable text | |
| `capabilities`* | array of `{icon, title, description}` | 6–10 items |
| `methodology` | array of `{step, title, description}` | ordered |
| `deliverables` | array of string | |
| `outcomes` | array of `{metric, label}` | |
| `frameworks` | array of ref → `framework` | |
| `relatedIndustries` | array of ref → `industry` | |
| `relatedSolution` | ref → `solution` | |
| `faqs` | array of `{question, answer}` | drives FAQPage schema |
| `relatedAssessment` | ref → `assessment` | |
| `seo`* | object | see 7.7 |

### 7.2 `industry`
`title*`, `slug*`, `heroHeadline*`, `heroSubhead*`, `heroImage*`, `challenges*[]`, `riskLandscape`, `capabilities*[]`, `relevantServices*[]`, `useCases[]`, `regulatoryConsiderations[]`, `caseStudies[]`, `insights[]`, `cta*`, `seo*`

### 7.3 `solution`
`name*`, `slug*`, `promise*` (3–5 words), `description*`, `components*[]`, `deliverables*[]`, `idealFor[]`, `relatedServices[]`, `tiers[]` *(scope only, no pricing — C-16)*, `cta*`, `seo*`

### 7.4 `insight`
`title*`, `slug*`, `category*` (enum: Cybersecurity · GRC · AI Governance · Digital Transformation · Technology Strategy · Executive Briefings), `contentType*` (enum: Article · Executive Brief · White Paper · Research · Checklist · Webinar · Video), `author*` → `person`, `publishedAt*`, `updatedAt`, `readingTime` *(computed)*, `heroImage*`, `excerpt*`, `executiveSummary`, `body*`, `keyTakeaways[]`, `relatedServices[]`, `relatedInsights[]`, `cta`, `seo*`

### 7.5 `resource`
`title*`, `slug*`, `resourceType*` (Guide · White Paper · Report · Checklist · Webinar · Capability Statement), `description*`, `coverImage*`, `gated*` (boolean), `file*`, `formVariant`, `relatedServices[]`, `nurtureTag*`, `seo*`

### 7.6 `caseStudy`
`title*`, `slug*`, `sector*`, `clientName` *[GATED]*, `anonymized*` (boolean), `challenge*`, `businessContext*`, `approach*`, `servicesUsed*[]`, `implementation*`, `results[]` → `{metric, direction, label, methodology*}` *[GATED — C-10]*, `frameworks[]`, `lessons`, `approvalStatus*` (enum: Draft · Client Review · **Approved for Publication**), `permissionEvidence*` (file, required before publish), `seo*`

**Publication gate:** an editor cannot set `approvalStatus = Approved` unless `permissionEvidence` is attached and every `results[].methodology` is non-empty. Enforce this in the CMS schema as a validation rule, not as a process note.

### 7.7 Shared objects

`seo`: `metaTitle*` (≤60 chars, validated), `metaDescription*` (≤155 chars, validated), `canonicalUrl`, `ogImage`, `noIndex` (boolean), `targetKeyword`, `schemaType`

`cta`: `label*`, `href*`, `variant*`, `analyticsId*`

`person`: `name*`, `title*`, `photo`, `bio*`, `expertise[]`, `linkedIn`, `credentials[]` *[GATED — C-11]*

`framework`: `name*`, `abbreviation`, `logo`, `description`, `applicability[]`

### 7.8 Singletons
`siteSettings` (nav structure, footer, social, contact, feature flags including `logoStripEnabled`, `searchEnabled`, `insightsEnabled`), `legalPages`, `governmentProfile` *(UEI, CAGE, NAICS[], contract vehicles — all [GATED], C-17)*

---

## 8. FORMS AND API CONTRACTS

### 8.1 Endpoints

| Endpoint | Method | Purpose |
|---|---|---|
| `/api/lead/contact` | POST | General contact and consultation requests |
| `/api/lead/download` | POST | Gated resource download |
| `/api/lead/newsletter` | POST | Subscription |
| `/api/assessment/submit` | POST | Score computation, ungated |
| `/api/assessment/report` | POST | Gated PDF + CRM write |

### 8.2 Contact payload

```json
{
  "firstName": "string, required, 1..80",
  "lastName": "string, required, 1..80",
  "businessEmail": "string, required, RFC5322, business-domain enforced",
  "phone": "string, optional, E.164",
  "company": "string, required, 1..120",
  "jobTitle": "string, optional",
  "industry": "enum, required",
  "companySize": "enum: 1-50|51-250|251-1000|1001-5000|5000+",
  "serviceInterest": "enum[], required, min 1",
  "engagementType": "enum: assessment|advisory|project|fractional|training|partnership",
  "timeframe": "enum: immediate|30-90d|3-6m|planning",
  "projectDescription": "string, required, 20..2000",
  "referralSource": "string, optional",
  "consent": "boolean, required, must be true",
  "turnstileToken": "string, required",
  "utm": { "source": "", "medium": "", "campaign": "", "term": "", "content": "" },
  "pageUri": "string",
  "sessionId": "uuid"
}
```

### 8.3 Validation rules

**Business-email enforcement** (S1 §41). Reject disposable-domain providers via a maintained blocklist. Free consumer providers (gmail, outlook, yahoo, icloud) are **accepted but flagged** `emailQuality: "consumer"` and score −5 (§10) — outright rejection loses legitimate SME and government-contractor leads who genuinely use consumer mail.

**Server-side validation is authoritative.** Client-side validation is a UX convenience only; every rule is re-run server-side. Never trust a hidden field or a client-computed score.

**Spam control, layered:** Cloudflare Turnstile (privacy-preserving, no user interaction) → honeypot field → time-to-submit floor of 3 seconds → rate limit 5 submissions per IP per hour → server-side content heuristics. Do **not** use reCAPTCHA v2 image challenges: they are an accessibility failure and a conversion tax on exactly the senior audience being targeted.

**Error presentation** (WCAG 3.3.1, 3.3.3): errors appear inline beneath the field, are linked by `aria-describedby`, are announced via `aria-live="polite"`, describe the fix rather than the failure ("Enter your work email address" not "Invalid input"), and never rely on red alone.

### 8.4 Response contract

```json
{ "ok": true,  "leadId": "uuid", "redirect": "/thank-you/?t=consultation" }
{ "ok": false, "errors": [{ "field": "businessEmail", "code": "DISPOSABLE_DOMAIN", "message": "..." }] }
```

### 8.5 Post-submission sequence

1. Validate server-side → 2. Deduplicate against CRM by email → 3. Create/update contact → 4. Apply lifecycle stage and tags → 5. Compute lead score (§10) → 6. Assign owner if score ≥ 30 → 7. Enqueue transactional email → 8. Enrol in nurture sequence → 9. Emit `form_submit` + conversion event → 10. Redirect to `/thank-you/`.

Steps 3–8 run asynchronously via queue. **The user's redirect never waits on the CRM.** If HubSpot is unavailable the submission is persisted to a durable queue and retried with exponential backoff — a lead is never lost to a third-party outage, and the user never sees a spinner because of one.

---

## 9. ASSESSMENT ENGINE

The highest-value asset on the site (S1 §33). Four products, one engine.

### 9.1 Products

| Product | Slug | Domains | Questions | Duration |
|---|---|---|---|---|
| Cybersecurity Readiness | `cybersecurity` | 10 | 25 | 10–15 min |
| GRC Maturity | `grc` | 8 | 20 | 10–15 min |
| AI Governance Readiness | `ai-governance` | 10 | 25 | 10–15 min |
| Digital Transformation Readiness | `digital-transformation` | 10 | 25 | 10–15 min |

**Domains — Cybersecurity:** Governance · Risk · Identity · Infrastructure · Applications · Data · Incident Response · Awareness · Third Party · Resilience

**Domains — GRC:** Governance · Policies · Risk · Controls · Compliance · Audit · Third Party · Reporting

**Domains — AI Governance:** Governance · Leadership · AI Inventory · Risk Management · Data · Security · Privacy · Human Oversight · Vendor Management · Monitoring

**Domains — Digital Transformation:** Strategy · Leadership · Process · Technology · Data · Cloud · People · Architecture · Change · Governance

### 9.2 Question schema

```json
{
  "id": "cyb-gov-01",
  "domain": "governance",
  "weight": 1.5,
  "text": "Does your organization have a documented cybersecurity strategy approved by executive leadership?",
  "helpText": "Approved means formally signed off, not drafted.",
  "options": [
    { "value": 0,   "label": "No documented strategy" },
    { "value": 0.33,"label": "Informal or in draft" },
    { "value": 0.67,"label": "Documented but not formally approved" },
    { "value": 1,   "label": "Documented, approved and reviewed annually" }
  ]
}
```

### 9.3 Scoring algorithm

Per domain:

```
domainScore(d) = 100 × Σ(answerValue × weight) / Σ(weight)     for questions in d
```

Overall:

```
overall = Σ(domainScore(d) × domainWeight(d)) / Σ(domainWeight(d))
```

Rounded half-up to an integer.

**Bands** (resolving C-08 in favour of S1):

| Score | Band | Interpretation |
|---|---|---|
| 0–20 | **Initial** | Ad hoc, undocumented, person-dependent |
| 21–40 | **Developing** | Emerging practices, inconsistent application |
| 41–60 | **Defined** | Documented and repeatable, not yet measured |
| 61–80 | **Managed** | Measured, monitored, governed |
| 81–100 | **Optimized** | Continuously improving, integrated with strategy |

**Strengths** = the three highest-scoring domains ≥ 60. **Priority gaps** = the three lowest-scoring domains < 60, ordered ascending. If fewer than three qualify, render only those that do — never pad.

**Do not skew scores downward to manufacture urgency.** A CISO who scores their organization honestly and gets an implausibly low result discounts the instrument and the firm behind it. The commercial value of the assessment is entirely dependent on its perceived integrity.

### 9.4 Flow and gating (C-15)

```
Landing → Start → Questions (progress "Question 4 of 10", back enabled, state in sessionStorage)
   → Scoring → RESULTS SHOWN IMMEDIATELY, UNGATED
        · overall score + band
        · per-domain bar chart
        · top 3 strengths
        · top 3 priority gaps
   → "Get your full report" → email capture → PDF + CRM + nurture
   → Consultation CTA
```

Scoring runs **server-side**. The client posts answers and receives a result; the question weights and band logic never reach the browser. This is both an IP concern and a data-integrity one — a client-computed score can be trivially forged before it reaches the CRM.

### 9.5 Report and recommendation mapping

Each domain below 60 maps to a service recommendation:

| Weakest domain | Recommended service | CTA |
|---|---|---|
| Governance, Leadership | `/services/it-governance/` | Discuss Your Governance Requirements |
| Risk, Third Party | `/services/grc/` | Assess Your GRC Maturity |
| Identity, Infrastructure, Applications, Data | `/services/cybersecurity/` | Request a Cybersecurity Assessment |
| Incident Response, Resilience | `/solutions/cybersecure-360/` | Request CyberSecure 360 |
| AI Inventory, Human Oversight, Monitoring | `/services/ai-governance/` | Request an AI Governance Workshop |
| Cloud, Architecture, Technology | `/services/digital-transformation/` | Discuss Your Transformation Roadmap |
| Awareness | `/services/cybersecurity/#awareness` | Discuss Security Awareness |

PDF is generated server-side, branded, and includes methodology and band definitions.

---

## 10. LEAD SCORING AND CRM

### 10.1 Scoring model (S1 §43, extended)

| Signal | Points |
|---|---|
| Homepage visit | 1 |
| Service page view | 3 |
| Three or more service pages | +5 |
| Pricing/engagement section viewed | 5 |
| Resource download | 5 |
| Assessment started | 10 |
| Assessment completed | 15 |
| Assessment report requested | 5 |
| Capability statement downloaded | 15 |
| Consultation requested | 30 |
| Business email domain | +5 |
| Consumer email domain | −5 |
| Company size 251+ | +5 |
| Timeframe "immediate" | +10 |
| Job title contains CISO/CIO/CTO/VP/Director/Chief | +10 |
| No activity for 30 days | −10 (decay, floor 0) |

### 10.2 Thresholds

| Range | Stage | Action |
|---|---|---|
| 0–14 | Marketing contact | Nurture only |
| 15–29 | MQL | Nurture + sales visibility |
| 30+ | SQL | Owner assigned, follow-up task, 24h SLA |

### 10.3 CRM fields

`leadSource`, `firstTouchChannel`, `lastTouchChannel`, `serviceInterest[]`, `industry`, `companySize`, `engagementType`, `timeframe`, `assessmentType`, `assessmentScore`, `assessmentBand`, `weakestDomains[]`, `leadScore`, `lifecycleStage`, `owner`, `estimatedOpportunity`, `salesStage`, `nextAction`, `utm*`

Assessment results written to the CRM are the single most valuable sales artifact the site produces: a salesperson opens the record and already knows which three domains the prospect is weakest in.

### 10.4 Nurture example (S3 §30)

AI Governance Guide download → Day 0 "Your AI Governance Guide" · Day 2 "Five AI governance risks organizations miss" · Day 5 "Does your organization have an AI inventory?" · Day 8 "How mature is your AI governance?" (→ assessment) · Day 12 "Request an AI Governance Readiness Consultation".

Every sequence exits immediately on consultation request. Nothing is more damaging than a prospect who has booked a meeting continuing to receive top-of-funnel nurture email.

---

## 11. SEO SPECIFICATION

### 11.1 Content clusters

Five authority clusters (S1 §61), each a hub page with supporting articles linking up to it:

1. **Cybersecurity** — Cybersecurity Consulting → Cyber Risk · Assessment · vCISO · Security Governance · Incident Response
2. **GRC** — GRC Consulting → IT Governance · Technology Risk · Compliance · Controls · Audit Readiness
3. **AI Governance** — AI Governance → Responsible AI · AI Risk · AI Security · AI Policy · AI Assessment
4. **Digital Transformation** — Digital Transformation → IT Strategy · Cloud · Enterprise Architecture · Automation · Modernization
5. **Executive Advisory** — Technology Advisory → Board Advisory · CIO/CTO Advisory · Due Diligence · Technology Investment

### 11.2 Per-page requirements

Unique `title` (≤60 chars) · unique `meta description` (≤155) · self-referencing `canonical` · exactly one `H1` · logical H2/H3 outline with no skipped levels · Open Graph + Twitter cards · JSON-LD · descriptive internal anchor text (never "click here" or "learn more" as the sole anchor).

### 11.3 Structured data

| Scope | Type |
|---|---|
| Global | `Organization` + `WebSite` |
| All pages | `BreadcrumbList` |
| Service pages | `Service` with `provider`, `areaServed: US`, `serviceType` |
| Articles | `Article` with `author`, `datePublished`, `dateModified` |
| FAQ blocks | `FAQPage` |
| Case studies | `Article` |
| Contact | `ContactPage` |
| Leadership | `Person` |

Validate every template against Schema.org and Google's Rich Results Test before launch. Never mark up content that is not visible on the page.

### 11.4 Technical

`sitemap.xml` auto-generated and split by type · `robots.txt` allowing all indexable content, disallowing `/api/`, `/thank-you/`, assessment result URLs · `noindex` on thank-you and result pages · no orphan pages · every Phase 1 page reachable within three clicks of the homepage · hreflang not required (single locale, `en-US`).

---

## 12. ACCESSIBILITY — WCAG 2.2 AA

**Contractual target: WCAG 2.2 Level AA** (resolving C-18). Lighthouse is a smoke test, never evidence.

### 12.1 Requirements

| Area | Requirement | SC |
|---|---|---|
| Contrast | 4.5:1 body, 3:1 large text and UI components — all tokens pre-verified in §4.1 | 1.4.3, 1.4.11 |
| Keyboard | Every function operable by keyboard, no traps, logical order | 2.1.1, 2.1.2 |
| Focus | Visible indicator, ≥2px, ≥3:1 against adjacent colour, never obscured by sticky header or mobile CTA | 2.4.7, **2.4.11** |
| Target size | ≥24×24px minimum, 44×44px for primary actions | **2.5.8** |
| Headings | Semantic, sequential, one H1 | 1.3.1, 2.4.6 |
| Images | Meaningful `alt`; `alt=""` for decorative; no text baked into images | 1.1.1 |
| Forms | Programmatic labels, `aria-describedby` errors, clear instructions, no reliance on placeholder-as-label | 1.3.1, 3.3.1, 3.3.2 |
| Motion | `prefers-reduced-motion` honoured throughout | 2.3.3 |
| Colour | Never the sole carrier of meaning | 1.4.1 |
| Zoom | Usable at 200% and at 320px width with no horizontal scroll | 1.4.4, 1.4.10 |
| Language | `lang="en-US"` | 3.1.1 |
| Video | Captions and transcripts | 1.2.2 |
| Consistency | Consistent navigation and identification | 3.2.3, 3.2.4 |
| Help | Consistent help mechanism placement | **3.2.6** |
| Auth | No cognitive-function test without alternative — Turnstile satisfies this, image CAPTCHAs do not | **3.3.8** |

Bold SC numbers are 2.2 additions absent from 2.1 and commonly missed.

### 12.2 Specific traps in this design

- **Sticky header vs focus (2.4.11):** a focused element scrolled beneath a sticky header is a failure. Apply `scroll-margin-top` equal to header height on every focusable target.
- **Mobile sticky CTA vs form fields (S1 §46):** the persistent bottom CTA must hide when a form field has focus, or it will cover the input and the error message on small viewports.
- **Mega-menu:** must be operable by keyboard with Escape to close and focus returned to the trigger. A hover-only mega-menu is a 2.1.1 failure.
- **Assessment progress:** communicate "Question 4 of 10" as text, not as a bar alone, and announce transitions via `aria-live`.
- **Horizontal industry scroller:** must be keyboard-scrollable and not trap focus.

### 12.3 Verification

axe-core in CI as a merge gate · manual keyboard traversal of every template · NVDA/Windows and VoiceOver/macOS spot checks · 200% zoom and 320px width · macOS/Windows high-contrast mode · published accessibility statement at `/legal/accessibility/`.

---

## 13. TECHNOLOGY STACK

The source documents defer this decision (C-12, C-13). Here it is, with reasoning — because for this client the stack *is* part of the pitch. A cybersecurity and governance consultancy is judged on the security posture of its own property.

### 13.1 Recommended stack

| Layer | Recommendation | Why |
|---|---|---|
| **Framework** | **Astro 5** | Static-first with islands. Ships zero JS by default, so Lighthouse 90+ is the baseline rather than a tuning exercise. Typed content collections give compile-time safety over CMS data. Interactive islands (assessment runner, mega-menu) hydrate individually. |
| **CMS** | **Sanity** | Schema-as-code (versioned in git, reviewable in PRs), real structured content rather than a page-builder blob, strong reference integrity for the cross-linking this IA depends on, and custom validation — which is how the C-10 case-study publication gate becomes enforceable rather than a policy document. |
| **Hosting / edge** | **Cloudflare Pages + Workers** | WAF, bot management, rate limiting, DDoS absorption, HSTS and CSP via `_headers`, Turnstile — all first-party, no plugin chain. Workers host the API routes next to the origin. |
| **CRM + automation** | **HubSpot** (Marketing Pro + Sales Starter) | Native lead scoring, nurture, forms API, and **Meetings**, which satisfies the scheduling requirement (S2 §50) without a fifth vendor. One integration instead of four means less glue code and fewer failure modes. |
| **Assessment engine** | **Custom, on Workers + D1** | The scoring model is the intellectual property and must stay server-side (§9.4). Third-party quiz SaaS cannot deliver server-side scoring, branded PDF reports, CRM writeback of per-domain scores, and CSP compliance simultaneously. |
| **PDF generation** | `@react-pdf/renderer` in a Node function | Deterministic, templatable, no headless-browser attack surface. |
| **Analytics** | **GA4** + Cloudflare Web Analytics | GA4 for the funnel; Cloudflare cookieless as the pre-consent baseline so traffic data survives consent rejection. |
| **Consent** | **Cookiebot** with Consent Mode v2 | CPRA and GDPR coverage; blocks tags pre-consent rather than post-hoc. |
| **Search** (Phase 2) | **Pagefind** | Static index, no server, no vendor, no CSP entry. |
| **Repo / CI** | GitHub + Actions | Lighthouse CI, axe-core, link checker and schema validation as merge gates. Dependabot on. |

### 13.2 Why not WordPress

It will be proposed, so the reasoning should be on record. WordPress powers a large share of the web and its plugin ecosystem is the single largest source of web application CVEs. A firm selling cybersecurity, third-party risk management and governance, running a public site on a PHP plugin supply chain it does not control, invites exactly the question it least wants asked in a sales cycle. The static-first alternative has no database to inject, no admin login on the public origin, and no plugin auto-update to monitor. **The site's own architecture becomes a talking point in the sales conversation instead of a liability.**

Sanity's editing experience is at least as good as the WordPress block editor for structured content of this kind, and the content model in §7 is genuinely structured — it is not a set of documents with a WYSIWYG field.

### 13.3 Security controls (S1 §57)

TLS 1.3, HSTS with preload · CSP with nonces, `default-src 'self'`, no `unsafe-inline` · `X-Content-Type-Options: nosniff` · `Referrer-Policy: strict-origin-when-cross-origin` · restrictive `Permissions-Policy` · SRI on any third-party script · CSRF tokens on state-changing routes · rate limiting · Turnstile · secure/`HttpOnly`/`SameSite=Lax` cookies · SPF, DKIM and DMARC (`p=reject`) · automated dependency scanning · MFA mandatory on every admin account · audit logging on CMS publish events · daily backups with a tested restore procedure.

Publish a `security.txt` at `/.well-known/security.txt`. For this client it costs nothing and signals competence to precisely the audience being sold to.

### 13.4 Performance budget

| Metric | Target |
|---|---|
| LCP | < 2.0s (budget 2.5s) |
| INP | < 200ms |
| CLS | < 0.05 |
| Total JS (initial) | < 100KB gzipped |
| Total page weight | < 1.2MB |
| Lighthouse Performance | ≥ 90 mobile, ≥ 95 desktop |
| Lighthouse SEO | ≥ 95 |
| Lighthouse Best Practices | ≥ 95 |

Enforced by Lighthouse CI on every PR against mobile throttling. Regressions block merge.

---

## 14. ANALYTICS AND MEASUREMENT

### 14.1 Events

`page_view` · `cta_click` (`{location, label, destination}`) · `nav_interaction` · `form_start` · `form_submit` · `form_error` · `assessment_start` (`{type}`) · `assessment_question` (`{type, index}`) · `assessment_complete` (`{type, score, band}`) · `assessment_report_request` · `resource_download` (`{title, type, gated}`) · `consultation_booking` · `newsletter_signup` · `outbound_click` · `scroll_depth` (25/50/75/100) · `search` (Phase 2)

### 14.2 Conversion events

Consultation Submitted · Assessment Completed · Assessment Report Requested · Resource Downloaded · Capability Statement Downloaded · Contact Submitted · Newsletter Signup.

`assessment_question` with an index is the diagnostic event that matters most: it shows exactly which question people abandon on, which is the fastest route to improving assessment completion rate — the metric the whole funnel hangs on.

### 14.3 KPIs (S3 §39)

**Traffic:** organic sessions, LinkedIn referral, direct, branded vs non-branded queries.
**Engagement:** assessment start rate, assessment completion rate, resource download rate, scroll depth on service pages.
**Leads:** MQLs, SQLs, discovery meetings booked, meeting show rate.
**Revenue:** pipeline value, win rate, average deal value, recurring (vCISO) revenue, CAC.
**Retention:** repeat engagements, cross-sell, referrals.

---

## 15. BUILD SEQUENCE

| Sprint | Scope | Exit criteria |
|---|---|---|
| **0 — Foundations** | Repo, CI, design tokens, type scale, grid, Sanity schemas, Cloudflare config, security headers | Storybook renders all tokens; axe + Lighthouse CI green on a blank page |
| **1 — Shell & conversion** | Header, MegaMenu, MobileDrawer, Footer, CTAButton, Hero, LeadForm, Contact, Consultation booking, thank-you, legal pages | Full keyboard traversal passes; a lead reaches HubSpot end-to-end |
| **2 — Homepage & About** | Homepage all 10 sections, About, CISOG Group, Leadership, Why CISOG, Our Approach | Homepage at Lighthouse ≥90 mobile; WCAG audit passes |
| **3 — Revenue services** | Services hub + Cybersecurity, vCISO, GRC, IT Governance, AI Governance *(flagship treatment)*, Digital Transformation, Technology Advisory | All service templates CMS-driven; schema validates |
| **4 — Segmentation** | Industries hub, Financial Services, SMEs, Government + capability statement, Solutions hub | Government page renders correctly with all [GATED] fields empty |
| **5 — Demand generation** | Insights hub + article template + 8 articles, Resources hub, Client Success (empty state), gated download flow, nurture sequences | 8 articles live (C-20); download → CRM → nurture verified |
| **6 — Assessment engine** | Runner, scoring service, results, PDF report, CRM writeback, 4 question banks | Scoring verified against hand-calculated fixtures; server-side only |
| **7 — Launch hardening** | Full WCAG audit, penetration test, performance tuning, redirect map, analytics QA, content freeze, UAT | §17 checklist fully signed off |

Phase 2 (post-launch): global search, webinars, CISOG Academy interest capture, gated research, case-study library, Board Advisory, Executive Advisory, remaining industries, Careers.

Phase 3: partner portal, client portal, AI-assisted recommendation layer, full LMS.

---

## 16. CONTENT REQUIREMENTS AT LAUNCH

| Asset | Quantity | Owner | Blocker? |
|---|---|---|---|
| Page copy, 24 pages | 24 | Client + copywriter | **Yes** |
| Insight articles | 8 | Client SME | **Yes** (C-20) |
| Lead magnets (guides) | 3 minimum | Client SME | **Yes** — the download flow needs something to download |
| Leadership profiles + photography | All named | Client | **Yes** |
| Hero and section imagery | ~20 | Design | **Yes** |
| Capability statement PDF | 1 | Client | Yes for `/government/` |
| Case studies | 0 acceptable | Client | No (C-10) |
| Client / partner logos | 0 acceptable | Client | No (C-11) |
| Legal pages | 4 | **U.S. counsel** | **Yes** |

The three lead magnets map to the three strongest clusters: Cybersecurity Readiness Guide, AI Governance Guide, and "Does Your Organization Need a vCISO?".

---

## 17. ACCEPTANCE CRITERIA

A page is accepted when every item passes.

**Content**
☐ One H1, sequential headings · ☐ Unique title ≤60 and description ≤155 · ☐ Self-referencing canonical · ☐ Exactly one dominant CTA · ☐ Every `[GATED]` field empty or verified · ☐ No placeholder or lorem text · ☐ No unverified claim or metric

**Design**
☐ Matches token system, zero hardcoded colours · ☐ Type scale respected · ☐ Grid and spacing scale respected · ☐ Renders at 1440 / 1280 / 1024 / 768 / 390 / 320 · ☐ All component states implemented · ☐ Empty states implemented

**Accessibility**
☐ axe-core: zero violations · ☐ Full keyboard traversal, no traps · ☐ Focus visible and never obscured (2.4.11) · ☐ Targets ≥24×24, primary ≥44×44 (2.5.8) · ☐ Screen-reader pass · ☐ 200% zoom and 320px, no horizontal scroll · ☐ `prefers-reduced-motion` honoured · ☐ Contrast verified against §4.1

**Performance**
☐ LCP <2.5s mobile · ☐ CLS <0.05 · ☐ INP <200ms · ☐ Lighthouse Perf ≥90 / SEO ≥95 / BP ≥95 · ☐ Images AVIF/WebP with dimensions · ☐ No render-blocking third-party script

**Technical**
☐ JSON-LD validates · ☐ No broken internal links · ☐ Security headers present · ☐ CSP with no `unsafe-inline` · ☐ Forms validate server-side · ☐ Analytics events fire correctly · ☐ CMS-driven, no hardcoded content

**Conversion**
☐ CTA reaches the correct destination · ☐ Form submits to CRM · ☐ Lead scored correctly · ☐ Nurture enrolment fires · ☐ Thank-you page contextual

---

## 18. GATED ITEMS — CLIENT ACTION REQUIRED

Nothing below can be resolved by the design or development team. Each blocks a specific deliverable.

| # | Item | Blocks | Owner |
|---|---|---|---|
| G-01 | U.S. LLC formation date and registered address | `/about/`, footer, `Organization` schema (C-09) | Client |
| G-02 | Written permission + methodology for the 90% phishing metric and any other outcome figure | All case studies (C-10) | Client |
| G-03 | Verified client logos with usage rights | `LogoStrip` (C-11) | Client |
| G-04 | Verified partner/reseller agreements | `/about/partners/` | Client |
| G-05 | Individual certifications and professional memberships | Leadership profiles, trust signals | Client |
| G-06 | UEI, CAGE, NAICS codes, contract vehicles, past performance | `/government/capability-statement/` (C-17) | Client |
| G-07 | Privacy Policy, Terms, Cookie Policy, Accessibility Statement | Launch — **hard blocker** | **U.S. counsel** |
| G-08 | vCISO tier scope definitions (deliverables, cadence, SLA, reporting) | `/services/vciso/` (C-16) | Client |
| G-09 | HubSpot tenancy, domain verification, DNS for SPF/DKIM/DMARC | Sprint 1 | Client |
| G-10 | Leadership photography and approved biographies | `/about/leadership/` | Client |
| G-11 | Eight insight articles | Insights launch (C-20) | Client SME |
| G-12 | Confirmation that CISOG Group content is approved for reference and linking | `/about/cisog-group/` | Client |

**G-07 is the only item that can delay launch on its own.** The others degrade gracefully — every gated field is nullable and every dependent component has a designed empty state. That is deliberate: the build should never be blocked waiting on content that may take weeks to verify.

---

## 19. WHAT CHANGED FROM THE SOURCE DOCUMENTS

For the client's review, the substantive departures:

1. **The twelve duplicate SEO landing pages are not built** (C-06). This is the highest-impact change and the one most likely to be questioned. The reasoning is in C-06.
2. **Government becomes a single top-level page**, not two competing ones (C-05).
3. **Assessment results are ungated; only the report is gated** (C-15). This changes the funnel shape and should lift completion rate materially.
4. **The maturity band contradiction is resolved** in favour of the CMMI-aligned scale (C-08).
5. **The trust strip is designed logo-free** rather than logo-dependent (C-11).
6. **Search, Careers-in-nav, and CISOG Academy move out of Phase 1** (C-19, C-21, C-22).
7. **WCAG 2.2 AA is separated from the Lighthouse score** as a distinct, manually verified target (C-18).
8. **The stack is decided**: Astro + Sanity + Cloudflare + HubSpot (§13), with the case against WordPress recorded.
9. **Insights will not launch below eight articles** (C-20).
10. **"Since 2003" is re-attributed to the Group**, not the U.S. entity (C-09).

---

## 20. PROTOTYPE COVERAGE

The accompanying prototype (`cisog-usa-prototype.html`) is a working build, not a mockup. Thirteen routes, all responsive, all keyboard-operable.

| Route | Template | What it demonstrates |
|---|---|---|
| `#/` | `home` | All ten homepage sections, problem-based router, logo-free trust strip |
| `#/services` | `hub` | Nine-service grid |
| `#/cybersecurity` | `service` | **The master template** — hero, problem, capabilities, methodology, deliverables, outcomes, frameworks, case-study empty state, related industries, FAQ, CTA |
| `#/ai-governance` | `service-flagship` | Bespoke governance diagram and six-stage lifecycle module |
| `#/financial-services` | `industry` | Challenges, risk landscape, priority services, regulatory context |
| `#/government` | `government` | Capability matrix, gated contracting identifiers, past-performance empty state |
| `#/solutions` | `hub` | Six 360 programs, with the vCISO omission explained inline |
| `#/insights` | `insights` | Working category filter with live region announcements |
| `#/article` | `article` | Full editorial template with pull quote, takeaways, next-step module |
| `#/contact` | `contact` | Intent selector, qualifying form, full client-side validation |
| `#/schedule` | `booking` | Four-step stepper with state, back navigation, confirmation |
| `#/assessment` | — | Live weighted scoring across ten domains, ungated result, gated report |
| `#/system` | — | Tokens, contrast table, type scale, grid, motion |

### 20.1 What was verified, and how

Verification was executed against the DOM, not by inspection:

- **Contrast** — all 26 foreground/background pairings computed from WCAG relative luminance. Zero failures. Two failures were found and fixed during the build (see §4.1 note on `--slate-500`, and the `cyan-500` rule).
- **Routing** — all 13 routes resolve to exactly one active view; zero orphan views; zero unroutable link targets.
- **Heading structure** — zero skipped levels across all 13 views; exactly one `<h1>` each. One violation was found on the Services hub (h1 → h3) and fixed by promoting the card headings to `<h2>` while keeping the `.t-h3` visual scale.
- **Forms** — every control has an associated `<label for>`; empty submission produces 7 errors on contact, 3 on booking, 4 on the report gate; consumer email domains are correctly flagged; `aria-invalid` is applied and removed.
- **Assessment scoring** — verified against an independent reimplementation. A mixed answer set produces 64 in both; band, domain ordering, strengths, gaps and service recommendations all correct. Weighted and unweighted results differ, confirming weights are actually applied rather than declared.
- **Keyboard** — mega-menus open on click and close on Escape with focus returned; the mobile drawer does the same; the sticky CTA hides when a form field takes focus (SC 2.4.11 / S1 §46).
- **Graceful degradation** — `matchMedia` and `IntersectionObserver` are feature-detected. Where absent, motion is disabled and all content renders visible rather than stuck at opacity 0.

### 20.2 Deliberate prototype limitations

- Scoring runs client-side for demonstration. **Production must compute server-side** (§9.4) — weights and band logic are IP, and a client-computed score can be forged before it reaches the CRM.
- Secondary service pages route to the Cybersecurity master template rather than duplicating it; the template is the deliverable, not eight copies of it.
- Booking slots are static. Production binds to HubSpot Meetings (§13.1).
- Imagery is represented by SVG and gradient placeholders pending the art direction in §4.6.

---

*End of specification. Version 2.2.*
