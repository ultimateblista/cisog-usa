# CLIENT CHANGE REGISTER — round 2

Sources: *Review of the website — Services*, *Review of the website — Industries*, Privacy Policy PDF, Terms & Conditions PDF, plus the `Downloads/files` asset drop (7 capability statements, 9 service datasheets).

**Status: BUILT AND VERIFIED — 51 automated assertions passed, 0 failures, 0 runtime errors.**

Deployment target changed from Vercel to **cPanel**. Vercel was test-only.

---

## SERVICES — 9 pages built

Every page uses his supplied copy verbatim: H1, intro, section headings, capability descriptions, methodology, framework list, FAQs and CTA labels.

| Route | Page | Datasheet |
|---|---|---|
| `#/services/cybersecurity` | Cybersecurity Consulting | ✅ |
| `#/services/vciso` | Virtual CISO — 3 engagement models | ✅ |
| `#/services/grc` | GRC & IT Governance | ✅ |
| `#/services/it-governance` | IT Governance & Technology Risk | ✅ |
| `#/services/ai-governance-service` | AI Governance & Responsible AI | ✅ |
| `#/services/digital-transformation` | Digital Transformation | ✅ |
| `#/services/technology-advisory` | Technology Advisory | ✅ |
| `#/services/cloud-infrastructure` | Cloud & Infrastructure | ✅ |
| `#/services/software-solutions` | Software & Application Solutions | ✅ |

All nine service datasheets wired, one per page. FAQs rendered as accordions on the seven pages that supplied them.

## INDUSTRIES — hub + 7 pages built

| Route | Page | Copy source | Capability statement |
|---|---|---|---|
| `#/industries` | Hub, 7 cards | Supplied | — |
| `#/industries/financial-services` | Financial Services | Supplied | ✅ |
| `#/industries/government` | Government & Public Sector | Supplied | ✅ |
| `#/industries/smes` | SMEs & Growth Companies | Supplied | ✅ |
| `#/industries/healthcare` | Healthcare | **Capability statement** | ✅ |
| `#/industries/energy-utilities` | Energy & Utilities | **Capability statement** | ✅ |
| `#/industries/manufacturing` | Manufacturing | **Capability statement** | ✅ |
| `#/industries/professional-services` | Professional Services | **Capability statement** | ✅ |

**Government added to the Industries submenu as requested, but kept as one page.** A second Government page would compete with the existing one for the same search term.

### The four duplicated pages — resolved

His Industries document repeated the *same* SME placeholder copy across Healthcare, Energy, Manufacturing and Professional Services, including SME keywords on the Manufacturing page.

Rather than duplicate it or invent replacements, each page was sourced from **his own capability statement for that sector** — real challenge statements, OT/ICS language for Energy, industrial cybersecurity for Manufacturing, client-confidentiality framing for Professional Services, plus each document's "Who We Serve" list. Nothing fabricated.

## LEGAL — 2 pages built

| Route | Source | Sections |
|---|---|---|
| `#/privacy` | Privacy Policy PDF | 14 |
| `#/terms` | Terms & Conditions PDF | 27 |

Full text rendered as real HTML pages with the PDF also downloadable. Footer links wired. **This clears G-07, the one hard launch blocker.**

**Still outstanding: Cookie Policy and Accessibility Statement.** The site sets analytics cookies, so the Cookie Policy has legal weight.

## DEPLOYMENT — switched to cPanel

- `vercel.json` deprecated and gitignored; `_headers` (Cloudflare format) neutralised
- **`.htaccess` rewritten for production** — HTTPS redirect, security headers, compression, caching, hardening, `404 → index.html` for hash routing
- **`robots.txt` now ALLOWS indexing** — this was `Disallow: /` for the review build
- **`sitemap.xml` generated** — 38 URLs
- **Canonical + `og:url`** set to `https://cisogusa.cisoggroup.com`
- Backup files moved out of the served directory
- `DEPLOY-CPANEL.md` written with the upload procedure

## ASSETS

| Group | Count | Note |
|---|---|---|
| Service datasheets | 9 | one per service page |
| Capability statements | 7 | one per industry page |
| Solution datasheets | 7 | unchanged |
| Legal PDFs | 2 | downloadable from their pages |

**vCISO solution datasheet compressed 2.6 MB → 92 KB** with no visible quality loss. It was the heaviest asset on the site.

---

## VERIFICATION

51 assertions, 0 failures:

- All **38 routes** resolve to exactly one view
- **Zero heading-level skips**, exactly one `<h1>` per view
- **Zero broken references** — 37 local links, 32 downloads, all resolve
- Forms, assessment engine, mega-menus, drawer all still functional
- Six dropdown menus, no column headings, logo-only branding

---

## TWO MANUAL STEPS REQUIRED

Both blocked by sandbox file permissions, not by the work:

1. **Delete `.git/index.lock`** — a stale lock from a crashed git process is blocking `git add`. Run `rm cisog-review-site/.git/index.lock`, then commit normally.
2. **Delete `vercel.json`** — neutralised and gitignored, but I could not remove the file.

---

## OPEN QUESTIONS FOR THE CLIENT

1. **Cookie Policy and Accessibility Statement** — the two remaining legal pages.
2. **CISOG Group** *(carried from round 1)* — his document says link out to `cisoggroup.com` but also supplies a full internal page. Currently the external link.
3. **He is reviewing a stale build.** None of round 1 or round 2 has been deployed. His Industries screenshot still shows the text logo and the column headings removed weeks ago.
