<p align="center"><img src="docs/banner.png" alt="clickd skills: skills for agents that fix websites. An example run in a terminal: clickd reads 100 pages, makes three fixes, reads the site again, and the score goes from 61 to 88." width="100%"></p>

<p align="center">
<a href="https://agentskills.io/specification"><img alt="Agent Skills format" src="https://img.shields.io/badge/format-Agent%20Skills-f78b77"></a>
<a href="#the-skills"><img alt="5 skills" src="https://img.shields.io/badge/skills-5-f78b77"></a>
<a href="https://clickd.com/agents"><img alt="Works in Claude Code, Codex and Cursor" src="https://img.shields.io/badge/works%20in-Claude%20Code%20%7C%20Codex%20%7C%20Cursor-2b2d31"></a>
<a href="LICENSE"><img alt="MIT license" src="https://img.shields.io/badge/license-MIT-2b2d31"></a>
</p>

<p align="center"><b>Agent skills that read your site the way search engines and AI assistants do,<br>fix it in your own code, and read it again to prove what moved.</b></p>

<p align="center"><a href="https://clickd.com">Reports</a> &nbsp;&nbsp; <a href="https://clickd.com/leaderboard">Leaderboard</a> &nbsp;&nbsp; <a href="https://clickd.com/tools">Free tools</a> &nbsp;&nbsp; <a href="https://clickd.com/docs/reference">API and MCP</a></p>

## Quick start

**1. Add the skills** from the top of your site's repository:

```sh
npx skills add subinternal/clickd
```

**2. Tell your agent:**

```text
Check yoursite.com with clickd and fix what's worth the most.
```

In Claude Code you can add them as a plugin instead, with clickd's MCP server wired in:

```text
/plugin marketplace add subinternal/clickd
/plugin install clickd@subinternal
```

That's it. The skills work from clickd's free public reports with nothing else to set up. [Connect over MCP](#connect-your-agent-optional-free) later if you want the full brief and a re-read on demand.

Set up on mttr.si before the move? It keeps working: the MCP server, the API and OAuth still answer there.

## Why

Your site has two audiences now: people, and the machines that answer for them. Google still crawls it. ChatGPT, Gemini, Claude and Perplexity read it too, and then decide whether to quote you or someone else.

Most sites are quietly failing the second audience. clickd has read almost 1M sites so far. From the latest full read of each of the 224,721 sites ranked by October 2026, 13.4 million pages:

| | |
|---|---|
| **90%** | of articles don't answer their first question right under it |
| **80%** | of sites have no `llms.txt` |
| **56%** | of pages have a description the wrong length |
| **47%** | of pages have images with nothing to describe them |
| **1 in 10** | home, service and article pages show their words only after a script runs, and most AI crawlers never run it |

Those are the ones you can count. The rest are harder to see: a `robots.txt` that blocks GPTBot without anyone meaning to, pages that bury the answer under three paragraphs of welcome. These skills give your agent the eyes to see all of it, and the order to fix it in.

## How a run goes

```
   read ───────► rank ───────► fix ───────► read again
   your site     every fix     in your      and see
   like an AI    by what it    own code     what moved
   reads it      is worth      (you approve)
       ▲                                        │
       └────────────────────────────────────────┘
```

clickd does the reading and the grading. Your agent does the fixing, in your repository, with the access it already has. Then clickd reads the live site again, and only a page that passes counts as fixed. No one grades their own homework.

## You say, it does

| You say | What happens |
|---|---|
| *"Check example.com with clickd and fix what's worth the most."* | Reads the site, ranks every fix by worth, makes the top ones in your code, reads it again. |
| *"Why isn't ChatGPT mentioning us?"* | Shows your site the way an agent gets it: what it can read, what it has to cut away, what it never sees. |
| *"Get our product pages ready for Google Shopping."* | Fixes the Product structured data in your templates, field by field, checked on the live pages. |
| *"Add an llms.txt."* | Builds one from your own pages, with tests so it never goes stale. |
| *"Get our drain repair page onto page one."* | Runs a campaign on one page for one search, through five gates, each opened only by proof. |
| *"Make this demo playable inside a post on X."* | Gives the route a player card and checks what X's crawler is really served. |

## The skills

| Skill | What it does | Version |
|---|---|---|
| **[clickd](skills/clickd)** | **Start here.** Checks your site and fixes it, worth the most first. For a shop, it also gets your product pages read right by Google's merchant listings and shopping agents, field by field ([Shop ready](skills/clickd/references/shop-ready.md), built in). | `2.1.0` |
| [Page system](skills/clickd-page-system) | Builds your page templates so every page reads well for search and assistants. | `2.1.0` |
| [llms.txt](skills/clickd-llms-txt) | Writes a `/llms.txt` from your own pages, with tests so it never goes stale. | `2.1.0` |
| [Livecards](skills/clickd-livecards) | Makes a page run inside a post on X: a demo, a tool or a short landing page. | `2.1.0` |
| [Rank a page](skills/clickd-rank-a-page) | Moves one page up for one search, step by step, with proof at each one. | `2.1.0` |

Each skill is a folder in the open [Agent Skills](https://agentskills.io/specification) format: a `SKILL.md`, the references it links, and its own changelog.

## Install

### One line

```sh
npx skills add subinternal/clickd
```

### Or ask Claude Code to do it

```text
Install the clickd skills: copy every folder under skills/ in https://github.com/subinternal/clickd into ~/.claude/skills/, then tell me which skills you installed and suggest checking my site with the clickd skill.
```

### Or by hand

Copy a skill's folder to where your agent loads skills from:

| Agent | Folder |
|---|---|
| Claude Code | `.claude/skills/` in the repo, or `~/.claude/skills/` for every project |
| Codex | `.agents/skills/` in the repo, or `~/.agents/skills/` |
| Cursor | `.cursor/skills/` or `.agents/skills/` in the repo, or `~/.cursor/skills/`. It also reads `.claude/skills/`. |
| Anything else | Save the folder in the repo and add a line to `AGENTS.md` pointing at its `SKILL.md`. |

## Connect your agent (optional, free)

Connected over MCP, your agent gets the full brief for a site, its history, the next page worth writing, and a re-read whenever it asks for one. No key is needed to start. In Claude Code:

```sh
claude mcp add --transport http clickd https://clickd.com/mcp
```

A free key, made with an email, adds re-reads on demand and your claimed sites' private parts. Cursor, VS Code, Codex and the rest are on [clickd.com/docs/mcp](https://clickd.com/docs/mcp). An assistant with no MCP can scan a site by opening `https://clickd.com/scan/example.com`.

## What you won't get

- **Promises.** A score from clickd says a site's pages are well formed for crawlers and assistants. It doesn't say an assistant will cite the site, and none of these skills promises rankings or citations. Assistants change their answers day to day; anyone who guarantees you a spot in ChatGPT is selling something.
- **A bot loose on your site.** clickd reads public pages only, under its own crawler name, `mttr`, and obeys `robots.txt`. Your agent makes every change in your own code, and you approve each one or review the pull request.
- **Busywork.** Fixes come in order of what they're worth, so the first hour does the most good.

## See it first

<p align="center"><img src="docs/report-card.png" alt="A clickd report card for clickd.com: A+, 100 of 100, top 0.1%, each of the four stages A+" width="640"></p>

- **[Read your own site](https://clickd.com),** free, in about a minute. Every report leads to its Agent View: the site as an AI agent reads it, page by page.
- **[The leaderboard](https://clickd.com/leaderboard):** every site clickd has read, ranked, and the board for your line of work.
- **[Free tools](https://clickd.com/tools):** one page at a time, with nothing to install: [headings](https://clickd.com/h1-checker), [schema](https://clickd.com/schema-checker), [AI crawlers](https://clickd.com/ai-crawler-checker), [share cards](https://clickd.com/og-image-checker), [speed](https://clickd.com/website-speed-test) and more.

## Moved from subinternal/mttr

These skills were `subinternal/mttr` until October 31, 2026. That repository is archived and still installs, but new versions are only here. The skills are renamed (`mttr` to `clickd`, `mttr-page-system` to `clickd-page-system`, and so on), and Shop ready is now part of the `clickd` skill. The MCP tools are named for clickd since November 1, 2026 (`clickd_brief`, `clickd_site` and the rest). The old `mttr_*` names still answer, so nothing you've connected breaks.

## Made by

[subinternal](https://subinternal.com). Testing the boundaries of what's possible. clickd is what we built to find out what AI assistants actually do with the web.

## License

MIT. See [LICENSE](LICENSE). Questions to contact@subinternal.com.
