# WCL Tool

*English summary: a small private Windows tool that averages and compares
World of Warcraft raid data across several [Warcraft Logs](https://www.warcraftlogs.com)
reports. It is built for one raid group and a few friends, is in early
testing, and this repository only hosts its installers. Not affiliated with
Warcraft Logs or Blizzard Entertainment.*

---

Das **WCL Tool** ist ein kleines Windows-Programm, das Daten aus
Warcraft-Logs-Berichten über **mehrere Raidabende hinweg** auswertet. Es
ist für unsere Raidgruppe und ein paar Mitspieler entstanden und befindet
sich in der Testphase.

**Dieses Repository enthält nur die Installationsdateien**, keinen
Quellcode. Es dient dem Programm als Bezugsquelle für automatische Updates.

## Was das Programm kann

- **Durchschnitt:** Schaden und DPS je Spieler über mehrere Abende, getrennt
  nach Schwierigkeit und gerechnet über die Zeit, in der jemand wirklich
  dabei war.
- **Fortschritt:** Pulls, Abende und bester Versuch je Boss, zum Beispiel
  „P3 · 67 %“, und wann der Kill fiel.
- **Tode:** Woran stirbt der Raid, und wer stirbt woran, mit oder ohne die
  Tode mitten im Wipe.
- **Daten-Export:** Rohdaten eines Spielers als CSV/JSON, aufbereitet für
  eigene Auswertungen oder eine KI.

## Installation

1. Unter **[Releases](../../releases/latest)** die Datei
   `WCL-Tool-Setup-<Version>.exe` herunterladen und starten.
2. Windows meldet sich eventuell mit „Der Computer wurde durch Windows
   geschützt“, weil das Programm nicht signiert ist. Dann
   **„Weitere Informationen“ → „Trotzdem ausführen“**.
3. Beim ersten Start fragt das Programm nach einem eigenen, kostenlosen
   API-Zugang bei Warcraft Logs. Die mitgelieferte Anleitung erklärt
   Schritt für Schritt, wie man ihn anlegt.

Die Installation braucht keine Administratorrechte. Spätere Versionen bietet
das Programm von selbst an.

## Datenschutz

- Deine Warcraft-Logs-Zugangsdaten und alle geladenen Logs bleiben **nur auf
  deinem Rechner**.
- Das Programm fragt höchstens einmal am Tag hier bei GitHub nach, ob es
  eine neue Version gibt. Dabei wird nichts von dir übertragen.

## Hinweise

- Ein privates Hobbyprojekt in der Testphase, ohne Gewähr und ohne
  zugesicherten Support.
- Nicht verbunden mit Warcraft Logs oder Blizzard Entertainment. World of
  Warcraft ist eine Marke von Blizzard Entertainment.
