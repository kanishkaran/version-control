# **Git Workflow: Forced Pushes and Recovery**

## **Introduction**
This documentation provides a step-by-step guide on handling forced pushes in Git, recovering lost commits using `git reflog`, and best practices for working in a collaborative environment.

## **1. Initializing the Repository and Setting Up Branches**

To start, initialize a Git repository and create the necessary branches.

```sh
git init versioncontrol
cd versioncontrol
git checkout -b master
echo "Initial commit" > file.txt
git add file.txt
git commit -m "Initial commit for task 10"
git push origin master  
```

Create a feature branch for task-10:

```sh
git checkout -b task-10
echo "Feature work for task 10" >> file.txt
git commit -am "Add feature work for task 10"
git push origin task-10
```

## **2. Simulating a Forced Push Scenario**

Rewriting history using an interactive rebase:

```sh
git checkout task-10
git rebase -i HEAD~2  # Rewriting last 2 commits
```

After making changes, force push the branch:

```sh
git push --force origin task-10
```

This can cause issues if someone else has already pulled the previous commits.

## **3. Recovering Lost Commits Using `git reflog`**

If a forced push removes important commits, you can recover them using `git reflog`.

### **1. View the Reflog to Find Lost Commits**

Run the following command to see the history of HEAD movements:

```sh
git reflog
```

This will display a list of commit hashes and their associated actions.
Identify the commit you need to recover.

### **2. Checkout the Lost Commit**

Once you have the correct commit hash, use this command:

```sh
git checkout 7efcf3d
```

This will put you in a detached HEAD state, allowing you to view the lost commit.

### **3. Create a New Branch to Save the Lost Commit**

To permanently restore the commit, create a new branch from it:

```sh
git branch recovered-commit
git checkout recovered-commit
```

### **4. Push the Restored Commit to Remote**

To ensure the commit is safely stored in the remote repository, push it:

```sh
git push origin recovered-task-10
```

## **4. Best Practices for Forced Pushes in Teams**

- **Avoid force pushes on shared branches** (e.g., `master`).
- **Use `git push --force-with-lease`** instead of `--force` to prevent overwriting others' changes.
- **Communicate with the team** before rewriting history.
- **Use feature branches** to limit the impact of force pushes.

## **Conclusion**

Forced pushes can be dangerous, but with proper handling using `git reflog`, lost commits can be recovered. Always follow best practices to avoid disrupting collaborative workflows.