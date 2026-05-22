# fpdev-registry

Official resource registry for [fpdev](https://github.com/dtamade/fpdev) — the Free Pascal development environment manager.

## What is this?

This repository is the single source of truth for all fpdev resource metadata:
- FPC compiler versions and download URLs
- Bootstrap compiler locations and hashes
- Lazarus IDE version information
- Cross-compilation target definitions
- Package registry (community libraries)
- Build step templates

## Usage

fpdev uses this repository automatically. To configure:

```bash
# Default (already configured)
fpdev source list

# Add a custom mirror
fpdev source add mymirror https://my-git-server.com/fpdev-registry.git

# Sync latest data
fpdev source sync
```

## Structure

```
├── index.json              # Schema version and metadata
├── sources.json            # FPC/Lazarus git source mirrors
├── fpc/
│   ├── versions.json       # FPC version → git ref mapping
│   └── binary.json         # Pre-built FPC binary downloads
├── lazarus/
│   └── versions.json       # Lazarus version information
├── bootstrap/
│   └── compilers.json      # Bootstrap compiler downloads + SHA256
├── cross/
│   └── targets.json        # Cross-compilation target definitions
├── packages/
│   └── index.json          # Package registry
└── build-steps/
    └── *.json              # Build step templates
```

## Contributing

To add a package, edit `packages/index.json` and submit a pull request.

Verify your changes: `fpdev registry verify`

## License

MIT
