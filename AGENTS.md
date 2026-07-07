# CorelDRAWer-Skill Project

A Reasonix skill project for generating CorelDRAW-compatible geological diagrams. Describe what you want in natural language and get production-ready SVG vector graphics — or VBA macros / COM automation for direct CorelDRAW integration.

## Project

- **Purpose**: Hosts the `coreldraw-vba` Reasonix skill for AI-assisted geological diagram generation
- **Core Skill**: `coreldraw-vba` — converts natural language descriptions into stratigraphic column SVGs, VBA macros, or CorelDRAW COM drawings
- **Skill Location**: `.reasonix/skills/coreldraw-vba/SKILL.md`

## Commands

No build/test commands. The main operations are:

- `/coreldraw-vba` — invoke the drawing skill (or describe your diagram naturally in conversation)
- `python3 generate_column.py data.json output.svg --style nature` — Nature style strat column
- `python3 generate_cross_section.py data.json output.svg --style nature` — Nature style cross-section
- `python3 coreldrawer.py column|xsection data.json out.svg --style nature` — Unified CLI
- `python3 batch_fetch_nature.py dois.txt` — Batch download + extract Nature figures
- `python3 nature_figure_hunter.py search "keyword" --extract` — Search Nature papers

## Output Channels

| Channel | Command | Platform |
|---------|---------|----------|
| SVG (default) | `python3 generate_column.py data.json output.svg` | Any |
| VBA Macro | `python3 cdr_com_auto.py --vba data.json` | Any |
| COM Automation | `python3 cdr_com_auto.py --com data.json` | Windows only |

## Architecture

```
.reasonix/skills/coreldraw-vba/SKILL.md   ← Skill definition (v2.2)
generate_column.py                         ← SVG generator — stratigraphic columns (--style nature)
generate_cross_section.py                  ← SVG generator — geological cross-sections (--style nature)
cdr_com_auto.py                            ← VBA/COM generator
data_template.json                         ← Column data format template
borehole_column.bas                        ← Legacy VBA macro (reference)
batch_fetch_nature.py                      ← Nature batch PDF download + figure extraction
nature_journal_dois.txt                    ← Multi-journal Nature DOI list
nature_strat_template.svg                  ← Nature style column reference template
nature_xsec_template.svg                   ← Nature style cross-section reference template
strat_ref_figures/                         ← 107 curated stratigraphic reference images
├── FIGURES_INDEX.md                       ← Image catalog by geological topic
├── NATURE_STYLE_ANALYSIS.md              ← Cross-journal style design patterns
├── README.md
nature_figures/                            ← 736 extracted JPG figures from 158 Nature papers
papers/                                    ← 158 Nature paper PDFs (not tracked in git)
cross_section_demo.svg                     ← Example cross-section output
output.svg                                 ← Example column output
AGENTS.md                                  ← This file
README.md                                  ← English documentation
README_zh.md                               ← Chinese documentation
CHANGELOG.md                               ← Version history
CONTRIBUTING.md                            ← Contribution guide
LICENSE                                    ← MIT License
```

## Conventions

- Default output: SVG with 7 named layer groups and `data-cdr-*` attributes for CorelDRAW
- All generated code includes undo grouping (`BeginCommandGroup`/`EndCommandGroup`) and error handling
- Default units: millimeters (mm)
- Default page: A4 landscape
- Font: SimHei with Heiti SC / sans-serif fallback (Chinese-compatible)
- Coordinate system: SVG standard (origin top-left, Y-down), internally Y-up for geology
- 18 standard lithology patterns per GB/T 958
- Zero external dependencies for SVG generation

## Notes

- The `borehole_column.bas` file is a legacy 688-line VBA macro kept for reference; the `cdr_com_auto.py` VBA generator is the recommended replacement (v2.0, 11 columns)
- Fossil and structure columns are adaptive — they only appear when the input data includes them
- On macOS/Linux, COM mode automatically falls back to VBA code generation
