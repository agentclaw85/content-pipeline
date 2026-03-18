# Review Cron

## Zeitplan

- **Cron:** `0 22 * * *` (22:00 Europe/Berlin)
- **Session:** isolated
- **Model:** DeepSeek Free
- **Delivery:** Telegram (announce)

## Prompt

```
Content-Pipeline: Review-Phase. Verarbeite GENAU EIN Research-Dokument.

SCHRITT 1: Finde nächstes Research-Dokument
- Lese [WORKSPACE]/content/research/
- Priorität: 1) status: inreview 2) status: draft
- Ignoriere: status: final, status: rejected, status: article_generated
- Falls kein Dokument gefunden → beenden

SCHRITT 2: Status setzen
- Wenn draft → setze auf inreview
- Wenn bereits inreview → weiter mit Review

SCHRITT 3: Dokument lesen

SCHRITT 4: Validierung
- Faktenprüfung: Alle Behauptungen auf Korrektheit
- Quellenprüfung: Mind. 5 Links per web_fetch testen
- Unbelegte Behauptungen markieren
- EU/deutsche Lösungen priorisiert?
- OS-Alternativen bei US-Anbietern genannt?

SCHRITT 5: Auto-Fix (kleine Fehler)
- Tote Links ersetzen, Fehlende Quellen ergänzen, Tippfehler korrigieren
- Alle Änderungen dokumentieren

SCHRITT 6: Unsicherheiten markieren
- ⚠️ bei größeren Unsicherheiten
- [NEEDS_VERIFICATION] bei unbelegten Behauptungen

SCHRITT 7: Review Notes am ENDE hinzufügen

SCHRITT 8: Status setzen
- Alle Probleme behoben? → status: final
- Kleine offene Punkte (markiert)? → status: final (mit Markierungen)
- Schwere Mängel (massenhaft unbelegt, schlechte Quellen)? → status: rejected
  → Grund in Review Notes dokumentieren

SCHRITT 9: Frontmatter aktualisieren
- status + reviewed_at

SCHRITT 10: Git Push
- cd [REPO]
- BRANCH="research"
- git checkout $BRANCH 2>/dev/null || git checkout -b $BRANCH
- git add content/
- git commit -m "Review [slug]: [status]"
- git push origin $BRANCH

SCHRITT 11: Telegram
- Bei final: "✅ Review [slug]: final | Confidence: [X/10]"
- Bei rejected: "❌ Review [slug]: rejected | Grund: [kurz]"

NUR EIN Dokument pro Lauf. Alles auf Deutsch.
```

## Status-Entscheidungen

| Szenario | Status |
|---|---|
| Alles passt, kleine Markierungen | `final` |
| Einige unbelegte Aussagen (markiert) | `final` mit ⚠️ |
| Massenhaft unbelegt, schlechte Quellen | `rejected` |
| Braucht manuelle Prüfung | `inreview` |
