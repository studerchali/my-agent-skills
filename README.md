# my-agent-skills

Personal collection of **Agent Skills** for Grok Build, Cursor, Claude Code and other AI coding agents.

## Structure

```
my-agent-skills/
├── notion-idea-expander/     # Custom: expands ideas/conversations into rich Notion educational pages
├── csv-portfolio-cleaner/    # Custom: cleans IBKR CSV exports for EcoPort / Grok analysis
└── (future skills...)
```

## How to use

### Install into Grok Build (recommended)

```bash
# Clone into your home
git clone https://github.com/studerchali/my-agent-skills.git ~/my-agent-skills

# Symlink the skills you want into the global Grok skills folder
mkdir -p ~/.grok/skills
ln -sf ~/my-agent-skills/notion-idea-expander ~/.grok/skills/
ln -sf ~/my-agent-skills/csv-portfolio-cleaner ~/.grok/skills/
```

Or simply copy them:

```bash
cp -R ~/my-agent-skills/notion-idea-expander ~/.grok/skills/
cp -R ~/my-agent-skills/csv-portfolio-cleaner ~/.grok/skills/
```

### Using the skills CLI (skills.sh)

```bash
npx skills add studerchali/my-agent-skills
```

## Custom Skills

| Skill | Description | Trigger |
|-------|-------------|---------|
| **notion-idea-expander** | Expands conversations or Notion pages into structured educational pages under Personal Home → Conversaciones | `#Exp`, "expande esto en Notion"... |
| **csv-portfolio-cleaner** | Cleans Interactive Brokers CSVs (Activity Statement + Flex Query), anonymizes, enriches with metrics for EcoPort | `#LimpiaCSV` or when providing portfolio CSV |

## Philosophy

- **Custom skills** live here and are version-controlled.
- **Popular community skills** are installed separately via `npx skills add ...` into `~/.grok/skills/`.
- Global skills go in `~/.grok/skills/`.
- Project-specific skills go in `project/.grok/skills/`.

## Author

Victor Studer (@studerchali) — Valencia, Spain
