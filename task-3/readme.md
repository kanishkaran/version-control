# README: Undoing Changes and Reverting Commits in Git

## Objective  
This document provides an overview of undoing changes in a Git repository, including restoring modified files, undoing commits, and safely reverting changes.

## Requirements  
The goal is to experiment with the following Git commands:  
- Undoing changes in the working directory using `git restore` or `git checkout <file>`.  
- Committing changes and then using `git revert` or `git reset` to undo commits safely.  
- Understanding the differences between these approaches.

## Key Concepts  

### 1. Undoing Changes in a Tracked File  
- Use `git restore <file>` or `git checkout <file>` to discard uncommitted changes and restore the file to its last committed state.  
- If changes have already been staged, use `git restore --staged <file>` to unstage them.

### 2. Undoing a Commit Safely  
- `git revert <commit>` creates a new commit that reverses the effects of a specific commit while preserving history.  
- `git reset` moves the branch pointer to a previous commit and can modify or delete changes depending on the reset mode.  

### 3. Difference Between `git revert` and `git reset`  
- `git revert` is **safe for shared repositories** because it does not rewrite history but instead records a new commit.  
- `git reset` **rewrites history**, making it **dangerous** for shared repositories but useful for local fixes.  

## Summary  
This experiment explores different Git commands for undoing changes, committing modifications, and rolling back updates while maintaining a clean and efficient workflow.

[View Commands](commands.txt)
