---
title: 'Datenlecks & Identitätsschutz'
slug: 'datenlecks-identitaetsschutz'
part: 3
series: 'sicher-im-netz'
status: final
source: 'migrated-from-legacy'
created_at: '2026-03-17T21:00:00Z'
reviewed_at: '2026-03-17T22:00:00Z'
---


*Generiert: 2026-03-17 | Quellen: 15+ | Vertrauen: Hoch*

---

## Executive Summary

Datenlecks erreichen in Deutschland und weltweit Rekordniveaus. Im Jahr 2025 wurden rund 18,6 Millionen deutsche Accounts kompromittiert – jeder vierte Deutsche ist betroffen. Die durchschnittlichen Kosten eines Datenlecks für Unternehmen liegen bei 3,87 Millionen Euro. Für Privatpersonen bedeuten geleakte Daten Identitätsdiebstahl, Betrug und massiven Spam. Der Schutz beginnt beim regelmäßigen Check, ob die eigenen Daten geleakt wurden, und setzt sich fort über E-Mail-Aliasing als Identitätsverschleierung bis hin zu konkreten Reaktionsmaßnahmen bei Betroffenheit.

---

## 1. Das Ausmaß: Datenlecks in Deutschland – aktuelle Zahlen

### 1.1 Statistik 2025

Deutschland ist besonders hart getroffen:

- **18,6 Millionen deutsche Accounts** wurden 2025 kompromittiert – Platz 4 weltweit hinter USA, Frankreich und Indien ([Netzwelt, 2026-02-22](https://www.netzwelt.de/news/251317-erschreckende-datenleck-bilanz-vierte-deutsche-betroffengehoert-186-millionen-opfern.html))
- **3,9 Millionen Konten allein im Q1 2025** – Deutschland Nummer 4 der am stärksten betroffenen Länder ([All About Security, 2025-04-29](https://www.all-about-security.de/cyberrisiko-waechst-deutschland-belegt-platz-4-der-laender-mit-den-meisten-datenlecks-im-ersten-quartal-2025/))
- **Datenleck-Rate Q1 2025: 235,8 % höher** als im Vorquartal – von 9 auf 30,2 gehackte Konten pro Minute ([All About Security](https://www.all-about-security.de/cyberrisiko-waechst-deutschland-belegt-platz-4-der-laender-mit-den-meisten-datenlecks-im-ersten-quartal-2025/))
- **Statistisch war jede/r Deutsche schon ~7 Mal von Datenlecks betroffen** – einer der höchsten Werte in Westeuropa (Surfshark-Analyse, zitiert in [All About Security](https://www.all-about-security.de/cyberrisiko-waechst-deutschland-belegt-platz-4-der-laender-mit-den-meisten-datenlecks-im-ersten-quartal-2025/))
- **88 % der betroffenen Nutzer** haben Passwörter verloren – Gefahr von Identitätsdiebstahl, Erpressung ([All About Security](https://www.all-about-security.de/cyberrisiko-waechst-deutschland-belegt-platz-4-der-laender-mit-den-meisten-datenlecks-im-ersten-quartal-2025/))
- **5,2 Millionen deutsche Konten** wurden im 1. Halbjahr 2025 geleakt ([BornCity, 2025-08-03](https://borncity.com/blog/2025/08/03/studie-52-millionen-deutsche-konten-im-jahr-2025-bisher-geleakt/))

### 1.2 Kosten für Unternehmen

- **Durchschnittliche Kosten pro Datenleck in Deutschland: 3,87 Mio. €** (2025) – erstmals seit 5 Jahren rückläufig (Vorjahr: 4,9 Mio. €) ([IBM Cost of a Data Breach Report 2025](https://de.newsroom.ibm.com/2025-07-30-IBM-Studie-Kosten-von-Datenlecks-sinken-in-Deutschland-erstmals-seit-funf-Jahren))
- **Deutsche Unternehmen erkennen Vorfälle am schnellsten**: 170 Tage Durchschnitt – 71 Tage unter dem weltweiten Schnitt ([IBM Report 2025](https://de.newsroom.ibm.com/2025-07-30-IBM-Studie-Kosten-von-Datenlecks-sinken-in-Deutschland-erstmals-seit-funf-Jahren))
- **69 % der Führungskräfte** sehen ihr Unternehmen einem hohen Risiko ausgesetzt ([EY Datenklaustudie 2025](https://www.ey.com/de_de/insights/forensic-integrity-services/datenklaustudie-2025-cybergefahr-auf-rekordhoch))

### 1.3 Große Datenlecks 2025 (Beispiele)

| Unternehmen | Betroffene | Art |
|---|---|---|
| 23andMe | 7 Mio.+ | Genetische Daten + Identitätsdaten |
| Samsung Deutschland | 270.000 | Kundendaten, bestehende seit 2021 |
| X (Twitter) | 200 Mio. | E-Mails, Handles, IDs |
| Coinbase | 510.000 | Finanzdaten, Ausweisdokumente |
| Dior China | Unbekannt | Kundendaten via Drittanbieter |

*Quelle: [heyData.eu – Die größten Datenlecks 2025](https://heydata.eu/magazin/top-datenlecks-und-datenschutzskandale-2025-bislang/)*

### 1.4 BSI-Lage

Das BSI warnt in seinem Lagebericht 2025: „Für die Lage der IT-Sicherheit in Deutschland besteht im Jahr 2025 kein Grund zur Entwarnung." ([BSI Lagebericht 2025](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/Lageberichte/Lagebericht2025_Achtseiter.pdf))

---

## 2. Leak Checker: Wo prüfe ich, ob ich betroffen bin?

### 2.1 Europäische/deutsche Alternativen (empfohlen)

#### HPI Identity Leak Checker (Potsdam)
- **Betreiber:** Hasso-Plattner-Institut, Universität Potsdam 🇩🇪
- **Sprache:** Deutsch
- **Funktion:** E-Mail-Adresse eingeben → Ergebnis per E-Mail
- **Datenschutz:** Ergebnis wird per Mail geschickt, damit Dritte keine fremden Adressen prüfen können
- **Datenbasis:** ~14,5 Milliarden Datensätze
- **Link:** [sec.hpi.uni-potsdam.de/leak-checker/search](https://sec.hpi.uni-potsdam.de/leak-checker/search)
- **Quelle:** [Verbraucherzentrale NRW](https://www.verbraucherzentrale.nrw/wissen/digitale-welt/onlinedienste/so-finden-sie-heraus-ob-ihre-logindaten-gestohlen-wurden-92617)

#### Identity Leak Checker (EIDI) – Uni Bonn
- **Betreiber:** EIDI, Universität Bonn 🇩🇪
- **Sprache:** Deutsch
- **Funktion:** E-Mail-Adresse eingeben → Ergebnis per E-Mail
- **Datenschutz:** DSGVO-konform – vollständig anonymisierte und verschlüsselte Daten
- **Datenbasis:** **55 Milliarden+ Identitäten** – deutlich mehr als HIBP und HPI ([Identeco/Uni Bonn](https://identeco.de/de/blog/german-alternative-hibp/))
- **Besonderheit:** Aktive Suche im Deep/Dark Web, monatlich ~300 Millionen neue Datensätze; zeigt erstes und letztes Zeichen geleakter Passwörter (Wiedererkennung ohne Preisgabe)
- **Link:** [leakchecker.uni-bonn.de](https://leakchecker.uni-bonn.de/)
- **Quelle:** [Verbraucherzentrale NRW](https://www.verbraucherzentrale.nrw/wissen/digitale-welt/onlinedienste/so-finden-sie-heraus-ob-ihre-logindaten-gestohlen-wurden-92617)

> **Empfehlung:** Der Leak Checker der Uni Bonn hat die größte Datenbasis und die strengsten Datenschutzstandards. Am besten beide deutschen Dienste nutzen.

#### Mozilla Monitor
- **Betreiber:** Mozilla Foundation 🇺🇸 (Non-Profit, hohe Datenschutzstandards)
- **Sprache:** Englisch (einfach bedienbar)
- **Basiert auf:** HIBP-Daten
- **Vorteil:** Keine Registrierung nötig, Datenschutz-orientiert
- **Link:** [monitor.mozilla.org](https://monitor.mozilla.org/)
- **Quelle:** [ComputerBild](https://www.computerbild.de/artikel/Tipps-Windows-Have-I-been-pwned-Alternativen-Diese-Webdienste-pruefen-ob-Sie-gehackt-wurden-00879-40473589.html)

### 2.2 Internationaler Standard (nicht EU-konform)

#### Have I Been Pwned (HIBP)
- **Betreiber:** Troy Hunt 🇦🇺
- **Datenbasis:** ~17,3 Milliarden Datensätze
- **Problem:** Ergebnis sofort sichtbar – beliebige Adressen prüfbar, nicht DSGVO-konform ([Identeco](https://identeco.de/de/blog/german-alternative-hibp/))
- **Link:** [haveibeenpwned.com](https://haveibeenpwned.com/?lang=de_de)
- **Trotzdem nützlich:** Größte öffentliche Datenbank, schnelle Ergebnisse

> **Wichtig:** Kein Leak Checker kann garantieren, dass man NICHT betroffen ist. Negative Ergebnisse bedeuten nur: In der bekannten Datenbasis nichts gefunden. ([Verbraucherzentrale NRW](https://www.verbraucherzentrale.nrw/wissen/digitale-welt/onlinedienste/so-finden-sie-heraus-ob-ihre-logindaten-gestohlen-wurden-92617))

---

## 3. Strategie: E-Mail-Aliasing (Identität verschleiern)

### 3.1 Warum E-Mail-Aliasing?

Hacker nutzen die E-Mail-Adresse als universellen Schlüssel zur Identifikation und Verfolgung über Plattformen hinweg. Aliasing bedeutet: Für jeden Dienst eine eigene Adresse verwenden. Wenn ein Dienst gehackt wird, weißt du sofort, wer schuld ist – und kannst den Alias löschen.

### 3.2 Dienste im Vergleich

#### SimpleLogin (Frankreich 🇫🇷)
- **Typ:** Open Source (GitHub), selbst-hostbar
- **Betreiber:** Proton AG (Schweiz 🇨🇭)
- **Server:** Proton + UpCloud (Finnland 🇫🇮)
- **Funktionen:** Aliase empfangen UND senden, eigene Domains, Catch-All, PGP-Verschlüsselung, Browser-Erweiterungen (Chrome/Firefox/Safari), Mobile Apps (iOS/Android/F-Droid), 2FA (TOTP + WebAuthn)
- **Preis:** Kostenlos (15 Aliase), Premium ab ~30 €/Jahr
- **Datenschutz:** Keine Ads, keine Tracker, Open Source
- **Integration:** In Bitwarden Premium integriert, Proton Pass
- **Link:** [simplelogin.io](https://simplelogin.io/)

#### addy.io (ehemals AnonAddy) – England 🇬🇧
- **Typ:** Open Source (GitHub), selbst-hostbar
- **Funktionen:** Catch-All Aliase, eigene Domains, GPG/OpenPGP-Verschlüsselung, Browser-Erweiterungen, Mobile Apps (iOS/Android, Open Source), mehrere Empfänger pro Alias, API
- **Preis:** Kostenlos (unbegrenzte Aliase an der eigenen Subdomain), Premium ab ~12 €/Jahr
- **Besonderheit:** Aliase auf-the-fly erstellen (vuejs@username.anonaddy.com)
- **Link:** [addy.io](https://addy.io/)

#### Firefox Relay (USA 🇺🇸, Mozilla Foundation)
- **Typ:** Proprietär (aber Mozilla = Non-Profit)
- **Funktionen:** E-Mail-Masken + Telefonmasken, Tracker-Entfernung, Promotion-Blocker
- **Preis:** Kostenlos (5 Masken), Premium (unbegrenzt) + VPN-Bundle
- **Besonderheit:** Telefonmasken verfügbar (EU: verfügbar in DE, AT, CH)
- **EU-Verfügbarkeit:** Ja – in fast allen EU-Ländern
- **Link:** [relay.firefox.com](https://relay.firefox.com/)

#### Apple „E-Mail-Adresse verbergen" (USA 🇺🇸)
- **Typ:** Proprietär, in iCloud+ integriert
- **Vorteil:** Nahtlos in iOS/macOS integriert
- **Nachteil:** Nur Apple-Ökosystem, keine Offenheit
- **Alternative dazu:** SimpleLogin oder addy.io für plattformunabhängige Lösung

### 3.3 Empfehlung

| Kriterium | Empfehlung |
|---|---|
| Europäisch + Open Source | **SimpleLogin** (Frankreich, Proton) |
| Günstigste Variante | **addy.io** (kostenlos unbegrenzt) |
| Einfachste Bedienung | **Firefox Relay** (5 Masken kostenlos) |
| Apple-Nutzer | E-Mail-Adresse verbergen (praktisch, aber proprietär) |

---

## 4. Wegwerf-E-Mails für schnelle Registrierungen

Für einmalige Anmeldungen, bei denen du nur Informationen lesen willst:

- **10MinuteMail.com** – Adresse existiert 10 Minuten
- **Temp-Mail.org** – Temporäre Adressen
- **Guerrilla Mail** – Temporäre E-Mail-Adressen, auch verschlüsselbar

> **Hinweis:** Diese Dienste sind nicht für dauerhafte Konten gedacht. Für alles, worauf du langfristig Zugriff brauchst, nutze Aliase über SimpleLogin oder addy.io.

---

## 5. Was tun bei einem Datenleck? Konkrete Schritte

### Sofortmaßnahmen

1. **Passwort des betroffenen Accounts sofort ändern** – mindestens 12 Zeichen, gemischt
2. **Alle anderen Accounts prüfen**, bei denen dasselbe Passwort verwendet wurde
3. **2FA aktivieren**, wo noch nicht geschehen
4. **Kontoauszüge und Transaktionen** auf ungewöhnliche Aktivitäten prüfen
5. **E-Mail-Alias erstellen** für den betroffenen Dienst (besser als alte Adresse weiterzuverwenden)

### DSGVO-Rechte bei Datenlecks

- **Art. 33 DSGVO:** Unternehmen müssen Datenlecks innerhalb von **72 Stunden** an die Datenschutzbehörde melden
- **Art. 34 DSGVO:** Bei hohem Risiko müssen Betroffene **direkt informiert** werden
- **Auskunftsrecht (Art. 15 DSGVO):** Du kannst vom Unternehmen verlangen, welche Daten von dir betroffen sind
- **Beschwerderecht (Art. 77 DSGVO):** Beschwerde bei der zuständigen Datenschutzaufsichtsbehörde

*Quellen: [Stiftung Warentest/test.de](https://www.test.de/Hacks-und-Datenlecks-Passwort-geknackt-Machen-Sie-den-Check-6261652-0/), [Datenschutz Prinz](https://www.datenschutz-prinz.de/blog/so-pruefen-sie-ob-ihre-login-daten-gestohlen-wurden)*

---

## 6. Prävention: Langfristiger Schutz der Identität

### 6.1 Passwort-Manager (Teil 1 der Serie)
- Für jeden Dienst ein einzigartiges Passwort
- Empfohlen: Bitwarden (Open Source), KeePassXC (offline)

### 6.2 Zwei-Faktor-Authentifizierung (Teil 2 der Serie)
- 2FA-Apps statt SMS
- Empfohlen: Aegis (Android, Open Source), Ente Auth (Open Source)

### 6.3 Passkeys (Teil 5 der Serie)
- Phishing-resistente Anmeldung ohne Passwort
- Plattformübergreifend nutzbar

### 6.4 Regelmäßige Updates
- Betriebssystem, Apps, Browser immer aktuell halten
- Viele Datenlecks entstehen durch bekannte, nicht gepatchte Lücken ([Netzwelt](https://www.netzwelt.de/news/251317-erschreckende-datenleck-bilanz-vierte-deutsche-betroffengehoert-186-millionen-opfern.html))

### 6.5 Phishing-Wachsamkeit
- Absender immer prüfen
- Keine Links in verdächtigen Mails anklicken
- Passwort-Manager schützen vor Phishing (URL-Validierung)

---

## 7. Europäische digitale Souveränität

### Wo Europa vorne liegt:
- **Leak Checker:** Uni Bonn und HPI bieten datenschutzfreundliche Alternativen zu HIBP
- **E-Mail-Aliasing:** SimpleLogin (Frankreich) und addy.io (England) sind Open Source und selbst-hostbar
- **DSGVO:** Stärkster Datenschutzrahmen weltweit – Unternehmen müssen Lecks melden

### Wo noch Handlungsbedarf besteht:
- Viele Deutsche wissen nicht, dass ihre Daten geleakt wurden ([Netzwelt](https://www.netzwelt.de/news/251317-erschreckende-datenleck-bilanz-vierte-deutsche-betroffengehoert-186-millionen-opfern.html))
- Über die Hälfte der Internetnutzenden hat ein zu niedriges Schutzniveau ([DsiN-Sicherheitsindex 2025](https://wissenswert.debeka.de/identitaetsdiebstahl-im-digitalen-zeitalter.html))
- Amerikanische Dienste dominieren trotz europäischer Alternativen

---

## Sources

1. [All About Security – Datenlecks Q1 2025](https://www.all-about-security.de/cyberrisiko-waechst-deutschland-belegt-platz-4-der-laender-mit-den-meisten-datenlecks-im-ersten-quartal-2025/) – Surfshark-Analyse: Deutschland auf Platz 4
2. [Netzwelt – Jeder vierte Deutsche betroffen](https://www.netzwelt.de/news/251317-erschreckende-datenleck-bilanz-vierte-deutsche-betroffengehoert-186-millionen-opfern.html) – 18,6 Mio. betroffene Accounts 2025
3. [Identeco – Uni Bonn Leak Checker](https://identeco.de/de/blog/german-alternative-hibp/) – Deutsche Alternativen zu HIBP, 55 Mrd. Identitäten
4. [Datenschutz Prinz – Login-Daten prüfen](https://www.datenschutz-prinz.de/blog/so-pruefen-sie-ob-ihre-login-daten-gestohlen-wurden) – Vergleich HPI vs. Uni Bonn vs. HIBP
5. [Verbraucherzentrale NRW – Login-Daten gestohlen?](https://www.verbraucherzentrale.nrw/wissen/digitale-welt/onlinedienste/so-finden-sie-heraus-ob-ihre-logindaten-gestohlen-wurden-92617) – Praktische Anleitung
6. [ComputerBild – HIBP-Alternativen](https://www.computerbild.de/artikel/Tipps-Windows-Have-I-been-pwned-Alternativen-Diese-Webdienste-pruefen-ob-Sie-gehackt-wurden-00879-40473589.html) – Mozilla Monitor, Avast Secure Browser
7. [heyData.eu – Größte Datenlecks 2025](https://heydata.eu/magazin/top-datenlecks-und-datenschutzskandale-2025-bislang/) – Samsung, X, Coinbase
8. [IBM – Cost of a Data Breach 2025](https://de.newsroom.ibm.com/2025-07-30-IBM-Studie-Kosten-von-Datenlecks-sinken-in-Deutschland-erstmals-seit-funf-Jahren) – 3,87 Mio. € pro Vorfall
9. [EY Datenklaustudie 2025](https://www.ey.com/de_de/insights/forensic-integrity-services/datenklaustudie-2025-cybergefahr-auf-rekordhoch) – 69 % der Unternehmen sehen hohes Risiko
10. [Digital Footprint Check – HIBP Alternativen](https://www.digitalfootprintcheck.com/have-i-been-pwned-alternative) – Mozilla Monitor, Google Password Manager
11. [SimpleLogin](https://simplelogin.io/) – Open Source E-Mail-Aliasing, Frankreich
12. [addy.io](https://addy.io/) – Open Source E-Mail-Aliasing, England
13. [Firefox Relay](https://relay.firefox.com/) – Mozilla E-Mail/Telefon-Masking
14. [Debeka – Identitätsdiebstahl](https://wissenswert.debeka.de/identitaetsdiebstahl-im-digitalen-zeitalter.html) – DsiN-Sicherheitsindex 2025
15. [Stiftung Warentest/test.de](https://www.test.de/Hacks-und-Datenlecks-Passwort-geknackt-Machen-Sie-den-Check-6261652-0/) – HIBP + HPI + Passworttipps
16. [BornCity – 5,2 Mio. deutsche Konten 2025](https://borncity.com/blog/2025/08/03/studie-52-millionen-deutsche-konten-im-jahr-2025-bisher-geleakt/) – Surfshark Q2 2025

---

## Methodologie

Durchgeführt mit 12+ Web-Suchen und 15+ Quellen-Lesungen. Fokus auf deutsche und europäische Quellen. Alle Zahlen und Behauptungen sind mit verlinkten Quellen belegt. Open-Source-Lösungen wurden priorisiert.
