---
title: 'Datenleck geprüft: So findest du heraus, ob deine Daten im Netz sind'
date: '2027-03-09'
slug: 'datenlecks-identitaetsschutz'
part: 3
series: 'sicher-im-netz'
status: draft
source: 'datenlecks-identitaetsschutz'
created_at: '2026-03-17T22:00:00Z'
author: 'Steffen'
description: 'Jeder vierte Deutsche war 2025 von einem Datenleck betroffen. So prüfst du deine E-Mail-Adresse und schützt dich mit Aliasen vor dem nächsten Leak.'
alias: 'sicher_im_netz_teil_3_datenlecks_identitaetsschutz'
schema: 'Article'
faq:
  - q: 'Wie prüfe ich ob meine E-Mail bei einem Datenleck betroffen ist?'
    a: 'Nutze den Leak Checker der Uni Bonn (leakchecker.uni-bonn.de) oder Have I Been Pwned (haveibeenpwned.com). Gib deine E-Mail-Adresse ein und du siehst sofort, in welchen Lecks sie aufgetaucht ist.'
  - q: 'Was ist der Unterschied zwischen Uni Bonn Leak Checker und HIBP?'
    a: 'Der Uni Bonn Checker hat 55 Milliarden Identitäten, ist DSGVO-konform und verschickt Ergebnisse per E-Mail. HIBP ist größer (öffentlich) zeigt Ergebnisse sofort an, ist aber nicht DSGVO-konform.'
  - q: 'Sind E-Mail-Aliase sicherer als Plus-Tricks bei Gmail?'
    a: 'Ja. Der Gmail-Plus-Trick (name+shop@gmail.com) ist trivial zu deanonymisieren. Echte Aliase über SimpleLogin oder addy.io sind deutlich sicherer und nicht rückverfolgbar.'
  - q: 'Welcher Alias-Dienst ist der beste für deutsche Nutzer?'
    a: 'SimpleLogin (Frankreich, Proton) für EU-Datenschutz und Bitwarden-Integration. addy.io für unbegrenzte kostenlose Aliase. Firefox Relay für einfachste Bedienung.'
  - q: 'Was soll ich bei einem Datenleck tun?'
    a: 'Sofort Passwort ändern, 2FA aktivieren, Kontoauszüge prüfen und einen Alias für den betroffenen Dienst erstellen. Details im Artikel.'
---

# Datenleck geprüft: So findest du heraus, ob deine Daten im Netz sind

Jeder vierte Deutsche. Das ist nicht irgendeine Zahl — das sind **18,6 Millionen Accounts**, die allein 2025 kompromittiert wurden ([Netzwelt, 2026](https://www.netzwelt.de/news/251317-erschreckende-datenleck-bilanz-vierte-deutsche-betroffengehoert-186-millionen-opfern.html)). Und das sind nur die bekannten Fälle.

Wenn du noch nie geprüft hast, ob deine E-Mail-Adresse in einem Leak aufgetaucht ist, ist die Wahrscheinlichkeit hoch, dass du dazugehörst. Aber: Gewissheit ist besser als Ignoranz. In fünf Minuten weißt du Bescheid — und danach richten wir dafür sorgen, dass dich das nächste Leak weniger trifft.

## Warum Datenlecks jeden betreffen

Ein Datenleck ist kein Nischenproblem für Tech-Nerds. Es trifft Amazon genauso wie den kleinen Online-Shop um die Ecke. Die Konsequenzen reichen von nervigem Spam bis hin zu Identitätsdiebstahl und finanziellen Schäden.

Die durchschnittlichen Kosten eines Datenlecks für ein Unternehmen liegen bei **3,87 Millionen Euro** ([IBM Cost of a Data Breach 2025](https://de.newsroom.ibm.com/2025-07-30-IBM-Studie-Kosten-von-Datenlecks-sinken-in-Deutschland-erstmals-seit-funf-Jahren)). Für dich als Nutzer bedeutet ein Leak im schlimmsten Fall: gekaperte Konten, missbrauchte Identität, geleerte Konten.

### Was in einem typischen Leak steckt

Nicht nur E-Mail-Adressen. Viele Lecks enthalten:

- E-Mail-Adresse und Passwort
- Name, Adresse, Telefonnummer
- Geburtsdatum
- Zahlungsdaten
- In manchen Fällen: biometrische Daten oder Gesundheitsdaten

Je mehr Informationen kombiniert sind, desto gefährlicher wird es. Denn Hacker verknüpfen Daten aus verschiedenen Lecks zu immer detaillierteren Profilen.

## So prüfst du deine Betroffenheit

Es gibt drei empfehlenswerte Dienste — zwei davon aus Deutschland. Und genau die sollten deine erste Wahl sein.

### 🇩🇪 Leak Checker der Uni Bonn (Empfehlung Nr. 1)

Der [EIDI Leak Checker](https://leakchecker.uni-bonn.de/) der Universität Bonn hat die **größte Datenbasis** aller deutschen Dienste: über **55 Milliarden Identitäten** ([Identeco](https://identeco.de/de/blog/german-alternative-hibp/)). Der Dienst durchsucht aktiv das Deep und Dark Web und aktualisiert monatlich rund 300 Millionen Datensätze.

Deine Vorteile:

- **DSGVO-konform:** Ergebnis wird per E-Mail verschickt — niemand anderes sieht deine Daten
- **Detailgrad:** Zeigt das erste und letzte Zeichen geleakter Passwörter (genug zur Wiedererkennung, ohne das Passwort preiszugeben)
- **Umfang:** Größte Datenbasis im deutschsprachigen Raum

### 🇩🇪 HPI Identity Leak Checker

Der [HPI Identity Leak Checker](https://sec.hpi.de/ilc/) des Hasso-Plattner-Instituts in Potsdam zeigt nicht nur, ob du betroffen bist, sondern auch **welche Art von Daten** geleakt wurden: E-Mail, Passwort, Telefonnummer, Adresse oder sogar Ausweisdaten. Ergebnis ebenfalls per E-Mail.

### 🌍 Have I Been Pwned

[Have I Been Pwned](https://haveibeenpwned.com/) (HIBP) ist die weltweit größte Leak-Datenbank mit über 17 Milliarden Datensätzen. Die Ergebnisse kommen sofort — allerdings sind sie auch sofort öffentlich einsehbar, was nicht DSGVO-konform ist ([Identeco](https://identeco.de/de/blog/german-alternative-hibp/)).

> **Tipp:** Nutze die Uni Bonn und HPI als erste Wahl. HIBP als Ergänzung. Und erstelle bei HIBP einen Account mit aktivierten **Alerts** — dann erfährst du sofort, wenn deine Adresse in einem neuen Leak auftaucht.

## E-Mail-Aliase: Dein Schutzschild gegen das nächste Leak

Hier die unbequeme Wahrheit: Datenlecks werden nicht aufhören. Du kannst aber kontrollieren, wie stark dich das nächste trifft. Das Zauberwort heißt **E-Mail-Aliasing**.

### Das Problem mit deiner E-Mail-Adresse

Deine E-Mail-Adresse ist der **universelle Identifikator** im Netz. Wer überall dieselbe Adresse nutzt, wird über Plattformen hinweg getrackt, bekommt gezielte Phishing-Mails auf mehrere Konten und kann nicht nachvollziehen, wer die Adresse weitergegeben hat.

Die Lösung: Für jeden Dienst eine eigene Adresse. Nicht deine echte, sondern ein Alias.

### So funktioniert ein Alias

Ein E-Mail-Alias ist eine Weiterleitungsadresse. Du gibst beim Registrieren eine Adresse wie `shoppen.xyz123@simplelogin.com` an. Alle Mails gehen an dein echtes Postfach weiter — aber der Absender erfährt nie deine echte Adresse.

Wenn dieser Dienst gehackt wird: Alias löschen. Fertig. Der Hacker hat eine wertlose Adresse.

### Die besten Alias-Dienste

#### SimpleLogin 🇫🇷 (Empfehlung)

[SimpleLogin](https://simplelogin.io/) gehört seit 2022 zur Proton AG (Schweiz) und ist damit europäisch, Open Source und DSGVO-konform. Features:

- Aliase empfangen **und** senden
- Eigene Domains möglich
- PGP-Verschlüsselung
- Browser-Erweiterungen für Chrome, Firefox, Safari
- Mobile Apps (auch über F-Droid)
- **Bitwarden-Integration:** Aliase werden automatisch beim Anlegen neuer Logins erstellt
- Self-Hosting via Docker

Die Basisversion ist kostenlos (15 Aliase), Premium ab ~30 €/Jahr.

#### addy.io 🇬🇧

[Addy.io](https://addy.io/) (ehemals AnonAddy) ist ebenfalls Open Source und punktet mit **unbegrenzten Aliasen** in der kostenlosen Stufe. Besonders clever: Aliase werden on-the-fly erstellt — du musst sie nicht vorher anlegen. Einfach `beliebig@username.anonaddy.com` nutzen.

#### Firefox Relay 🇺🇸

[Mozilla Firefox Relay](https://relay.firefox.com/) bietet bis zu 5 E-Mail-Masks kostenlos, Premium liefert unbegrenzte Masks plus Telefonmaskierung. Mit Tracker-Entfernung und Werbeblocker. Verfügbar in Deutschland, Österreich und der Schweiz.

#### Apple „E-Mail verbergen" 🇺🇸

Über iCloud+ (ab 0,99 €/Monat) bietet Apple eine nahtlos integrierte Alias-Funktion. Der Haken: Nur im Apple-Ökosystem nutzbar.

### Was ist der beste Alias-Dienst für dich?

| Dein Szenario | Empfehlung |
|---|---|
| Du nutzt Bitwarden | **SimpleLogin** (integriert direkt) |
| Du willst es kostenlos und unbegrenzt | **addy.io** |
| Du willst es einfach | **Firefox Relay** (5 Masken) |
| Du bist im Apple-Ökosystem | **E-Mail verbergen** (nahtlos) |

## Wegwerf-Adressen für Einmal-Nutzung

Für Registrierungen, die du wirklich nur einmal brauchst — Artikel-Lesezwänge, Newsletter-Probeabos, Testzugänge — eignen sich temporäre Adressen von Diensten wie **[10MinuteMail](https://10minutemail.com/)** oder **[Guerrilla Mail](https://www.guerrillamail.com/)**. Diese Adressen existieren Minuten, dann sind sie weg.

> **Wichtig:** Wegwerf-Adressen sind keine dauerhafte Lösung. Für alles, worauf du langfristig Zugriff brauchst, nutze Aliase.

## Was du bei einem Datenleck tun solltest

Falls deine Daten geleakt wurden — keine Panik, aber handle:

1. **Passwort sofort ändern** — beim betroffenen Dienst und überall, wo du dasselbe Passwort verwendest
2. **2FA aktivieren** — falls noch nicht geschehen (siehe [Teil 2 unserer Serie](./sicher_im_netz_teil_2_authentifizierungs_apps))
3. **Kontoauszüge prüfen** — auf ungewöhnliche Transaktionen achten
4. **Alias einrichten** — den betroffenen Dienst auf eine separate E-Mail-Adresse umstellen

### Deine Rechte bei Datenlecks

Die DSGVO gibt dir konkrete Rechte:

- **Art. 33:** Unternehmen müssen Lecks innerhalb von **72 Stunden** melden
- **Art. 34:** Bei hohem Risiko musst du **direkt informiert** werden
- **Art. 15:** Du kannst Auskunft verlangen, welche Daten betroffen sind
- **Art. 77:** Beschwerderecht bei der Datenschutzaufsichtsbehörde

## Fazit: Kontrolle zurückgewinnen

Datenlecks werden nicht verschwinden. Aber du kannst entscheiden, wie stark dich das nächste trifft. Fünf Minuten Aufwand heute:

1. **Jetzt prüfen** → [Uni Bonn Leak Checker](https://leakchecker.uni-bonn.de/) oder [HPI](https://sec.hpi.de/ilc/)
2. **Alerts aktivieren** → bei [Have I Been Pwned](https://haveibeenpwned.com/)
3. **Alias-Dienst einrichten** → [SimpleLogin](https://simplelogin.io/) oder [addy.io](https://addy.io/)

Dann bist du beim nächsten Leak nicht überrascht, sondern informiert — und der Schaden ist minimal.

---

**Im nächsten Teil:** [Teil 4 – Der YubiKey](./sicher_im_netz_teil_4_yubikey) — Der physische Schlüssel, der das Phishing-Problem löst.
