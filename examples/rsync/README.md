# CS Rsync

Sync files and directories between your local machine and remote sandbox workspaces using rsync.

[Rsync CLI Docs](https://docs.sandboxes.cloud/docs/command-line-tool#/rsync)

## Usage

```bash
$ cs rsync LOCAL-PATH SANDBOX/WORKSPACE:REMOTE-PATH
$ cs rsync SANDBOX/WORKSPACE:REMOTE-PATH LOCAL-PATH
```

## Passing Rsync Flags

To pass flags to the underlying `rsync` command, use `--` followed by the rsync flags:

```bash
$ cs rsync LOCAL-PATH SANDBOX/WORKSPACE:REMOTE-PATH -- [RSYNC-FLAGS]
```

Common rsync flags:
- `-a` : Archive mode (recursive, preserves permissions, timestamps, etc.)
- `-r` : Recursive
- `-v` : Verbose
- `-z` : Compress during transfer

## Examples

**Sync a single file:**
```bash
cs rsync ./rsync/README.md remote-code-demo/app:remote-target/ --org demo
```

**Sync an entire directory (recursive):**
```bash
cs rsync ./rsync remote-code-demo/app:remote-target/ --org demo -- -a
```

**Sync with verbose output:**
```bash
cs rsync ./rsync remote-code-demo/app:remote-target/ --org demo -- -av
```

