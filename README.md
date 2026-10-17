# GOATreader

GOATreader lets you read PDFs, Word and Pages files and pasted texts faster: one word at a time, with a focus letter, sentence rewind, a context view and honest speed numbers. The start page offers two ways in: read your own text, or train with the GOAT test (four short texts at 300 to 600 words per minute, one question after each). Everything runs in the browser: texts are never uploaded, there are no cookies and no tracking of individuals, and all files come from this server. On goatreader.app only, visits, a few fixed events (way in chosen on the start page, PDF, Word or Pages file loaded, text loaded, reading started, reading test started, its result step, share button used) and rough time steps (page visible 10 s to 60 min, reading 15 s to 60 min) are counted anonymously with GoatCounter (EU servers), never texts, titles or file names; Do Not Track, Global Privacy Control and an opt-out on the privacy page are respected.

The site is fully static (HTML, CSS, JavaScript). It needs no server code, no database and no build step, so any static host works.

The language follows the browser: if German is the visitor's first preferred language (de, de-DE, de-AT, de-CH …), the site starts in German, otherwise in English. The EN/DE buttons still switch the language, and that choice is remembered and wins over the browser language. A link with `?lang=de` or `?lang=en` forces a language and is remembered as well, so German campaign links can keep using `https://goatreader.app/?lang=de`. The detected browser language itself is never stored. The legal notice and the privacy policy follow the same rules. The fixed page head (title, description, preview image for link previews) is German.

## Files

| File / folder | Purpose |
|---|---|
| `index.html` | the app |
| `legal.html` | legal notice / Impressum (EN/DE) |
| `privacy.html` | privacy policy / Datenschutzerklärung (EN/DE) |
| `legal.css` | styles for both legal pages |
| `fonts/` | Literata and IBM Plex Sans, self-hosted |
| `vendor/pdfjs/` | pdf.js 3.11.174 for reading PDFs |
| `icon.svg`, `favicon-32.png`, `apple-touch-icon.png` | icons for browser tabs and home screens |
| `og-image.png` | preview image when the link is shared in messengers or social media |
| `robots.txt`, `sitemap.xml` | for search engines |
| `.nojekyll` | tells GitHub Pages to serve the files unchanged (hidden file, may be missing) |

## Licenses

- pdf.js by Mozilla, Apache License 2.0 (`vendor/pdfjs/LICENSE`)
- Literata and IBM Plex Sans, SIL Open Font License 1.1 (`fonts/LICENSE-*.txt`)
- GOATreader itself has no license yet, so all rights are reserved.

---

## Deutsch: Veröffentlichen mit eigener Domain

### 1. Auf GitHub Pages hochladen

1. Auf github.com oben rechts **+ → New repository**. Name `goatreader`, Sichtbarkeit **Public**, dann **Create repository**.
2. Auf der leeren Repository-Seite **uploading an existing file** anklicken. Den *Inhalt* dieses Ordners (alle Dateien und die Ordner `fonts` und `vendor`) in das Fenster ziehen, dann **Commit changes**.
3. Im Repository **Settings → Pages**. Unter „Build and deployment“: Source **Deploy from a branch**, Branch **main**, Ordner **/ (root)**, **Save**.
4. Nach ein bis zwei Minuten läuft die Seite unter `https://DEIN-GITHUB-NAME.github.io/goatreader/`.

Mit einem kostenlosen GitHub-Konto funktioniert Pages nur mit öffentlichen Repositorys, der Quelltext ist also sichtbar. Das Datenvolumen ist weich auf 100 GB pro Monat begrenzt. Für ein kommerzielles Angebot (zum Beispiel ein Bezahl-Abo) ist GitHub Pages nicht gedacht.

### 2. Domain und E-Mail bei IONOS

1. Bei IONOS `goatreader.app` bestellen und `hello@goatreader.app` als Weiterleitung an dein Postfach anlegen (beim Domain-Vertrag inklusive). Die Vereinbarung zur Auftragsverarbeitung ist seit Juli 2022 Teil der IONOS-AGB.
2. Eine Testmail an hello@goatreader.app schicken. Die Adresse steht im Impressum und muss funktionieren, bevor die Seite unter der Domain online geht.
3. Bei der Domain die **DNS**-Einstellungen öffnen. Die vorhandenen A- und AAAA-Einträge für die Domain selbst (Host „@“) löschen, sie zeigen auf eine IONOS-Seite. Die E-Mail-Einträge (MX und Co.) nicht anfassen.
4. Diese Einträge anlegen (GitHub empfiehlt alle vier A- und AAAA-Einträge):

| Typ | Host | Wert |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | DEIN-GITHUB-NAME.github.io |

Bei anderen Anbietern (Porkbun, Cloudflare und Co.) sind die Einträge dieselben, dort bleibt das Host-Feld für die Domain selbst oft leer. Läuft die E-Mail-Adresse dann über einen anderen Dienst, zum Beispiel die Weiterleitung von Porkbun, müssen die Absätze „Contact by email“ und „Kontakt per E-Mail“ in `privacy.html` angepasst werden.

### 3. Domain mit GitHub verbinden

1. Empfohlen: Domain bei GitHub bestätigen. Profilbild → **Settings → Pages → Add a domain** → `goatreader.app`. GitHub zeigt einen TXT-Eintrag (`_github-pages-challenge-…`), den du beim Domain-Anbieter anlegst, dann **Verify**. So kann niemand anderes deine Domain mit seinem GitHub-Konto verknüpfen.
2. Im Repository **Settings → Pages → Custom domain**: `goatreader.app` eintragen, **Save**. GitHub legt dabei eine Datei `CNAME` im Repository an. Die bitte nicht löschen.
3. Sobald der DNS-Check grün ist, **Enforce HTTPS** anhaken. Das kann bis zu 24 Stunden dauern. .app-Domains funktionieren nur mit HTTPS; bis das Zertifikat da ist, zeigt der Browser unter der Domain eine Fehlermeldung.

### Aktualisieren

Geänderte Dateien im Repository über **Add file → Upload files** ersetzen. GitHub Pages veröffentlicht danach automatisch neu.

### Sprache

Die Seite richtet sich nach der Browsersprache: Ist Deutsch die erste bevorzugte Sprache (de, de-DE, de-AT, de-CH …), startet sie auf Deutsch, sonst auf Englisch. Mit EN/DE lässt sich weiter umschalten; diese Wahl merkt sich der Browser, und sie gilt dann vor der Browsersprache. Ein Link mit `?lang=de` oder `?lang=en` erzwingt die Sprache und wird ebenfalls gemerkt. Deutsche Kampagnenlinks können also weiter `https://goatreader.app/?lang=de` verwenden. Die erkannte Browsersprache selbst wird nicht gespeichert. Impressum und Datenschutzerklärung folgen denselben Regeln. Der feste Seitenkopf (Titel, Beschreibung und Vorschaubild für Linkvorschauen) ist deutsch.

### Rechtliches (keine Rechtsberatung)

- Impressum und Datenschutzerklärung enthalten deinen Namen, deine Anschrift und hello@goatreader.app. Bei der Datenschutzerklärung ist die deutsche Fassung maßgeblich.
- Beide Seiten sind für Suchmaschinen gesperrt (`noindex`). Das hält seriöse Suchmaschinen fern, verbirgt die Anschrift aber nicht vollständig: Das Repository ist öffentlich, und Webarchive können die Seiten speichern.
- Solange GOATreader kostenlos und werbefrei ist, ist vertretbar, dass Name, Anschrift und E-Mail genügen. Die Landesmedienanstalten sehen das strenger. Sobald du damit Geld verdienst (Werbung, Affiliate-Links, Bezahlfunktionen), brauchst du einen zweiten schnellen Kontaktweg, zum Beispiel eine Telefonnummer. Bei Bezahl-Abos kommen Widerrufsbelehrung, AGB und Kündigungsbutton dazu.
- Die Besuchszählung läuft über GoatCounter (Konto goatreader.goatcounter.com, Betreiber Martin Tournoij in Irland, Server bei Hetzner in Deutschland und Finnland). Einen Vertrag zur Auftragsverarbeitung nennt GoatCounter nicht; das ist eine kleine formale Lücke. Der Kontoname steht in `GC_CODE` in tools/build_site.py.
- Die Datenschutzerklärung geht davon aus, dass IONOS die Mails an hello@goatreader.app an ein Gmail-Postfach weiterleitet. Wenn du Hosting, E-Mail oder andere Dienste änderst (zum Beispiel Render statt GitHub Pages, Statistik-Tools, Newsletter), muss sie angepasst werden.
- Wenn du GOATreader über Instagram bewirbst, verlinke dort auch das Impressum, zum Beispiel über den Link in der Bio.
