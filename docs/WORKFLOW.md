# Workflow

## Übersicht

Die Pipeline verarbeitet Content-Ideen in vier Phasen:

1. **Proposal → Research:** Deep Research mit Quellenanalyse (Cron 21:00)
2. **Research → Review:** Faktenprüfung, Auto-Fix, Status-Validierung (Cron 22:00)
3. **Research → Artikel:** SEO-optimierter Blogartikel (Cron 23:00)
4. **Human Feedback:** Unstrukturiertes Chat-Feedback → strukturierte Änderungen (event-driven, kein Cron)

---

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

---

## Phase 2: Research

### Erstellt durch Research Cron (21:00)

- Liest Proposal mit `status: pending`
- Führt Deep Research durch (10-15+ Quellen)
- Erstellt Research-Dokument mit `status: draft`
- Ändert Proposal auf `status: inresearch`

### Review durch Review Cron (22:00)

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
status: draft              # draft | inreview | final | rejected
created_at: '2026-03-18T21:00:00Z'
---

# Deep Research: [Titel]

## Executive Summary
...

## 1. [Hauptthema]
...

## Review Notes  # Wird durch Review Cron hinzugefügt
### 2026-03-18 - [Änderung] - [Grund]
```

---

## Phase 3: Artikel

### Erstellt durch Article Cron (23:00)

- Liest Research mit `status: final`
- Prüft ob Artikel bereits existiert (Slug-Matching)
- Generiert SEO-optimierten Artikel mit `seo-article-gen` Skill
- Setzt Research auf `status: article_generated`

### Artikel-Anforderungen

- 2.000-2.500 Wörter
- H1 (keine separate Meta-Description)
- Hook → Problem → Lösung
- H2/H3-Hierarchie
- Keine FAQ, kein Fazit-Call-to-Action
- Natürlicher, erzählender Ton
- Frontmatter minimal: nur `title`, `date`, `author`, `slug`

### Dateiformat

```markdown
---
title: 'SEO-optimierter Titel'
date: '2027-03-09'
author: 'Steffen'
image: '/img/blog-placeholder-1.png'
description: 'Meta-Description (155-160 chars)'
slug: 'url-slug'
alias: 'dateiname_ohne_endung'
status: draft              # draft | inreview | final
created_at: '2026-03-18T23:00:00Z'
processed_at: '...'        # Optional: bei Feedbacks etc.
---

# [Artikel-Content]
```

---

## Phase 4: Human Feedback (event-driven, kein Cron)

Unstrukturiertes Feedback aus Chatnachrichten wird in strukturierte Änderungen übersetzt und direkt auf Artikel angewendet.

### Trigger

Kein Cron. Feedback wird **sofort** verarbeitet, wenn es im Chat eingereicht wird:

1. User sendet Feedback-Nachricht (Freitext)
2. Clawie speichert es als strukturierte Datei in `/content/human/`
3. Clawie wendet Feedback **direkt** an
4. Ergebnis wird im Chat zurückgemeldet

### Strukturierte Aktionen

| Aktion | Beschreibung | Trigger-Beispiel |
|---|---|---|
| `expand_section` | Abschnitt erweitern | "Abschnitt X ist zu kurz" |
| `shorten_section` | Abschnitt kürzen | "Abschnitt Y ist zu langatmig" |
| `rewrite_section` | Abschnitt neu schreiben | "Einleitung überarbeiten" |
| `add_source` | Quelle hinzufügen | "Fehlt Quelle für Statistik Z" |
| `remove_source` | Quelle entfernen | "Quelle X ist nicht seriös" |
| `change_tone` | Ton ändern | "Etwas weniger akademisch" |
| `add_section` | Neuer Abschnitt | "Fehlt Abschnitt über Kosten" |
| `fix_fact` | Fakt korrigieren | "Preis ist falsch, es sind 10€" |

### Verarbeitungsregeln

1. **Klare Änderungen** → direkt umsetzen
2. **Unklare Änderungen** → **direkt nachfragen** (nicht raten)
3. **Widersprüchliches Feedback** → nachfragen
4. **Jede Änderung dokumentieren** → ins Änderungsprotokoll

### Feedback-Datei-Format

```markdown
---
title: 'Feedback: [Artikel-Titel]'
slug: '[artikel-slug]'
target: '[artikel-dateiname].md'
status: open          # open | inprogress | done | rejected
created_at: '2026-03-18T15:30:00Z'
processed_at: '...'   # Nach Verarbeitung
---

## Original Feedback

[Freitext aus Chat-Nachricht]

## Strukturierte Aktionen

### 1. expand_section — "Browser-Speicher"
- **Begründung:** Abschnitt ist zu kurz
- **Priorität:** mittel

### 2. add_section — "Kosten von Bitwarden Premium"
- **Begründung:** Fehlt komplett
- **Priorität:** hoch

## Änderungsprotokoll

### [Uhrzeit] - expand_section "Browser-Speicher"
- Abschnitt von ~100 auf ~250 Wörter erweitert
- Neue Quellen: [Heise-Artikel]
```

### Dateinamen-Konvention

```
[artikel-slug]_[YYYY-MM-DD_HHMMSS].md
```

### Status-Übergänge

| Feedback-Status | Bedeutung |
|---|---|
| `open` | Neu, noch nicht verarbeitet |
| `inprogress` | Wird gerade bearbeitet |
| `done` | Angewendet, Artikel aktualisiert |
| `rejected` | Verworfen (mit Begründung) |

---

## Kritische Regeln

1. **Ein Dokument pro Cron-Lauf** — nie mehrere verarbeiten
2. **Status = Lock** — nur passende Status werden verarbeitet
3. **Idempotent** — existierende Dateien nicht überschreiben
4. **Deterministische Slugs** — gleicher Slug über alle Phasen
5. **EU-Fokus** — deutsche/europäische Quellen zuerst
6. **Belegbar** — alle Behauptungen mit Quellen
7. **SEO-Struktur** — immer `seo-article-gen` Skill nutzen
8. **Keine stillen Änderungen** — alles nachvollziehbar dokumentiert
