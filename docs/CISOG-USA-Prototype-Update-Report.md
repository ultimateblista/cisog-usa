# CISOG USA — PROTOTYPE UPDATE REPORT

**Working prototype, reconciled specification and launch content**
Progress report · 9 August 2026 · For client review

---

## 1. WHERE WE ARE

Your four documents have been consolidated into a single build specification, and a working prototype now covers every Phase 1 page template. Launch content is written.

Three things are ready for your review:

| Deliverable | Status |
|---|---|
| **Working prototype** — 13 routes, responsive, keyboard-operable | Ready for review |
| **Master Build Specification v2.2** — supersedes all four source documents | Ready for review |
| **Insights Content Pack** — nine launch articles | Ready for review |

The prototype is a functioning build rather than a set of images. Navigation works, forms validate, the assessment engine scores. It is intended to be used, not looked at.

**The critical path is no longer design.** It is the verification items in section 5 and the legal pages in section 6. Both sit with you, and both take longer than they appear to.

---

## 2. WHAT HAS BEEN BUILT

### 2.1 The prototype

Thirteen routes, each demonstrating a template that the remaining pages inherit.

| Route | Template | Covers |
|---|---|---|
| `#/` | Home | All ten sections including the problem-based entry point |
| `#/services` | Hub | Nine-practice grid |
| `#/cybersecurity` | **Service master** | The template all eight other service pages inherit |
| `#/ai-governance` | Flagship | Bespoke governance diagram and six-stage lifecycle |
| `#/financial-services` | Industry | Challenges, risk landscape, regulatory context |
| `#/government` | Government | Capability matrix, contracting identifiers, procurement |
| `#/solutions` | Hub | The six 360 programs |
| `#/insights` | Insights | Category filtering |
| `#/article` | Article | Full editorial template |
| `#/contact` | Contact | Intent selector and qualifying form |
| `#/schedule` | Booking | Four-step consultation booking |
| `#/assessment` | Assessment | Working scoring engine |
| `#/system` | Design system | Tokens, contrast verification, type scale, grid |

Only one service page has been built in full. That is deliberate — the template is the deliverable, and eight copies of it would be eight things to maintain when the design changes.

### 2.2 The assessment engine

This works. It is not a demonstration.

Ten weighted questions across ten security domains produce a maturity score, a per-domain breakdown, ranked strengths and priority gaps, and a service recommendation mapped to the weakest domains. The scoring was verified against an independent implementation of the same algorithm — a mixed answer set produces an identical result in both.

**One decision is embedded here that changes the funnel.** Your documents gated the result behind email capture. In the prototype the score, maturity band and priority gaps display immediately, and only the detailed PDF report requires an email address. Reasoning is in section 4.

### 2.3 The design system

A complete token set — colour, type scale, spacing, grid, elevation, motion — with every colour pairing contrast-verified by calculation rather than by eye. Twenty-eight components with defined variants, states and empty states.

The system is visible and browsable at `#/system`, including the contrast table.

### 2.4 Launch content

Nine articles, complete with SEO titles, meta descriptions, target keywords, excerpts, key takeaways and calls to action. Supplied as a Word document for review and as a JSON file that imports directly into the content management system without retyping.

---

## 3. HOW TO REVIEW IT — FIFTEEN MINUTES

Open the HTML file in any modern browser. There is nothing to install.

**Start at `#/cybersecurity`.** This is the template that matters most, because eight other service pages will inherit it. Read it as a prospect would: does it move you from *these people understand the problem* to *I should talk to them*?

**Then `#/assessment`.** Complete it honestly — it takes about four minutes. Watch what happens at the end. The score appearing without an email request is the single most consequential funnel decision in the build.

**Then `#/government`.** Note that the contracting identifiers read *Pending verification* rather than being hidden. That is intentional and explained in section 5.

**Then resize the window,** or open it on your phone. Every breakpoint is built.

**Finally `#/system`,** if you want to see the underlying rigour — particularly the contrast table.

Two things to look at with a critical eye, because they are where taste matters more than correctness: the hero treatment on the homepage, and the density of the service page. Both are defensible as built and both are legitimately arguable.

---

## 4. WHERE WE DEPARTED FROM YOUR DOCUMENTS

Your four documents contained twenty-two points of conflict or duplication. Most were resolved mechanically. Three are judgement calls that change commercial outcomes, and you should have the opportunity to disagree with them.

### 4.1 We did not build the twelve duplicate SEO landing pages

Your documents specify both `/cybersecurity-consulting/` and `/services/cybersecurity/`, and eleven similar pairs.

**We built one page per topic** and registered the others as redirects.

Two near-identical pages targeting the same query compete against each other in the index. Inbound links and internal links are split between them, and the search engine selects which to show — a selection you do not control. Keyword-in-URL is a weak ranking signal relative to page content, title and the anchor text of links pointing at it. Concentrating everything on one strong page is materially more effective than dividing it across two.

This is the largest single departure from your documents and the one most likely to warrant discussion.

### 4.2 Assessment results are shown before the email request

Your documents place email capture between completion and result.

**The score, band and top three gaps now display immediately.** Email is required only for the detailed report.

Asking a CISO for fifteen minutes and then withholding the outcome produces two results: high abandonment at the final step, and a meaningful proportion of deliberately false email addresses from those who continue. Both damage the asset. The score is the hook; the report is the thing worth exchanging an address for. This also removes any tension with describing the assessments as free.

### 4.3 Government is one page, not two

Your documents specify both `/industries/government/` and a top-level `/government/` hub with overlapping content.

**One page, at `/government/`.** Public sector buyers evaluate differently — capability statement, registration identifiers, past performance, contract vehicles — and that deserves a distinct treatment rather than an industry page with procurement content appended.

---

## 5. WHAT NEEDS YOUR VERIFICATION

These are stated plainly because each one carries real exposure if it ships unexamined. None reflects on the quality of the underlying business; all are normal for an entity establishing a U.S. presence.

### 5.1 "Since 2003" is attributed to the wrong legal entity

Your documents place *Since 2003* in the homepage trust strip. That date belongs to the CISOG Group. CISOG Technology Consults LLC is a U.S. entity with its own, later formation date.

An unqualified founding-date claim attached to the U.S. entity is a misrepresentation risk under FTC advertising rules, and more practically it is the kind of assertion a procurement officer or a competitor checks against state incorporation records.

**Built as:** *"Part of the CISOG Group — operating internationally since 2003."* Accurate, and it retains the credibility the original was reaching for.

**Needed from you:** the LLC formation date and registered address, so `/about/` can state the U.S. position correctly and separately.

### 5.2 The 90% phishing reduction cannot be published yet

Your documents cite a 90% reduction in phishing click rates over three months for a fintech engagement. That is a strong, specific and commercially valuable outcome — which is exactly why it cannot be published without support.

A cybersecurity consultancy publishing a security metric will be asked how it was measured. Baseline, population, simulation methodology, and whether the comparison periods were equivalent. If the answer is not immediately available, the claim damages more credibility than it builds.

**Needed from you:** the measurement methodology in writing, and the client's written permission to publish — named or anonymised.

**If it cannot be obtained,** nothing breaks. The case study section has a designed empty state, visible at `#/cybersecurity`, which explains that outcomes are published only when verified. That position is itself a credibility signal to this audience.

### 5.3 No logos, certifications or partnerships are shown

Your documents call for client logos, partner logos and certifications, while also cautioning against publishing them before verification.

**The trust strip is built to work with none of them.** This was a design constraint, not an omission — a strip designed around six logo slots looks broken with zero, and adding logos later is straightforward.

**Needed from you:** verified client logos with written usage rights, confirmed partner or reseller agreements, and individual certifications with the issuing body and current status.

### 5.4 Government contracting identifiers are unverified

UEI, CAGE code, NAICS codes and contract vehicles all appear in your capability statement outline.

**Built as:** visible fields reading *Pending verification*, so the page is complete without them and complete with them.

**Needed from you:** the identifiers, once SAM.gov registration is confirmed. Publishing an unverified UEI to a procurement audience is among the faster ways to lose a public-sector opportunity.

### 5.5 Legal pages require U.S. counsel

Privacy Policy, Terms of Use, Cookie Policy and an Accessibility Statement.

**This is the only item that can delay launch on its own.** Everything else in this section degrades gracefully. These cannot — the site collects personal data through forms, assessments and downloads from the day it goes live, and the privacy policy must reflect what is actually collected, where it is stored and who processes it.

We can supply your counsel with a precise description of every data flow to work from, which shortens their task considerably. Instructing them early is the single most useful thing that can happen this month.

---

## 6. DECISIONS WE NEED FROM YOU

Four. Two unblock further build work immediately.

### Decision 1 — Design direction · requested by Friday 14 August

Confirm the visual direction, the six-item navigation model, and the six flagship practices.

Everything built from here inherits these. Changing them after the remaining pages are built is expensive; changing them now costs nothing.

**We need:** approve, approve with comments, or a conversation.

### Decision 2 — The three departures in section 4 · requested by Friday 14 August

Confirm or challenge the single-page SEO structure, the ungated assessment result, and the consolidated Government page.

We believe each is right and have given the reasoning. If you disagree, now is the point at which reversal is inexpensive.

### Decision 3 — Verification items · dates below

| Item | Needed by | Why that date |
|---|---|---|
| Instruct U.S. counsel on the four legal pages | **This week** | Longest lead time; the only hard launch blocker |
| LLC formation date and registered address | 21 August | Required for `/about/` and organisation metadata |
| HubSpot access and DNS for email authentication | 21 August | Blocks the lead capture build |
| vCISO tier definitions — scope, cadence, reporting | 21 August | Blocks the vCISO page, the highest-value commercial page |
| Leadership photographs and approved biographies | 28 August | Blocks the leadership page |
| Phishing metric evidence and permission | When available | Nothing breaks without it |
| Client and partner logos, certifications | When available | Nothing breaks without it |
| SAM.gov identifiers | When available | Nothing breaks without it |

### Decision 4 — Article length · requested by 21 August

The nine launch articles run about three minutes each. Written deliberately short for an executive audience that does not finish long-form content.

The trade-off: competing pages on the same search terms often run considerably longer, so the harder informational rankings may take longer to reach.

**Our recommendation** is to publish at this length and measure for two quarters. If the clusters are not ranking, extend with worked examples and sector variations rather than padding.

**We need:** confirmation of the length and the voice. Read any two of the articles — that is enough to judge both.

---

## 7. WHAT HAPPENS NEXT

On confirmation of decisions 1 and 2, work continues on:

- Remaining service pages, built from the approved master template
- The vCISO page, once tier definitions arrive
- About, CISOG Group, Leadership, Why CISOG and Our Approach
- The three remaining assessment question banks — GRC, AI Governance, Digital Transformation
- Three lead magnets — Cybersecurity Readiness Guide, AI Governance Guide, and *Does Your Organization Need a vCISO?*

None of this is blocked today. All of it is faster with design direction confirmed.

---

## 8. A NOTE ON HOW THE SITE ITSELF IS BUILT

One point worth raising, because it is unusual to treat as a commercial matter.

The recommended stack is a statically generated site on an edge platform with a headless content management system — rather than WordPress. WordPress is capable and familiar, and its plugin ecosystem is the single largest source of web application vulnerabilities.

For most organizations that is an acceptable trade. For a firm selling cybersecurity, third-party risk management and governance, it invites a question you would rather not be asked in a sales cycle: *how do you manage the supply chain risk on your own public-facing property?*

The recommended architecture has no database to attack, no administrative login on the public origin, and no plugin update cycle to monitor. It also produces measurably faster pages, which helps search performance.

**The point is that your own site becomes a demonstration of the thing you are selling** rather than something you would prefer prospects did not examine closely. Full reasoning is in §13.2 of the specification.

---

## APPENDIX — DOCUMENTS IN THIS RELEASE

| Document | Purpose |
|---|---|
| `cisog-usa-prototype.html` | Working prototype — open in any browser |
| `CISOG-USA-Master-Build-Spec.docx` | Full specification, v2.2 — supersedes all four source documents |
| `CISOG-USA-Insights-Content-Pack.docx` | Nine launch articles with SEO metadata |
| `cisog-insights-cms-import.json` | The same articles, structured for direct CMS import |
| `CISOG-USA-Prototype-Update-Report.docx` | This report |

Section references throughout are to the Master Build Specification. Conflict references (C-01 to C-22) and gate references (G-01 to G-12) are catalogued in §1 and §18 of that document.
