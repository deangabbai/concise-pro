# Concise Pro

A Claude Code output style for anyone who keeps asking for the TL;DR. It builds on [built-in Concise](https://code.claude.com/docs/en/output-styles#concise) and keeps Claude’s coding instructions.

**[See the exact diff from built-in Concise](https://github.com/deangabbai/concise-pro/commit/80aaef48ab9fabb34ef4f705aa73f41a19a691e5)** · [Read the prompt](concise-pro.md) · [Compare real replies](docs/examples.md)

## What changes?

Concise Pro asks Claude to make one more editing pass:

> Before sending, ask whether a shorter reply would answer the user’s question just as well. If so, cut the extra material, even whole paragraphs or sections.

It drops blanket instructions to report outcomes and decisions, give full detail on request, and reproduce error or test output in full. It keeps the instruction to preserve correctness. Claude decides what to say before choosing prose, a list, or a table.

## Install

[Download the style](https://github.com/deangabbai/concise-pro/releases/latest/download/concise-pro.md) into `~/.claude/output-styles/`, or use the terminal command below.

<details>
<summary>Install with curl</summary>

```sh
curl -fsSL --create-dirs \
  -o ~/.claude/output-styles/concise-pro.md \
  https://github.com/deangabbai/concise-pro/releases/latest/download/concise-pro.md
```

</details>

Restart Claude Code, then select the style for your project:

```text
/output-style Concise Pro
```

To switch back, run `/output-style Concise`.

<details>
<summary>Which version of built-in Concise does the diff use?</summary>

The comparison uses the built-in prompt from Claude Code **2.1.327** and the published **Concise Pro v0.1** file. The built-in name, description, and coding-instructions setting are shown as Markdown frontmatter so the files compare directly.

Claude Code also sends a separate turn reminder. Built-in Concise gets “Be concise: lead with the result, skip preamble and narration, keep only what the user needs.” Custom styles get “Remember to follow the specific guidelines for this style.”

[Download the unified diff](https://github.com/deangabbai/concise-pro/commit/80aaef48ab9fabb34ef4f705aa73f41a19a691e5.diff).

</details>
