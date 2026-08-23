# Lender-Wise status page

Static status page for https://lender-wise.com, served by GitHub Pages at **https://status.lender-wise.com** — deliberately hosted outside the Lender-Wise Azure stack so it still answers when the service doesn't.

- `index.html` — the page. It calls `https://lender-wise.com/api/health` from the visitor's browser every 60 s (the endpoint allows this origin via CORS) and shows application/database status plus the incident list.
- `incidents.json` — the incident/maintenance log, newest last. Add an object `{ "start", "end" | null, "title", "summary" }` and push; the page re-reads it on load.
- `CNAME` — the custom domain for GitHub Pages.

Operations context, severities and the support channels live in the LenderReady repo: `docs/SUPPORT-AND-OPERATIONS.md`. Automated monitoring (availability tests from three regions, alert rules, the App Service health check) is described there too — this page is the human-readable surface, not the alerting system.
