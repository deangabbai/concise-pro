# Concise Pro

A Claude Code output style based on [built-in Concise](https://code.claude.com/docs/en/output-styles#concise). It asks Claude to do the work thoroughly, then cut anything you don’t need to read. That can mean dropping a whole section.

## Install

```sh
mkdir -p ~/.claude/output-styles
curl -fsSL https://raw.githubusercontent.com/deangabbai/concise-pro/main/concise-pro.md -o ~/.claude/output-styles/concise-pro.md
```

Restart Claude Code and select the style for your project:

```text
/output-style Concise Pro
```

[Read the full prompt](concise-pro.md).

## Example

One prompt, two fresh Claude Code sessions, both using Sonnet 5.5 at medium effort:

> Release handoff: CI passed. Staging runs v2. Production still runs v1 because deploy approval is pending. The changelog and dashboard are updated. Are we live?

<details>
<summary>Built-in Concise</summary>

> No, not live. Production still runs v1 until the pending deploy approval is granted and the rollout completes. Staging on v2 with passing CI means it's ready, not released.
>
> Before calling it live:
> - Get the deploy approval.
> - Confirm prod reports v2 after the rollout.
> - Note that the changelog and dashboard already say v2, so they're ahead of reality. Consider holding or flagging them until prod actually switches, so users and teammates aren't misled.

</details>

<details>
<summary>Concise Pro</summary>

> Not live. Production still runs v1 until the pending deploy approval is granted and the deploy completes. CI and staging are good, but the changelog and dashboard now describe a release users can't see yet.
>
> Next steps: get the approval, run the production deploy, then verify v2 is serving in prod. If the changelog or dashboard are already public-facing, consider holding or flagging them until then.

</details>
