Reflection

1. What could have happened if the key was real, and how fast? Bots scan public GitHub all the time, so someone could find a real key in minutes. They could use my cloud account to run expensive servers, steal data, or delete things. I could get a huge bill before I even noticed.

2. Why rotate the secret before rewriting history? Once a key is pushed, someone may already have it. Rewriting history only cleans my repo, not the copies other people already took. Rotating the key makes the old one stop working right away, so that comes first.

3. Which Part 4 protection would have stopped the mistake earliest? The gitleaks check on pull requests. It scans for secrets and blocks the merge into main if it finds one. The other protections don't look for secrets in files.

4. What did my partner find that I missed? Don't have an answer as my partner hasn't completed his side.

5. One thing I will do differently in every project: I will never put keys in my code. I will use a .gitignore and run gitleaks before I push.
