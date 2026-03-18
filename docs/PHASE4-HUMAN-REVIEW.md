# Human Review & Feedback Integration

## Übersicht

Phase 4 der Content-Pipeline: Unstrukturiertes Feedback aus Chatnachrichten wird in strukturierte Änderungen übersetzt und auf Artikel angewendet.

## Workflow

```
Chat-Nachricht (Freitext)
  ↓ [Manuell: Feedback speichern]
/content/human/[slug]_[timestamp].md (status: open)
  ↓ [Feedback Cron]
Feedback wird angewendet
  ↓
Artikel aktualisiert (status: draft)
Feedback-Datei → status: done
```

## Input-Format

Jede beliebige Chat-Nachricht, z.B.:

> "Der Artikel über Passwort-Manager ist gut, aber der Abschnitt über Browser-Speicher ist zu kurz. Außerdem fehlt ein Hinweis auf die Kosten von Bitwarden Premium. Der Ton ist etwas zu akademisch."

## Strukturierte Aktionen

| Aktion | Beschreibung | Beispiel |
|---|---|---|
| `expand_section` | Abschnitt erweitern | "Abschnitt X ist zu kurz" |
| `shorten_section` | Abschnitt kürzen | "Abschnitt Y ist zu langatmig" |
| `rewrite_section` | Abschnitt neu schreiben | "Einleitung überarbeiten" |
| `add_source` | Quelle hinzufügen | "Fehlt Quelle für Statistik Z" |
| `remove_source` | Quelle entfernen | "Quelle X ist nicht seriös" |
| `change_tone` | Ton ändern | "Etwas weniger akademisch" |
| `add_section` | Neuer Abschnitt | "Fehlt Abschnitt über Kosten" |
| `fix_fact` | Fakt korrigieren | "Preis ist falsch, es sind 10€" |

## Feedback-Datei-Format

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

### 3. change_tone — "Weniger akademisch"
- **Begründung:** Zielgruppe ist Einsteiger
- **Priorität:** niedrig

## Änderungsprotokoll

### [Uhrzeit] - expand_section "Browser-Speicher"
- Abschnitt von ~100 auf ~250 Wörter erweitert
- Neue Quellen: [Heise-Artikel]

### [Uhrzeit] - add_section "Kosten"
- Neuer H2-Abschnitt "Was kostet Bitwarden?"
- Tabelle Free vs. Premium hinzugefügt

### [Uhrzeit] - change_tone
- Akademische Formulierungen durch direkte Sprache ersetzt
```

## Verarbeitungsregeln

1. **Klare Änderungen** → direkt umsetzen
2. **Unklare Änderungen** → per Telegram nachfragen
3. **Widersprüchliches Feedback** → nachfragen
4. **Änderungen dokumentieren** → ins Änderungsprotokoll

## Status-Übergänge

| Feedback-Status | Bedeutung |
|---|---|
| `open` | Neu, noch nicht verarbeitet |
| `inprogress` | Wird gerade bearbeitet |
| `done` | Angewendet, Artikel aktualisiert |
| `rejected` | Verworfen (mit Begründung) |

## Dateinamen-Konvention

```
[artikel-slug]_[YYYY-MM-DD_HHMMSS].md
```

Beispiel: `passwort-manager_2026-03-18_153000.md`
