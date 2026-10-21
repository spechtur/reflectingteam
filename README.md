# Reflecting Team · Kurzberatung

Eine einfache Web-App für die schnelle kollegiale Fallberatung im Dreierformat. Sie führt eine Gruppe von drei Personen in rund 7 Minuten durch vier Phasen und stellt für jede Phase einen passenden Timer bereit.

Die App besteht aus einer einzigen HTML-Datei ohne externe Abhängigkeiten. Sie läuft im Browser, auf dem Handy genauso wie auf dem Beamer, und funktioniert auch offline.

## Ablauf

Drei Personen (A, B und C) sitzen zusammen. A bringt einen Fall mit.

| Phase | Wer | Dauer | Was passiert |
|---|---|---|---|
| 1. Fall schildern | A erzählt | 2 Min. | A schildert den Fall und die Frage dahinter. B und C hören nur zu. |
| 2. Rückfragen | B und C fragen | 1 Min. | Nur Verständnisfragen, keine Lösungsvorschläge, keine Bewertungen. |
| 3. Reflecting Team | B und C sprechen | 3 Min. | A dreht sich weg und hört nur zu. B und C besprechen Hypothesen, Ideen und mögliche Lösungen. |
| 4. Mitnehmen | A erzählt | 1 Min. | A sagt, was er oder sie aus dem Gespräch von B und C mitnimmt. |

Die Methode orientiert sich am Reflecting Team (nach Tom Andersen): Die fallgebende Person muss nicht reagieren, erklären oder rechtfertigen, sondern kann das Gehörte in Ruhe aufnehmen.

## Funktionen

- Startscreen mit Titel, Kurzbeschreibung und Übersicht der Phasen
- Pro Phase ein Countdown mit Fortschrittsbalken, der beim Wechsel automatisch startet
- Pause und Weiter sowie Verlängerung um jeweils 30 Sekunden (beliebig oft, auch nach Ablauf der Zeit)
- Signalton und Vibration am Ende einer Phase (wo vom Gerät unterstützt)
- Bildschirm bleibt während der Beratung eingeschaltet (Wake Lock, wo unterstützt)
- Vollbildmodus für Beamer und Tablet
- Mobile-first-Layout, skaliert aber auch auf grosse Bildschirme

## Benutzung

1. Die Datei `reflecting-team.html` im Browser öffnen, entweder lokal per Doppelklick oder über die gehostete Version.
2. Auf **Start** tippen. Die erste Phase beginnt sofort.
3. Mit **Weiter** zur nächsten Phase wechseln, mit **←** eine Phase zurück.
4. Am Schluss erscheint ein Abschlussbildschirm, von dem aus man neu starten kann.

### Tastaturkürzel

| Taste | Aktion |
|---|---|
| `→`, `Enter`, `Bild ↓` | nächste Phase |
| `←`, `Rücktaste`, `Bild ↑` | vorherige Phase |
| `Leertaste` | Pause / Weiter |
| `+` oder `P` | 30 Sekunden verlängern |
| `F` | Vollbild ein/aus |
| `Pos1` | zurück zur Startseite |

## Anpassen

Phasen, Texte, Dauern und Farben stehen oben im Skript im Block `PHASES`:

```js
var PHASES = [
  { name:'Fall schildern', who:'A erzählt', secs:120, bg:'#23b2c6', fg:'#1c1c1c',
    desc:'A schildert den Fall und die Frage dahinter. B und C hören nur zu.' },
  // ...
];
```

- `name`: Titel der Phase
- `who`: Rollenzeile, die gross angezeigt wird
- `secs`: Dauer in Sekunden
- `bg` / `fg`: Hintergrund- und Schriftfarbe der Phase
- `desc`: kurze Anweisung für die Gruppe

Die Gesamtdauer auf dem Startscreen wird automatisch aus den Phasen berechnet.

## Technik

- Reines HTML, CSS und JavaScript in einer Datei, keine Frameworks, keine Bibliotheken
- Der Timer rechnet mit Zeitstempeln und bleibt auch bei kurzzeitig gedrosseltem Browser-Tab genau
- Signalton über die Web Audio API, Bildschirmsperre über die Screen Wake Lock API
- Gestaltung im phGR-Stil

## Hosting über GitHub Pages

Die Datei lässt sich direkt über GitHub Pages ausliefern: unter *Settings → Pages* den Branch und Ordner wählen. Damit die Seite unter der Basis-URL erscheint, kann die Datei in `index.html` umbenannt werden. Für den Einsatz im Kurs lässt sich der Link auch als QR-Code teilen.
