# Angelwerk

**Digitale Infrastruktur für Anglervereine in DACH.**
Vereinswebsite, Mitglieder-App und Verwaltungs-CMS aus einem System — eingerichtet an einem Vereinsabend, gepflegt von ehrenamtlichen Vorständen ohne IT-Hintergrund.

→ <https://angelwerk.com>

## Repos

| Repo | Zweck |
|---|---|
| [`angelwerk`](https://github.com/Angelwerk/angelwerk) | Monorepo: SaaS-App (Next.js), Mobile (Expo), Supabase-Schema, geteilte Packages |
| [`angelwerk-www`](https://github.com/Angelwerk/angelwerk-www) | Marketing-Site auf `angelwerk.com` (Next.js auf Vercel) |
| [`aw-tasks`](https://github.com/Angelwerk/aw-tasks) | Internes Terminal-Tool (Go/Bubble Tea): k9s-artige Ansicht der Obsidian-Aufgaben nach Status, review→done direkt im Markdown |
| [`.github`](https://github.com/Angelwerk/.github) | Organisationsweite Community-Health-Files |

## Konventionen

Alle Repos arbeiten nach den im **Engineering Handbook** dokumentierten Regeln —
Branch-Naming, Conventional Commits, Squash-Merge, Vercel-Git-Integration,
Lefthook + Biome + Commitlint Gates. Siehe [`CONTRIBUTING.md`](./CONTRIBUTING.md) für die Kurzfassung.

## Stack

Next.js · Expo · Supabase · Vercel · pnpm · TypeScript · Biome
