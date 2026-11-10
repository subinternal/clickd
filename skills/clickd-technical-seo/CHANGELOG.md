# Changelog

Versions follow semantic versioning: a major version changes what the skill asks of the person or the agent, a minor one adds or tightens steps, a patch corrects wording. The version is in `SKILL.md` under `metadata`, as the Agent Skills format keeps anything it does not define.

## 2.3.0 (2026-11-01)

- Every tool is named for clickd: `clickd_brief`, `clickd_structure`, `clickd_check`, `clickd_rescan`, `clickd_changes` and the rest, where they were `mttr_*`. The old names still answer, so an agent set up before keeps working. The MCP server needs no key to start, and an assistant that only opens web pages can scan a site at `https://clickd.com/scan/example.com`.

## 2.2.0 (2026-11-01)

- The skill works best connected at `https://clickd.com/mcp/all`, which lists every tool including `mttr_structure` and `mttr_links`. `mttr_pages` with a path gives one page, `mttr_check` checks TLS and agent HTML readability on the spot, and `mttr_changes` with the job from `mttr_rescan` follows a live read.

## 2.1.0 (2026-10-31)

- clickd.com: every address is clickd.com now, and clickd's MCP server is at `https://clickd.com/mcp`. Anything set up on mttr.si keeps working there: the MCP server, the API and OAuth still answer on it.

## 2.0.0 (2026-10-31)

- First release under `subinternal/clickd`: five-step technical SEO audit and code-level fix workflow covering crawl access, sitemaps, canonicals, server-rendered HTML, security headers and live verification.
