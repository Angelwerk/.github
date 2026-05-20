# Contributing to Angelwerk

This file is the org-wide default that GitHub shows on every Angelwerk repo
that doesn't ship its own `CONTRIBUTING.md`. The authoritative source for
all conventions is the **Engineering Handbook** (Obsidian vault,
`Angelwerk/Technik/Engineering Handbook.md`) — this is the public-facing
condensate.

## Branch naming

```
<type>/aw-NNNN-short-kebab-slug      # with AW-XXXX ticket
<type>/short-kebab-slug              # ticketless (chore, docs, hotfix)
```

`<type>` is one of: `feat`, `fix`, `chore`, `docs`, `refactor`, `perf`,
`test`, `build`, `ci`, `revert`, `style`. Lowercase, kebab-case, no umlauts,
≤ 50 chars. `main` is the only long-lived branch; everything else is short
and goes through PR.

## Commits

[Conventional Commits](https://www.conventionalcommits.org/) with an
optional `[AW-XXXX]` ticket tag:

```
<type>(<scope>): [<AW-XXXX>] <imperative subject>
```

Repo gates (all simultaneously enforced):

- Lefthook `commit-msg` runs **commitlint** (`config-conventional`)
- Lefthook `pre-commit` runs **Biome** on staged files
- Claude Code PreToolUse hook blocks `--no-verify` / `-n` / `--no-gpg-sign`
- GitHub `pr-title-lint` validates the PR title (= squash-commit subject)

If a gate fails, **never `--amend`** — the failed commit was never created.
Fix the cause, then create a **new** commit.

## Pull-Request flow

1. Branch off `main`, name per schema above.
2. Atomic commits; push.
3. Vercel preview deploy auto-builds for linked repos.
4. Open PR with **PR title = Conventional Commit** — that title becomes the
   squash-commit subject on `main` and feeds `release-please`.
5. Wait for required checks: `pr-gate`, `pr-title-lint`, repo-specific gates.
6. Self-review the diff like a stranger would.
7. **Squash & Merge** — no merge commits, no rebase merges, no exceptions.
   Auto-delete head branches is on.

## Deployment

**Never run `vercel --prod` from local.** Production deploys happen
automatically via Vercel Git Integration on merge to `main`. Preview
deploys happen automatically on every branch push.

Rollback: Vercel UI → "Instant Rollback", or `vercel rollback <url>`.
No rebuild — atomic alias switch back to the previous deployment.

Env vars live in the Vercel UI / `vercel env`. Never commit secrets to
repos.

## Database migrations (monorepo only)

**Expand/contract**, never destructive-in-place. A migration must not
break the previous app version, so that Vercel Instant Rollback stays
instant. Destructive changes split across releases: expand (add new
shape, dual-write/read) → ship → contract (drop old shape) later.

See `ADR-005` for the full pattern.

## Tooling stack

| Tool | What | Config |
|---|---|---|
| pnpm | Package manager | `pnpm-workspace.yaml`, `.nvmrc` |
| Biome | Lint + format (single tool) | `biome.json` |
| TypeScript | strict, `noUncheckedIndexedAccess` | `tsconfig.base.json` |
| Lefthook | Git hooks (commit-msg + pre-commit) | `lefthook.yml` |
| commitlint | Conv Commit validation | `commitlint.config.mjs` |
| Claude Code hook | Block `--no-verify` on `git commit` | `.claude/hooks/block-commit-bypass.sh` |
| release-please | Versioning (monorepo) | `release-please-config.json` |

Major-version bumps land in the monorepo first, soak for ~1 week, then
propagate to `angelwerk-www` (and any future repo).

## Tasks (`AW-XXXX`)

Stored in the Obsidian vault under `Angelwerk/Aufgaben/`. The
`angelwerk-tasks` skill operates them. Create a task before any
non-trivial code change. Trivial = under 5 minutes, no risk, no
refactor.

After a commit lands on `main`, append the commit SHA to the task's
`Notizen` section for the bidirectional link.

## Questions

Ping Felix. Or open a discussion on the relevant repo.
