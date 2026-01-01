# 🧠 My Skills

A curated collection of documentation optimized for AI assistants and LLMs.

Each skill is structured for easy consumption by AI coding assistants like Cursor, Claude Code, enabling them to provide accurate, up-to-date guidance. Browse the directories to see what's available.

## Skill Structure

Each skill follows a consistent format:

```
skill-name/
├── SKILL.md      # Entry point with overview and navigation
├── Articles/     # Conceptual guides and tutorials
└── ...           # Additional documentation files
```

The `SKILL.md` file serves as the index with metadata, structure, and links.

---

## 🛠️ DocC Converter

This repository includes `swift_docc_to_skill.py` — a tool to convert Apple's DocC documentation format into the skill format used here.

### Usage

```bash
python swift_docc_to_skill.py <input_docc_dir> <output_dir> [options]
```

### Examples

```bash
# Convert Swift language documentation
python swift_docc_to_skill.py TSPL.docc ./programming-swift --skill-name "programming-swift"

# Convert a library's documentation
python swift_docc_to_skill.py Documentation.docc ./my-library --skill-name "my-library"
```

### Options

| Option | Description |
|--------|-------------|
| `--skill-name` | Name for the skill (default: derived from input) |
| `--skill-description` | Description for the skill |
| `--main-doc` | Specify the main documentation file |
| `--skip-wip` | Skip work-in-progress files |
| `--strip-test-comments` | Remove test code comments |
| `--skip-assets` | Don't copy the Assets directory |
| `--dry-run` | Preview without making changes |

### What It Converts

- `<doc:PageName>` → standard markdown links
- `@Metadata`, `@Snippet`, `@Image` → removed/processed
- Double-backtick symbol links → inline code
- Term lists → bold definitions
- Generates `SKILL.md` with full documentation index