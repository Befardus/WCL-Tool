# WCL Tool

**WCL Tool** is a small Windows program that analyzes
[Warcraft Logs](https://www.warcraftlogs.com) reports **across several raid
nights**. It was built for one raid group and a few friends and is in its
testing phase.

**This repository only contains the installers**, no source code. The
program uses it as its source for automatic updates.

*Deutsche Fassung: [weiter unten](#deutsch).*

## What the program can do

- **Average:** damage and DPS per player across several nights, separated
  by difficulty, for all bosses, one boss or selected pulls, and calculated
  over the time someone was actually present.
- **Progress:** pulls, nights and best attempt per boss, for example
  “P3 · 67%”, and when the kill happened.
- **Deaths:** what kills the raid, and who dies to what, with or without the
  deaths in the middle of a wipe, also for single selected pulls.
- **Data export:** one player's raw data as CSV/JSON, prepared for your own
  analyses or an AI.

## Installation

1. Under **[Releases](../../releases/latest)**, download the file
   `WCL-Tool-Setup-<version>.exe` and run it. If your browser warns that
   the file isn't commonly downloaded, click **Keep**.
2. Windows may show “Windows protected your PC”, because the program is not
   signed. Then click **More info → Run anyway**.
3. On the first start the program asks for your own free API access at
   Warcraft Logs. The included guide explains step by step how to create
   it.

The installation needs no administrator rights. The program offers later
versions by itself.

## Language

The program is available in English and German. On the first start it
follows the language of Windows; you can change it any time under
**Settings → Language**. The installer and the included guide come in both
languages too.

The **data export is always in English**, whatever language the program is
set to – field names, file names and the explanation file. That way export
files look the same for everyone.

## Templates for your own analysis

The folder [`vorlagen/`](vorlagen/) contains two files for analyzing an
export with an AI: `INSTRUCTION_RAIDANALYSE.md` (an analysis instruction
that explains how to read the export files) and `GEMINI_SKILL.md` (a short
skill for Google Gemini that uses the instruction as its reference file).
Both are in English. There is deliberately no example report – the
instruction defines what a report has to contain, not what it has to look
like.

To set up the skill in Gemini: create a new skill, take the name and the
description from the header of `GEMINI_SKILL.md`, paste everything below
the header as the instructions, and add `INSTRUCTION_RAIDANALYSE.md` as a
reference file.

## Privacy

- Your Warcraft Logs credentials and all loaded logs stay **only on your
  computer**.
- The program asks GitHub here at most every 12 hours whether there is a new
  version. Nothing about you is sent.

## Notes

- A private hobby project in its testing phase, without warranty and without
  guaranteed support.
- Not affiliated with Warcraft Logs or Blizzard Entertainment. World of
  Warcraft is a trademark of Blizzard Entertainment.

---

## Deutsch

Das **WCL Tool** ist ein kleines Windows-Programm, das Daten aus
Warcraft-Logs-Berichten über **mehrere Raidabende hinweg** auswertet. Es
ist für unsere Raidgruppe und ein paar Mitspieler entstanden und befindet
sich in der Testphase.

**Dieses Repository enthält nur die Installationsdateien**, keinen
Quellcode. Es dient dem Programm als Bezugsquelle für automatische Updates.

### Was das Programm kann

- **Durchschnitt:** Schaden und DPS je Spieler über mehrere Abende, getrennt
  nach Schwierigkeit, für alle Bosse, einen Boss oder ausgewählte Pulls, und
  gerechnet über die Zeit, in der jemand wirklich dabei war.
- **Fortschritt:** Pulls, Abende und bester Versuch je Boss, zum Beispiel
  „P3 · 67 %“, und wann der Kill fiel.
- **Tode:** Woran stirbt der Raid, und wer stirbt woran, mit oder ohne die
  Tode mitten im Wipe, auch für einzelne ausgewählte Pulls.
- **Daten-Export:** Rohdaten eines Spielers als CSV/JSON, aufbereitet für
  eigene Auswertungen oder eine KI.

### Installation

1. Unter **[Releases](../../releases/latest)** die Datei
   `WCL-Tool-Setup-<Version>.exe` herunterladen und starten. Warnt der
   Browser, dass die Datei selten heruntergeladen wird, auf **Behalten**
   klicken.
2. Windows meldet sich eventuell mit „Der Computer wurde durch Windows
   geschützt“, weil das Programm nicht signiert ist. Dann
   **„Weitere Informationen“ → „Trotzdem ausführen“**.
3. Beim ersten Start fragt das Programm nach einem eigenen, kostenlosen
   API-Zugang bei Warcraft Logs. Die mitgelieferte Anleitung erklärt
   Schritt für Schritt, wie man ihn anlegt.

Die Installation braucht keine Administratorrechte. Spätere Versionen bietet
das Programm von selbst an.

### Sprache

Das Programm gibt es auf Deutsch und Englisch. Beim ersten Start richtet es
sich nach der Sprache von Windows; ändern lässt sie sich jederzeit unter
**Einstellungen → Sprache**. Auch Installer und mitgelieferte Anleitung gibt
es in beiden Sprachen.

Der **Daten-Export ist immer englisch**, egal welche Sprache eingestellt ist
– Feldnamen, Dateinamen und die Erklärungsdatei. So sehen die Exportdateien
bei allen gleich aus.

### Vorlagen für eigene Auswertungen

Im Ordner [`vorlagen/`](vorlagen/) liegen zwei Dateien, um einen Export mit
einer KI auszuwerten: `INSTRUCTION_RAIDANALYSE.md` (eine Analyse-Anweisung,
die erklärt, wie die Exportdateien zu lesen sind) und `GEMINI_SKILL.md` (ein
kurzer Skill für Google Gemini, der die Anweisung als Referenzdatei nutzt).
Beide sind englisch. Einen Beispielbericht gibt es bewusst nicht – die
Anweisung legt fest, was ein Bericht enthalten muss, nicht wie er aussieht.

So richtest du den Skill in Gemini ein: einen neuen Skill anlegen, Name und
Beschreibung aus dem Kopf von `GEMINI_SKILL.md` übernehmen, alles unterhalb
des Kopfs als Anleitung einfügen und `INSTRUCTION_RAIDANALYSE.md` als
Referenzdatei hinzufügen.

### Datenschutz

- Deine Warcraft-Logs-Zugangsdaten und alle geladenen Logs bleiben **nur auf
  deinem Rechner**.
- Das Programm fragt höchstens alle 12 Stunden hier bei GitHub nach, ob es
  eine neue Version gibt. Dabei wird nichts von dir übertragen.

### Hinweise

- Ein privates Hobbyprojekt in der Testphase, ohne Gewähr und ohne
  zugesicherten Support.
- Nicht verbunden mit Warcraft Logs oder Blizzard Entertainment. World of
  Warcraft ist eine Marke von Blizzard Entertainment.
