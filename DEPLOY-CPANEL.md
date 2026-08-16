# Deploying to cPanel

The site is plain static files. There is no build step.

**Upload the entire contents of `public/`** to the document root for
`cisogusa.cisoggroup.com` — including the dotfile `.htaccess`, which
File Manager hides by default (Settings → Show Hidden Files).

```
public/
├── index.html          the whole site
├── .htaccess           HTTPS, security headers, caching, 404 → index.html
├── robots.txt          indexing ALLOWED (production)
├── sitemap.xml         38 URLs
├── images/             logo, favicons, photography
├── datasheets/         solution + service datasheets, capability statements
└── legal/              privacy + terms PDFs
```

## Before first upload

1. **cPanel → Domains** → create `cisogusa.cisoggroup.com`, note the document root.
2. **cPanel → SSL/TLS Status** → run **AutoSSL** and wait for a valid certificate.
   `.htaccess` forces HTTPS; without a certificate the browser will refuse to connect.
3. Upload `public/` contents to the document root.

## After upload — check these

- `https://cisogusa.cisoggroup.com` loads, padlock is valid
- Hard-refresh and confirm the logo and photos appear
- Open a datasheet link — PDFs download
- `https://cisogusa.cisoggroup.com/robots.txt` shows `Allow: /`

## If you get a 500 error

It is almost always `.htaccess`. Rename it to `.htaccess.off` via File Manager to
confirm, then reintroduce sections one at a time — some shared hosts do not enable
`mod_headers` or `mod_expires`.

## Indexing

`robots.txt` and the page headers now **allow** indexing. This is production
configuration. If you put a staging copy on another URL, add `noindex` there —
never leave two indexable copies of this site online.

## HSTS

Deliberately commented out in `.htaccess`. Enable it only after HTTPS is confirmed
working on the live domain — it is difficult to reverse.

## Vercel — still used for testing

Vercel remains the review/test deployment. Production is cPanel. The two coexist
safely because each platform reads a different config file and ignores the other's:

| Platform | Reads | Ignores | Indexing |
|---|---|---|---|
| Vercel (test) | `vercel.json` | `.htaccess` | **Blocked** — `X-Robots-Tag: noindex` |
| cPanel (production) | `public/.htaccess` | `vercel.json` | **Allowed** |

`robots.txt` says `Allow: /` on both, which is correct for production. On Vercel the
`noindex` response header overrides it, so the test URL is crawled but never indexed
and cannot compete with the live domain.

**Vercel setting that catches people out:** the site is at `cisog-review-site/public`,
not the repo root. In Vercel set **Root Directory = `cisog-review-site`**; `vercel.json`
then resolves `outputDirectory: public` correctly. Leave it at default and you get a 404.

When the site goes live on cPanel, either delete the Vercel project or leave it —
the noindex header means it stays invisible to search either way.
