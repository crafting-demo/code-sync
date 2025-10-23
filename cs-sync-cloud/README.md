# cs-sync-cloud

A tool for syncing your local code changes to a remote Crafting sandbox in the cloud.

## What Does It Do?

Think of this as a "quick save" button for your code. When you're working on code locally and want to test it in a cloud sandbox environment, this script instantly transfers your changes without needing to commit them to git or go through a normal push/pull workflow.

## How It Works

### 1. **Finds Your Code**
The script looks at your current directory's git repository and figures out:
- Where your code lives locally
- Which remote sandbox you want to sync to
- Where that same repository is located in the sandbox

### 2. **Backs Up Remote Work**
If you've made changes in the remote sandbox, the script automatically:
- Creates a backup branch with a timestamp (e.g., `crafting/backup/20251023120000`)
- Saves all your remote changes there
- Provides instructions on how to restore them if needed

### 3. **Syncs Your Changes**
The script transfers your local changes using two methods:
- **Modified files**: Creates a "diff" (only the changes) and applies it remotely
- **New files**: Packages them up and sends them over

This is much faster than copying entire files because it only sends what actually changed.

### 4. **Updates Remote Branch**
Your changes appear on a timestamped branch in the remote sandbox (e.g., `crafting/sync/20251023120000`), and the remote workspace automatically switches to that branch.

## Installation

Install this as a CS CLI extension:

```bash
cs extensions install https://github.com/crafting-demo/code-sync.git --subdir cs-sync-cloud
```

This will make the `sync-cloud` command available through the `cs` CLI.

## When to Use It

- You're developing code locally but need to test it in a cloud environment
- You want to quickly see how your changes work in the actual sandbox
- You don't want to commit "work in progress" code to git
- You need to iterate quickly between local edits and remote testing

## How to Use It

Run from within your git repository:

```bash
cs sync-cloud
```

The command will:
- Prompt you to select a target sandbox (unless `CRAFTING_SANDBOX_WORKSPACE` is set)
- Automatically sync all your uncommitted changes
- Show you what's happening along the way

## Requirements

- Must be run from inside a git repository
- The repository must have an `origin` remote configured
- The target sandbox must have a matching git checkout
- The `cs` CLI tool must be installed and configured

## Technical Details

- **Language**: Zsh script
- **Transfer method**: Git patches for diffs, tar streaming for new files
- **Connection**: Uses `cs ssh` to communicate with the sandbox
- **Safety**: Always backs up remote changes before syncing

