# Auftrag für Claude Code: Männergrillabend-Terminseite

Baue aus den mitgelieferten Dateien eine funktionsfähige, mobil optimierte Einseiten-Webseite für die Terminfindung eines Männergrillabends.

## Wichtigste Sicherheits- und Bildregeln

Diese Regeln sind verbindlich:

1. Verwende für alle Personen ausschließlich die Originaldateien aus `assets/people/`.
2. Keine KI-Neugenerierung von Personenbildern.
3. Keine Retusche, Verschönerung, Gesichtsveränderung oder Hautbearbeitung.
4. Keine Vermischung von Personen.
5. Keine Veränderung von Haaren, Kleidung, Gesicht oder Hintergrund.
6. Zulässig sind nur:
   - Größenanpassung,
   - `object-fit: cover`,
   - `object-position`,
   - kreisförmige Anzeige per CSS.
7. Ludwig darf keinen zusätzlichen weißen inneren Halbkreis oder zweiten Bildrand bekommen.
8. Martin.F. soll im Kreis mit dem Gesicht mittig und etwas kleiner erscheinen. Die Flaschen dürfen nur durch den sichtbaren Kreisausschnitt ausgeblendet werden. Das Originalfoto selbst darf nicht bearbeitet werden.
9. Ein neunter Kreis bleibt als Platzhalter frei.

Nutze `config/people.json` als verbindliche Zuordnung und als Ausgangspunkt für die Bildausschnitte.

## Ziel

Eine einzige Webseite, keine Unterseiten und keine Navigation wie „Mission“, „Trupp“ oder „Info“.

Die Seite soll aus WhatsApp geöffnet werden können und auf dem Smartphone vollständig bedienbar sein.

## Aufbau der Seite

### 1. Kopfbereich

- Titel: `MÄNNER GRILLABEND`
- großes Grill-/Feuer-Hintergrundbild
- Text:
  - `FLEISCH.`
  - `FEUER.`
  - `FREUNDE.`
  - `EIN LEGENDÄRER ABEND.`
- kurze Erklärung:
  `Damit möglichst viele dabei sein können, finden wir hier gemeinsam den perfekten Termin.`
- Bier visuell integrieren, zum Beispiel Bierkrug oder Bierflasche.
- Slogan:
  `GUTES FLEISCH. KALTES BIER.`

### 2. Erklärung der Terminfindung

Deutlich sichtbare Box:

`WANN HAST DU ZEIT?`

`Klicke im Kalender alle Tage an, an denen du Zeit hast.`

Button:

`ZEIT EINTRAGEN`

Der Button scrollt zum Kalender.

### 3. Teilnehmer

Alle acht Personen kreisförmig mit Namen anzeigen:

- Bernhard
- Martin.W.
- Alex
- Ludwig
- Martin.F.
- Dominik
- Seraphin
- Martin H.

Daneben ein leerer Kreis:

`Freier Platz`

Die Originalbilder liegen unter `assets/people/`.

### 4. Wochenkalender

Immer genau eine komplette Woche von Montag bis Sonntag anzeigen.

Funktionen:

- vorherige Woche
- nächste Woche
- heute
- sichtbare Kalenderwoche und Datumsbereich
- jeder Teilnehmer kann für jeden Tag auswählen:
  - `Passt`
  - `Eher fraglich`
  - `Passt nicht`
  - `Noch nicht gewählt`

Der Status kann durch wiederholtes Anklicken durchgeschaltet werden.

### 5. Datenerfassung

Beim ersten Bearbeiten:

- Teilnehmer auswählen oder Namen eingeben
- danach eigene Verfügbarkeit bearbeiten
- andere Einträge dürfen nur gelesen werden

Für die erste lokale Version darf `localStorage` genutzt werden.

Strukturiere den Code aber so, dass später leicht ein echtes Backend ergänzt werden kann.

Keine Cloud, kein Azure und kein Deployment ausführen.

### 6. Auswertung

Rechts oder unterhalb des Kalenders:

- aktuell bester Termin
- Anzahl der Zusagen
- Rangliste der besten drei Termine
- Wochenende optisch hervorheben

### 7. Zwei Phasen

#### Phase A: Terminfindung läuft

- Verfügbarkeit kann eingetragen werden
- Hinweis: `Eintragungen noch möglich`
- Countdown zum Grillabend zeigt noch keinen endgültigen Termin oder ist deaktiviert

#### Phase B: Termin ist festgelegt

Der Gastgeber kann einen Termin verbindlich auswählen.

Danach:

- Terminfindung sperren oder als abgeschlossen markieren
- Countdown automatisch bis zum festgelegten Grillabend starten
- Text: `Bis zum Grillabend`

Die Gastgeberfunktion darf in der lokalen Demo über einen klar getrennten Admin-Modus simuliert werden.

### 8. Design

- dunkler Hintergrund
- Schwarz, Anthrazit, Orange und warme Feuerfarben
- Fleisch und Feuer als Hauptmotiv
- Bier als zusätzliches Designelement
- robuste, klare Typografie
- nicht zu viel Text
- keine überladene Navigation
- responsive
- gute Lesbarkeit auf Smartphones
- keine horizontalen Scrollprobleme

Nutze `assets/reference/onepage_mockup.png` als Layoutreferenz.
Nutze `assets/reference/bbq_style_reference.png` nur als Stilreferenz für Grill, Feuer und Bier, nicht als Quelle für Personenbilder.

## Technische Umsetzung

Bevorzugt:

- einfaches HTML, CSS und JavaScript
- oder React/Vite, falls das bestehende Arbeitsumfeld darauf ausgelegt ist

Wichtig:

- sauber getrennte Komponenten/Funktionen
- verständliche Dateistruktur
- keine unnötigen Abhängigkeiten
- barrierearme Buttons
- Status nicht nur über Farben kennzeichnen
- mobile Ansicht zuerst testen
- README mit Startanleitung erstellen
- keine Veröffentlichung oder GitHub-Pages-Aktivierung ohne ausdrückliche Freigabe

## Erwartetes Ergebnis

1. funktionsfähige lokale Webseite
2. alle acht Originalfotos korrekt eingebunden
3. ein freier Teilnehmerplatz
4. Wochenwechsel im Kalender
5. editierbare Verfügbarkeit
6. automatische Auswertung
7. Abschluss der Terminfindung
8. danach laufender Countdown
9. Grill-, Feuer- und Bierdesign
10. keine KI-Veränderung an Personenbildern

Erstelle zuerst einen kurzen Umsetzungsplan und prüfe danach die bereitgestellten Dateien. Setze die Seite anschließend lokal um. Am Ende nenne:

- erstellte Dateien
- Startbefehl
- offene Punkte
- welche Funktionen nur lokal simuliert sind

Kein Deployment, kein Merge und keine Änderung an bestehenden Business-App-Dateien ohne ausdrückliche Freigabe.