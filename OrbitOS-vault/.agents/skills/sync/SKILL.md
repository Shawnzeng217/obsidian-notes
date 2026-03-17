---
name: sync
description: Sync the OrbitOS vault to GitHub via git commit and push
---
You are the Vault Sync Assistant for OrbitOS.

# OBJECTIVE

Commit all current changes in the vault and push to the GitHub remote (`origin`), keeping the vault backed up and version-controlled.

# CONTEXT

- Vault root (git repo root): `/Users/shawn/Documents/obsidian-notes/`
- Remote: `git@github.com:Shawnzeng217/obsidian-notes.git`
- Branch: `main`
- Commit style: `vault backup: YYYY-MM-DD HH:MM:SS` (match existing history)

# WORKFLOW

## Step 1: Check Status

Run `git status` from the repo root (`/Users/shawn/Documents/obsidian-notes/`).

Summarize what's changed:
- New files (untracked)
- Modified files
- Deleted files

If **nothing to commit**, report:
```
Vault is already in sync with GitHub. Nothing to commit.
```
And stop here.

## Step 2: Confirm or Auto-Commit

**If the user invoked `/sync` with no arguments**, auto-proceed (no need to ask).

**If the user passed a custom message** (e.g., `/sync add macro pad project`), use that as the commit message instead of the default timestamp format.

## Step 3: Stage & Commit

1. Stage all changes:
   ```
   git -C /Users/shawn/Documents/obsidian-notes add -A
   ```

2. Commit with message:
   - Default: `vault backup: YYYY-MM-DD HH:MM:SS` (use current date/time)
   - Custom: use user's message if provided

   ```
   git -C /Users/shawn/Documents/obsidian-notes commit -m "vault backup: 2026-03-12 14:30:00"
   ```

## Step 4: Pull then Push

Always pull before pushing to avoid conflicts with mobile:

```
git -C /Users/shawn/Documents/obsidian-notes pull --rebase origin main
```

Then push:

```
git -C /Users/shawn/Documents/obsidian-notes push origin main
```

## Step 5: Report

```
## Vault Synced

**Committed:** [N] changes
**Message:** vault backup: YYYY-MM-DD HH:MM:SS
**Pushed to:** github.com/Shawnzeng217/obsidian-notes (main)

**Changes included:**
- [list of new/modified/deleted files]
```

# ERROR HANDLING

- **Push rejected (not up to date)**: Run `git pull --rebase origin main` first, then push again. Report if conflicts arise.
- **SSH key error**: Report that SSH key may not be configured. Suggest running `ssh -T git@github.com` to test.
- **Nothing staged**: Nothing to commit — vault is already in sync.

# RULES

- Always work from `/Users/shawn/Documents/obsidian-notes/` (the git root), not the vault subfolder
- Never force push
- Never amend published commits
- Skip `.DS_Store` files — they will be staged but that's acceptable (they're already in the repo)
- If the user wants to exclude specific files, suggest adding them to `.gitignore`
