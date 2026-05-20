# `.github` — Angelwerk org defaults

GitHub uses this repo for **organisation-wide community health files**:
PR template, issue templates, CODEOWNERS, profile README. Whatever a
specific Angelwerk repo doesn't ship locally, GitHub falls back to here.

## Contents

| Path | Effect |
|---|---|
| `profile/README.md` | Rendered on <https://github.com/Angelwerk> as the org landing page |
| `CONTRIBUTING.md` | Linked from every repo's "Contributing" sidebar / PR sidebar; condenses the Engineering Handbook |
| `.github/PULL_REQUEST_TEMPLATE.md` | Prefilled when opening a PR on any Angelwerk repo |
| `.github/ISSUE_TEMPLATE/*.yml` | Issue-form templates (bug / feature) — apply org-wide |
| `.github/ISSUE_TEMPLATE/config.yml` | Disables blank issues; surfaces docs links |
| `.github/CODEOWNERS` | Default reviewer assignment |
| `.github/workflows/pr-title-lint.yml` | **Reusable** workflow — repos call it via `uses: Angelwerk/.github/.github/workflows/pr-title-lint.yml@main` |

## Authoritative source for conventions

The **Engineering Handbook** in the Angelwerk Obsidian vault
(`Technik/Engineering Handbook.md`) is the autoritative source. This repo
is its public-facing surface; if the two ever disagree, the Handbook
wins and this repo gets a fix-up PR.

## Updating

Branch off `main`, follow [`CONTRIBUTING.md`](./CONTRIBUTING.md) like
any other Angelwerk repo (Conv Commits, squash-merge, PR-title gate).
After landing, walk every dependent repo and confirm nothing relies on
the prior shape of a template.
