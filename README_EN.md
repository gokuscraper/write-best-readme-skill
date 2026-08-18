<div align="center">
  <h1>🦉 write-best-readme-skill</h1>
  <p><em>An Agent Skill for writing READMEs: bilingual, one fixed skeleton, comparison table required, delivers 4 files in one pass.</em></p>
</div>

<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/中文-gray?style=flat-square" alt="中文"></a>
  <a href="README_EN.md"><img src="https://img.shields.io/badge/English-blue?style=flat-square" alt="English"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/gokuscraper/write-best-readme-skill?style=flat-square" alt="License"></a>
  <a href="https://github.com/gokuscraper/write-best-readme-skill/stargazers"><img src="https://img.shields.io/github/stars/gokuscraper/write-best-readme-skill?style=flat-square" alt="Stars"></a>
  <a href="SKILL.md"><img src="https://img.shields.io/badge/Agent_Skill-ready-8A2BE2?style=flat-square" alt="Agent Skill"></a>
  <img src="https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown" alt="Markdown">
</p>

<p align="center">
  <img src="assets/banner.png" alt="write-best-readme-skill banner">
</p>

write-best-readme-skill (skill name `readme-writer`) is a skill that AI agents like Claude Code and opencode can load. It scans real project code and produces four files in one pass — `README.md` (Chinese), `README_EN.md` (English), `.github/FUNDING.yml`, and `LICENSE` — so that **every project's README looks like it was written by the same team**: a fixed section skeleton, bilingual chapters that mirror each other, and nothing missing from "why choose it" to the comparison table to SEO keywords.

## Why write-best-readme-skill?

- **One skeleton for every project**: a fixed 12-section template (Why → Comparison → Install → Usage → How it works → Roadmap → Contributing → Support → License → SEO Keywords). No more stylistic drift between projects
- **Comparison table is mandatory**: no table, no delivery; if competitors are unclear, it asks you instead of skipping — readers instantly see how you differ from the alternatives
- **Bilingual in one pass**: `README.md` + `README_EN.md` with fully mirrored chapters and in-row language badges to switch between them; the English version is not a lazy machine translation
- **Nothing left behind at release**: banner slot reserved, FUNDING.yml and LICENSE generated upfront; if assets are missing (e.g. no banner), it explicitly says "not publishable yet" instead of pushing
- **No fabrication**: every command, feature, and number comes from the real project code or your confirmation — nothing invented, no parroting of an old README
- **Personality, not boredom**: the H1 must carry a living-creature emoji (🐹🦋🦉…), CLI projects show real terminal output, and the support section keeps a light tone
- **Agent-friendly**: SKILL.md documents the full workflow and hard rules, so any agent produces the same reliable result

## Comparison

| Capability | write-best-readme-skill | general-readme-skill | awesome-copilot readme | readme-ai |
|------|:---:|:---:|:---:|:---:|
| Form factor | Agent Skill | Agent Skill | Agent Skill | CLI tool |
| Bilingual (mirrored structure) | ✅ | ❌ | ❌ | ❌ |
| Unified section template across projects | ✅ | ❌ | ❌ | ❌ |
| Comparison table required | ✅ | ❌ | ❌ | ❌ |
| Ships FUNDING.yml + LICENSE | ✅ | ❌ | ❌ | ❌ |
| Banner slot reserved | ✅ | ❌ | ❌ | ❌ |
| Facts sourced from code (no fabrication) | ✅ | Model-dependent | ❌ (examples only) | Model-dependent |
| Price | Free OSS | Free OSS | Free OSS | Free OSS |

> Comparison is based on snapshots of each project's public page; features may change — check each repo for the latest.

## Install

```bash
# Option 1: clone the repo and use its skill directory
git clone https://github.com/gokuscraper/write-best-readme-skill.git

# Option 2: copy just the readme-writer directory into your agent's skill folder
cp -r write-best-readme-skill/readme-writer <skill directory>/
```

Common skill directories: `~/.claude/skills/` (Claude Code), `.agents/skills/` (opencode, project-level), `~/.config/opencode/skills/` (opencode, global).

## Usage

Say one of these trigger phrases to your agent: 写 README, generate project docs, polish the repo homepage, 中英文 readme, sponsorship file, open source license.

The agent runs a 4-step workflow:

1. **Scan the project**: read manifests, CLI entry points, docs, and existing files (facts come from code, not from re-reading the old README)
2. **Confirm interactively**: project name / one-liner / emoji preference, author name and year, donation platform (default `ko_fi: gokuscraper`), and comparison-table competitors
3. **Generate README.md (Chinese)**: fill in the fixed 12-section template section by section
4. **Generate the rest**: README_EN.md (mirrored translation), FUNDING.yml, LICENSE (MIT, or keep an existing one)

Deliverables:

| File | Description |
|------|------|
| `README.md` | Chinese version, fixed 12-section template, SEO keywords at the end |
| `README_EN.md` | English version, chapters fully mirrored, language badges switch inline |
| `.github/FUNDING.yml` | Sponsorship config, defaults to `ko_fi: gokuscraper` |
| `LICENSE` | MIT (generated when the project has none), or keeps the existing license |

## How it works

Fixed section template (required / optional):

```
1. Centered header (H1 with creature emoji + italic one-liner + badge row + banner slot) [required]
2. Intro paragraph                                                        [optional]
3. Why choose it? (3-6 differentiated selling points)                     [required]
4. Comparison table (feature matrix vs alternatives)                      [required]
5. Install / Quick start                                                  [required]
6. Usage (real commands + code blocks; CLI shows terminal output)         [required]
7. How it works / deep dive                                              [optional]
8. Roadmap (one-line link, only if ROADMAP.md exists)                    [optional]
9. Contributing & development                                             [required]
10. Support / donation                                                    [required]
11. License (one-line link)                                               [required]
12. SEO Keywords (italic keyword line, both languages)                    [required]
```

The core logic lives in [`SKILL.md`](SKILL.md): the workflow plus hard rules (no fabrication, creature emoji required, comparison table required, unified structure, release checklist, bilingual parity).

## Contributing & Development

Run the skill against any real project, then self-check the output against the template:

- ✅ Section order and names match the template exactly
- ✅ Comparison table exists and most claims trace back to project code
- ✅ Chinese and English chapters mirror each other
- ✅ H1 has a creature emoji; the one-liner is italic
- ✅ SEO keywords present at the bottom
- ✅ Banner slot reserved (placeholder comment)

To change the rules, edit `SKILL.md` and keep the hard-rules section in sync. PRs welcome.

## Support

If this skill helps you, you can feed my two cats some [canned food 🥩](https://ko-fi.com/gokuscraper).

## License

[MIT](LICENSE) © gokuscraper.

---

*Keywords: readme skill, generate readme, bilingual readme, github readme generator, agent skill, claude code skill, opencode skill, readme template, comparison table, open source documentation, fund.yml, license generator, 中文 readme, 英文 readme, 项目文档*