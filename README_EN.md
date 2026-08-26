<div align="center">

[简体中文](README.md) · [English](README_EN.md)

# 🎲 dnd-replay

### D&D Campaign Replay & Chronicle Skill

Turn messy session transcripts into a campaign chronicle that remembers.

[![Codex Skill](https://img.shields.io/badge/Codex-Skill-111827?style=flat-square)](https://github.com/openai/codex)
[![skills.sh](https://img.shields.io/badge/skills.sh-install-7c3aed?style=flat-square)](https://skills.sh/yuzilan/dnd-replay/dnd-replay)
[![GitHub Stars](https://img.shields.io/github/stars/yuzilan/dnd-replay?style=flat-square)](https://github.com/yuzilan/dnd-replay/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-7c3aed?style=flat-square)](LICENSE)

**Transcript → Adventure Reconstruction → Session Report → Campaign State → Persistent Chronicle**

</div>

![dnd-replay — Transcript to Persistent Campaign Chronicle](assets/social-preview.png)

---

`dnd-replay` reconstructs what your table actually experienced from transcripts, chat logs, combat logs, and player notes. Across later sessions, it keeps track of PCs, NPCs, items, quests, clues, theories, and unresolved mysteries.

> **Record the adventure your players actually experienced—never invent a plausible story to fill the gaps.**

## Highlights

| | Capability | | Capability |
| --- | --- | --- | --- |
| 🎭 | Mixed-speaker transcript analysis | 📚 | Persistent campaign continuity |
| ⚔️ | Story, combat, and resource reconstruction | 🧩 | Facts, theories, and mysteries kept separate |
| 🧙 | Character sections based on the actual party | 🔗 | Cross-session NPC, item, and location tracking |
| 🛡️ | No fabricated missing events | 📄 | Mandatory Markdown + optional exports |

## Install

```bash
npx skills add yuzilan/dnd-replay -g -a codex
```

Then invoke `$dnd-replay` in a new task.

<details>
<summary>Other installation methods</summary>

Ask Codex:

```text
$skill-installer Install the root skill from https://github.com/yuzilan/dnd-replay and name it dnd-replay.
```

Or clone it directly:

```bash
git clone https://github.com/yuzilan/dnd-replay.git ~/.codex/skills/dnd-replay
```

</details>

## Quick Start

Provide a `.txt` or `.md` transcript plus the campaign basics:

```text
$dnd-replay

Campaign: Tomb of Annihilation
Type: Long campaign
Progress: Session 1
Characters: player | character | ancestry | class | level
Optional export: PDF

Process the attached transcript.txt, create the Campaign Profile,
write the Session 1 chronicle, and initialize the Campaign Ledger.
```

The skill asks only for missing information that materially affects the result.

## What You Can Provide

- Meeting or voice transcripts, Discord chat logs
- Combat logs, VTT exports, and dice records
- Character sheets, player notes, and DM notes
- Module summaries and terminology references
- Previous reports or an existing Campaign Ledger

Audio should be transcribed first. Module material may clarify background and terminology, but is never treated as an event the party has already experienced.

## Campaign Workspace

Keep source material with the campaign, not inside the installed skill:

```text
dnd-campaigns/<campaign>/
├── campaign-profile.md
├── campaign-ledger.md
├── sources/
│   └── session-001/
│       ├── transcript.txt
│       ├── combat-log.txt
│       └── player-notes.md
├── sessions/
│   └── session-001.md
└── exports/
    ├── session-001.docx
    └── session-001.pdf
```

You can also upload files directly or give Codex their existing paths.

## Output

Every full session chronicle includes:

1. Story Recap
2. Character Highlights
3. Combat Log
4. Loot & Finances
5. NPC Relationship Changes
6. Known Clues
7. Unresolved Mysteries
8. Memorable Moments

It also includes an end-of-session party status summary. Long campaigns update a separate Campaign Ledger.

### Markdown Is Mandatory

Whenever the skill writes a session report, it always creates a Markdown source file. Markdown is the canonical, most reliable format for fact checking, maintenance, history queries, and future conversion.

Word, PDF, and TXT are optional additional exports. Even if you ask for “PDF only,” the Markdown source is still preserved.

### Convert Locally to Save Tokens

If you do not need a polished export immediately, generate Markdown only and convert it locally later. This avoids additional model-driven formatting and visual QA work.

```bash
pandoc session-001.md -o session-001.docx
```

For PDF—especially with CJK fonts—using your Markdown editor’s **Export PDF** or **Print to PDF** command is often the most reliable option. Ask for `Optional export: PDF` or `Optional export: Word + PDF` when you want the skill to create and verify those files.

## Language Behavior

One repository and one `dnd-replay` skill support both Chinese and English campaigns. The output language follows this priority:

1. The user’s explicit language choice
2. The language of the current request
3. The transcript’s dominant language

The chosen campaign language is stored in the Campaign Profile for continuity. English transcripts use natural English headings and prose; they are not translated into Chinese before analysis. Important quotes remain in their source language unless a translation is explicitly requested.

## Real Example

The repository includes a user-authorized Chinese *Tomb of Annihilation* example:

- [`session-01-transcript.txt`](examples/tomb-of-annihilation/session-01-transcript.txt) — raw meeting transcript with one mixed speaker label
- [`session-001-report.md`](examples/tomb-of-annihilation/session-001-report.md) — reconstructed session chronicle
- [`campaign-ledger.md`](examples/tomb-of-annihilation/campaign-ledger.md) — persistent state after Session 1

## Trust Model

```text
Actual session record
  > Explicit user clarification
  > Existing campaign history
  > Module reference material
  > General D&D knowledge
  > Model inference
```

Confirmed facts, player theories, uncertain material, and module background remain clearly separated. Missing speakers, dice results, NPCs, decisions, rewards, and item ownership are never invented.

## License

[MIT](LICENSE) © 2026 yuzilan
