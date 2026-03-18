# Human Feedback (Event-driven, kein Cron)

## Trigger

Kein Cron. Feedback wird **sofort** verarbeitet, wenn es im Chat eingereicht wird:

1. User sendet Feedback-Nachricht
2. Clawie speichert es in `/content/human/`
3. Clawie wendet Feedback direkt an
4. Ergebnis wird im Chat zurückgemeldet

## Prompt

```
Content-Pipeline: Human Feedback. Verarbeite GENAU EINE Feedback-Datei.

SCHRITT 1: Finde nächstes offenes Feedback
- Lese [WORKSPACE]/content/human/
- Finde erstes Dokument mit status: open
- Falls kein offenes Feedback existiert → beenden

SCHRITT 2: Feedback lesen
- Lese die Feedback-Datei komplett
- Extrahiere: target (Artikel), Original Feedback, Strukturierte Aktionen

SCHRITT 3: Zielartikel lesen
- Lese [WORKSPACE]/content/generated/[target]
- Status auf inprogress setzen (in Feedback-Datei)

SCHRITT 4: Aktionen anwenden
Für jede strukturierte Aktion:

- expand_section: Abschnitt finden, erweitern mit mehr Details/Beispielen
- shorten_section: Abschnitt finden, auf Kernesenz kürzen
- rewrite_section: Abschnitt komplett neu formulieren
- add_source: Neue Quelle recherchieren und einfügen
- remove_source: Quelle entfernen, ggf. ersetzen
- change_tone: Sprache anpassen (z.B. weniger akademisch, direkter)
- add_section: Neuen Abschnitt erstellen
- fix_fact: Falsche Angabe korrigieren

WICHTIG:
- Jede Änderung dokumentieren (Änderungsprotokoll in Feedback-Datei)
- Unklare Änderungen → NICHT raten, per Telegram nachfragen
- Widersprüchliches Feedback → nachfragen
- Keine stillen Änderungen!

SCHRITT 5: Artikel aktualisieren
- Artikel speichern
- Änderungsprotokoll in Feedback-Datei eintragen
- Referenz zur Feedback-Datei im Artikel (am Ende, als Kommentar)

SCHRITT 6: Status aktualisieren
- Feedback-Datei: status: open → status: done
- processed_at: [ISO-Timestamp] hinzufügen
- Artikel: status bleibt draft (oder auf inreview bei größeren Änderungen)

SCHRITT 7: Git Push
- cd [REPO]
- BRANCH="research/$(date +%Y-%m-%d)"
- git checkout $BRANCH 2>/dev/null || git checkout -b $BRANCH
- git add content/
- git commit -m "Feedback applied: [slug] - [anzahl] changes"
- git push origin $BRANCH

SCHRITT 8: Telegram
- "✅ Feedback [slug] verarbeitet: [Zusammenfassung der Änderungen]"
- Bei Unklarheiten: "❓ Unklar bei [slug]: [Frage an User]"

NUR EIN Feedback pro Lauf. Alles auf Deutsch.
```

## Cron-Erstellung (OpenClaw CLI)

```bash
openclaw cron add \
  --name "Human Feedback" \
  --cron "*/30 * * * *" \
  --tz "Europe/Berlin" \
  --session isolated \
  --message "[PROMPT OBEN]" \
  --model "openrouter/deepseek/deepseek-chat-v3-0324:free" \
  --light-context \
  --thinking off \
  --announce \
  --channel telegram \
  --to "$CHAT_ID"
```

## Manueller Trigger

Feedback kann auch manuell über den Chat eingereicht werden:

1. User schickt Feedback-Nachricht
2. Clawie speichert es als Datei in `/content/human/`
3. Cron verarbeitet es beim nächsten Lauf (oder manuell via `openclaw cron run`)

## Beispiel

**User-Message:**
> "Der YubiKey-Artikel ist gut, aber der Abschnitt über Verlust ist zu knapp. Erkläre genauer, wie die Backup-Strategie funktioniert. Außerdem fehlt ein Preisvergleich zwischen YubiKey 5 NFC und Nitrokey."

**Clawie erstellt:**
```markdown
---
title: 'Feedback: YubiKey'
slug: 'yubikey-physischer-schluessel'
target: 'yubikey-physischer-schluessel.md'
status: open
created_at: '2026-03-18T15:30:00Z'
---

## Original Feedback

Der YubiKey-Artikel ist gut, aber...

## Strukturierte Aktionen

### 1. expand_section — "Verlust/Backup"
- Backup-Strategie genauer erklären
- Priorität: hoch

### 2. add_section — "Preisvergleich YubiKey vs. Nitrokey"
- Tabelle mit Specs und Preisen
- Priorität: mittel
```
