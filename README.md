# jaydtrader

Day-trading skills for Claude Code. Open this repo in Claude Code and the 11
skills in `.claude/skills/` load on their own. Ask in plain words ("scan the
market", "set my stop and target") or type `/trader-scanner` and so on.

```
scanner -> news -> entry -> exit -> timemachine -> budget -> risk -> broker   (one trade)
alerts: stop, target, flat by the close                                       (while it is open)
news / analyst / pelosi                                                        (any time)
```

Each skill writes its output to a `trader/` folder that the next one reads.

## Two copies: yours and Jake's

- `/trader-scanner` and the other plain names run **this repo's copy** in
  `.claude/skills/`. Change these freely; they are your base.
- `/day-trader-skill:trader-scanner` and so on run **Jake's plugin**, installed
  from his marketplace through `.claude/settings.json`, which gets his updates.
- To pull his updates: `/plugin marketplace update day-trader-skill`, then
  restart Claude Code. To compare his new version with yours, diff his repo
  against `.claude/skills/`.

## Safety

- Only `trader-broker` can lead to an order, through a broker connection you
  set up yourself (Alpaca's MCP server, paper by default, or the Interactive
  Brokers connector). Every order needs a risk-check PASS, your typed yes and
  an Allow click.
- `.claude/settings.json` keeps Alpaca order tools on ask and blocks
  close-all, cancel-all, options and crypto order tools.
- Broker keys never go in this repo or in chat.
- Education and tooling, not financial advice.

## Setup

- `SEC_USER_AGENT="Your Name you@example.com"` for trader-analyst and trader-news.
- `pdftotext` (poppler) helps trader-pelosi read House filings.
- Tests: `python3 -m unittest discover tests`

## Credit

The skills are copied from
[Jakeschincariol/day-trader-skill](https://github.com/Jakeschincariol/day-trader-skill)
v2.0.0 (commit 3d0f4ef), by Jake Schincariol, MIT licensed. See
`LICENSE-day-trader-skill`. The tests were adjusted only to find the skills in
`.claude/skills/`.
