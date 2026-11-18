# Concise Pro

A Claude Code output style for anyone who keeps asking for the TL;DR. It builds on [Concise](https://code.claude.com/docs/en/output-styles#concise) and keeps Claude’s coding instructions. The [prompt](concise-pro.md) ends with this check:

> Before sending, ask whether a shorter reply would answer the user’s question just as well. If so, cut the extra material, even whole paragraphs or sections.

## Install

[Download the style](https://github.com/deangabbai/concise-pro/releases/latest/download/concise-pro.md) into `~/.claude/output-styles/`, or install it from the terminal.

<details>
<summary>Copy the install command</summary>

```sh
curl -fsSL --create-dirs \
  -o ~/.claude/output-styles/concise-pro.md \
  https://github.com/deangabbai/concise-pro/releases/latest/download/concise-pro.md
```

</details>

Restart Claude Code, then run:

```text
/output-style Concise Pro
```

## Example

**Are we live?** In this example, CI passed and staging runs v2. Production still runs v1.

**Concise Pro**

> Not live. Production still runs v1 until the pending deploy approval is granted and the deploy completes. CI and staging are good, but the changelog and dashboard now describe a release users can't see yet.
>
> Next steps: get the approval, run the production deploy, then verify v2 is serving in prod. If the changelog or dashboard are already public-facing, consider holding or flagging them until then.

<details>
<summary>Compare with built-in Concise and see the exact prompt</summary>

Both replies came from fresh Claude Code sessions using Sonnet 5.5 at medium effort.

**Prompt**

> Release handoff: CI passed. Staging runs v2. Production still runs v1 because deploy approval is pending. The changelog and dashboard are updated. Are we live?

**Built-in Concise**

> No, not live. Production still runs v1 until the pending deploy approval is granted and the rollout completes. Staging on v2 with passing CI means it's ready, not released.
>
> Before calling it live:
> - Get the deploy approval.
> - Confirm prod reports v2 after the rollout.
> - Note that the changelog and dashboard already say v2, so they're ahead of reality. Consider holding or flagging them until prod actually switches, so users and teammates aren't misled.

</details>
