# Built-in Concise and Concise Pro in practice

Three questions, each asked in two fresh Claude Code sessions using Sonnet 5.5 at medium effort. Both styles received the same input for each pair. These are the complete final replies from those runs.

## Is the release live?

> Release handoff: CI passed. Staging runs v2. Production still runs v1 because deploy approval is pending. The changelog and dashboard are updated. Are we live?

**Concise Pro**

> Not live. Production still runs v1 until the pending deploy approval is granted and the deploy completes. CI and staging are good, but the changelog and dashboard now describe a release users can't see yet.
>
> Next steps: get the approval, run the production deploy, then verify v2 is serving in prod. If the changelog or dashboard are already public-facing, consider holding or flagging them until then.

**Built-in Concise**

> No, not live. Production still runs v1 until the pending deploy approval is granted and the rollout completes. Staging on v2 with passing CI means it's ready, not released.
>
> Before calling it live:
> - Get the deploy approval.
> - Confirm prod reports v2 after the rollout.
> - Note that the changelog and dashboard already say v2, so they're ahead of reality. Consider holding or flagging them until prod actually switches, so users and teammates aren't misled.

## What did the reviewer recommend?

> The reviewer said: “The cache key ignores the language. Include the language in the key and add a regression test. The rest can ship.” What did the reviewer recommend?

**Both styles gave the same reply.**

> The reviewer recommended two changes: include the language in the cache key, and add a regression test for it. Everything else can ship as is.

## Why did the deploy stop?

> Look at release.log. Why did the deploy stop?

<details>
<summary>See the synthetic release.log both sessions read</summary>

```text
10:00:01 release 42 approved for production
10:00:08 image build succeeded
10:00:14 smoke tests: 18 passed
10:00:23 staging rollout healthy
10:00:34 production preflight checks started
10:00:35 WARNING previous release metadata is 30 days old
10:00:36 ERROR database schema is v11; release 42 requires v12
10:00:36 pending migration: 012_add_locale.sql
10:00:37 deploy halted before production traffic moved
10:00:38 production remains on release 41
```

</details>

**Concise Pro**

> The deploy halted at the production preflight check because of a database schema mismatch. Production is on v11, and release 42 needs v12 (`release.log:7`). The migration `012_add_locale.sql` hasn't been applied (`release.log:8`).
>
> No production traffic moved, and production is still on release 41. To fix it, run that migration and then retry the deploy.
>
> The 30-day-old release metadata warning on line 6 didn't stop the deploy.

**Built-in Concise**

> The production preflight check failed because the database is on schema v11 and release 42 needs v12. The migration `012_add_locale.sql` hasn't been applied. The deploy halted before any production traffic moved, so production is still on release 41.
>
> To fix it, apply `012_add_locale.sql` to the production database and re-run the deploy.
>
> The log also warns that the previous release metadata is 30 days old. That warning didn't stop the deploy.

[Back to Concise Pro](../README.md)
