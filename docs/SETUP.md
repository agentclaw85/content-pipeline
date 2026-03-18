# Setup Guide

## Voraussetzungen

- OpenClaw installiert
- SSH-Key für GitHub konfiguriert
- Blog-Repository geklont
- ClawHub Skills installiert

## 1. Skills installieren

```bash
clawhub install deep-research-pro
clawhub install seo-article-gen
clawhub install content-generation
```

## 2. Blog-Repository klonen

```bash
cd [WORKSPACE]
git clone git@github.com:[ORG]/[BLOG-REPO].git
```

## 3. Verzeichnisstruktur erstellen

```bash
cd [WORKSPACE]/[BLOG-REPO]
mkdir -p content/{proposals,research,generated}
```

## 4. Crons einrichten

### Variablen setzen

```bash
WORKSPACE="[DEIN_WORKSPACE]"        # z.B. /root/.openclaw/workspace/portable-tools-blog
CHAT_ID="[DEINE_TELEGRAM_ID]"       # z.B. 20239839
```

### Research Cron (21:00)

```bash
openclaw cron add \
  --name "Content Research" \
  --cron "0 21 * * *" \
  --tz "Europe/Berlin" \
  --session isolated \
  --message "Content-Pipeline: Research-Phase. [VOLLER PROMPT SIEHE crons/research-cron.md]" \
  --model "openrouter/deepseek/deepseek-chat-v3-0324:free" \
  --light-context \
  --thinking off \
  --announce \
  --channel telegram \
  --to "$CHAT_ID"
```

### Review Cron (22:00)

```bash
openclaw cron add \
  --name "Content Review" \
  --cron "0 22 * * *" \
  --tz "Europe/Berlin" \
  --session isolated \
  --message "Content-Pipeline: Review-Phase. [VOLLER PROMPT SIEHE crons/review-cron.md]" \
  --model "openrouter/deepseek/deepseek-chat-v3-0324:free" \
  --light-context \
  --thinking off \
  --announce \
  --channel telegram \
  --to "$CHAT_ID"
```

### Article Cron (23:00)

```bash
openclaw cron add \
  --name "Content Article" \
  --cron "0 23 * * *" \
  --tz "Europe/Berlin" \
  --session isolated \
  --message "Content-Pipeline: Artikel-Generator. [VOLLER PROMPT SIEHE crons/article-cron.md]" \
  --model "openrouter/deepseek/deepseek-chat-v3-0324:free" \
  --light-context \
  --thinking off \
  --announce \
  --channel telegram \
  --to "$CHAT_ID"
```

## 5. Erstes Proposal erstellen

```bash
cat > [WORKSPACE]/[BLOG-REPO]/content/proposals/mein-erstes-thema.md << 'EOF'
---
title: 'Mein erstes Thema'
slug: 'mein-erstes-thema'
status: pending
created_at: '$(date -Iseconds)'
---

## Thema

Beschreibung des Themas.

## Recherche-Fokus

- Punkt 1
- Punkt 2
- Punkt 3

## Quellen-Hinweise

- Empfohlene Quellen
EOF
```

## 6. Pipeline starten

```bash
# Manuell testen
openclaw cron run [RESEARCH_CRON_ID]

# Oder warten auf automatische Ausführung um 21:00
```

## 7. Status prüfen

```bash
openclaw cron list
openclaw cron runs --id [CRON_ID] --limit 5
```

## Hinweise

- **Free Models:** DeepSeek Free hat Rate-Limits. Bei Problemen Retry nach ein paar Minuten.
- **Branches:** Alle Änderungen gehen auf `research/YYYY-MM-DD`, nicht auf `main`.
- **Logging:** Jeder Cron schreibt eine Telegram-Nachricht bei Abschluss.
- **Idempotent:** Mehrfaches Ausführen erzeugt keine Duplikate (Status-Locking).
