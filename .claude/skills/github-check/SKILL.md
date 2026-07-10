---
name: github-check
description: Prueft Branch, Commitstatus, offene Aenderungen und Pull-Request-Bereitschaft ohne Push, Merge oder Loeschaktionen.
---

# GitHub Check Skill

Nutze diesen Skill fuer eine sichere Git- und GitHub-Pruefung.

## Pruefen

- aktueller Branch
- ob auf main gearbeitet wird
- git status
- offene Aenderungen
- unversionierte Dateien
- letzter Commit
- Remote-Konfiguration
- Pull-Request-Bereitschaft

## Verbote

- Nie automatisch pushen.
- Nie automatisch mergen.
- Nie Branches oder Tags loeschen.
- Kein force push.
- Keine Secrets in Logs oder Dateien schreiben.
- Keine GitHub-Rechte oder Repository-Einstellungen aendern.

## Ergebnisformat

Berichte:

- Branch
- Status sauber oder offen
- welche Dateien betroffen sind
- ob ein Commit sinnvoll ist
- ob ein Pull Request vorbereitet werden kann
- Risiken oder Blocker
