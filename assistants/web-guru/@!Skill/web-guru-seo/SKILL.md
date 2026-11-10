---
name: web-guru-seo
version: 0.1.0
description: >
  SEO-Analyse einer Website mit Schwerpunkt lokale Suche: Website finden und bestätigen lassen,
  kurz klären, öffentliche Seiten lesen (rohes HTML mit curl), sechs Bereiche bewerten, Bericht
  mit priorisierten Maßnahmen und fertigen Texten im Chat zeigen, nach Ja unter
  <projekt>/@Data/assistant-web-guru/ ablegen und mit dem letzten Bericht vergleichen. Verwenden bei
  "mache eine SEO der Webseite …", "SEO-Analyse", "prüf die Website auf SEO".
---

# SEO einer Website

Ein Skill des Web-Gurus. Alles, was du sagst und schreibst, ist **Deutsch** (wörtliche Zitate und JSON-LD im Original). Schritte 1–4 **lesen nur**; geschrieben wird nur in Schritt 5, nach Ja zum gezeigten Plan. Der Wunsch „mache eine SEO“ ist keine Bestätigung des Plans.

**Werkzeuge:** Websuche und Seitenabruf des Hosts für Suche und Lesetext; rohes HTML mit `curl` über die Shell, je Aufruf ein einzelner Befehl, z. B. `curl -sL --max-time 20 -A "Mozilla/5.0 (compatible; web-guru)" "<url>"` und für Header `curl -sIL --max-time 20 "<url>"`. Den Inhalt nicht in Dateien im Projekt schreiben; Zwischenstände bleiben im Chat oder im temporären Verzeichnis der Session.

## 1. Klären

1. **Website finden:** Nennt der User eine URL, nimm sie. Sonst suche mit Firmenname und Ort (Websuche). Zeig die gefundene Adresse mit Firmenname und Ort aus dem Treffer und lass sie bestätigen; bei mehreren plausiblen Treffern lass auswählen (Auswahlwerkzeug, falls vorhanden). Ohne Treffer: sag das und frag nach der Adresse.
2. **Kurz klären**, in **einer** Fragegruppe, je mit Empfehlung zuerst (abgeleitet aus Treffer und Startseite):
   - **Ziel:** mehr Anfragen aus der Region (Empfohlen bei lokalen Betrieben) · Sichtbarkeit überregional · eigene Antwort
   - **Region:** Ort und Umgebung aus der Adresse (Empfohlen) · eigene Antwort
   - **Hauptleistungen und Mitbewerber:** aus der Navigation abgeleitet (Empfohlen) · eigene Antwort
   „weiter“ übernimmt die Empfehlungen.
3. **Früheren Bericht suchen:** Gibt es `<projekt>/@Data/assistant-web-guru/seo/<domain>/` (`<projekt>` ist der Projektordner, das Arbeitsverzeichnis der Session; `@Data/` liegt neben `@/`, nicht darin), merk dir den neuesten Bericht für den Vergleich. `<domain>` ist der Hostname ohne `www.`, z. B. `huber-sturm.at`.

## 2. Erfassen

Lies, höchstens **20 Seiten** je Lauf:

1. `robots.txt` und `sitemap.xml` (bzw. die Sitemap aus `robots.txt`) mit `curl`. Was `robots.txt` sperrt, liest du nicht.
2. Header der Startseite mit `curl -sIL` (Weiterleitungen, HTTPS, `X-Robots-Tag`), auch für `http://` und die Variante mit bzw. ohne `www`.
3. Rohes HTML der Startseite und der wichtigsten Unterseiten (Leistungen, Über uns, Kontakt, Impressum; aus Navigation oder Sitemap) mit `curl -sL`. Notiere je Seite: Statuscode, `<title>`, Meta-Beschreibung, `canonical`, `robots`, `viewport`, `lang`, Überschriften, Bilder ohne `alt`, JSON-LD, interne Links.
4. Lesetext der wichtigsten Seiten mit dem Seitenabruf des Hosts, wenn das HTML schwer lesbar ist.
5. **Lokale Präsenz** per Websuche: Unternehmensprofil, Verzeichniseinträge, Bewertungen; Suche nach den drei wichtigsten Begriffen (Leistung + Ort): wo erscheint der Betrieb, wer davor.

Scheitert `curl` (nicht erlaubt oder Fehler): sag das kurz, arbeite mit dem Lesetext weiter und markiere die Prüfpunkte mit **(HTML)** als ⚪ „nicht geprüft“.

## 3. Analysieren

Lies `@@SEO/pruefpunkte.md` deines Wissens. Bewerte die sechs Bereiche — Technik, On-Page, Inhalt, Lokal, Strukturierte Daten, Vertrauen und Branche — mit Ampel nach der Ampelregel. Jeder Befund nennt die **Quelle** (URL und Fundstelle). Leite Maßnahmen ab und priorisiere sie (hoch, mittel, niedrig; schnelle Erfolge markieren). Zu jeder Maßnahme, wo möglich, ein **fertiger Vorschlag**: neuer Seitentitel, neue Meta-Beschreibung, Schema.org-JSON-LD mit den Daten der Website (fehlende Werte `TODO`, nie erfunden).

## 4. Bericht zeigen

Im Chat, kurz:

1. Eine Zeile: Website, Datum, Ziel, Region.
2. Tabelle: Bereich, Ampel, wichtigster Befund in einem Satz.
3. Die **fünf wichtigsten Maßnahmen**, schnelle Erfolge zuerst, je mit fertigem Vorschlag.
4. Bei einem früheren Bericht: Vergleich in drei Zeilen (behoben, neu, unverändert).
5. Ein Satz zu den Grenzen dieser Analyse.

## 5. Ablegen — Plan, Rückfrage, Ausführen

1. **Plan zeigen:** Pfad `<projekt>/@Data/assistant-web-guru/seo/<domain>/<YYYY-MM-DD>.md` — im Projektordner neben `@/`, **nie in `@/`** — (gibt es den Tag schon, Suffix `-2`, `-3`), Gliederung (unten), ob ein Vergleich enthalten ist.
2. **Fragen:** „Soll ich den vollständigen Bericht so ablegen?“ — Empfohlen: Ja · Nein.
3. **Nach Ja** schreiben; den Ordner beim ersten Mal anlegen. Nur in `<projekt>/@Data/assistant-web-guru/`, nie in `@/` und nie ins Paket. Bei Nein nichts schreiben.
4. **Nicht committen:** Du schreibst nur die Datei; den Commit macht der User oder `/aios-sync`.
5. Den Pfad als Link nennen.

**Gliederung des Berichts** (Markdown):

```markdown
# SEO-Bericht — <domain>

**Datum:** YYYY-MM-DD
**Website:** <url>
**Ziel:** …
**Region:** …

## Zusammenfassung
Tabelle: Bereich | Ampel | wichtigster Befund

## Maßnahmen
Tabelle: # | Maßnahme | Priorität | schneller Erfolg | Bereich

## Befunde
### Technik … ### Vertrauen und Branche
je Befund: Beschreibung, Quelle (URL, Fundstelle)

## Fertige Texte
Seitentitel und Meta-Beschreibungen je geprüfter Seite (alt → neu); Schema.org-JSON-LD

## Vergleich
(nur ab dem zweiten Bericht) behoben | neu | unverändert, mit Verweis auf den früheren Bericht

## Grenzen dieser Analyse
geprüfte Seiten, nicht Geprüftes mit Grund, Websuche als Momentaufnahme, keine Daten aus Search Console
```
