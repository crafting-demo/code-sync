# Code Sync Tools for Crafting Sandboxes

Tools and examples for syncing code between your local machine and remote Crafting sandbox workspaces.

## What's Inside

### [cs-sync-cloud](./cs-sync-cloud/)
CS CLI extension for syncing uncommitted git changes to remote sandboxes. Perfect for quick iteration without committing work-in-progress code.

### [Examples](./examples/)

- **[mutagen](./examples/mutagen/)** - Two-way real-time sync between local and remote directories
- **[rsync](./examples/rsync/)** - One-way file/directory sync with rsync (supports all rsync flags)
- **[scp](./examples/scp/)** - Simple file copying to/from workspaces

## Quick Start

Choose the sync method that fits your workflow:

- **Git-based changes?** → Use `cs sync-cloud`
- **Real-time two-way sync?** → Use `cs mutagen`
- **One-time directory sync?** → Use `cs rsync`
- **Single file copy?** → Use `cs scp`

See individual tool directories for detailed usage and examples.

