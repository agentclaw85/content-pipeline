# Article Generation Cron

## Zeitplan

- **Cron:** `0 23 * * *` (23:00 Europe/Berlin)
- **Session:** isolated
- **Model:** DeepSeek Free
- **Delivery:** Telegram (announce)

## Prompt

```
Content-Pipeline: Artikel-Generator. Verarbeite GENAU EIN Research-Dokument.

SCHRITT 1: Finde nächstes validiertes Research
- Lese [WORKSPACE]/content/research/
- Finde erstes Dokument mit status: final
- Bestimme Slug aus Frontmatter
- Prüfe ob /content/generated/[slug].md bereits existiert → falls ja, nächste nehmen
- Falls kein final-Dokument existiert → beenden

SCHRITT 2: Prüfe ob Artikel existiert
- [WORKSPACE]/content/generated/[slug].md
- Falls existiert → beenden (keine Duplikate)

SCHRITT 3: Skills lesen (PFLICHT)
- [WORKSPACE]/skills/seo-article-gen/SKILL.md (HAUPTSKILL)

SCHRITT 4: Artikel generieren (2.000-2.500 Wörter, Deutsch)
- H1: SEO-optimierter Titel mit Haupt-Keyword
- Meta-Description (155-160 Zeichen)
- Hook → Problem → Lösung in Einleitung
- H2/H3-Hierarchie, Fließtext (keine Stichpunktlisten)
- Zahlen/Fakten mit Quellen belegt
- FAQ-Sektion (4-6 Fragen)
- Fazit mit Call-to-Action
- Quellen am Ende
- Frontmatter: title, date, author, description, alias, status: draft, source: [research-slug], created_at: [ISO-Timestamp]

SCHRITT 5: Content-Richtlinien (EU-Fokus)
- Europäische/deutsche Lösungen zuerst
- Open Source bevorzugt
- US-Anbieter nur bei Dominanz → immer EU/OS-Alternative dazu
- Alle Behauptungen belegbar

SCHRITT 6: Speichern
- [WORKSPACE]/content/generated/[slug].md

SCHRITT 7: Research-Status ändern
- Setze Research-Dokument status: final → status: article_generated

SCHRITT 8: Git Push
- cd [REPO]
- BRANCH="research"
- git checkout $BRANCH 2>/dev/null || git checkout -b $BRANCH
- git add content/
- git commit -m "Article: [slug]"
- git push origin $BRANCH

SCHRITT 9: Telegram: "Artikel [slug] generiert ([Wortanzahl] Wörter, status: draft)"

WICHTIG: seo-article-gen Struktur einhalten. Kein Handout, kein Bullet-Point-Dump.
Blog-Artikel mit Fließtext und Struktur.

NUR EIN Artikel pro Lauf. Idempotent.
```

## Artikel-Anforderungen (seo-article-gen)

| Element | Anforderung |
|---|---|
| Titel | H1, SEO-optimiert, Haupt-Keyword |
| Meta | 155-160 Zeichen |
| Einleitung | Hook → Problem → Lösung |
| Struktur | H2/H3-Hierarchie |
| Stil | Fließtext, nicht Stichpunkte |
| Länge | 2.000-2.500 Wörter |
| FAQ | 4-6 Fragen |
| Fazit | CTA |
| Quellen | Am Ende aufgeführt |
| Schema | Article + FAQ |
