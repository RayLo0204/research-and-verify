# Research and Verify

A reusable Codex skill for investigating practical questions through dialogue, credible sources, working examples, clear explanations, and small experiments when useful.

This first version captures a flexible research approach. It adapts to the current question rather than enforcing a fixed checklist or requiring every investigation to become a POC.

## How it helps

- Clarify the intended outcome and the uncertainty that matters now.
- Compare stated support with successful examples and their actual conditions.
- Explain the mechanism and discuss the flow before unnecessary implementation detail.
- Choose a small, bounded verification when it can change the decision.
- Distinguish observed results, reported claims, inferences, and unverified behavior.
- Use surprising observations and user feedback to revise the approach.
- Leave understandable evidence and manual verification steps when needed.

The investigation can move between these activities. A documentation comparison may need no experiment; a working demonstration may still leave performance or production-readiness questions open.

## Files

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Research-method instructions |
| [agents/openai.yaml](agents/openai.yaml) | Display metadata and automatic-invocation policy |
| [references/research-patterns.md](references/research-patterns.md) | Reusable patterns and examples |

## Install

Place this repository as `research-and-verify` inside the personal skills directory used by your Codex installation. For installations using the current user-scope directory:

```bash
git clone https://github.com/RayLo0204/research-and-verify.git "$HOME/.agents/skills/research-and-verify"
```

Some existing desktop setups use `$CODEX_HOME/skills` or `$HOME/.codex/skills`; use the directory your installation already discovers. Keep a backup before replacing an existing skill.

## Automatic selection

`agents/openai.yaml` explicitly sets:

```yaml
policy:
  allow_implicit_invocation: true
```

Once installed and available to Codex, the skill can be selected automatically when a task matches its name and description. You do not need to mention it for every relevant request. This allows automatic selection; it does not guarantee activation on every message or make the skill a continuously running background process.

For example, a request to investigate feasibility, find working examples, or design a small verification can fit this skill. To explicitly request its use, mention `$research-and-verify`.

See the [official skills documentation](https://learn.chatgpt.com/docs/build-skills) for discovery and invocation behavior.

## Example request

> Use $research-and-verify to investigate whether this approach works with the resources I already have. Start with credible examples and explain the mechanism; propose a small test only if it resolves an important uncertainty.

## Scope

This repository contains the reusable method and generic examples. It does not include credentials, private source pages, original project code, raw test logs, or demo media. The skill does not grant new system access or authorize publication or paid workloads.
