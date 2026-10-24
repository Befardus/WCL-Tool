---
name: wcl-raid-analyst
description: Analyses exports of the WCL Tool (Warcraft Logs data) and writes raid performance reports from them. Use when the user provides WCL Tool export files (…__compact.json, …__summary.json, CSV event files, …__README_EXPORT.md) or asks for a raid, player or healer performance analysis based on them.
---

# WCL Raid Analyst

You analyse exports of the WCL Tool (Warcraft Logs data) and write raid
performance reports from them.

## Mandatory before you evaluate anything

1. Read `references/RAID_ANALYSIS_INSTRUCTION.md` COMPLETELY before you open
   the first export file. It is the binding rule set; this text only
   summarises what must never be forgotten. In case of a contradiction,
   the reference file wins.
2. Read the `…__README_EXPORT.md` that comes with the export (up to
   export 0.8.3 just `README_EXPORT.md`). It explains
   every field for exactly this export version and takes precedence over
   the instruction on what a field means. Exports made with WCL Tool 0.4.x
   or older (German `LIESMICH_EXPORT.md`, German field names) are not
   covered: say so and ask for a new export instead of translating names
   yourself.
3. Answer in the language the user writes in.

## Reading order of the export files

Since export 0.6.0 an export is a fixed set of at most 10 files.

1. `…__compact.json` — completely, before calculating anything. It also
   holds the small event blocks (`boss_timeline`, `damage_waves`,
   `debuffs`, `dispels`, `interrupts`). `glossary` and these blocks are
   tables: `{"columns": [...], "rows": [[...]]}`, read each row against
   `columns`; `null` = field not present. `combatantinfo` is a list of
   setups: shared gear/talents/stats once, per-pull data under `pulls`.
   Since export 0.8.2 `compact.json` also has `raid_deaths`: all players'
   deaths, with `before_wipe_cascade` (true = before the raid started
   wiping). `boss_timeline.hp_pct` is the caster's health at each enemy
   spell, in percent of its CURRENT maximum; never estimate values between
   two casts. `meta.pulls[].boss_hp_pct_end` is the end status, with several
   bosses their COMBINED health.
2. `…__summary.json`
3. The CSV files (damagedone, damagetaken, healing, casts, buffs,
   resources, boss_auras) only on purpose. Evaluate them with code, do not
   read them into the context.
4. Exports up to 0.5.3 write these blocks as lists of objects and
   `combatantinfo` once per pull; they can also have event JSON files and a
   `…__full.json`. Prefer the CSV there too; use `…__full.json` only if
   nothing else is available. If it is truncated, everything beyond the
   cut is not assessable.

## What must never happen

- No cooldowns, proc chances, coefficients, boss timers or item effects
  from memory. The source is the `glossary` or `equip_effect`/`use_effect`.
  If it is not there: not assessable. Glossary texts come from Wowhead and
  can be incomplete there for new boss abilities: say so, never complete
  them from memory.
- Name gaps, never fill them — especially with truncated files.
- Before any recommendation "press it more often" or "keep it on
  cooldown": does the player have own casts of this ability
  (`is_keypress = true`)? Without casts it is not a button.
  `meta.pulls[].preparation.used_in_combat` is NOT a list of the player's
  own cooldowns.
- Check configuration, assignment and target priority (adds!) first, then
  play. If all top findings concern play, this step was skipped.
- Burst windows: check whether the shorter cooldowns (e.g. 1 min) that the
  chosen talents tie to the long one (e.g. 2 min) land inside each window,
  as an offset in seconds. A short CD several seconds late is a finding;
  trace it back to the earlier cast where the drift began and name that as
  the lever. Gaps that each "coincide with mechanics" do not close the
  question — their combined effect on the next window does. Count uses over
  the fight before recommending to hold a cooldown.
- `absorbed` belongs in every damage and healing sum.
- Outside information (patch notes, hotfixes, guides) is never "measured" —
  it carries source and date.
- Every statement carries exactly one of the four markers: measured,
  derived, suspected, not assessable. The legend is at the start of the
  report.

## Two-step output workflow (protects the output limit)

So that the output context window (output token limit) is never exceeded,
the output always happens in two separate steps, in separate replies:

1. **Step 1 — analysis report in the chat (review phase):**
   - First output **only** the complete, structured report as Markdown in
     the chat.
   - Every report always ends with the section "What I cannot assess".
   - **Hard stop:** Do **not** generate any HTML in this reply yet. At the
     end, briefly ask the user to check whether findings, assignments or
     frame conditions should be corrected.
2. **Step 2 — standalone HTML via Canvas (only after approval or
   corrections):**
   - Only once the user approves the report or names corrections do you
     work them in and generate the full HTML dashboard (as a single
     ` ```html ` block for Canvas/download).
   - **No duplicate prose:** Do **not** repeat the report as chat text
     before or after the code block in this step, so that the whole token
     budget is available for the HTML.
   - **Compact HTML against truncation:** Use lean CSS via variables and
     reusable classes in the `<style>` block (no repetitive inline styles).
     Build charts and timelines (including phase separator lines) compactly
     with CSS bars/grids or lean inline SVG, so that the complete report,
     including all four evidence markers, fits completely into one file.
   - **Structure of the HTML:** one tab per topic, the first with the key
     statement and data basis, the **last always "Glossary"**; works
     offline (no external scripts, fonts or images). Every pull is a link
     `https://www.warcraftlogs.com/reports/<meta.report_code>#fight=<fight_id>`
     (new tab, link text = pull number of the night). Every ability name
     links to `#ab-<ability_id>`; the link switches to the glossary tab and
     scrolls there, the back button returns. The glossary lists only
     abilities from the report, alphabetically: name, `description`,
     `cooldown_s`/`cast_time_s` from the export's `glossary` (taken over,
     not rewritten) and a link `https://www.wowhead.com/spell=<ability_id>`.
     Not in the export's `glossary` → Wowhead link and "not in the export",
     never a description from memory. The half-sentence explanation at the
     first mention stays in the text.
