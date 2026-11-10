# Prüfpunkte der SEO-Analyse

Sechs Bereiche, je mit Prüfpunkten, woher der Befund kommt und Richtwert. Was ohne rohes HTML nicht prüfbar ist, ist mit **(HTML)** markiert.

## Ampelregel

| Ampel | Bedeutung |
|---|---|
| 🟢 | keine oder nur kleine Befunde |
| 🟡 | Befunde, die Sichtbarkeit kosten, aber nichts blockieren |
| 🔴 | Befund, der Auffinden oder Vertrauen ernsthaft verhindert (z. B. `noindex` auf der Startseite, kein HTTPS, kein Unternehmensprofil bei einem lokalen Betrieb) |
| ⚪ | nicht geprüft (Grund nennen) |

Priorität einer Maßnahme: **hoch** (🔴-Befund oder großer Nutzen bei kleinem Aufwand), **mittel**, **niedrig**. **Schnelle Erfolge** = hoher Nutzen, Aufwand unter einer Stunde.

## 1. Technik

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Indexierbar | `robots.txt`, `<meta name="robots">` **(HTML)**, Header `X-Robots-Tag` (`curl -sI`) | kein `Disallow: /`, kein `noindex` auf wichtigen Seiten |
| Sitemap | `/sitemap.xml` oder Eintrag in `robots.txt` | vorhanden, enthält die wichtigen Seiten |
| HTTPS | Abruf mit `http://` folgt auf `https://` | eine Weiterleitung (301) auf HTTPS; keine Mischinhalte |
| Eine Hauptadresse | `www` und ohne `www` | beide führen per 301 auf dieselbe Adresse |
| Kanonische URL | `<link rel="canonical">` **(HTML)** | vorhanden, zeigt auf sich selbst bzw. die Hauptadresse |
| Mobil | `<meta name="viewport">` **(HTML)** | `width=device-width` |
| Ladezeit (Schätzung) | Größe des HTML, Zahl und Größe der Bilder | HTML unter etwa 200 KB; große Bilder (> 500 KB) nennen |
| Defekte Links | Statuscodes der verlinkten internen Seiten (`curl -sI`) | keine 404 |
| Sprache | `<html lang>` **(HTML)** | gesetzt, z. B. `de-AT` |

## 2. On-Page

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Seitentitel | `<title>` **(HTML)** | je Seite eigener Titel, 30–60 Zeichen, Hauptbegriff vorne, Ort bei lokalen Betrieben, Firmenname hinten |
| Meta-Beschreibung | `<meta name="description">` **(HTML)** | je Seite eigene, 120–160 Zeichen, Nutzen und Handlungsaufforderung |
| H1 | `<h1>` **(HTML)** | genau eine je Seite, passt zum Titel |
| Überschriften | `<h2>`–`<h3>` **(HTML)** | logische Gliederung, keine leeren oder rein dekorativen Überschriften |
| Bilder | `alt` der `<img>` **(HTML)**, Dateinamen | beschreibende Alt-Texte, sprechende Dateinamen |
| URLs | Pfade der Seiten | kurz, sprechend, Kleinbuchstaben, Bindestriche |
| Interne Links | Navigation, Links im Text | jede wichtige Seite in höchstens zwei Klicks erreichbar; sprechende Linktexte statt „hier“ |

## 3. Inhalt

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Suchbegriffe | Leistungen und Region aus Schritt 1, eigene Websuche | die drei bis fünf Hauptbegriffe kommen in Titel, H1 und Text der passenden Seite vor (z. B. „Bestatter St. Johann in Tirol“) |
| Seite je Leistung | Navigation | jede Hauptleistung hat eine eigene Seite mit genug Text (Richtwert ab 300 Wörtern) |
| Suchabsicht | Inhalt | beantwortet die Fragen der Zielgruppe (z. B. „Todesfall – was tun?“, Kosten, Ablauf) |
| Aktualität | Datumsangaben, Copyright im Fuß, Neuigkeiten | nichts sichtbar Veraltetes |
| Lesbarkeit | Lesetext | kurze Absätze, klare Sprache |

## 4. Lokal

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Google-Unternehmensprofil | Websuche nach Firmenname und Ort | vorhanden, Kategorie passend, Öffnungszeiten, Fotos, Link zur Website |
| NAP | Name, Adresse, Telefonnummer auf Website, Profil, Verzeichnissen | überall gleich geschrieben |
| Verzeichnisse | Websuche (in Österreich z. B. Herold, Firmen-ABC, WKO-Firmen-A-Z, Branchenverzeichnisse) | Einträge vorhanden und aktuell |
| Bewertungen | Websuche, Profil | Zahl, Schnitt, Antworten des Betriebs |
| Einzugsgebiet | Website | Orte und Region im Text genannt (z. B. Nachbargemeinden, Bezirk) |
| Sichtbarkeit | Websuche nach den Hauptbegriffen | wo erscheint der Betrieb, wer erscheint davor (höchstens drei Mitbewerber nennen) |

Ergebnisse von Websuchen sind eine Momentaufnahme und ortsabhängig; kennzeichne sie so.

## 5. Strukturierte Daten

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Schema.org vorhanden | `<script type="application/ld+json">` **(HTML)** | ein `LocalBusiness` bzw. passender Untertyp |
| Typ | JSON-LD | passend zur Branche, z. B. `FuneralHome`, `Restaurant`, `Dentist`, `HomeAndConstructionBusiness` |
| Felder | JSON-LD | `name`, `address`, `telephone`, `url`, `openingHoursSpecification`, `geo`, `image`, `areaServed` |
| Übereinstimmung | JSON-LD und sichtbarer Text | gleiche Daten wie auf der Seite (NAP) |

## 6. Vertrauen und Branche

| Prüfpunkt | Quelle | Richtwert |
|---|---|---|
| Impressum, Datenschutz | Links im Fuß | vorhanden und erreichbar (in Österreich Impressumspflicht nach ECG/MedienG) |
| Kontakt | Kopf, Kontaktseite | Telefonnummer klickbar (`tel:`), Adresse, Anfahrt |
| Erreichbarkeit | Text | bei Notfall-Branchen (Bestatter, Installateur) 24-Stunden-Erreichbarkeit gut sichtbar |
| Ton und Bilder | Lesetext, Bilder | passend zur Branche (bei Bestattern: würdevoll, ruhig, eigene statt Stockfotos) |
| Belege | Text | Team mit Namen, Geschichte des Betriebs, Mitgliedschaften |

## Vorlagen für fertige Texte

**Seitentitel:** `<Hauptbegriff> in <Ort> | <Firmenname>` — z. B. „Bestattung in St. Johann in Tirol | Huber Sturm“.

**Meta-Beschreibung:** Nutzen + Ort + Handlungsaufforderung, 120–160 Zeichen — z. B. „Einfühlsame Begleitung im Trauerfall in St. Johann in Tirol und Umgebung. Rund um die Uhr erreichbar: Rufen Sie uns an.“

**Schema.org (Gerüst, Werte nur aus der Website übernehmen, fehlende als `TODO` kennzeichnen):**

```json
{
  "@context": "https://schema.org",
  "@type": "FuneralHome",
  "name": "TODO",
  "url": "https://TODO",
  "telephone": "TODO",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "TODO",
    "postalCode": "TODO",
    "addressLocality": "TODO",
    "addressCountry": "AT"
  },
  "areaServed": ["TODO"],
  "openingHoursSpecification": [{
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
    "opens": "TODO",
    "closes": "TODO"
  }]
}
```

Erfinde keine Daten (Adresse, Öffnungszeiten, Telefon): Was nicht auf der Website steht, bleibt `TODO`.
