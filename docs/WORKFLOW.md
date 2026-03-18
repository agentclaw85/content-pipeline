# Workflow

## Übersicht

Die Pipeline verarbeitet Content-Ideen in drei deterministischen Schritten:

1. **Proposal → Research:** Deep Research mit Quellenanalyse
2. **Research → Review:** Faktenprüfung, Auto-Fix, Status-Validierung
3. **Research → Artikel:** SEO-optimierter Blogartikel (nur bei validiertem Research)

## Phase 1: Proposals

### Dateiformat

```markdown
---
title: 'Titel des Themas'
slug: 'url-freundlicher-slug'
part: 4                    # Optional: Serienteil
series: 'sicher-im-netz'   # Optional: Serienname
status: pending            # Immer pending beim Erstellen
created_at: '2026-03-18T07:48:00Z'
---

## Thema

Kurze Beschreibung des Themas.

## Zielgruppe

Wer soll den Artikel lesen?

## Recherche-Fokus

- Punkt 1
- Punkt 2
- Punkt 3

## Quellen-Hinweise

- Empfohlene Quellen oder Hinweise
```

### Status-Übergänge

- `pending` → `inresearch` (durch Research Cron)
- `inresearch` → bleibt so (Research wurde erstellt)

## Phase 2: Research

### Erstellt durch Research Cron

- Liest Proposal mit `status: pending`
- Führt Deep Research durch (10-15+ Quellen)
- Erstellt Research-Dokument mit `status: draft`
- Ändert Proposal auf `status: inresearch`

### Review durch Review Cron

Priorität: `inreview` > `draft`

**Wenn draft:**
- Setzt auf `inreview`
- Führt Review durch

**Review-Prozess:**
1. Faktenprüfung
2. Link-Validierung (mind. 5 Links)
3. EU/OS-Check
4. Auto-Fix (kleine Fehler)
5. Markierung (große Probleme)
6. Review Notes anhängen

**Ergebnis:**
- `final` → bereit für Artikel
- `rejected` → verworfen (mit Begründung)
- `inreview` → braucht manuelle Prüfung

### Dateiformat

```markdown
---
title: 'Titel'
slug: 'url-slug'
part: 4
series: 'sicher-im-netz'
status: draft              # draft | inreview | final | rejected
source: 'proposal-dateiname'
created_at: '2026-03-18T21:00:00Z'
reviewed_at: '...'        # Nach Review hinzugefügt
---

# Deep Research: [Titel]

## Executive Summary
...

## 1. [Hauptthema]
...

## Review Notes  # Wird durch Review Cron hinzugefügt
### 2026-03-18 - [Änderung] - [Grund]
```

## Phase 3: Artikel

### Erstellt durch Article Cron

- Liest Research mit `status: final`
- Prüft ob Artikel bereits existiert (Slug-Matching)
- Generiert SEO-optimierten Artikel mit `seo-article-gen` Skill
- Setzt Research auf `status: article_generated`

### Artikel-Anforderungen

- 2.000-2.500 Wörter
- H1 + Meta-Description (155-160 Zeichen)
- Hook → Problem → Lösung
- H2/H3-Hierarchie
- FAQ-Sektion (4-6 Fragen)
- Fazit mit CTA
- Schema: Article + FAQ
- Frontmatter mit allen Metadaten

### Dateiformat

```markdown
---
title: 'SEO-optimierter Titel'
date: '2027-03-09'
author: 'Steffen'
description: 'Meta-Description (155-160 chars)'
slug: 'url-slug'
part: 4
series: 'sicher-im-netz'
status: draft              # draft | inreview | final
source: 'research-slug'
created_at: '2026-03-18T23:00:00Z'
alias: 'dateiname_ohne_endung'
schema: 'Article'
faq:
  - q: 'Frage?'
    a: 'Antwort.'
---

# [Artikel-Content]
```

## Kritische Regeln

1. **Ein Dokument pro Cron-Lauf** — nie mehrere verarbeiten
2. **Status = Lock** — nur passende Status werden verarbeitet
3. **Idempotent** — existierende Dateien nicht überschreiben
4. **Deterministische Slugs** — gleicher Slug über alle Phasen
5. **EU-Fokus** — deutsche/europäische Quellen zuerst
6. **Belegbar** — alle Behauptungen mit Quellen
7. **SEO-Struktur** — immer `seo-article-gen` Skill nutzen
