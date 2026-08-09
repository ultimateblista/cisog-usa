# Project documents

Markdown files are the source of truth. The `.docx` versions are generated from
them with pandoc and are what gets sent to the client.

| File | Purpose |
|---|---|
| `CISOG-USA-Master-Build-Spec.md` | The specification. Supersedes the four original client documents. |
| `CISOG-USA-Insights-Content-Pack.md` | Nine launch articles with SEO metadata. |
| `cisog-insights-cms-import.json` | The same articles, structured for CMS import. |
| `CISOG-USA-Prototype-Update-Report.md` | Client progress report. |
| `covering-email-draft.md` | Email drafts to accompany the report. |

To regenerate a .docx after editing the markdown:

    pandoc FILE.md -o FILE.docx --toc --toc-depth=2 -f markdown+pipe_tables -t docx

This folder is not published. Only `public/` is deployed.
