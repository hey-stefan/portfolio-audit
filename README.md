# Portfolio Audit Skill

Audit any product design portfolio website against what top design leaders actually look for when hiring.

## Where this comes from

The rubric behind this skill was built by scraping and analyzing transcripts from 143 episodes of [Dive Club](https://www.dive.club) — a design podcast hosted by [Ridd](https://x.com/ridd_design) where he interviews design leaders from companies like Lovable, Duolingo, Stripe, Shopify, Perplexity, Anthropic, Ramp, Airbnb, Cash App, Linear, Discord, and Figma.

We extracted every mention of portfolios, hiring, what makes candidates stand out, and what gets people rejected, then distilled it all into a scoring rubric based on what these specific people said they actually care about when reviewing portfolios.

## What it does

Give it a portfolio URL and it will:

1. Visit the site with a headless browser
2. Screenshot the homepage (viewport + full page)
3. Extract all text and links
4. Follow internal links — case study pages, project pages, about page — and screenshot those too
5. Score the portfolio across 8 categories
6. Output a detailed audit with specific, actionable feedback

## Categories

| Category | Weight |
|---|---|
| 10-Second Gut Check | Critical |
| Work Is the Hero / Visuals over Text | High |
| Ruthless Curation | High |
| Storytelling & Framing | Medium |
| Ambition & Scope | High |
| Soul & Uniqueness | Medium |
| Portfolio as Product | Medium |
| Builder Signals | Medium |

Each scores 1-5. Total out of 40.

## Install

### One command (all agents)

```bash
npx skills add hey-stefan/portfolio-audit
```

Auto-detects your installed agents and installs to each. Works with Claude Code, Codex, OpenClaw, Cursor, Gemini CLI, Windsurf, OpenCode, and [35+ more](https://github.com/vercel-labs/skills).

### Claude Code only

```bash
npx skills add hey-stefan/portfolio-audit -a claude-code
```

### Manual install

Copy `SKILL.md` into your agent's skills directory:

| Agent | Path |
|-------|------|
| Claude Code | `~/.claude/skills/portfolio-audit/` |
| Codex | `~/.codex/skills/portfolio-audit/` |
| OpenClaw | `~/.openclaw/skills/portfolio-audit/` |
| Cursor | `~/.cursor/skills/portfolio-audit/` |
| Gemini CLI | `~/.gemini/skills/portfolio-audit/` |
| Windsurf | `~/.codeium/windsurf/skills/portfolio-audit/` |
| OpenCode | `~/.config/opencode/skills/portfolio-audit/` |

Or clone:

```bash
git clone https://github.com/hey-stefan/portfolio-audit.git ~/.claude/skills/portfolio-audit
```

### Note

The skill uses [agent-browser](https://agent-browser.dev/) to browse and screenshot sites. On first run, you may need to install the browser: `npx agent-browser install`

## Usage

```
/portfolio-audit https://mikematas.com
```

## Example output

```
# Portfolio Audit: example.com

## Overall Impression
[2-3 sentence gut reaction]

## Scores
| Category | Score | |
|---|---|---|
| 10-Second Gut Check | 4/5 | Clean, custom, clearly a designer's site. |
| Work Is the Hero | 3/5 | Homepage cards are nice but need more visible work. |
| ... | ... | ... |

**Overall: 32/40**

## What's Working
- [specific observations]

## What Needs Work
- [specific, actionable feedback]

## Priority Fixes (Do These First)
1. [highest impact change]
2. [second highest]
3. [third]

## The Hiring Manager Gut Check
[honest 2-3 sentences from a hiring manager's perspective]
```

## How it works under the hood

The skill uses `npx agent-browser` to browse portfolio sites like a real user:

- Opens the site in a headless Chromium browser
- Takes screenshots and reads the page structure
- Scrolls through pages, clicks into case studies and internal links
- Claude reads the screenshots visually and the page data to perform the audit

No data is sent anywhere. Everything runs locally.

## Credits

Built on top of [Dive Club](https://www.dive.club) by [Ridd](https://x.com/ridd_design), go watch the episodes.
