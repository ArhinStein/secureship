# Incident Report: Hardcoded API Key

## Summary
I accidentally committed a weather API key in config.py to my public GitHub
repo. Deleting it later didn't help because it was still in the Git history.
I removed it from the history and now load the key from a .env file.

## Timeline
- 2026-10-30, 4:54 PM: API key committed in 3377544 (file: config.py)
- 2026-10-30: key deleted from the file in 92e1e4e (PR #5), but still in history
- 2026-10-30, 8:20 PM: leak detected with gitleaks
- 2026-10-31: history rewritten with git filter-repo and force-pushed
- 2026-10-31: secrets moved to a .env file that Git ignores (PR #6, 4ead701)

## What was exposed
A weather API key starting with wx_7H.

## Impact
Someone could use the key to make requests on my account, use up my limit,
or cause charges if the plan is paid.

## Actions taken
1. Rotated the key: simulated, because the key was fake
2. Removed the key from all history with git filter-repo
3. Moved configuration to environment variables and a .env file

## Still visible after cleanup
The key could still be seen on GitHub in the old pull request (PR #5) and
old commit links. This matters because once a secret is public, deleting it
isn't enough. You have to change (rotate) the key.

## Prevention
1. Use a gitleaks pre-commit hook to block secrets before committing
2. Turn on GitHub secret scanning and push protection
3. Keep secrets in a .env file and add .env to .gitignore
