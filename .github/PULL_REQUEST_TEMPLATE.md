<!--
PR title must be a Conventional Commit (it becomes the squash-commit
subject on main). Format:

  <type>(<scope>): [<AW-XXXX>] <imperative subject>

Example: feat(web): [AW-0017] resolve tenant from host header

The `pr-title-lint` workflow will block the merge if the title isn't
conventional. See CONTRIBUTING.md (org-level) for the full rules.
-->

## Summary

<!-- 1-3 sentences. What changes and why? Focus on the *why* — the diff
already shows the *what*. -->

## Linked task

<!-- AW-XXXX from the Obsidian vault, or "no task — trivial fix < 5 min". -->

AW-XXXX

## Test plan

<!-- Bulleted checklist of what was tested. For UI changes, describe the
flows you walked through in a browser. For DB migrations, confirm the
expand/contract discipline. -->

- [ ]
- [ ]

## Risk & rollback

<!-- Is there anything risky in this PR? If something breaks in
production, what's the rollback path? Most PRs: "Vercel Instant
Rollback". Migrations: explain the contract step. -->

## Screenshots / demo

<!-- If UI changed, attach before/after or a Loom. Skip if no UI change. -->
