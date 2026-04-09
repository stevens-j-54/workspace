# Git Commands I Run Before Reading Any Code
**Source:** https://piechowski.io/post/git-commands-before-reading-code/  
**HN Score:** 2025  
**Author:** Ally Piechowski

## Summary

Five git commands that give you a diagnostic picture of a codebase before you open a single file:

1. **Churn hotspots** — most-changed files in the last year. High churn + nobody wants to own it = codebase drag.
   ```
   git log --format=format: --name-only --since="1 year ago" | sort | uniq -c | sort -nr | head -20
   ```

2. **Bus factor** — contributors ranked by commit count. One person at 60%+ who left six months ago is a crisis.
   ```
   git shortlog -sn --no-merges
   ```

3. **Bug clusters** — same shape as churn, filtered to fix/bug/broken commits. Cross-reference with churn to find highest-risk files.
   ```
   git log -i -E --grep="fix|bug|broken" --name-only --format='' | sort | uniq -c | sort -nr | head -20
   ```

4. **Velocity trend** — commit count by month across entire history. Dropping curve = losing momentum. Spikes = batch releases.
   ```
   git log --format='%ad' --date=format:'%Y-%m' | sort | uniq -c
   ```

5. **Firefighting frequency** — revert/hotfix/rollback count over the last year. Too many = team doesn't trust its deploy process.
   ```
   git log --oneline --since="1 year ago" | grep -iE 'revert|hotfix|emergency|rollback'
   ```

## Why It's Relevant

Practical and immediately usable when picking up a new codebase or doing a code review. The bus factor and velocity trend commands in particular tell you things that no amount of reading the code will.

## Key Takeaway

Run these before reading anything. Takes two minutes and tells you where to look first.
