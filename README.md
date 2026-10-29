# KAIROS Observer — plugin for Grok Bot, Cursor, and MCP hosts

**What it does.** Shows what a company's public pages reveal about
its stack. Your agent inspects the public site and reports its
findings across three signal families — helpdesk/support widgets,
CMS/site platform, analytics/measurement — and Observer composes
the coverage report: which families were checked, what was detected,
what was only inferred, and what wasn't checked at all. Every
detected finding carries the evidence it rests on (the script, meta
tag, or signature seen). Detected means seen on public pages, not
verified.

This is a coverage report, not a quality grade: it says what is
visible from outside, never whether the stack is good. The plugin
is free and needs no account.

**Tools**

| Tool | Label | What it does |
|---|---|---|
| `kairos_observer_report` | Write | Composes the public-signal coverage report for a domain from the signals your agent gathered |
| `kairos_observer_cta` | Read | Returns the next-step link (free KAIROS assessment) for a completed report |

**Configure variables.** None. No key, no sign-in, and no
credentials are ever requested or stored — yours or the observed
company's.

**Privacy.** The reporting server stores nothing and fetches
nothing: signals come from your agent's own inspection of public
pages, and the report you carry between calls holds only a summary
inside a signed token. Personal data from public pages is never
collected — stack signals only.

## Test locally

The package points at the hosted endpoint in `mcp.json` (deployed
with the plugin's marketplace submission). To exercise the tools
before that, run the bundled server and point any MCP client at it:

```bash
python3 server/mcp_server.py --port 8733   # POST JSON-RPC to /mcp
python3 tests/test_flow.py                # full flow test
```

Cursor IDE local load:

```bash
ln -s /path/to/kairos-observer "$HOME/.cursor/plugins/local/kairos-observer"
```

Then reload the window and confirm the `kairos-observer` skill and
MCP server load.

## Submit

- Grok Bot / Cursor marketplace: https://x.ai/bot/marketplace/submit-a-plugin
- License: MIT (see LICENSE) — the plugin package is open; the
  reporting service itself is hosted by KAIROS AI Systems.

Built by KAIROS AI Systems — https://kairosasi.com
