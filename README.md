# ruby-lsp

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/claude-plugin-orange.svg)](https://docs.anthropic.com/en/docs/claude-code/plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-zircote--lsp-purple.svg)](https://github.com/zircote/lsp-marketplace)
[![Ruby](https://img.shields.io/badge/Ruby-CC342D?logo=ruby&logoColor=white)](https://www.ruby-lang.org/)

A Claude Code plugin providing comprehensive Ruby development support through:

- **ruby-lsp** (Shopify) integration for IDE-like features
- **12 automated hooks** for linting, formatting, testing, and security scanning
- **Ruby ecosystem** integration (RuboCop, RSpec, Bundler, Brakeman)

## Quick Setup

```bash
# Run the setup command (after installing the plugin)
/setup
```

Or manually:

```bash
# Install Ruby LSP
gem install ruby-lsp

# Install development tools
gem install rubocop bundler-audit brakeman
```

## Features

### LSP Integration

The plugin configures ruby-lsp for Claude Code via `.lsp.json`:

```json
{
    "ruby": {
        "command": "ruby-lsp",
        "args": [],
        "extensionToLanguage": {
            ".rb": "ruby",
            ".rake": "ruby",
            ".gemspec": "ruby"
        },
        "transport": "stdio"
    }
}
```

**Capabilities:**
- Go to definition / references
- Hover documentation
- Gem resolution
- YARD documentation
- Real-time diagnostics

### Automated Hooks

| Hook | Trigger | Description |
|------|---------|-------------|
| `ruby-syntax-check` | `**/*.rb` | Ruby syntax validation |
| `rubocop-on-edit` | `**/*.rb` | Lint and auto-fix with RuboCop |
| `brakeman-check` | `**/*.rb` | Security scanning (Rails) |
| `ruby-todo-fixme` | `**/*.rb` | Surface TODO/FIXME comments |

## Required Tools

| Tool | Installation | Purpose |
|------|--------------|---------|
| `ruby-lsp` | `gem install ruby-lsp` | LSP server |
| `rubocop` | `gem install rubocop` | Linting & formatting |
| `bundler-audit` | `gem install bundler-audit` | Dependency security |
| `brakeman` | `gem install brakeman` | Rails security |

## Project Structure

```
ruby-lsp/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── .lsp.json                  # ruby-lsp configuration
├── commands/
│   └── setup.md              # /setup command
├── hooks/
│   └── scripts/
│       └── ruby-hooks.sh
├── tests/
│   └── sample_spec.rb        # Test file
├── CLAUDE.md                  # Project instructions
└── README.md                  # This file
```

## License

MIT
