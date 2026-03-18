# Research Cron

## Zeitplan

- **Cron:** `0 21 * * *` (21:00 Europe/Berlin)
- **Session:** isolated
- **Model:** DeepSeek Free
- **Delivery:** Telegram (announce)

## Prompt

```
Content-Pipeline: Research-Phase. Verarbeite GENAU EIN Proposal.

SCHRITT 1: Finde nächstes Proposal
- Lese [WORKSPACE]/content/proposals/
- Finde erstes Proposal mit status: pending
- Bestimme Slug aus dem Proposal (frontmatter: slug)
- Prüfe ob /content/research/[slug].md bereits existiert → falls ja, nächste Proposal nehmen
- Falls kein pending Proposal existiert → beenden

SCHRITT 2: Proposal lesen
- Lese das gefundene Proposal komplett
- Extrahiere: Thema, Recherche-Fokus, Quellen-Hinweise

SCHRITT 3: Deep Research
- Nutze deep-research-pro Skill
- Mindestens 10-15 Quellen
- Priorität: Deutsche Quellen (Heise, Golem, BSI, CCC) → EU → OS → US (nur bei Dominanz)
- Alle Behauptungen belegbar

SCHRITT 4: Research speichern
- Datei: [WORKSPACE]/content/research/[slug].md
- Frontmatter:
  ---
  title: [aus Proposal]
  slug: [aus Proposal]
  part: [aus Proposal]
  status: draft
  source: [Proposal-Dateiname]
  created_at: [ISO-Timestamp]
  ---

SCHRITT 5: Proposal-Status ändern
- Setze im Proposal status: pending → status: inresearch

SCHRITT 6: Git Push auf Branch
- cd [REPO]
- BRANCH="research/$(date +%Y-%m-%d)"
- git checkout $BRANCH 2>/dev/null || git checkout -b $BRANCH
- git add content/
- git commit -m "Research: [slug] - status: draft"
- git push origin $BRANCH

SCHRITT 7: Telegram: "Research [slug] erstellt (status: draft)"

NUR EIN Dokument pro Lauf. Idempotent.
```

## Variablen

- `[WORKSPACE]` — OpenClaw Workspace (z.B. `/root/.openclaw/workspace/portable-tools-blog`)
- `[REPO]` — Blog-Repository-Pfad

## Cron-Erstellung (OpenClaw CLI)

```bash
openclaw cron add \
  --name "Content Research" \
  --cron "0 21 * * *" \
  --tz "Europe/Berlin" \
  --session isolated \
  --message "[PROMPT OBEN]" \
  --model "openrouter/deepseek/deepseek-chat-v3-0324:free" \
  --light-context \
  --thinking off \
  --announce \
  --channel telegram \
  --to "[CHAT_ID]"
```
