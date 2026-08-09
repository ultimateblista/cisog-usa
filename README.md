# CISOG USA — review site deployment

**Push to `main` → live in seconds. No manual uploading.**

This repository is configured for three hosts. Pick one now, switch later without changing anything but where the repo is connected.

| Host | Setup | Cost for this use | Password protection |
|---|---|---|---|
| **Cloudflare Pages** | ~3 min | Free, commercial use permitted | Free, up to 50 people |
| **Vercel** | ~3 min | **Pro, $20/mo** — see below | $150/mo add-on |
| **cPanel via FTPS** | ~20 min | Included in existing hosting | Free, built into cPanel |

---

## READ THIS BEFORE CHOOSING VERCEL

Vercel works perfectly for this and takes three minutes. There is one commercial detail worth knowing.

**Vercel's Hobby plan does not permit commercial use.** Their fair-use guidance lists *being paid to create or host the site* as an example of commercial usage. A client prototype you are being paid to produce falls inside that definition, so the correct plan is **Pro at $20 per month per seat**.

**Password protection is a separate cost.** It now requires the Advanced Deployment Protection add-on at **$150 per month** on top of Pro. For a review site that is difficult to justify.

Neither point is a reason to avoid Vercel — $20 a month is nothing against an engagement of this size, and the platform is excellent. But you should decide it rather than discover it, particularly on an account where you are advising on governance.

**Cloudflare Pages has neither issue.** Commercial use is explicitly permitted on the free plan, and Cloudflare Access gives you genuine email-gated protection free for up to 50 people. That is why it is first in the table.

---

## OPTION A · Cloudflare Pages — recommended

**1.** Push this repository to GitHub (private).

```bash
git init && git branch -M main
git add . && git commit -m "CISOG USA review site"
git remote add origin https://github.com/YOUR-ORG/cisog-review.git
git push -u origin main
```

**2.** [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git** → select the repository.

**3.** Build settings:

| Field | Value |
|---|---|
| Framework preset | None |
| Build command | *leave empty* |
| Build output directory | `public` |

**4.** **Save and Deploy.** Live in about 30 seconds at `cisog-review.pages.dev`.

The `public/_headers` file applies the `noindex` and cache rules automatically. Nothing to configure.

### Gating it behind a login (free)

Zero Trust → **Access** → **Applications** → **Add an application** → **Self-hosted**

Set the domain to your Pages URL, add a policy with action **Allow**, selector **Emails**, and list the addresses that should get in. Anyone visiting receives a one-time code by email.

Free for up to 50 users. This is the cleanest way to give the client a private link without managing a shared password.

---

## OPTION B · Vercel

Read the note above first, then:

**1.** Push to GitHub as in Option A.

**2.** [vercel.com/new](https://vercel.com/new) → **Import Git Repository** → select it.

**3.** Vercel reads `vercel.json` and configures itself. Confirm:

| Field | Value |
|---|---|
| Framework Preset | Other |
| Build Command | *empty* |
| Output Directory | `public` |

**4.** **Deploy.** Live in about 30 seconds at `cisog-review.vercel.app`.

`vercel.json` applies the `noindex` and security headers. Nothing else to set up.

### Protecting it without the $150 add-on

Options, in order of practicality:

- **Leave it open and rely on `noindex`.** The URL is unguessable and excluded from search. For a two-week review window this is usually proportionate.
- **Vercel Authentication** — free on all plans, but it protects preview deployments and requires the viewer to hold a Vercel account with team access. Workable if the client is technical, clumsy otherwise.
- **Put Cloudflare Access in front of it.** Point a subdomain at Vercel through Cloudflare DNS and apply an Access policy. Free, and it works across hosts.

---

## OPTION C · cPanel over FTPS

For when you have the client's server. The GitHub Actions workflow in `.github/workflows/deploy.yml` is ready.

**Check first:** cPanel → **Files** → **Git™ Version Control**. If present, use it — the server pulls from GitHub directly and your FTP password never leaves cPanel. Tell me and I will write that configuration.

Otherwise:

**1.** cPanel → **Domains** → create `review.cisogusa.com`. Note the document root exactly.

**2.** cPanel → **SSL/TLS Status** → run **AutoSSL** for the subdomain. Wait for a valid certificate — `.htaccess` forces HTTPS and without a certificate the browser refuses the connection.

**3.** cPanel → **FTP Accounts** → create `deploy-review`, restricted to that folder. Never use the main cPanel login for CI.

**4.** GitHub → **Settings** → **Secrets and variables** → **Actions**:

| Secret | Value |
|---|---|
| `FTP_SERVER` | `ftp.cisogusa.com` |
| `FTP_USERNAME` | `deploy-review@cisogusa.com` — exactly as cPanel shows it |
| `FTP_PASSWORD` | from step 3 |
| `FTP_TARGET_DIR` | `/` — the account is already locked to the folder |

**5.** Push. Watch the **Actions** tab.

**6.** Password protection: cPanel → **Directory Privacy**. Let cPanel generate the credentials — never paste a hash from an online generator, which hands a third-party site a working credential for your server.

### cPanel troubleshooting

| Symptom | Cause |
|---|---|
| Green run, site unchanged | Wrong `FTP_TARGET_DIR`. Connect once manually, note where you land. |
| `530 Login authentication failed` | Username needs the full `user@domain.com` form. |
| `421` / timeout | Host blocks CI FTP. Ask support to permit FTPS, or use Option A. |
| Certificate warning | AutoSSL not run for this subdomain. |
| Redirect loop | Host terminates TLS upstream. Remove the `RewriteCond %{HTTPS} !=on` line. |
| 500 after first deploy | `.htaccess`. Rename to `.htaccess.off`, reintroduce sections one at a time. |

---

## DAILY USE — identical on all three

```bash
# edit public/index.html
git add -A
git commit -m "Tighten the service page hero"
git push
```

Client comments, you push, you reply "refresh." That loop is the entire reason to spend a few minutes on this rather than uploading files for the next three months.

`index.html` is served with `must-revalidate` on every host, so the client always sees the current version without being told to hard-refresh.

---

## WHAT IS IN HERE

```
cisog-review/
├── .github/workflows/deploy.yml   cPanel FTPS pipeline (Option C only)
├── vercel.json                    Vercel config — headers, output dir
├── .gitignore
├── README.md
└── public/                        Everything here is published
    ├── index.html                 The prototype
    ├── _headers                   Cloudflare Pages headers
    ├── .htaccess                  Apache / cPanel config
    └── robots.txt                 Crawler exclusion
```

The three host configs coexist harmlessly. Cloudflare ignores `vercel.json`, Vercel ignores `_headers`, and both ignore `.htaccess`. Nothing needs removing when you switch.

---

## KEEPING IT OUT OF SEARCH

All three configurations send `X-Robots-Tag: noindex`, and `robots.txt` disallows everything.

This matters more than it appears. A staging copy that gets indexed competes with the real site later and can outrank it — an unpleasant problem to unpick after launch. Do not remove those headers when the production site goes live on a different host; remove the staging site instead.

---

## A NOTE ON PRODUCTION

This is the review prototype only. **It is not the production architecture.**

The live site needs server-side assessment scoring, form handling that writes to the CRM, and PDF generation — none of which run on static hosting. §13 of the Master Build Specification covers that.

Worth noting: if you end up preferring Cloudflare here, it aligns with the specified production stack, where Workers handle the API routes alongside the static site. Vercel is equally capable and would mean Vercel Functions instead. Either is defensible; the decision belongs with the production hosting conversation, not this one.
