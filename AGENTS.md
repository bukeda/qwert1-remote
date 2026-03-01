# Agent Instructions for GitHub Workflow

## GitHub Repository Setup & Management

### Quick Start Checklist

When working with ANY project, always follow this workflow:

1. **Check for Git repository**
   ```bash
   git status
   ```
   - If "fatal: not a git repository" → Initialize Git (see below)
   - If files shown in red/green → Git is ready

2. **Check for GitHub remote**
   ```bash
   git remote -v
   ```
   - If empty → Connect to GitHub (see below)
   - If shows origin URL → Already connected

### Setting Up GitHub for New Projects

**Step 1: Initialize Git (if needed)**
```bash
git init
git config user.name "your-name"
git config user.email "your-email@example.com"
```

**Step 2: Create GitHub Repository**
1. Go to https://github.com/new
2. Name your repo (match your project folder name)
3. Keep it empty (no README, no .gitignore)
4. Click "Create repository"
5. Copy the HTTPS URL (looks like: `https://github.com/username/repo-name.git`)

**Step 3: Connect and Push**
```bash
git remote add origin https://github.com/username/repo-name.git
git branch -m main
git add .
git commit -m "Initial commit"
git push -u origin main
```

### Best Practices for GitHub

#### 1. Commit Messages
**Good commit messages are short and descriptive.**

**Examples:**
- ✅ `Add login form validation`
- ✅ `Fix navbar alignment on mobile`
- ✅ `Update README with installation steps`
- ✅ `Refactor user authentication logic`

**Avoid:**
- ❌ `Update` (too vague)
- ❌ `Fix` (what did you fix?)
- ❌ `asd` (nonsense)
- ❌ `Changes` (redundant)

#### 2. Commit Frequency
- **Commit early, commit often** - Don't wait for perfection
- **One logical change = One commit** - Don't mix unrelated changes
- **Commit when something works** - Even if it's small

#### 3. Branching Strategy for Beginners
**Simple workflow:**
```
main branch → Always stable, deployable code
    ↓
Create feature branch → Work on new stuff
    ↓
Test it → Make sure it works
    ↓
Merge to main → Add your work to the stable code
    ↓
Push to GitHub → Backup and share
```

**When to use branches:**
- ✅ Working on a new feature
- ✅ Fixing a bug
- ✅ Experimenting with changes
- ✅ Any time you're unsure about changes

#### 4. Before You Push
Always check:
```bash
git status          # What's changed?
git diff            # What exactly changed?
git log --oneline   # What did I commit?
```

#### 5. Recovery Commands
**I messed up, help!**
```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Restore a deleted file
git restore filename

# Go back to previous version
git checkout COMMIT_ID -- filename

# See what you did
git log --oneline
git show COMMIT_ID
```

### Auto-Generated Commit Message Helper

When generating commit messages, follow this pattern:

**Format:** `<Action> <What> [optional: Why/Where]`

**Actions to use:**
- `Add` - New files/features
- `Fix` - Bug fixes
- `Update` - Changes to existing files
- `Remove` - Deleting files/features
- `Refactor` - Code restructuring (no behavior change)
- `Docs` - Documentation changes
- `Style` - Formatting, CSS, visual changes
- `Test` - Adding/updating tests

**Examples by situation:**

*Adding new files:*
- `Add user authentication module`
- `Add contact page with form`
- `Add dark mode toggle`

*Fixing bugs:*
- `Fix login redirect loop`
- `Fix mobile menu not closing`
- `Fix typo in about page`

*Updating existing code:*
- `Update navbar styling for mobile`
- `Refactor database queries for performance`
- `Update dependencies to latest versions`

*Documentation:*
- `Docs: Add API usage examples`
- `Docs: Update installation instructions`
- `README: Add project screenshots`

### Daily Workflow Summary

```bash
# 1. Start of day - get latest
git pull

# 2. Make changes to files
# ... edit your code ...

# 3. Check what changed
git status
git diff

# 4. Stage changes
git add filename        # Specific file
git add .               # All changed files

# 5. Commit with good message
git commit -m "Add feature X"

# 6. Push to GitHub
git push

# 7. Verify it worked
git log --oneline
git status
```

### Common Issues & Solutions

**Issue: "fatal: not a git repository"**
→ Run `git init` in your project folder

**Issue: "Permission denied" when pushing**
→ You need to authenticate with GitHub (browser will open)

**Issue: "rejected: non-fast-forward"**
→ Someone else pushed changes. Run `git pull` first, then `git push`

**Issue: Accidentally committed secrets/passwords**
→ Don't panic! But DO change the password immediately. Then remove the file from Git history (ask for help).

**Issue: "Your branch is ahead of origin/main by 3 commits"**
→ You have local commits not pushed yet. Run `git push` to sync.

### Remember

- **Git is your safety net** - Commit frequently
- **GitHub is your backup** - Push regularly
- **Branches are your playground** - Experiment freely
- **Commit messages are your diary** - Write clearly
- **When in doubt, commit** - You can always undo

### Quick Reference Card

```
git init              # Initialize new repo
git status            # Check current state
git add .             # Stage all changes
git commit -m "msg"   # Save changes locally
git push              # Upload to GitHub
git pull              # Download from GitHub
git log --oneline     # View history
git branch            # List branches
git checkout -b name  # Create & switch branch
git merge branch      # Combine branches
git restore file      # Undo file changes
```
