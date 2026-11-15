# GameVault — Git & GitHub Assignment

This folder contains the GameVault sample website and the Login System test-case design for the assignment PDF.

## Project files

- `index.html` — home page
- `about.html` — about page and feature description
- `styles.css` — shared page styling
- `.gitignore` — ignores `*.log` files and the `temp/` folder
- `git_commands.txt` — Git command explanations used in the workflow
- `test_cases.md` — eight login test cases and coverage summary

## Run the website

Open `index.html` in a browser. No package installation or build step is required.

## Git workflow already prepared

The local Git history has been initialized with:
1. Initial project structure
2. Home page update
3. Feature branch commit
4. Merge of `feature` into `main`
5. Git ignore rules
6. Temporary-file demonstration commit
7. Revert commit that removes `temporary.txt`
8. Assignment documentation commit

The `feature` branch is retained and pushed separately when you publish the repository.

## Push to your GitHub account

1. Create a **new empty public repository** on GitHub named `GameVault`. Do not add a README, license, or `.gitignore` on GitHub.
2. Open a terminal in this `GameVault` folder.
3. Replace `YOUR_USERNAME` below with your GitHub username and run:

```bash
git remote add origin https://github.com/YOUR_USERNAME/GameVault.git
git push -u origin main
git push -u origin feature
```

If `origin` is already configured, use `git remote set-url origin https://github.com/YOUR_USERNAME/GameVault.git` instead of `git remote add origin`.

## Verify before submission

```bash
git status
git log --oneline --graph --decorate --all
git check-ignore debug.log temp/
Test-Path temporary.txt
```

Expected: clean working tree; both `main` and `feature` visible in the graph; ignore checks identify the rules; and `Test-Path temporary.txt` returns `False` in PowerShell.

**Note:** `debug.log` and `temp/` are intentionally not included in the ZIP because they are ignored demonstration items. You can recreate them locally with:

```powershell
New-Item -ItemType Directory -Force temp
"sample log" | Out-File debug.log
git status --short
git check-ignore debug.log temp/
```
