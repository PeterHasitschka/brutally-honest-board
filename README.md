# Brutally Honest Board

A Claude Code project that evaluates business ideas without mercy, validation bias, or feel-good summaries. You pitch an idea. The board tears it apart.

## What it is

The Brutally Honest Board is a multi-agent system built with [Claude Code subagents](https://docs.anthropic.com/en/docs/claude-code/sub-agents). It simulates a panel of six ruthless board members, each with a distinct perspective, who evaluate your business idea from every angle — and then deliver a cold, structured verdict.

No cheerleading. No "great idea!" No softening with "but if you just...". Only specific, honest analysis.

## The Board Members

| Agent | Role |
|---|---|
| **The Enthusiast** | Finds what is *actually* strong — not a yes-man, but the one voice that looks for real signal |
| **The Market Realist** | Searches the web for real competitors, market data, and historical failures before speaking |
| **The Copycat** | Thinks like a well-funded rival: "How do I clone this in 3 months and charge half the price?" |
| **The CFO** | Only speaks in numbers: CAC, LTV, margins, burn rate. If the math fails, nothing else matters |
| **The Customer** | The tired, skeptical end user who has seen too many apps and will never read a landing page twice |
| **The Chairman** | Speaks last. Delivers the final structured verdict: BUILD / PIVOT / KILL |

## How to use it

### Prerequisites

- [Claude Code](https://claude.ai/code) CLI installed and authenticated

### Run a board session

Open Claude Code in this project directory and just describe your idea:

```
A subscription app that sends personalized book summaries via WhatsApp every morning.
```

Claude reads the `CLAUDE.md` instructions and automatically orchestrates the full board session — no command needed.

### What you get

The five board members run in parallel, then the Chairman delivers a structured verdict:

```
## VERDICT

✅ WHAT'S REAL:
[What actually has merit]

☠️ KILL FACTOR:
[The single biggest threat or flaw]

📊 MARKET REALITY:
[What the market looks like right now]

🎯 DECISION: BUILD / PIVOT / KILL

REASONING:
[Max 3 sentences. Cold. Specific. No padding.]
```

### Language

The board responds in whatever language you submit your idea in. Write in German, get the session in German. Write in English, get it in English.

## Project structure

```
brutally-honest-board/
├── CLAUDE.md                        # Project rules and orchestration instructions
└── .claude/
    └── agents/
        ├── board-session.md         # Orchestrator agent — runs the full session
        ├── enthusiast.md
        ├── market-realist.md
        ├── copycat.md
        ├── cfo.md
        ├── customer.md
        └── chairman.md
```

## How it works

This project uses Claude Code's [subagent feature](https://docs.anthropic.com/en/docs/claude-code/sub-agents). Each `.md` file in `.claude/agents/` defines a specialized agent with its own persona, constraints, and instructions. The `board-session` orchestrator invokes all five board members in parallel, waits for their outputs, then passes the results to the Chairman for the final verdict.

The Market Realist is the only agent that performs a live web search — it looks up real competitors, pricing, and market data before responding.
