# assistant-web-guru

Assistent *Web-Guru* von AIbex AIOS, Version 0.1.0: prüft Websites auf Suchmaschinenoptimierung (SEO), mit Schwerpunkt auf der lokalen Suche kleiner Betriebe, und schlägt priorisierte, konkrete Maßnahmen mit fertigen Texten vor. Jede Antwort beginnt mit „🤓 ".

## Holen

**Voraussetzung:** AIbex AIOS v0.6 ist installiert, und der Vault ist an der Vault-Root mit `aios --activate v0.6.<n>` gebunden (ein AIBOS-Workspace).

```bash
aios --fetch assistant-web-guru
```

Zuordnen mit `/aios-assistant web-guru` im Projekt, in dem du Websites prüfen willst. Der Web-Guru wirkt **ab dem nächsten Chat** in diesem Projekt.

## Benutzen

Sag im Chat zum Beispiel:

> Webguru, mache eine SEO der Webseite der Firma Huber Sturm (Bestatter in St. Johann in Tirol).

Der Web-Guru sucht die Website, lässt dich die Adresse bestätigen, klärt kurz Ziel und Region, liest die öffentlichen Seiten und zeigt einen Bericht im Chat: Ampel für sechs Bereiche (Technik, On-Page, Inhalt, Lokal, Strukturierte Daten, Vertrauen und Branche) und die wichtigsten Maßnahmen mit fertigen Texten. Nach deinem Ja legt er den Bericht unter `@Data/assistant-web-guru/seo/<domain>/<datum>.md` ab; ein späterer Lauf vergleicht mit dem letzten Bericht.

Das rohe HTML liest er mit `curl`; Claude Code fragt beim ersten Aufruf nach Erlaubnis.

## Grenzen

Nur öffentliche Seiten, keine Änderungen an der Website, keine Anmeldung, keine Versprechen zu Platzierungen. Ohne Daten aus der Google Search Console gibt es keine echten Zahlen zu Klicks und Positionen.
