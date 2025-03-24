# **Git Pre-Commit Hook for Blocking "bug" Files**

This repository includes a **Git pre-commit hook** that prevents committing files named **"bug"** with any extension (e.g., `bug.py`, `bug.txt`, `bug.js`).

## **Setup Instructions**


 **Script to `pre-commit`**  

   ```bash
   #!/bin/bash

   echo "Checking for files named 'bug' with any extension before commit..."

   # Get a list of staged files
   FILES=$(git diff --cached --name-only)

   # Check if any file matches "bug.*"
   for FILE in $FILES; do
       if [[ "$(basename "$FILE")" =~ ^bug\..* ]]; then
           echo "Error: A file named 'bug' (e.g., bug.py, bug.txt) is staged for commit. Remove or rename it before committing."
           exit 1
       fi
   done

   echo "No 'bug' file found. Proceeding with commit."
   ```

4. **Verify the Hook**  
   - Try adding a file named `bug.py` or `bug.txt`:  
     ```bash
     touch bug.py bug.txt
     git add bug.py bug.txt
     git commit -m "Testing hook"
     ```
   - The commit should be **blocked** with an error message.

## **How It Works**
- The hook scans the staged files before each commit.
- If a file named `bug.*` (e.g., `bug.py`, `bug.txt`) is found, the commit is **aborted**.
- This helps prevent mistakenly committing placeholder or problematic files.

## **Why Use Git Hooks?**
- **Enforces project rules** automatically.
- **Prevents bad commits** from being pushed.
- **Improves team workflow** by catching issues early.

---