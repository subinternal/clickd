# Changelog

Versions follow semantic versioning: a major version changes what the skill asks of the person or the agent, a minor one adds or tightens steps, a patch corrects wording. The version is in `SKILL.md` under `metadata`, as the Agent Skills format keeps anything it does not define.

## 2.3.0 (2026-11-01)

- Every tool is named for clickd: `clickd_citations`, `clickd_cite`, `clickd_check`, `clickd_tells`, `clickd_schema_create`, `clickd_rescan`, `clickd_changes` and the rest, where they were `mttr_*`. The old names still answer, so an agent set up before keeps working. The MCP server needs no key to start, and an assistant that only opens web pages can scan a site at `https://clickd.com/scan/example.com`.

## 2.2.0 (2026-11-01)

- `mttr_citations`, `mttr_site` (`view: "agent"`), `mttr_check` (`kind: "agent"`) and `mttr_schema_create` are in the focused list at `https://clickd.com/mcp`, while `https://clickd.com/mcp/all` also lists `mttr_cite` and `mttr_tells`.

## 2.1.0 (2026-10-31)

- clickd.com: every address is clickd.com now, and clickd's MCP server is at `https://clickd.com/mcp`. Anything set up on mttr.si keeps working there: the MCP server, the API and OAuth still answer on it.

## 2.0.0 (2026-10-31)

- First release under `subinternal/clickd`: GEO and AEO audit and fix workflow covering AI search crawlers, non-JS HTML readability, answer-first passages, entity `sameAs` schema and live assistant citation tracking.
