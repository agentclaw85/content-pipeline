# Content Pipeline

Automatisierte Content-Pipeline für Blogartikel. Von der Idee (Proposal) über Deep Research und Review bis zum fertigen SEO-optimierten Artikel.

## Struktur

```
content-pipeline/
├── README.md                    # Dieses Dokument
├── docs/
│   ├── WORKFLOW.md              # Detaillierter Workflow
│   ├── STATUS_MODEL.md          # Status-Definitionen
│   └── SETUP.md                 # Einrichtung auf neuem System
├── crons/
│   ├── research-cron.md         # Research Cron Konfiguration
│   ├── review-cron.md           # Review Cron Konfiguration
│   └── article-cron.md          # Artikel-Generator Cron Konfiguration
├── scripts/
│   └── migrate-legacy.sh        # Migration alter Daten
└── content/
    ├── proposals/               # Input: Content-Ideen
    ├── research/                # Zwischenstufe: Recherchen
    └── generated/               # Output: Artikel
```

## Schnellstart

1. `content/proposals/` eine neue `.md`-Datei mit Frontmatter anlegen
2. Crons einrichten (siehe `docs/SETUP.md`)
3. Pipeline läuft automatisch um 21:00 / 22:00 / 23:00 (Europe/Berlin)

## Cron-Zeitplan

| Zeit | Phase | Input | Output |
|------|-------|-------|--------|
| 21:00 | Deep Research | `proposals/[slug]` (pending) | `research/[slug]` (draft) |
| 22:00 | Review | `research/[slug]` (inreview/draft) | `research/[slug]` (final/rejected) |
| 23:00 | Artikel | `research/[slug]` (final) | `generated/[slug]` (draft) |
| Chat | Human Feedback | Chat-Nachricht | `generated/[slug]` aktualisiert |

## Status-Flow

```
Proposal (pending)
  ↓ Research Cron
Research (draft)
  ↓ Review Cron
Research (inreview → final | rejected)
  ↓ Article Cron (nur bei final)
Article (draft)
  ↓ Human Feedback (bei Bedarf)
Article (draft → final)
```

## Phase 4: Human Feedback

Unstrukturiertes Chat-Feedback wird in strukturierte Änderungen übersetzt:
- `expand_section` / `shorten_section` / `rewrite_section`
- `add_source` / `remove_source`
- `change_tone` / `add_section` / `fix_fact`

Details: `docs/PHASE4-HUMAN-REVIEW.md`

## Richtlinien

- **EU-Fokus:** Deutsche/europäische Quellen zuerst
- **Open Source:** OS-Lösungen bevorzugt
- **US-Anbieter:** Nur bei gesellschaftlicher Dominanz (+ OS-Alternative)
- **SEO:** Alle Artikel mit `seo-article-gen` Skill
- **Belegbar:** Alle Behauptungen mit Quellen
- **Idempotent:** Keine Duplikate, Status als Lock
- **Deterministisch:** Slugs über alle Stufen konsistent
