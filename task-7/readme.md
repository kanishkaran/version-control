# Cherry-Picking Commits Between Branches

## **Objective**  
Selectively apply a commit from one branch to another using `git cherry-pick`.

## **Requirements**  

1. **Create Two Branches with Distinct Commits**  
   - Initialize a repository and create a base branch (`master`).  
   - Create a new branch (`feature-branch`) and add distinct commits.  

2. **Identify a Commit to Cherry-Pick**  
   - Use `git log --oneline` on `feature-branch` to identify the commit hash.  

3. **Apply the Commit Using Cherry-Pick**  
   - Switch to `master` and use:  
     ```sh
     git cherry-pick <commit-hash>
     ```
   - Resolve conflicts if any arise.  

4. **Verify the Commit History**  
   - Run `git log --oneline` on `master` to confirm the commit has been applied.  

[View Commands](commands.txt)